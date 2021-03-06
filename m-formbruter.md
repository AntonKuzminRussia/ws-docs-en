# \[M\] Forms

### Common description

Module using for forms bruteforce. In «raw» mode requests sends by POST method. In «selenium» mode bruteforce doing according to target site logic. Passwords getting from dictionary.

### Attack configuration

Config for bruteforce in «raw» mode is POST params with markers «^USER^» and «^PASS^» on relevant places. Result string put in «--conf-str» param. Examples:

* login=^USER^&password=^PASS^ 
* {"login":"^USER^","pwd":"^PASS^"}

After marker string must contains tab-symbol \(\t\). And after that, put there CSS selector of element. Example:

```text
^USER^ #user 
^PASS^ #pass 
^SUBMIT^ #submit
```

With this configuration WS put login in text field id=user, password go to text field id=pass. After that WS will click by element id=submit.

## Examples

Simple POST form bruteforce:

```text
./ws.py Forms --url http://simple.polygon.web-scout.online/admin.php --dict bases/demo/dict.txt --conf-str "login=^USER^&password=^PASS^" --false-re "User: " --login admin
```

Bruteforce form in selenium mode:

```text
./ws.py Forms --url http://selenium.polygon.web-scout.online/admin.php --dict bases/demo/dict.txt --conf-file bases/demo/form-brute.conf --false-re "User: " --login admin --selenium 1 --browser-wait-re "checking"
```

## Options \(\* - necessary\)

{% hint style="info" %}
Params «-conf-file», «--conf-str» - you must specify one of them. Params «--true-phrase», «--false-phrase», «--false-size» too.
{% endhint %}

{% hint style="info" %}
**R** - available in raw mode  
**S** - available in Selenium mode.
{% endhint %}

| Name | By default | R | S | Description |
| :--- | :--- | :--- | :--- | :--- |
| --url \* |  | Yes | Yes | Target URL |
| --dict \* |  | Yes | Yes | Path to dict |
| --login \* |  | Yes | Yes | Login |
| --conf-str \* |  | Yes | No | Raw mode only. Bruteforce config string. |
| --conf-file \* |  | No | Yes | Bruteforce config file for selenium mode |
| --true-re \* |  | Yes | Yes | RegEx \(python.re\), if matching — we got positive answer. |
| --false-re \* |  | Yes | Yes | RegEx \(python.re\), if matching — we got negative answer. |
| --false-size \* |  | Yes | Yes | Response size of negative answer. Remember, this size can be different in different tools. Use test mode for get right size. |
| --pass-max-len |  | Yes | Yes | Passwords with length more than this will be skipped. |
| --pass-min-len |  | Yes | Yes | Passwords with length less than this will be skipped. |
| --first-stop | 0 | Yes | Yes | Stop work after first positive result. |
| --follow-redirects | 1 | Yes | No | Raw-mode only. Follow to redirects which server returns. In selenium-mode this is always enabled. |
| --reload-form-page | 0 | No | Yes | Selenium-mode Only. This param need for re-open target link after every form send. It may be useful if server not return you to auth form after false try. |
| --proxies |  | Yes | Yes | HTTP-proxy list. |
| --retest-re |  | Yes | Yes | RegEx \(python.re\) for check if request repeat is need. For example «Service Temporarily Unavailable». |
| --retest-codes |  | Yes | No | Set of status codes \(separated by comma\) as signature for request re-send. |
| --headers-file |  | Yes | No | File with HTTP headers for put it in work requests. |
| --msymbol | @ | Yes | Yes | Mark symbol for search template \(--template\) |
| --delay | 0 | Yes | Yes | Delay in seconds  between requests. It\`s options not for all threads together, it's for every thread separately. |
| --threads | 10 | Yes | Yes | Work threads count. |
| --parts | 0 | Yes | Yes | Split on X parts target dict or mask. |
| --part | 0 | Yes | Yes | Which part number we using in work? |
| --test | 0 | Yes | Yes | Test mode enable |
| --xml-report | 0 | Yes | Yes | Path to save xml-report |
| --selenium | 0 | No | Yes | Selenium-mode enable |
| --browser-recreate-re |  | No | Yes | RegEx \(python.re\) for detect browser recreation need. If you using proxies, browser select new one. |
| --browser-wait-re |  | No | Yes | RegEx \(python.re\). If match, browser stop working and will wait for match disappear. You may use it for solve captcha by hands or wait for anti-ddos check \(«wait 5 secs, we check your browser»\). |

