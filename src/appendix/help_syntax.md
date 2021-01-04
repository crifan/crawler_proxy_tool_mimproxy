# help语法

## mitmdump --help

```bash
 mitmdump --help
usage: mitmdump [options] [filter]

positional arguments:
  filter_args           Filter expression, equivalent to setting both the view_filter and save_stream_filter options.

optional arguments:
  -h, --help            show this help message and exit
  --version             show version number and exit
  --options             Show all options and their default values
  --commands            Show all commands and their signatures
  --set option[=value]  Set an option. When the value is omitted, booleans are set to true, strings and integers are set to None (if permitted),
                        and sequences are emptied. Boolean values can be true, false or toggle.
  -q, --quiet           Quiet.
  -v, --verbose         Increase log verbosity.
  --mode MODE, -m MODE  Mode can be "regular", "transparent", "socks5", "reverse:SPEC", or "upstream:SPEC". For reverse and upstream proxy modes,
                        SPEC is host specification in the form of "http[s]://host[:port]".
  --no-anticache
  --anticache           Strip out request headers that might cause the server to return 304-not-modified.
  --no-showhost
  --showhost            Use the Host header to construct URLs for display.
  --rfile PATH, -r PATH
                        Read flows from file.
  --scripts SCRIPT, -s SCRIPT
                        Execute a script. May be passed multiple times.
  --stickycookie FILTER
                        Set sticky cookie filter. Matched against requests.
  --stickyauth FILTER   Set sticky auth filter. Matched against requests.
  --save-stream-file PATH, -w PATH
                        Stream flows to file as they arrive. Prefix path with + to append.
  --no-anticomp
  --anticomp            Try to convince servers to send us un-compressed data.
  --flow-detail LEVEL   The display detail level for flows in mitmdump: 0 (almost quiet) to 3 (very verbose). 0: shortened request URL, response
                        status code, WebSocket and TCP message notifications. 1: full request URL with response status code 2: 1 + HTTP headers 3:
                        2 + full response content, content of WebSocket and TCP messages.

Proxy Options:
  --listen-host HOST    Address to bind proxy to.
  --listen-port PORT, -p PORT
                        Proxy service port.
  --no-server, -n
  --server              Start a proxy server. Enabled by default.
  --ignore-hosts HOST   Ignore host and forward all traffic without processing it. In transparent mode, it is recommended to use an IP address
                        (range), not the hostname. In regular mode, only SSL traffic is ignored and the hostname should be used. The supplied
                        value is interpreted as a regular expression and matched on the ip or the hostname. May be passed multiple times.
  --allow-hosts HOST    Opposite of --ignore-hosts. May be passed multiple times.
  --tcp-hosts HOST      Generic TCP SSL proxy mode for all hosts that match the pattern. Similar to --ignore, but SSL connections are intercepted.
                        The communication contents are printed to the log in verbose mode. May be passed multiple times.
  --upstream-auth USER:PASS
                        Add HTTP Basic authentication to upstream proxy and reverse proxy requests. Format: username:password.
  --proxyauth SPEC      Require proxy authentication. Format: "username:pass", "any" to accept any user/pass combination, "@path" to use an Apache
                        htpasswd file, or "ldap[s]:url_server_ldap:dn_auth:password:dn_subtree" for LDAP authentication.
  --no-rawtcp
  --rawtcp              Enable/disable experimental raw TCP support. TCP connections starting with non-ascii bytes are treated as if they would
                        match tcp_hosts. The heuristic is very rough, use with caution. Disabled by default.
  --no-http2
  --http2               Enable/disable HTTP/2 support. HTTP/2 support is enabled by default.

SSL:
  --certs SPEC          SSL certificates of the form "[domain=]path". The domain may include a wildcard, and is equal to "*" if not specified. The
                        file at path is a certificate in PEM format. If a private key is included in the PEM, it is used, else the default key in
                        the conf dir is used. The PEM file should contain the full certificate chain, with the leaf certificate as the first
                        entry. May be passed multiple times.
  --no-ssl-insecure
  --ssl-insecure, -k    Do not verify upstream server SSL/TLS certificates.
  --key-size KEY_SIZE   TLS key size for certificates and CA.

Client Replay:
  --client-replay PATH, -C PATH
                        Replay client requests from a saved file. May be passed multiple times.

Server Replay:
  --server-replay PATH, -S PATH
                        Replay server responses from a saved file. May be passed multiple times.
  --no-server-replay-kill-extra
  --server-replay-kill-extra
                        Kill extra requests during replay.
  --no-server-replay-nopop
  --server-replay-nopop
                        Don't remove flows from server replay state after use. This makes it possible to replay same response multiple times.
  --no-server-replay-refresh
  --server-replay-refresh
                        Refresh server replay responses by adjusting date, expires and last-modified headers, as well as adjusting cookie
                        expiration.

Replacements:
  --replacements PATTERN, -R PATTERN
                        Replacement patterns of the form "/pattern/regex/replacement", where the separator can be any character. May be passed
                        multiple times.

Set Headers:
  --setheaders PATTERN, -H PATTERN
                        Header set pattern of the form "/pattern/header/value", where the separator can be any character. May be passed multiple
                        times.
```

## mitmproxy --help

```bash
 mitmproxy --help
usage: mitmproxy [options]

optional arguments:
  -h, --help            show this help message and exit
  --version             show version number and exit
  --options             Show all options and their default values
  --commands            Show all commands and their signatures
  --set option[=value]  Set an option. When the value is omitted, booleans are set to true, strings and integers are set to None (if permitted),
                        and sequences are emptied. Boolean values can be true, false or toggle.
  -q, --quiet           Quiet.
  -v, --verbose         Increase log verbosity.
  --mode MODE, -m MODE  Mode can be "regular", "transparent", "socks5", "reverse:SPEC", or "upstream:SPEC". For reverse and upstream proxy modes,
                        SPEC is host specification in the form of "http[s]://host[:port]".
  --no-anticache
  --anticache           Strip out request headers that might cause the server to return 304-not-modified.
  --no-showhost
  --showhost            Use the Host header to construct URLs for display.
  --rfile PATH, -r PATH
                        Read flows from file.
  --scripts SCRIPT, -s SCRIPT
                        Execute a script. May be passed multiple times.
  --stickycookie FILTER
                        Set sticky cookie filter. Matched against requests.
  --stickyauth FILTER   Set sticky auth filter. Matched against requests.
  --save-stream-file PATH, -w PATH
                        Stream flows to file as they arrive. Prefix path with + to append.
  --no-anticomp
  --anticomp            Try to convince servers to send us un-compressed data.
  --console-layout {horizontal,single,vertical}
                        Console layout.
  --no-console-layout-headers
  --console-layout-headers
                        Show layout component headers

Proxy Options:
  --listen-host HOST    Address to bind proxy to.
  --listen-port PORT, -p PORT
                        Proxy service port.
  --no-server, -n
  --server              Start a proxy server. Enabled by default.
  --ignore-hosts HOST   Ignore host and forward all traffic without processing it. In transparent mode, it is recommended to use an IP address
                        (range), not the hostname. In regular mode, only SSL traffic is ignored and the hostname should be used. The supplied
                        value is interpreted as a regular expression and matched on the ip or the hostname. May be passed multiple times.
  --allow-hosts HOST    Opposite of --ignore-hosts. May be passed multiple times.
  --tcp-hosts HOST      Generic TCP SSL proxy mode for all hosts that match the pattern. Similar to --ignore, but SSL connections are intercepted.
                        The communication contents are printed to the log in verbose mode. May be passed multiple times.
  --upstream-auth USER:PASS
                        Add HTTP Basic authentication to upstream proxy and reverse proxy requests. Format: username:password.
  --proxyauth SPEC      Require proxy authentication. Format: "username:pass", "any" to accept any user/pass combination, "@path" to use an Apache
                        htpasswd file, or "ldap[s]:url_server_ldap:dn_auth:password:dn_subtree" for LDAP authentication.
  --no-rawtcp
  --rawtcp              Enable/disable experimental raw TCP support. TCP connections starting with non-ascii bytes are treated as if they would
                        match tcp_hosts. The heuristic is very rough, use with caution. Disabled by default.
  --no-http2
  --http2               Enable/disable HTTP/2 support. HTTP/2 support is enabled by default.

SSL:
  --certs SPEC          SSL certificates of the form "[domain=]path". The domain may include a wildcard, and is equal to "*" if not specified. The
                        file at path is a certificate in PEM format. If a private key is included in the PEM, it is used, else the default key in
                        the conf dir is used. The PEM file should contain the full certificate chain, with the leaf certificate as the first
                        entry. May be passed multiple times.
  --no-ssl-insecure
  --ssl-insecure, -k    Do not verify upstream server SSL/TLS certificates.
  --key-size KEY_SIZE   TLS key size for certificates and CA.

Client Replay:
  --client-replay PATH, -C PATH
                        Replay client requests from a saved file. May be passed multiple times.

Server Replay:
  --server-replay PATH, -S PATH
                        Replay server responses from a saved file. May be passed multiple times.
  --no-server-replay-kill-extra
  --server-replay-kill-extra
                        Kill extra requests during replay.
  --no-server-replay-nopop
  --server-replay-nopop
                        Don't remove flows from server replay state after use. This makes it possible to replay same response multiple times.
  --no-server-replay-refresh
  --server-replay-refresh
                        Refresh server replay responses by adjusting date, expires and last-modified headers, as well as adjusting cookie
                        expiration.

Replacements:
  --replacements PATTERN, -R PATTERN
                        Replacement patterns of the form "/pattern/regex/replacement", where the separator can be any character. May be passed
                        multiple times.

Set Headers:
  --setheaders PATTERN, -H PATTERN
                        Header set pattern of the form "/pattern/header/value", where the separator can be any character. May be passed multiple
                        times.

Filters:
  See help in mitmproxy for filter expression syntax.

  --intercept FILTER    Intercept filter expression.
  --view-filter FILTER  Limit the view to matching flows.
```

## mitmweb --help

```bash
 mitmweb --help
usage: mitmweb [options]

optional arguments:
  -h, --help            show this help message and exit
  --version             show version number and exit
  --options             Show all options and their default values
  --commands            Show all commands and their signatures
  --set option[=value]  Set an option. When the value is omitted, booleans are set to true, strings and integers are set to None (if permitted),
                        and sequences are emptied. Boolean values can be true, false or toggle.
  -q, --quiet           Quiet.
  -v, --verbose         Increase log verbosity.
  --mode MODE, -m MODE  Mode can be "regular", "transparent", "socks5", "reverse:SPEC", or "upstream:SPEC". For reverse and upstream proxy modes,
                        SPEC is host specification in the form of "http[s]://host[:port]".
  --no-anticache
  --anticache           Strip out request headers that might cause the server to return 304-not-modified.
  --no-showhost
  --showhost            Use the Host header to construct URLs for display.
  --rfile PATH, -r PATH
                        Read flows from file.
  --scripts SCRIPT, -s SCRIPT
                        Execute a script. May be passed multiple times.
  --stickycookie FILTER
                        Set sticky cookie filter. Matched against requests.
  --stickyauth FILTER   Set sticky auth filter. Matched against requests.
  --save-stream-file PATH, -w PATH
                        Stream flows to file as they arrive. Prefix path with + to append.
  --no-anticomp
  --anticomp            Try to convince servers to send us un-compressed data.

Mitmweb:
  --no-web-open-browser
  --web-open-browser    Start a browser.
  --web-port PORT       Web UI port.
  --web-iface INTERFACE
                        Web UI interface.

Proxy Options:
  --listen-host HOST    Address to bind proxy to.
  --listen-port PORT, -p PORT
                        Proxy service port.
  --no-server, -n
  --server              Start a proxy server. Enabled by default.
  --ignore-hosts HOST   Ignore host and forward all traffic without processing it. In transparent mode, it is recommended to use an IP address
                        (range), not the hostname. In regular mode, only SSL traffic is ignored and the hostname should be used. The supplied
                        value is interpreted as a regular expression and matched on the ip or the hostname. May be passed multiple times.
  --allow-hosts HOST    Opposite of --ignore-hosts. May be passed multiple times.
  --tcp-hosts HOST      Generic TCP SSL proxy mode for all hosts that match the pattern. Similar to --ignore, but SSL connections are intercepted.
                        The communication contents are printed to the log in verbose mode. May be passed multiple times.
  --upstream-auth USER:PASS
                        Add HTTP Basic authentication to upstream proxy and reverse proxy requests. Format: username:password.
  --proxyauth SPEC      Require proxy authentication. Format: "username:pass", "any" to accept any user/pass combination, "@path" to use an Apache
                        htpasswd file, or "ldap[s]:url_server_ldap:dn_auth:password:dn_subtree" for LDAP authentication.
  --no-rawtcp
  --rawtcp              Enable/disable experimental raw TCP support. TCP connections starting with non-ascii bytes are treated as if they would
                        match tcp_hosts. The heuristic is very rough, use with caution. Disabled by default.
  --no-http2
  --http2               Enable/disable HTTP/2 support. HTTP/2 support is enabled by default.

SSL:
  --certs SPEC          SSL certificates of the form "[domain=]path". The domain may include a wildcard, and is equal to "*" if not specified. The
                        file at path is a certificate in PEM format. If a private key is included in the PEM, it is used, else the default key in
                        the conf dir is used. The PEM file should contain the full certificate chain, with the leaf certificate as the first
                        entry. May be passed multiple times.
  --no-ssl-insecure
  --ssl-insecure, -k    Do not verify upstream server SSL/TLS certificates.
  --key-size KEY_SIZE   TLS key size for certificates and CA.

Client Replay:
  --client-replay PATH, -C PATH
                        Replay client requests from a saved file. May be passed multiple times.

Server Replay:
  --server-replay PATH, -S PATH
                        Replay server responses from a saved file. May be passed multiple times.
  --no-server-replay-kill-extra
  --server-replay-kill-extra
                        Kill extra requests during replay.
  --no-server-replay-nopop
  --server-replay-nopop
                        Don't remove flows from server replay state after use. This makes it possible to replay same response multiple times.
  --no-server-replay-refresh
  --server-replay-refresh
                        Refresh server replay responses by adjusting date, expires and last-modified headers, as well as adjusting cookie
                        expiration.

Replacements:
  --replacements PATTERN, -R PATTERN
                        Replacement patterns of the form "/pattern/regex/replacement", where the separator can be any character. May be passed
                        multiple times.

Set Headers:
  --setheaders PATTERN, -H PATTERN
                        Header set pattern of the form "/pattern/header/value", where the separator can be any character. May be passed multiple
                        times.

Filters:
  See help in mitmproxy for filter expression syntax.

  --intercept FILTER    Intercept filter expression.
```
