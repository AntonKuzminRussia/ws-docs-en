# \[M\] DnsDict, DnsMask & DnsCombine

## Common description

Modules using for subdomains search by bruteforce methods. Contains functions for search throw wildcard records.

Modules working by sending requests other DNS servers from bases/dns-servers.txt. By default this list contains some public DNS. But in some cases will be better if you put there DNS servers of target domain \(speed up\).

Every working thread get DNS server from list by queue, from first to last. If threads count more than servers, selection go around. Remember, big threads count with small DNS servers count can make big stress for every DNS and you may got IP blocking on server side.

WS got two functions for wildcard records. First, simplest, it's ignore of default IP address in results. This solution allow save bruteforce speed, but may skip real subdomains placed on default IP address. Second — sending «HTTP GET /» on every found subdomain and searching some phrase in response. Speed slow down here, but you not skip exists subdomains. If using both method, IP ignoring will be first check. HTTP requests will be send if IP was not ignored.

Module can search objects by mask, dictionary and by combination \(mask + dict\).

Working only raw mode.

## Examples

Simple subdomains search:

```text
./ws.py DnsDict --template @.standart-zone.polygon.web-scout.online --dict bases/demo/dict.txt
```

Simple subdomains search by mask:

```text
./ws.py DnsMask --template @.standart-zone.polygon.web-scout.online --mask ?l,1,4
```

Searching subdomains in wildcard-zone with default IP ignoring:

```text
./ws.py DnsDict --template @.wildcard-ip.polygon.web-scout.online --dict bases/demo/dict.txt --ignore-ip 8.8.8.8
```

Searching subdomains in wildcard-zone by requesting it on web-server:

```text
./ws.py DnsDict --template @.wildcard-web.polygon.web-scout.online --dict bases/demo/dict.txt --http-not-found-re "Ubuntu Default Page"
```

## Options \(\* - necessary\)

| Name | By default | Description |
| :--- | :--- | :--- |
| --template \* |  | Template for work with mark symbol \(@ by default\) in place, where target phrase will be put. Examples:  «@.site.com», «@-admin.site.com». |
| --dict \* |  | For DnsBruterDict. Path to dict. |
| --mask \* |  | For DnsBruterMask. Symbols mask. |
| --combine-template \* |  | For DnsBruterCombine. Template for combined work. String with markers «%m%» and «%d%», which is place for dict word and mask word. |
| --dns-protocol | auto | Protocol for DNS servers. May be «udp», «tcp», «auto». If «auto», servers first check for TCP support. If it not — using UDP. If some server not response on TCP/UDP requests — it ignoring. |
| --zone | A | DNS-zone for bruteforce. It may be «А» and «CNAME». |
| --http-not-found-re |  | RegEx \(python.re\) for detect «not found» responses. Using in work with wildcard zones. If you set it, WS will send HTTP GET / to every founded host. |
| --http-protocol | http | Protocol for sending HTTP GET / requests. «http»/«https». |
| --http-proxies |  | Proxies list |
| --http-retest-re |  | RegEx \(python.re\) for check HTTP response if request repeat is need. For example «Service Temporarily Unavailable». |
| --headers-file |  | File with HTTP headers for put it in work requests. |
| --ignore-ip |  | WS will ignore this IP in positive detections. For wildcard zones. |
| --msymbol | @ | Mark symbol for search template \(--template\) |
| --delay | 0 | Delay in seconds  between requests. It's options not for all threads together, it's for every thread separately. |
| --threads | 10 | Work threads count. |
| --parts | 0 | Split on X parts target dict or mask. |
| --part | 0 | Which part number we using in work? |
| --test | 0 | Test mode enable |
| --xml-report | 0 | Path to save xml-report |

