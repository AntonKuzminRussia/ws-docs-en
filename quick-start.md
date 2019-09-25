# Quick Start

### URLs search

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

## Discovery new Content

Discovery new URLs:

```text
./main.py ContentDiscovery --template http://simple.polygon.web-scout.online/@ --urls-file bases/demo/cd-urls.txt 
```

## Search params of URL 

Params search by GET method \(in URL\) by dict:

```text
./main.py ParamsDict --url http://simple.polygon.web-scout.online/params-bruter-dict-get.php --dict bases/demo/dict.txt --max-params-length 1000 --params-method GET --not-found-re NOT
```

Params search by GET method \(in URL\) by mask:

```text
./main.py ParamsMask --url http://simple.polygon.web-scout.online/params-bruter-dict-get.php --mask ?l,1,2 --max-params-length 1000 --params-method GET --not-found-re NOT
```

Searching params of file upload script:

```text
./main.py ParamsDict --url http://simple.polygon.web-scout.online/params-bruter-dict-files.php --dict bases/demo/dict.txt --max-params-length 10 --params-method FILES --not-found-re NOT
```

## Brutoforce form

Simple POST form bruteforce:

```text
./main.py Forms --url http://simple.polygon.web-scout.online/admin.php --dict bases/demo/dict.txt --conf-str "login=^USER^&password=^PASS^" --false-re "User: " --login admin
```

Bruteforce form in selenium mode:

```text
./main.py Forms --url http://selenium.polygon.web-scout.online/admin.php --dict bases/demo/dict.txt --conf-file bases/demo/form-brute.conf --false-re "User: " --login admin --selenium 1 --browser-wait-re "checking"
```

## Find subdomains

Simple subdomains search by dict:

```text
./main.py DnsDict --template @.standart-zone.polygon.web-scout.online --dict bases/demo/dict.txt
```

Simple subdomains search by mask:

```text
./main.py DnsMask --template @.standart-zone.polygon.web-scout.online --mask ?l,1,4
```

## Find virtual hosts

Searching virtual hosts on IP by dict:

```text
./main.py HostsDict --ip 82.146.56.21 --dict bases/demo/dict.txt --template @.hostsbrute.polygon.web-scout.online --false-re "Ubuntu Default Page"
```

Searching virtual hosts on IP by mask:

```text
./main.py HostsMask --ip 82.146.56.21 --mask ?l,1,4 --template @.hostsbrute.polygon.web-scout.online --false-re "Ubuntu Default Page"
```


## Fuzzing

URLs params fuzzing:

```text
./main.py FuzzerUrls --urls-file bases/demo/fuzzer-urls.txt
```

URLs headers fuzzing:

```text
./main.py FuzzerHeaders --urls-file bases/demo/fuzzer-headers.txt
```