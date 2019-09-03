# TOR

WS can work with .onion-domains. For it you must specify IP and port of TOR socks proxy in config.ini, in “\[tor\]” section. It’s 127.0.0.1:9050 by default. In this section you may see “http\_timeout” param with very big value. It’s need because TOR gates has very slow speed sometimes. Increase it if you has connection troubles.

If you specify proxies list \(--proxies-list\) with .onion domain – it will be ignored.

