# Run

WS running by ./ws.py with args. First argument is module name. If you specify wrong module name, WS show help with modules list.

```text
ERROR: Module 'FooBar' not exists!
Possible modules:
    ContentDiscovery
    DafsCombine
    DafsDict
    DafsMask
    DnsBruterCombine
    DnsBruterDict
    DnsBruterMask
    FormBruter
    FuzzerHeaders
    FuzzerUrls
    HostsBruterCombine
    HostsBruterDict
    HostsBruterMask
    ParamsBruterCombine
    ParamsBruterDict
    ParamsBruterMask
```

After that specify parameters and their values. If necessarily parameters not specified, of wrong params specified, WS show help with modules params list. You can see it by run module with param «-h». «./ws.py DafsDict -h» for example.

```text
$ ./ws.py DafsDict -h

usage: ./ws.py DafsDict [-h] [--found-re FOUND-RE]
                          [--not-found-size NOT-FOUND-SIZE]
                          [--retest-codes RETEST-CODES]
                          [--browser-wait-re BROWSER-WAIT-RE]
                          [--xml-report XML-REPORT] [--msymbol MSYMBOL]
                          [--tor TOR] [--selenium SELENIUM]
                          [--retest-re RETEST-RE] [--delay DELAY]
                          [--parts PARTS] --dict DICT --template TEMPLATE
                          [--ignore-words-re IGNORE-WORDS-RE] [--test TEST]
                          [--browser-recreate-re BROWSER-RECREATE-RE]
                          [--method METHOD]
                          [--not-found-codes NOT-FOUND-CODES] [--part PART]
                          [--threads THREADS] [--proxies PROXIES]
                          [--not-found-ex NOT-FOUND-EX]
                          [--headers-file HEADERS-FILE]
                          [--not-found-re NOT-FOUND-RE]

optional arguments:
  -h, --help            show this help message and exit
  --found-re FOUND-RE   Regex for detect 'Found' response (200)
  --not-found-size NOT-FOUND-SIZE
                        Size in bytes for detect 'Not found' response (404)
  --retest-codes RETEST-CODES
                        Custom codes for re-test object after 5 sec
  --browser-wait-re BROWSER-WAIT-RE
                        RegEx for detect moments when selenium browser need
                        wait (ddos check, human action need)
  --xml-report XML-REPORT
                        XML report file
  --msymbol MSYMBOL     Symbol of mask position in target URL (default @)
  --tor TOR             Use TOR
  --selenium SELENIUM   Use Selenium for scanning
  --retest-re RETEST-RE
                        RegEx in response for retest
  --delay DELAY         Deley for every thread between requests (secs)
  --parts PARTS         How many parts will be create from current source
                        (dict/mask)
  --dict DICT           Dictionary for work
  --template TEMPLATE   Template for scan (@ as mark symbol)
  --ignore-words-re IGNORE-WORDS-RE
                        Regex for ignore some words from dict or mask
  --test TEST           Test run with results dump
  --browser-recreate-re BROWSER-RECREATE-RE
                        Regex for recreate browser with new proxy
  --method METHOD       Requests method (default - GET)
  --not-found-codes NOT-FOUND-CODES
                        Custom codes for detect 'Not found' response (404)
  --part PART           Number of part for use from --parts
  --threads THREADS     Threads count, default 10
  --proxies PROXIES     File with list of proxies
  --not-found-ex NOT-FOUND-EX
                        Phrase for detect 'Not found' exception (perceived as
                        404)
  --headers-file HEADERS-FILE
                        File with list of HTTP headers
  --not-found-re NOT-FOUND-RE
                        Regex for detect 'Not found' response (404)
```

All parameters exclude «-h» have only long form \(«--param»\). You can specify those values standardly — through space \(--param value\), with equal sign \(--param=value\), in single or double quotes \(--param 'value'\). For example, next two commands are equal:

```text
./ws.py DafsDict --template http://site.com/@  --dict=1.txt 
./ws.py DafsDict --template 'http://site.com/@' --dict "1.txt"
```

Every param must have value. Many tools allow you specify only param name if you want set it to true \(--param\). And if you not specify it, param understand as False. But in WS it not so. «--param=1» - param set in True, «--param=0» - param set in False. If param not specified, WS get value by default.

