# Test mode

All modules supports test mode run. You can enable it by «--test=1» param. In this mode module request first 3 items \(domains, URLs, …\) from dict/mask and show results to you. This mode can help you to known rights signs of \(not\)found objects.

Example for DafsDict:

```text
http://site.com/a => {'positive': True, 'code': 200, 'size': 276}
http://site.com/b => {'positive': True, 'code': 200, 'size': 276}
http://site.com/c => {'positive': True, 'code': 200, 'size': 276}
```

Here you can see module requested URLs /a, /b, /c. Module «think» it exists \(positive=True\), server responses has code 200 and size of responses — 276. This may suggest that target site response on every not found requests by code 200 and content with size 276. You may specify param «--nof-found-size=276» and WS start see this URLs \(/a,/b,/c\) like not found \(404\). Important: Different tools may show you different response size for same request. If you want use response size for work, run WS in test mode and use size from results.

One more example, test mode of DnsBruteDict:

```text
antivirus.site.com => {'ip': '1.1.1.1', 'dns': '8.8.8.8', 'positive': True}
beta.site.com => {'ip': '1.1.1.1', 'dns': '8.8.8.8', 'positive': True}
test.site.com => {'ip': '1.1.1.1', 'dns': '8.8.8.8', 'positive': True}
```

Module found them «alive» with same IP. It may be result of wildcard DNS record. In this case we may use param «--ignore-ip 1.1.1.1» or «--http-not-found-re» with keyphrase from web-server response about host not exists.

