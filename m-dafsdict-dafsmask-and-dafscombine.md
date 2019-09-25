# \[M\] UrlsDict, UrlsMask & UrlsCombine

## Common description

Using for URLs search on target web-sites. Search made by template with mark symbol which replacing by target name.

Like «Not Found» response signature \(404 status code\) you may using regexps \(matches searching in response headers and body\), response size, different status codes. Besides, you may use param for regexp for detecting found pages \(status code 200 analogue\).

If you specify more than one signature of positive/negative responses, they be have next priority:

1. Regexp for detect positive response \(status code 200 analogue\) 
2. Size of negative response 
3. Regexp for detect negative response \(status code 404 analogue\) 
4. Status codes which negative responses

If one of this signatures detect existing item, it stop other detections. Example. You specify regexp «found» like positive response signature. WS make request of item X and get response with status code 404 and phrase «found» in body. WS get it as existing element \(like status code 200\) because regexp of positive response more priority than status codes check.

Module can search objects by mask, dictionary and by combination \(mask + dict\).

Module working in «raw» and «selenium» modes.

### Examples

Simple search by dict:

```text
./main.py UrlsDict --template http://simple.polygon.web-scout.online/@ --dict bases/demo/dict.txt
```

Simple search by mask:

```text
./main.py UrlsMask --template http://simple.polygon.web-scout.online/@ --mask ?l,1,4
```

Search by dict in selenium mode:

```text
./main.py UrlsDict --template http://selenium.polygon.web-scout.online/@ --dict bases/demo/dict.txt --selenium 1 --browser-wait-re "checking" --not-found-re "Not Found"
```

Search on site with 200 response on not found pages requests:

```text
./main.py UrlsDict --template http://always-200.polygon.web-scout.online/@ --dict bases/demo/dict.txt --not-found-re "Page not found"
```

Search with response code 500 like 404:

```text
./main.py UrlsDict --template http://always-500.polygon.web-scout.online/@ --dict bases/demo/dict.txt --not-found-codes 500
```

Search with retry request if response code is 503:

```text
./main.py UrlsDict --template http://sometimes-503.polygon.web-scout.online/@ --dict bases/demo/dict.txt --retest-codes 503
```

Search with retry request if response contains phrase "Too big load":

```text
./main.py UrlsDict --template http://sometimes-503.polygon.web-scout.online/@ --dict bases/demo/dict.txt --retest-re "Too big load"
```

## Options \(\* - necessary\)

{% hint style="info" %}
**R** - available in raw mode  
**S** - available in Selenium mode.
{% endhint %}

| Name | By default | R | S | Description |
| :--- | :--- | :--- | :--- | :--- |
| --template \* |  | Yes | Yes | Template for work with mark symbol \(@ by default\) in place, where target phrase will be put. For example:  «[http://site.com/@»](http://site.com/@»), «[https://site.com/@.php»](https://site.com/@.php»). |
| --dict \* |  | Yes | Yes | For UrlsDict. Path to dictionary |
| --mask \* |  | Yes | Yes | For UrlsMask. Symbols mask. |
| --combine-template \* |  | Yes | Yes | for UrlsCombine. Template for combined work. String with markers «%m%» and «%d%», which is place for dict word and mask word. |
| --found-re |  | Yes | Yes | RegEx \(python.re\) for check positive web-server response \(code 200 analogue\) |
| --not-found-re |  | Yes | Yes | RegEx \(python.re\) for check negative web-server response  \(code 404 analogue\) |
| --not-found-size |  | Yes | Yes | Size of negative answer \(code 404 analogue\). Remember, this size can be different in different tools. Use test mode for get right size. |
| --not-found-codes |  | Yes | No | Status codes, analogues of 404. Separated by comma. |
| --method | GET | Yes | No | HTTP-method for work: HEAD, POST, GET. |
| --proxies |  | Yes | Yes | HTTP-proxy list. |
| --retest-re |  | Yes | Yes | RegEx \(python.re\) for check if request repeat is need. For example «Service Temporarily Unavailable». |
| --retest-codes |  | Yes | No | Set of status codes \(separated by comma\) as signature for request re-send. |
| --headers-file |  | Yes | No | File with HTTP headers for put it in work requests. |
| --ignore-words-re |  | Yes | Yes | RegEx \(python.re\) for ignoring target phrases. May be useful when you don't want check some phrases, for example contains “.ht”. |
| --msymbol | @ | Yes | Yes | Mark symbol for search template \(--template\) |
| --delay | 0 | Yes | Yes | Delay in seconds  between requests. It's options not for all threads together, it's for every thread separately. |
| --threads | 10 | Yes | Yes | Work threads count. |
| --parts | 0 | Yes | Yes | Split on X parts target dict or mask. |
| --part | 0 | Yes | Yes | Which part number we using in work? |
| --test | 0 | Yes | Yes | Test mode enable |
| --xml-report | 0 | Yes | Yes | Path to save xml-report |
| --selenium | 0 | No | Yes | Selenium-mode enable |
| --browser-recreate-re |  | No | Yes | RegEx \(python.re\) for detect browser recreation need. If you using proxies, browser select new one. |
| --browser-wait-re |  | No | Yes | RegEx \(python.re\). If match, browser stop working and will wait for match disappear. You may use it for solve captcha by hands or wait for anti-ddos check \(«wait 5 secs, we check your browser»\). |

