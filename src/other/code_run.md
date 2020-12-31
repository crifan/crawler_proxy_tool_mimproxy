# 代码调用

* **背景需求**

Mac中想要用Python代码去控制`mitmdump`，即可以启动和停止`mitmdump`

问题就转化为，Mac中如何写Python代码，能够检测到mitmdump的进程状态，如何解析具体信息，如何杀死对应，mitmdump进程等过程。

* **最后代码**

```python
def stopExistingMitmproxy(curDevId):
    logging.info("curDevId=%s", curDevId)
    curDevIdInt = int(curDevId)
    isCheckCmdRunOk, mitmdumpInfoList = checkMitmdumpStatus()
    logging.info("isCheckCmdRunOk=%s, mitmdumpInfoList=%s", isCheckCmdRunOk, mitmdumpInfoList)
    isRunning = bool(mitmdumpInfoList)
    logging.info("isRunning=%s", isRunning)

    if isCheckCmdRunOk and isRunning:
        foundExistedDevId = False
        existedPid = None

        for eachMitmdumpInfo in mitmdumpInfoList:
            eachDevId = eachMitmdumpInfo["devId"]
            if eachDevId == curDevIdInt:
                foundExistedDevId = True
                existedPid = eachMitmdumpInfo["pid"]
                break

        if foundExistedDevId:
            killOK, errCode = utils.killProcess(existedPid)
            logging.info("killOK=%s, errCode=%s", killOK, errCode)

def debugStartProxy():
    stopExistingMitmproxy(gCurDevId)

    taskFileFullPath = "/Users/limao/dev/xxx/crawler/appAutoCrawler/AppCrawler/task/191115_card_DongKaKongJian/191115_card_DongKaKongJian_wexin.txt"
    taskId = "5e9552d1c5c2eb3ccdf777bc"
    startTaskProxy(taskId, gCurDevId, taskFileFullPath)

    time.sleep(2)

    isCheckCmdRunOk, mitmdumpInfoList = checkMitmdumpStatus()
    logging.info("isCheckCmdRunOk=%s, mitmdumpInfoList=%s", isCheckCmdRunOk, mitmdumpInfoList)

def checkMitmdumpStatus():
    # check mitmdump is indeed running
    isCheckCmdRunOk, mitmdumpInfoList = False, []
    checkMitmdumpCmd = "ps aux | grep mitmdump"
    isCheckCmdRunOk, cmdResult = utils.getCommandOutput(checkMitmdumpCmd)
    logging.info("isCheckCmdRunOk=%s, cmdResult=%s", isCheckCmdRunOk, cmdResult)
    if isCheckCmdRunOk:
        # resultList = cmdResult.split("\n")
        resultList = cmdResult.split(os.linesep)
        logging.info("resultList=%s", resultList)
        # limao            56562   0.0  0.0  4267948    664 s006  R+    5:53下午   0:00.00 grep mitmdump
        # limao            56560   0.0  0.0  4268636   1112 s006  S+    5:53下午   0:00.00 /bin/sh -c ps aux | grep mitmdump
        # limao            55396   0.0  0.1  4381268  11568 s011  S+    5:19下午   0:05.04 /Users/limao/.pyenv/versions/3.8.0/Python.framework/Versions/3.8/Resources/Python.app/Contents/MacOS/Python /Users/limao/.pyenv/versions/3.8.0/bin/mitmdump -p 8081 -s middleware/Save1.py
        if resultList:
            for eachLine in resultList:
                logging.info("eachLine=%s", eachLine)
                mitmdumpP = "^\s*(?P<username>\w+)\s+(?P<pid>\d+)\s+.+?mitmdump\s+-p\s+(?P<port>\d+)\s+-s\s+(?P<scriptFile>middleware/Save(?P<devId>\d+)\.py)\s*$"
                foundMitmdump = re.search(mitmdumpP, eachLine)
                logging.info("foundMitmdump=%s", foundMitmdump)
                if foundMitmdump:
                    username = foundMitmdump.group("username")
                    pid = foundMitmdump.group("pid")
                    port = foundMitmdump.group("port")
                    devId = foundMitmdump.group("devId")
                    scriptFile = foundMitmdump.group("scriptFile")
                    logging.info("username=%s, pid=%s, port=%s, scriptFile=%s, devId=%s", username, pid, port, scriptFile, devId)
                    curMitmdumpDict = {
                        "username": username,
                        "pid": int(pid),
                        "port": int(port),
                        "scriptFile": scriptFile,
                        "devId": int(devId),
                    }
                    mitmdumpInfoList.append(curMitmdumpDict)
    logging.info("mitmdumpInfoList=%s", mitmdumpInfoList)
    return isCheckCmdRunOk, mitmdumpInfoList

def killProcess(pid):
    """Kill process by pid

    Args:
        pid (id): process ID
    Returns:
    Raises:
    """
    isKillOk, errCode = False, 0
    pidInt = int(pid)
    killCmd = "kill -9 %s" % pidInt
    returnCode = os.system(killCmd)
    logging.debug("Command: %s -> returnCode=%s", killCmd, returnCode)
    RETURN_CODE_OK = 0
    if returnCode == RETURN_CODE_OK:
        isKillOk = True
    else:
        errCode = returnCode
    return isKillOk, errCode
```


基本完成了想要的功能：

* 在启动任务前，启动mitmproxy
* 如果之前已有当前设备id的mitmdump在运行，就kill掉
  * 因为很可能是之前的旧的task的对应的代理，所以要关闭掉，再重新启动，才能传递当前task的data文件
* 然后再去启动mitmproxy，之后再去检测看看是否的确已启动

## 后续优化版本

```python

MitmdumpPortBase = 8080
curDevId = 1
RunProxyShellFilename = "runProxy.sh"


def generateShellFile(fileContentStr, shellFilename, taskId=None):
    """Generate shell file, which is used to run command
        such as
            mitmdump proxy
            crawlerStart.py
            USB port forward
            wda server(xcodebuild/XCode)
    """
    logging.debug("fileContentStr=%s, shellFilename=%s, taskId=%s", fileContentStr, shellFilename, taskId)
    if taskId:
        shellFolder = getTaskShellFolder(taskId)
        # /Users/limao/dev/xxx/crawler/appAutoCrawler/AppCrawler/platformIntegration/output/tasks/5e9552d1c5c2eb3ccdf777bc/shell
    else:
        shellFolder = OutputRootFolder
    logging.debug("shellFolder=%s", shellFolder)
    shellFullPath = os.path.join(shellFolder, shellFilename)
    logging.debug("shellFullPath=%s", shellFullPath)
    # /Users/limao/dev/xxx/crawler/appAutoCrawler/AppCrawler/platformIntegration/output/tasks/5e9552d1c5c2eb3ccdf777bc/shell/runProxy.sh
    shellAbsFullPath = os.path.abspath(shellFullPath)
    logging.debug("shellAbsFullPath=%s", shellAbsFullPath)
    respShellFullPath = shellAbsFullPath
    utils.saveTextToFile(respShellFullPath, fileContentStr)
    utils.chmodAddX(shellFullPath, isOnlySelf=False)
    # utils.chmodAddX(respShellFullPath)
    logging.debug("respShellFullPath=%s", respShellFullPath)
    # /Users/limao/dev/xxx/crawler/appAutoCrawler/AppCrawler/platformIntegration/output/tasks/5e9552d1c5c2eb3ccdf777bc/shell/runProxy.sh
    return respShellFullPath

#---------- generate start service command ----------

def generateMitmproxyStartCommand(curDevId):
    curMitmdumpPort = MitmdumpPortBase + int(curDevId)
    # mitmproxyStartCommand = "mitmdump -p %d -s middleware/Save%d.py" % (curMitmdumpPort, curDevId)
    mitmproxyStartCommand = "mitmdump -k -p %d -s middleware/Save%d.py" % (curMitmdumpPort, curDevId)
    logging.debug("mitmproxyStartCommand=%s", mitmproxyStartCommand)
    # mitmdump -k -p 8081 -s middleware/Save1.py
    mitmproxyCommandList = [
        # "cd /Users/limao/dev/xxx/crawler/appAutoCrawler/AppCrawler",
        "cd %s" % AppCralwerFolder,
        "pwd",
        mitmproxyStartCommand,
    ]
    logging.debug("mitmproxyCommandList=%s", mitmproxyCommandList)
    # ['cd /Users/limao/dev/xxx/crawler/appAutoCrawler/AppCrawler', 'pwd', 'mitmdump -k -p 8081 -s middleware/Save1.py']
    # mitmproxyCommandStr = ";".join(mitmproxyCommandList)
    # mitmproxyCommandStr = "; ".join(mitmproxyCommandList)
    mitmproxyCommandStr = "\n".join(mitmproxyCommandList)
    # cd /Users/limao/dev/xxx/crawler/appAutoCrawler/AppCrawler
    # pwd
    # mitmdump -k -p 8081 -s middleware/Save1.py
    logging.debug("mitmproxyCommandStr=%s", mitmproxyCommandStr)
    return mitmproxyCommandStr

#---------- generate shell file ----------

def generateRunProxyShell(devId, taskId):
    mitmproxyCmdStr = generateMitmproxyStartCommand(devId)
    logging.debug("mitmproxyCmdStr=%s", mitmproxyCmdStr)
    return generateShellFile(mitmproxyCmdStr, RunProxyShellFilename, taskId)

#---------- detect service status ----------

def detectMitmdumpStatus():
    # crifanli 9428 0.0 0.6 4341956 19792 s006 S+ 9:16上午 0:23.78 /Users/crifanli/.pyenv/versions/3.8.3/bin/python3.8 /Users/crifanli/.pyenv/versions/3.8.3/bin/mitmdump -k -p 8081 -s middleware/Save1.py
    # crifanli 10982 0.0 0.0 4268032 776 s005 S+ 1:51下午 0:00.00 grep mitmdump
    # crifanli 10980 0.0 0.0 4278852 1116 s005 S+ 1:51下午 0:00.01 /bin/sh -c ps aux | grep mitmdump
    # mitmdumpP = "^\s*(?P<username>\w+)\s+(?P<pid>\d+)\s+.+?mitmdump\s+-p\s+(?P<port>\d+)\s+-s\s+(?P<scriptFile>middleware/Save(?P<devId>\d+)\.py)\s*$"
    mitmdumpP = "^\s*(?P<username>\w+)\s+(?P<pid>\d+)\s+.+?mitmdump\s+(-k\s+)?-p\s+(?P<port>\d+)\s+-s\s+(?P<scriptFile>middleware/Save(?P<devId>\d+)\.py)\s*$"
    return utils.grepProcessStatus("mitmdump", mitmdumpP)

def startTaskProxy(devId, taskId):
    logging.info("Start proxy for: devId=%s, taskId=%s", devId, taskId)
    proxyShellFile = generateRunProxyShell(devId, taskId)
    logging.debug("proxyShellFile=%s", proxyShellFile)
    utils.launchTerminalRunShellCommand(proxyShellFile)

#---------- makesure service running ----------

def makesureProxyingRunning(devId, taskId):
    def checkProxyStatus():
        isCheckOk, isRunning, infoList = detectMitmdumpStatus()
        return isCheckOk and isRunning

    def startCurTaskProxy():
        startTaskProxy(devId, taskId)

    makesureServiceRunning(checkProxyStatus, startCurTaskProxy, "Proxy")

```

相关的：

`other/common/libs/utils.py`

```python
import re


#-------------------------------------------------------------------------------
# Process
#-------------------------------------------------------------------------------

def runCommand(consoleCommand):
    """run command using subprocess call"""
    isRunCmdOk = False
    errMsg = "Unknown Error"

    try:
        resultCode = subprocess.check_call(consoleCommand, shell=True)
        if resultCode == 0:
            isRunCmdOk = True
            errMsg = ""
        else:
            isRunCmdOk = False
            errMsg = "%s return code %s" % (consoleCommand, resultCode)
    except subprocess.CalledProcessError as callProcessErr:
        isRunCmdOk = False
        errMsg = str(callProcessErr)
        # "Command 'ffmpeg -y -i /Users/crifan/.../debug/extractAudio/show_112233_video.mp4 -ss 00:00:05.359 -to 00:00:06.763 -b:a 128k /.../show_112233_video_000005359_000006763.mp3 2> /dev/null' returned non-zero exit status 1."

    return isRunCmdOk, errMsg


def getCommandOutput(consoleCommand, consoleOutputEncoding="utf-8"):
    """
        get command output from terminal
    """
    # print("getCommandOutput: consoleCommand=%s" % consoleCommand)
    isRunCmdOk = False
    consoleOutput = ""
    try:
        # consoleOutputByte = subprocess.check_output(consoleCommand)

        consoleOutputByte = subprocess.check_output(consoleCommand, shell=True)

        # commandPartList = consoleCommand.split(" ")
        # print("commandPartList=%s" % commandPartList)
        # consoleOutputByte = subprocess.check_output(commandPartList)
        # print("type(consoleOutputByte)=%s" % type(consoleOutputByte)) # <class 'bytes'>
        # print("consoleOutputByte=%s" % consoleOutputByte) # b'640x360\n'

        consoleOutput = consoleOutputByte.decode(consoleOutputEncoding) # '640x360\n'
        consoleOutput = consoleOutput.strip() # '640x360'
        isRunCmdOk = True
    except subprocess.CalledProcessError as callProcessErr:
        cmdErrStr = str(callProcessErr)
        print("Error %s for run command %s" % (cmdErrStr, consoleCommand))

    # print("isRunCmdOk=%s, consoleOutput=%s" % (isRunCmdOk, consoleOutput))
    return isRunCmdOk, consoleOutput

def launchTerminalRunShellCommand(shellFile, isForceNewInstance=True, isUseiTerm2=False):
    """in Mac, Launch terminal(Mac Terminal / iTerm2) and execute shell file, which contain command to run

    Args:
        shellFile (str): shell file full path
        isUseiTerm2 (bool): True to use iTerm2, False to use Mac builtin Terminal
        isForceNewInstance (bool): whether pase -n to open, which means: Open a new instance of the application even if one is already running
    Returns:
    Raises:
    """
    logging.debug("shellFile=%s, isForceNewInstance=%s, isUseiTerm2=%s", shellFile, isForceNewInstance, isUseiTerm2)

    TerminalApp_iTerm2 = '/Applications/iTerm.app'
    TerminalApp_Terminal = 'Terminal'
    if isUseiTerm2:
        terminalApp = TerminalApp_iTerm2
    else:
        terminalApp = TerminalApp_Terminal

    cmdList = [
        "/usr/bin/open",
    ]

    if isForceNewInstance:
        cmdList.append("-n")

    extarArgs = shellFile
    restCmdList = [
        "-a",
        terminalApp,
        '--args',
        extarArgs,
    ]
    cmdList.extend(restCmdList)
    logging.debug("cmdList=%s" % cmdList)

    curProcess = subprocess.Popen(cmdList, stdin=subprocess.PIPE, stdout=subprocess.PIPE)
    logging.debug("curProcess=%s" % curProcess)

    returnCode = None
    while True:
        returnCode = curProcess.poll()
        logging.debug("returnCode=%s", returnCode)
        if returnCode is not None:
            logging.debug("subprocess end: returnCode=%s", returnCode)
            break
        time.sleep(0.5)

    logging.debug("Final returnCode=%s", returnCode)
    logging.debug("Complete launch %s and run shell %s", terminalApp, shellFile)

def killProcess(pid):
    """Kill process by pid

    Args:
        pid (id): process ID
    Returns:
    Raises:
    """
    isKillOk, errCode = False, 0
    pidInt = int(pid)
    killCmd = "kill -9 %s" % pidInt
    returnCode = os.system(killCmd)
    logging.debug("Command: %s -> returnCode=%s", killCmd, returnCode)
    RETURN_CODE_OK = 0
    if returnCode == RETURN_CODE_OK:
        isKillOk = True
    else:
        errCode = returnCode
    return isKillOk, errCode

def grepProcessStatus(processFile, singleLinePattern, psCmd="ps aux"):
    """grep process info status from ps output

    Args:
        processFile (str): process file name
        singleLinePattern (str): single process line search pattern
        psCmd (str): ps command, default: ps aux
    Returns:
    Raises:
    Examples:
        input: "crawlerStart.py", "^\s*(?P<username>\w+)\s+(?P<pid>\d+)\s+.+?python\s+crawlerStart\.py\s+-task\s+(?P<taskFile>\S+)\s+-id\s+(?P<curDevId>\d+)$"
        output: [{'username': 'limao', 'pid': '64320', 'taskFile': '/Users/limao/dev/xxx/crawler/appAutoCrawler/AppCrawler/task/191115_card_DongKaKongJian/191115_card_DongKaKongJian_wexin.txt', 'curDevId': '1'}]
    """
    logging.debug("processFile=%s, singleLinePattern=%s", processFile, singleLinePattern)
    isCheckCmdRunOk, isRunning, processInfoList = False, False, []

    groupNameList = re.findall("\(\?P<(\w+)>", singleLinePattern)
    logging.debug("groupNameList=%s", groupNameList)
    # groupNameList=['username', 'pid', 'port', 'scriptFile', 'devId']
    grepProcessCmd = "%s | grep %s" % (psCmd, processFile)
    logging.debug("grepProcessCmd=%s", grepProcessCmd)
    isCheckCmdRunOk, cmdResult = getCommandOutput(grepProcessCmd)
    logging.debug("isCheckCmdRunOk=%s, cmdResult=%s", isCheckCmdRunOk, cmdResult)
    if isCheckCmdRunOk:
        # lineSeparator = "\n"
        lineSeparator = os.linesep
        resultList = cmdResult.split(lineSeparator)
        logging.debug("resultList=%s", resultList)
        # limao            56562   0.0  0.0  4267948    664 s006  R+    5:53下午   0:00.00 grep mitmdump
        # limao            56560   0.0  0.0  4268636   1112 s006  S+    5:53下午   0:00.00 /bin/sh -c ps aux | grep mitmdump
        # limao            55396   0.0  0.1  4381268  11568 s011  S+    5:19下午   0:05.04 /Users/limao/.pyenv/versions/3.8.0/Python.framework/Versions/3.8/Resources/Python.app/Contents/MacOS/Python /Users/limao/.pyenv/versions/3.8.0/bin/mitmdump -p 8081 -s middleware/Save1.py
        if resultList:
            for eachLine in resultList:
                logging.debug("eachLine=%s", eachLine)
                foundProcess = re.search(singleLinePattern, eachLine)
                logging.debug("foundProcess=%s", foundProcess)
                if foundProcess:
                    curProcessInfoDict = {}
                    for eachKey in groupNameList:
                        curValue = foundProcess.group(eachKey)
                        curProcessInfoDict[eachKey] = curValue
                    logging.debug("curProcessInfoDict=%s", curProcessInfoDict)
                    processInfoList.append(curProcessInfoDict)

    isRunning = bool(processInfoList)
    logging.debug("isRunning=%s, processInfoList=%s", isRunning, processInfoList)
    return isCheckCmdRunOk, isRunning, processInfoList

```

注：

相关库文件的最新版，详见：

* https://github.com/crifan/crifanLibPython/blob/master/python3/crifanLib/crifanSystem.py
  * `grepProcessStatus`
  * `killProcess`
  * `launchTerminalRunShellCommand`
  * `getCommandOutput`
  * `runCommand`

