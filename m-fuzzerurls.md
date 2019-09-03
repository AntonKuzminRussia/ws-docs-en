# \[M\] FuzzerUrls

### Common description 

Module using for URLs params fuzzing. It works by GET mode at this time. You must specify list of already known URLs in «--urls-file» param. For every param WS generate requests with some modifications \(one param per once\). You can find modification templates in bases/fuzzer/templates.txt. Templates has markers «\|name\|» for place param's name, and «\|value\|» for place param's value \(from origin URL\). For example, for URL «[http://site.com/file.php?a=1&b=2»](http://site.com/file.php?a=1&b=2») and template «\|name\|\[\]\[\]=\|value\|» WS request next URLs: • [http://site.com/file.php?a\[\]\[\]=1&b=2](http://site.com/file.php?a[][]=1&b=2) • [http://site.com/file.php?a=1&b\[\]\[\]=2](http://site.com/file.php?a=1&b[][]=2) WS report to you about some headers if server response 500 status code, or if response body contains phrases from file bases/bad-words.txt.

Module works in «raw» and «selenium» modes.

### Options \(\* - necessary\)

{% hint style="info" %}
**R** - присутствует ли в raw режиме  
**S** - присутствует ли в selenium режиме.
{% endhint %}

| Name | By default | R | S | Description |
| :--- | :--- | :--- |
| --urls-file \* |  | Yes | Yes | Path to already known URLs list. Host of this URLs and target host may not be equal. |
| --proxies |  | Да | Да | HTTP-proxy list. |
| --retest-re |  | Да | Да | RegEx (python.re) for check if request repeat is need. For example «Service Temporarily Unavailable». |
| --retest-codes |  | Да | Нет | Set of status codes (separated by comma) as signature for request re-send. |
| --headers-file |  | Да | Нет | File with HTTP headers for put it in work requests. |
| --msymbol | @ | Да | Да | Mark symbol for search template (--template) |
| --delay | 0 | Да | Да | Delay in seconds  between requests. It`s options not for all threads together, it`s for every thread separately. |
| --threads | 10 | Да | Да | Work threads count. |
| --parts | 0 | Да | Да | Split on X parts target dict or mask. |
| --part | 0 | Да | Да | Which part number we using in work? |
| --test | 0 | Да | Да | Test mode enable |
| --xml-report | 0 | Да | Да | Path to save xml-report |
| --selenium | 0 | Нет | Да | Selenium-mode enable |
| --browser-recreate-re |  | Нет | Да | RegEx (python.re) for detect browser recreation need. If you using proxies, browser select new one. |
| --browser-wait-re |  | Нет | Да | RegEx (python.re). If match, browser stop working and will wait for match disappear. You may use it for solve captcha by hands or wait for anti-ddos check («wait 5 secs, we check your browser»). |


