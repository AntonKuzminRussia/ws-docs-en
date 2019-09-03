# \[M\] FuzzerHeaders

### Common description

Module using for HTTP headers fuzzing with one or multiple URLs. All list of headers you may get in bases/fuzzer/headers.txt. You must specify list of already known URLs in «--urls-file» param. For every URL WS generate multiple requests with one modified header per once. String from bases/fuzzer/evil-value.txt using as value of header. WS report to you about some headers if server response 500 status code, or if response body contains phrases from file bases/bad-words.txt.

Module work only in «raw» mode.

