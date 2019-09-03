# \[M\] DafsDict, DafsMask & DafsCombine

### Common description

Using for files and directories search on target web-sites \(DAFS — abbreviation of «Directories and Files Search»\). Search made by template with mark symbol which replacing by target name.

Like «Not Found» response signature \(404 status code\) you may using regexps \(matches searching in response headers and body\), response size, different status codes. Besides, you may use param for regexp for detecting found pages \(status code 200 analogue\).

If you specify more than one signature of positive/negative responses, they be have next priority:

1. Regexp for detect positive response \(status code 200 analogue\) 
2. Size of negative response 
3. Regexp for detect negative response \(status code 404 analogue\) 
4. Status codes which negative responses

If one of this signatures detect existing item, it stop other detections. Example. You specify regexp «found» like positive response signature. WS make request of item X and get response with status code 404 and phrase «found» in body. WS get it as existing element \(like status code 200\) because regexp of positive response more priority than status codes check.

Module can search objects by mask, dictionary and by combination \(mask + dict\).

Module working in «raw» and «selenium» modes.

