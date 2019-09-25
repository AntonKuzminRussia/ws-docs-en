# \[M\] FuzzerUrls

## Common description

Module using for URLs params fuzzing. It works by GET mode at this time. You must specify list of already known URLs in «--urls-file» param. For every param WS generate requests with some modifications \(one param per once\). You can find modification templates in bases/fuzzer/templates.txt. Templates has markers «\|name\|» for place param's name, and «\|value\|» for place param's value \(from origin URL\). For example, for URL «[http://site.com/file.php?a=1&b=2»](http://site.com/file.php?a=1&b=2») and template «\|name\|\[\]\[\]=\|value\|» WS request next URLs: • [http://site.com/file.php?a\[\]\[\]=1&b=2](http://site.com/file.php?a[][]=1&b=2) • [http://site.com/file.php?a=1&b\[\]\[\]=2](http://site.com/file.php?a=1&b[][]=2) WS report to you about some headers if server response 500 status code, or if response body contains phrases from file bases/bad-words.txt.

Module works in «raw» and «selenium» modes.

## Examples

URLs params fuzzing:

```text
./main.py FuzzerUrls --urls-file bases/demo/fuzzer-urls.txt
```

## Options \(\* - necessary\)

{% hint style="info" %}
**R** - available in raw mode  
**S** - available in Selenium mode.
{% endhint %}

| Name | By default | R | S | Description |
| :--- | :--- | :--- | :--- | :--- |
| --urls-file \* |  | Yes | Yes | Path to already known URLs list. Host of this URLs and target host may not be equal. |
| --proxies |  | Yes | Yes | HTTP-proxy list. |
| --retest-re |  | Yes | Yes | RegEx \(python.re\) for check if request repeat is need. For example «Service Temporarily Unavailable». |
| --retest-codes |  | Yes | No | Set of status codes \(separated by comma\) as signature for request re-send. |
| --headers-file |  | Yes | No | File with HTTP headers for put it in work requests. |
| --msymbol | @ | Yes | Yes | Mark symbol for search template \(--template\) |
| --delay | 0 | Yes | Yes | Delay in seconds  between requests. It's options not for all threads together, it's for every thread separately. |
| --threads | 10 | Yes | Yes | Work threads count. |
| --test | 0 | Yes | Yes | Test mode enable |
| --xml-report | 0 | Yes | Yes | Path to save xml-report |
| --selenium | 0 | No | Yes | Selenium-mode enable |
| --browser-recreate-re |  | No | Yes | RegEx \(python.re\) for detect browser recreation need. If you using proxies, browser select new one. |
| --browser-wait-re |  | No | Yes | RegEx \(python.re\). If match, browser stop working and will wait for match disappear. You may use it for solve captcha by hands or wait for anti-ddos check \(«wait 5 secs, we check your browser»\). |

