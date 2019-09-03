# \[M\] DnsBruterDict, DnsBruterMask & DnsBruterCombine

### Common description

Modules using for subdomains search by bruteforce methods. Contains functions for search throw wildcard records.

Modules working by sending requests other DNS servers from bases/dns-servers.txt. By default this list contains some public DNS. But in some cases will be better if you put there DNS servers of target domain \(speed up\).

Every working thread get DNS server from list by queue, from first to last. If threads count more than servers, selection go around. Remember, big threads count with small DNS servers count can make big stress for every DNS and you may got IP blocking on server side.

WS got two functions for wildcard records. First, simplest, it's ignore of default IP address in results. This solution allow save bruteforce speed, but may skip real subdomains placed on default IP address. Second — sending «HTTP GET /» on every found subdomain and searching some phrase in response. Speed slow down here, but you not skip exists subdomains. If using both method, IP ignoring will be first check. HTTP requests will be send if IP was not ignored.

Module can search objects by mask, dictionary and by combination \(mask + dict\).

Working only raw mode.

