# Win

## 安装遇到的问题

之前在win10中安装mitmproxy，遇到过2个问题：

### build _openssl.c error C2065 X509_V_FLAG_CB_ISSUER_CHECK undeclared identifier

```bash
creating build\temp.win-amd64-3.8\Release\build\temp.win-amd64-3.8\Release
  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\BIN\x86_amd64\cl.exe /c /nologo /Ox /W3 /GL /DNDEBUG /MD "-Ic:\program files\python38\include" "-Ic:\program files\python38\include" "-IC:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\INCLUDE" "-IC:\Program Files (x86)\Windows Kits\10\include\10.0.10240.0\ucrt" "-IC:\Program Files (x86)\Windows Kits\8.1\include\shared" "-IC:\Program Files (x86)\Windows Kits\8.1\include\um" "-IC:\Program Files (x86)\Windows Kits\8.1\include\winrt" /Tcbuild\temp.win-amd64-3.8\Release\_openssl.c /Fobuild\temp.win-amd64-3.8\Release\build\temp.win-amd64-3.8\Release\_openssl.obj
  _openssl.c
  build\temp.win-amd64-3.8\Release\_openssl.c(1369): warning C4098: 'Cryptography_HMAC_CTX_free': 'void' function returning a value
  build\temp.win-amd64-3.8\Release\_openssl.c(11095): error C2065: 'X509_V_FLAG_CB_ISSUER_CHECK': undeclared identifier
  build\temp.win-amd64-3.8\Release\_openssl.c(11096): error C2065: 'X509_V_FLAG_CB_ISSUER_CHECK': undeclared identifier
  build\temp.win-amd64-3.8\Release\_openssl.c(12429): warning C4013: 'ASN1_STRING_data' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(12429): warning C4047: 'return': 'unsigned char *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(12452): warning C4047: '=': 'unsigned char *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(13565): warning C4090: 'return': different 'const' qualifiers
  build\temp.win-amd64-3.8\Release\_openssl.c(13575): warning C4090: '=': different 'const' qualifiers
  build\temp.win-amd64-3.8\Release\_openssl.c(13589): warning C4090: 'return': different 'const' qualifiers
  build\temp.win-amd64-3.8\Release\_openssl.c(13599): warning C4090: '=': different 'const' qualifiers
  build\temp.win-amd64-3.8\Release\_openssl.c(16441): warning C4013: 'CRYPTO_cleanup_all_ex_data' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(16465): warning C4013: 'CRYPTO_get_locking_callback' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(16465): warning C4047: 'return': 'void (__cdecl *)(int,int,const char *,int)' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(16475): warning C4047: '=': 'void (__cdecl *)(int,int,const char *,int)' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(16575): warning C4013: 'CRYPTO_num_locks' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(16599): warning C4013: 'CRYPTO_set_locking_callback' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(19290): warning C4013: 'DTLSv1_client_method' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(19290): warning C4047: 'return': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(19300): warning C4047: '=': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(19350): warning C4013: 'DTLSv1_method' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(19350): warning C4047: 'return': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(19360): warning C4047: '=': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(19374): warning C4013: 'DTLSv1_server_method' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(19374): warning C4047: 'return': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(19384): warning C4047: '=': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(22275): warning C4013: 'ENGINE_cleanup' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(23380): warning C4013: 'ENGINE_load_dynamic' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(23404): warning C4013: 'ENGINE_load_openssl' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(25957): warning C4013: 'EVP_CIPHER_CTX_cleanup' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(26094): warning C4013: 'EVP_CIPHER_CTX_init' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(32153): warning C4013: 'OBJ_cleanup' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(34129): warning C4090: 'return': different 'const' qualifiers
  build\temp.win-amd64-3.8\Release\_openssl.c(34152): warning C4090: '=': different 'const' qualifiers
  build\temp.win-amd64-3.8\Release\_openssl.c(34609): warning C4013: 'OPENSSL_config' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(34709): warning C4013: 'OPENSSL_no_config' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(34793): warning C4013: 'OpenSSL_add_all_algorithms' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(38288): warning C4013: 'RAND_cleanup' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(46480): warning C4090: 'function': different 'const' qualifiers
  build\temp.win-amd64-3.8\Release\_openssl.c(46520): warning C4090: 'function': different 'const' qualifiers
  build\temp.win-amd64-3.8\Release\_openssl.c(46713): warning C4013: 'SSL_library_init' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(46773): warning C4013: 'SSL_load_error_strings' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(49146): warning C4013: 'TLSv1_1_client_method' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(49146): warning C4047: 'return': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49156): warning C4047: '=': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49170): warning C4013: 'TLSv1_1_method' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(49170): warning C4047: 'return': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49180): warning C4047: '=': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49194): warning C4013: 'TLSv1_1_server_method' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(49194): warning C4047: 'return': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49204): warning C4047: '=': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49218): warning C4013: 'TLSv1_2_client_method' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(49218): warning C4047: 'return': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49228): warning C4047: '=': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49242): warning C4013: 'TLSv1_2_method' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(49242): warning C4047: 'return': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49252): warning C4047: '=': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49266): warning C4013: 'TLSv1_2_server_method' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(49266): warning C4047: 'return': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49276): warning C4047: '=': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49290): warning C4013: 'TLSv1_client_method' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(49290): warning C4047: 'return': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49300): warning C4047: '=': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49314): warning C4013: 'TLSv1_method' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(49314): warning C4047: 'return': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49324): warning C4047: '=': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49338): warning C4013: 'TLSv1_server_method' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(49338): warning C4047: 'return': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(49348): warning C4047: '=': 'const SSL_METHOD *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(50421): warning C4013: 'X509_CRL_get_lastUpdate' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(50421): warning C4047: 'return': 'ASN1_OCTET_STRING *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(50444): warning C4047: '=': 'ASN1_OCTET_STRING *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(50457): warning C4013: 'X509_CRL_get_nextUpdate' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(50457): warning C4047: 'return': 'ASN1_OCTET_STRING *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(50480): warning C4047: '=': 'ASN1_OCTET_STRING *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(50659): warning C4013: 'X509_CRL_set_lastUpdate' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(50712): warning C4013: 'X509_CRL_set_nextUpdate' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(53826): warning C4013: 'X509_STORE_CTX_get_chain' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(53826): warning C4047: 'return': 'Cryptography_STACK_OF_X509 *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(53849): warning C4047: '=': 'Cryptography_STACK_OF_X509 *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(54363): warning C4013: 'X509_STORE_CTX_set_chain' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(54620): warning C4013: 'X509_STORE_CTX_trusted_stack' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(57001): warning C4013: 'X509_get_notAfter' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(57001): warning C4047: 'return': 'ASN1_OCTET_STRING *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(57024): warning C4047: '=': 'ASN1_OCTET_STRING *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(57037): warning C4013: 'X509_get_notBefore' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(57037): warning C4047: 'return': 'ASN1_OCTET_STRING *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(57060): warning C4047: '=': 'ASN1_OCTET_STRING *' differs in levels of indirection from 'int'
  build\temp.win-amd64-3.8\Release\_openssl.c(57500): warning C4013: 'X509_set_notAfter' undefined; assuming extern returning int
  build\temp.win-amd64-3.8\Release\_openssl.c(57553): warning C4013: 'X509_set_notBefore' undefined; assuming extern returning int
  error: command 'C:\\Program Files (x86)\\Microsoft Visual Studio 14.0\\VC\\BIN\\x86_amd64\\cl.exe' failed with exit status 2
  ----------------------------------------
  ERROR: Failed building wheel for cryptography
  Running setup.py clean for cryptography
Failed to build cryptography
ERROR: Could not build wheels for cryptography which use PEP 517 and cannot be installed directly
```

经过一番折腾，但最后是没解决。

具体过程详见：

* 【未解决】windows中pip安装mitmproxy报错：  build _openssl.c  error C2065 X509_V_FLAG_CB_ISSUER_CHECK undeclared identifier

### ERROR: Could not build wheels for cryptography which use PEP 517 and cannot be installed directly

```bash
> pip install mitmproxy
......
Collecting pycparser
  Using cached https://files.pythonhosted.org/packages/68/9e/49196946aee219aead1290e00d1e7fdeab8567783e83e1b9ab5585e6206a/pycparser-2.19.tar.gz
Building wheels for collected packages: cryptography
  Building wheel for cryptography (PEP 517) ... error
  ERROR: Command errored out with exit status 1:
   command: 'c:\program files\python38\python.exe' 'c:\program files\python38\lib\site-packages\pip\_vendor\pep517\_in_process.py' build_wheel 'C:\Users\xxx~1\AppData\Local\Temp\tmp38qbzrlq'
       cwd: C:\Users\xxx\AppData\Local\Temp\pip-install-x4h_xxr8\cryptography
  Complete output (112 lines):
  running bdist_wheel
  running build
  running build_py
  creating build
  creating build\lib.win-amd64-3.8
  creating build\lib.win-amd64-3.8\cryptography
  copying src\cryptography\exceptions.py -> build\lib.win-amd64-3.8\cryptography
  copying src\cryptography\fernet.py -> build\lib.win-amd64-3.8\cryptography
  copying src\cryptography\utils.py -> build\lib.win-amd64-3.8\cryptography
  copying src\cryptography\__about__.py -> build\lib.win-amd64-3.8\cryptography
  copying src\cryptography\__init__.py -> build\lib.win-amd64-3.8\cryptography
  creating build\lib.win-amd64-3.8\cryptography\hazmat
  copying src\cryptography\hazmat\_oid.py -> build\lib.win-amd64-3.8\cryptography\hazmat
  copying src\cryptography\hazmat\__init__.py -> build\lib.win-amd64-3.8\cryptography\hazmat
  creating build\lib.win-amd64-3.8\cryptography\x509
  copying src\cryptography\x509\base.py -> build\lib.win-amd64-3.8\cryptography\x509
  copying src\cryptography\x509\certificate_transparency.py -> build\lib.win-amd64-3.8\cryptography\x509
  copying src\cryptography\x509\extensions.py -> build\lib.win-amd64-3.8\cryptography\x509
  copying src\cryptography\x509\general_name.py -> build\lib.win-amd64-3.8\cryptography\x509
  copying src\cryptography\x509\name.py -> build\lib.win-amd64-3.8\cryptography\x509
  copying src\cryptography\x509\ocsp.py -> build\lib.win-amd64-3.8\cryptography\x509
  copying src\cryptography\x509\oid.py -> build\lib.win-amd64-3.8\cryptography\x509
  copying src\cryptography\x509\__init__.py -> build\lib.win-amd64-3.8\cryptography\x509
  creating build\lib.win-amd64-3.8\cryptography\hazmat\backends
  copying src\cryptography\hazmat\backends\interfaces.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends
  copying src\cryptography\hazmat\backends\__init__.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends
  creating build\lib.win-amd64-3.8\cryptography\hazmat\bindings
  copying src\cryptography\hazmat\bindings\__init__.py -> build\lib.win-amd64-3.8\cryptography\hazmat\bindings
  creating build\lib.win-amd64-3.8\cryptography\hazmat\primitives
  copying src\cryptography\hazmat\primitives\cmac.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives
  copying src\cryptography\hazmat\primitives\constant_time.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives
  copying src\cryptography\hazmat\primitives\hashes.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives
  copying src\cryptography\hazmat\primitives\hmac.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives
  copying src\cryptography\hazmat\primitives\keywrap.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives
  copying src\cryptography\hazmat\primitives\mac.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives
  copying src\cryptography\hazmat\primitives\padding.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives
  copying src\cryptography\hazmat\primitives\serialization.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives
  copying src\cryptography\hazmat\primitives\__init__.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives
  creating build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\aead.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\backend.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\ciphers.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\cmac.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\decode_asn1.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\dh.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\dsa.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\ec.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\encode_asn1.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\hashes.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\hmac.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\ocsp.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\rsa.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\utils.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\x25519.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\x509.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  copying src\cryptography\hazmat\backends\openssl\__init__.py -> build\lib.win-amd64-3.8\cryptography\hazmat\backends\openssl
  creating build\lib.win-amd64-3.8\cryptography\hazmat\bindings\openssl
  copying src\cryptography\hazmat\bindings\openssl\binding.py -> build\lib.win-amd64-3.8\cryptography\hazmat\bindings\openssl
  copying src\cryptography\hazmat\bindings\openssl\_conditional.py -> build\lib.win-amd64-3.8\cryptography\hazmat\bindings\openssl
  copying src\cryptography\hazmat\bindings\openssl\__init__.py -> build\lib.win-amd64-3.8\cryptography\hazmat\bindings\openssl
  creating build\lib.win-amd64-3.8\cryptography\hazmat\primitives\asymmetric
  copying src\cryptography\hazmat\primitives\asymmetric\dh.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\asymmetric
  copying src\cryptography\hazmat\primitives\asymmetric\dsa.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\asymmetric
  copying src\cryptography\hazmat\primitives\asymmetric\ec.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\asymmetric
  copying src\cryptography\hazmat\primitives\asymmetric\padding.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\asymmetric
  copying src\cryptography\hazmat\primitives\asymmetric\rsa.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\asymmetric
  copying src\cryptography\hazmat\primitives\asymmetric\utils.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\asymmetric
  copying src\cryptography\hazmat\primitives\asymmetric\x25519.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\asymmetric
  copying src\cryptography\hazmat\primitives\asymmetric\__init__.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\asymmetric
  creating build\lib.win-amd64-3.8\cryptography\hazmat\primitives\ciphers
  copying src\cryptography\hazmat\primitives\ciphers\aead.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\ciphers
  copying src\cryptography\hazmat\primitives\ciphers\algorithms.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\ciphers
  copying src\cryptography\hazmat\primitives\ciphers\base.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\ciphers
  copying src\cryptography\hazmat\primitives\ciphers\modes.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\ciphers
  copying src\cryptography\hazmat\primitives\ciphers\__init__.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\ciphers
  creating build\lib.win-amd64-3.8\cryptography\hazmat\primitives\kdf
  copying src\cryptography\hazmat\primitives\kdf\concatkdf.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\kdf
  copying src\cryptography\hazmat\primitives\kdf\hkdf.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\kdf
  copying src\cryptography\hazmat\primitives\kdf\kbkdf.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\kdf
  copying src\cryptography\hazmat\primitives\kdf\pbkdf2.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\kdf
  copying src\cryptography\hazmat\primitives\kdf\scrypt.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\kdf
  copying src\cryptography\hazmat\primitives\kdf\x963kdf.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\kdf
  copying src\cryptography\hazmat\primitives\kdf\__init__.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\kdf
  creating build\lib.win-amd64-3.8\cryptography\hazmat\primitives\twofactor
  copying src\cryptography\hazmat\primitives\twofactor\hotp.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\twofactor
  copying src\cryptography\hazmat\primitives\twofactor\totp.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\twofactor
  copying src\cryptography\hazmat\primitives\twofactor\utils.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\twofactor
  copying src\cryptography\hazmat\primitives\twofactor\__init__.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\twofactor
  running egg_info
  writing src\cryptography.egg-info\PKG-INFO
  writing dependency_links to src\cryptography.egg-info\dependency_links.txt
  writing requirements to src\cryptography.egg-info\requires.txt
  writing top-level names to src\cryptography.egg-info\top_level.txt
  reading manifest file 'src\cryptography.egg-info\SOURCES.txt'
  reading manifest template 'MANIFEST.in'
  no previously-included directories found matching 'docs\_build'
  warning: no previously-included files matching '*' found under directory 'vectors'
  writing manifest file 'src\cryptography.egg-info\SOURCES.txt'
  running build_ext
  generating cffi module 'build\\temp.win-amd64-3.8\\Release\\_padding.c'
  creating build\temp.win-amd64-3.8
  creating build\temp.win-amd64-3.8\Release
  generating cffi module 'build\\temp.win-amd64-3.8\\Release\\_constant_time.c'
  generating cffi module 'build\\temp.win-amd64-3.8\\Release\\_openssl.c'
  building '_openssl' extension
  creating build\temp.win-amd64-3.8\Release\build
  creating build\temp.win-amd64-3.8\Release\build\temp.win-amd64-3.8
  creating build\temp.win-amd64-3.8\Release\build\temp.win-amd64-3.8\Release
  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\BIN\x86_amd64\cl.exe /c /nologo /Ox /W3 /GL /DNDEBUG /MD "-Ic:\program files\python38\include" "-Ic:\program files\python38\include" "-IC:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\INCLUDE" "-IC:\Program Files (x86)\Windows Kits\10\include\10.0.10240.0\ucrt" "-IC:\Program Files (x86)\Windows Kits\8.1\include\shared" "-IC:\Program Files (x86)\Windows Kits\8.1\include\um" "-IC:\Program Files (x86)\Windows Kits\8.1\include\winrt" /Tcbuild\temp.win-amd64-3.8\Release\_openssl.c /Fobuild\temp.win-amd64-3.8\Release\build\temp.win-amd64-3.8\Release\_openssl.obj
  _openssl.c
  build\temp.win-amd64-3.8\Release\_openssl.c(498): fatal error C1083: Cannot open include file: 'openssl/opensslv.h': No such file or directory
  error: command 'C:\\Program Files (x86)\\Microsoft Visual Studio 14.0\\VC\\BIN\\x86_amd64\\cl.exe' failed with exit status 2
  ----------------------------------------
  ERROR: Failed building wheel for cryptography
  Running setup.py clean for cryptography
Failed to build cryptography
ERROR: Could not build wheels for cryptography which use PEP 517 and cannot be installed directly
```

也试了：

```bash
pip install cryptography
```

但问题依旧。

以及：

```bash
python -m pip install --no-use-pep517 mitmproxy
```

但报其他错误：

```bash
    copying src\cryptography\hazmat\primitives\twofactor\__init__.py -> build\lib.win-amd64-3.8\cryptography\hazmat\primitives\twofactor
    running egg_info
    writing src\cryptography.egg-info\PKG-INFO
    writing dependency_links to src\cryptography.egg-info\dependency_links.txt
    writing requirements to src\cryptography.egg-info\requires.txt
    writing top-level names to src\cryptography.egg-info\top_level.txt
    reading manifest file 'src\cryptography.egg-info\SOURCES.txt'
    reading manifest template 'MANIFEST.in'
    no previously-included directories found matching 'docs\_build'
    warning: no previously-included files matching '*' found under directory 'vectors'
    writing manifest file 'src\cryptography.egg-info\SOURCES.txt'
    running build_ext
    generating cffi module 'build\\temp.win-amd64-3.8\\Release\\_padding.c'
    creating build\temp.win-amd64-3.8
    creating build\temp.win-amd64-3.8\Release
    generating cffi module 'build\\temp.win-amd64-3.8\\Release\\_constant_time.c'
    generating cffi module 'build\\temp.win-amd64-3.8\\Release\\_openssl.c'
    building '_openssl' extension
    creating build\temp.win-amd64-3.8\Release\build
    creating build\temp.win-amd64-3.8\Release\build\temp.win-amd64-3.8
    creating build\temp.win-amd64-3.8\Release\build\temp.win-amd64-3.8\Release
    C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\BIN\x86_amd64\cl.exe /c /nologo /Ox /W3 /GL /DNDEBUG /MD "-IC:\Program Files\Python38\include" "-IC:\Program Files\Python38\include" "-IC:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\INCLUDE" "-IC:\Program Files (x86)\Windows Kits\10\include\10.0.10240.0\ucrt" "-IC:\Program Files (x86)\Windows Kits\8.1\include\shared" "-IC:\Program Files (x86)\Windows Kits\8.1\include\um" "-IC:\Program Files (x86)\Windows Kits\8.1\include\winrt" /Tcbuild\temp.win-amd64-3.8\Release\_openssl.c /Fobuild\temp.win-amd64-3.8\Release\build\temp.win-amd64-3.8\Release\_openssl.obj
    _openssl.c
    build\temp.win-amd64-3.8\Release\_openssl.c(498): fatal error C1083: Cannot open include file: 'openssl/opensslv.h': No such file or directory
    error: command 'C:\\Program Files (x86)\\Microsoft Visual Studio 14.0\\VC\\BIN\\x86_amd64\\cl.exe' failed with exit status 2
    ----------------------------------------
  Rolling back uninstall of cryptography
  Moving to c:\program files\python38\lib\site-packages\cryptography-2.8.dist-info\
   from C:\Program Files\Python38\Lib\site-packages\~ryptography-2.8.dist-info
  Moving to c:\program files\python38\lib\site-packages\cryptography\
   from C:\Program Files\Python38\Lib\site-packages\~ryptography
ERROR: Command errored out with exit status 1: 'C:\Program Files\Python38\python.exe' -u -c 'import sys, setuptools, tokenize; sys.argv[0] = '"'"'C:\\Users\\xxx\\AppData\\Local\\Temp\\pip-install-wkntcchc\\cryptography\\setup.py'"'"'; __file__='"'"'C:\\Users\\xxx\\AppData\\Local\\Temp\\pip-install-wkntcchc\\cryptography\\setup.py'"'"';f=getattr(tokenize, '"'"'open'"'"', open)(__file__);code=f.read().replace('"'"'\r\n'"'"', '"'"'\n'"'"');f.close();exec(compile(code, __file__, '"'"'exec'"'"'))' install --record 'C:\Users\xxx\AppData\Local\Temp\pip-record-dqgnm_3i\install-record.txt' --single-version-externally-managed --compile Check the logs for full command output.
```

以及其他折腾。

但最后是没解决。

具体过程详见：

* 【未解决】windows中pip install mitmproxy失败：ERROR Could not build wheels for cryptography which use PEP 517 and cannot be installed directly
