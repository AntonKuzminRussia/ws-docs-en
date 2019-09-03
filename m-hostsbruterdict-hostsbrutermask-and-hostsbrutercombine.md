# \[M\] HostsBruterDict, HostsBruterMask & HostsBruterCombine

### Common description 

This modules using for web-hosts search directly on target servers, without DNS participation. Work of this modules it\`s a HTTP requests sending to target IP with «Host» header contains a hostname. This may be usable for searching hidden hosts with DNS records on internal DNS servers, or fully without them. Or for hosts, which was moved to new server, but not deleted from old server.

Module can search objects by mask, dictionary and by combination \(mask + dict\).

Module works only in «raw» mode.

### Options \(\* - necessary\)

| Name | By default | Description |
| :--- | :--- | :--- |
| --template \* |  | Template for work with mark symbol (@ by default) in place, where target phrase will be put. Examples:  «@.site.com», «@-admin.site.com». |
| --dict \* |  | For HostsBruterDict. Path to dict. |
| --mask \* |  | For HostsBruterMask. Symbols mask. |
| --combine-template \* |  | For HostsBruterCombine. Template for combined work. String with markers «%m%» and «%d%», which is place for dict word and mask word. |
| --ip \* |  | Traget IP. |
| --false-re \* |  | Да | Да | RegEx (python.re) for detect negative answers. |
| --false-size \* |  | Да | Да | Size of negative answer (code 404 analogue). Remember, this size can be different in different tools. Use test mode for get right size. |
| --http-protocol | http | Protocol for requests sending. http/https. |
| --msymbol | @ | Mark symbol for search template (--template) |
| --proxies |  | Да | Да | HTTP-proxy list. |
| --retest-re |  | Да | Да | RegEx (python.re) for check if request repeat is need. For example «Service Temporarily Unavailable». |
| --retest-codes |  | Да | Нет | Set of status codes (separated by comma) as signature for request re-send. |
| --headers-file |  | Да | Нет | File with HTTP headers for put it in work requests. |
| --ignore-words-re |  | Да | Да | RegEx (python.re) for ignoring target phrases. May be useful when you don't want check some phrases, for example contains “.ht”. |
| --msymbol | @ | Да | Да | Mark symbol for search template (--template) |
| --delay | 0 | Да | Да | Delay in seconds  between requests. It`s options not for all threads together, it`s for every thread separately. |
| --threads | 10 | Да | Да | Work threads count. |
| --parts | 0 | Да | Да | Split on X parts target dict or mask. |
| --part | 0 | Да | Да | Which part number we using in work? |
| --test | 0 | Да | Да | Test mode enable |
| --xml-report | 0 | Да | Да | Path to save xml-report |