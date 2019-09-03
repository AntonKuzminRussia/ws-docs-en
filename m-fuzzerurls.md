# \[M\] FuzzerUrls

### Common description 

Module using for URLs params fuzzing. It works by GET mode at this time. You must specify list of already known URLs in «--urls-file» param. For every param WS generate requests with some modifications \(one param per once\). You can find modification templates in bases/fuzzer/templates.txt. Templates has markers «\|name\|» for place param's name, and «\|value\|» for place param's value \(from origin URL\). For example, for URL «[http://site.com/file.php?a=1&b=2»](http://site.com/file.php?a=1&b=2») and template «\|name\|\[\]\[\]=\|value\|» WS request next URLs: • [http://site.com/file.php?a\[\]\[\]=1&b=2](http://site.com/file.php?a[][]=1&b=2) • [http://site.com/file.php?a=1&b\[\]\[\]=2](http://site.com/file.php?a=1&b[][]=2) WS report to you about some headers if server response 500 status code, or if response body contains phrases from file bases/bad-words.txt.

Module works in «raw» and «selenium» modes.

