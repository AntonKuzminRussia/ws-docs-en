# Proxies

At this moment WS can work only with http\(s\) proxies without auth. Every work module have param «--proxies» where you can specify path to proxy-list in format «ip:port» at string.

In start of work every thread get individual proxy \(random get from list\). The thread send some requests through this proxy. Count of requests by one proxy you can find in config.ini, section «\[main\]», param «requests\_per\_proxy». After that thread get new random proxy from list. In selenium mode proxy change with re-create browser window.

WS check every proxy which go to work thread. It\`s try to request target host. If request failed WS try to get next proxy server.

In config.ini, section «\[main\]», param «proxies\_died\_limit» you can find limit of died proxy for work stop. If this count of died proxy WS get one-by-one, than work be stop.

