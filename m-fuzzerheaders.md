# \[M\] FuzzerHeaders

### Common description

Module using for HTTP headers fuzzing with one or multiple URLs. All list of headers you may get in bases/fuzzer/headers.txt. You must specify list of already known URLs in «--urls-file» param. For every URL WS generate multiple requests with one modified header per once. String from bases/fuzzer/evil-value.txt using as value of header. WS report to you about some headers if server response 500 status code, or if response body contains phrases from file bases/bad-words.txt.

Module work only in «raw» mode.

### Options \(\* - necessary\)

| Name | By default | Description |
| :--- | :--- | :--- |
| --urls-file \* |  | Path to already known URLs list. Host of this URLs and target host may not be equal. |
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