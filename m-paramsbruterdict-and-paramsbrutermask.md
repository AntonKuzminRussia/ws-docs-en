# \[M\] ParamsBruterDict and ParamsBruterMask

## Common description

Modules searching the parameters for target URL. Work based on changeable URL content depends some parameters.

Now possible 4 search ways — by GET/POST methods, by cookies and files uploading. Search by GET it''s URL request with many params in it. And POST search like it — params puts in request body. Cookies based method it''s requests to target URL with multiple cookies with different names. And files uploading method it''s multiple tries to upload small files on server with different files fields names.

Attention. You may specify count of searching params per request by option «--max-params-length». This option has double meaning. For GET and POST it''s a maximum params string length with values and amps \(a=1&b=1&c=1…\). Recommended value - 1000. For cookies and files this option set a count of names for check per request. Recommended value — 20.

As values of searching params using «1» by default. You can change it by «--value» option.

Module can search objects by mask, dictionary and by combination \(mask + dict\).

Module working in «raw» and «selenium» modes.

## Options \(\* - necessary\)

{% hint style="info" %}
**R** - available in raw mode  
**S** - available in Selenium mode.
{% endhint %}

| Name | By default | R | S | Description |
| :--- | :--- | :--- | :--- | :--- |
| --url \* |  | Yes | Yes | Target URL |
| --params-method \* |  | Yes | Yes | Search method: GET, POST, COOKIES, FILES |
| --max-params-length \* |  | Yes | Yes | For GET and POST this is maximum params string length, with their values \(a=1&b=1&c=1...\). For COOKIES and FILES it\`s a check names count per once. I recommend value of «--max-params-length» for GET and POST - 1000. For COOKIES and FILES — 20. |
| --dict \* |  | Yes | Yes | For ParamsBruterDict. Path to dictionary. |
| --mask \* |  | Yes | Yes | For ParamsBruterMask. Symbols mask. |
| --combine-template \* |  | Yes | Yes | For ParamsBruterCombine. Template for combined work. String with markers «%m%» and «%d%», which is place for dict word and mask word. |
| --value | 1 | Yes | Yes | Values of params |
| --not-found-re |  | Yes | Yes | RegEx \(python.re\) for check negative web-server response  \(code 404 analogue\) |
| --not-found-size |  | Yes | Yes | Size of negative answer \(code 404 analogue\). Remember, this size can be different in different tools. Use test mode for get right size. |
| --not-found-codes |  | Yes | No | Status codes, analogues of 404. Separated by comma. |
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

