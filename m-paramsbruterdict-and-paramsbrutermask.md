# \[M\] ParamsBruterDict and ParamsBruterMask

### Common description 

Modules searching the parameters for target URL. Work based on changeable URL content depends some parameters.

Now possible 4 search ways — by GET/POST methods, by cookies and files uploading. Search by GET it''s URL request with many params in it. And POST search like it — params puts in request body. Cookies based method it''s requests to target URL with multiple cookies with different names. And files uploading method it''s multiple tries to upload small files on server with different files fields names.

Attention. You may specify count of searching params per request by option «--max-params-length». This option has double meaning. For GET and POST it''s a maximum params string length with values and amps \(a=1&b=1&c=1…\). Recommended value - 1000. For cookies and files this option set a count of names for check per request. Recommended value — 20.

As values of searching params using «1» by default. You can change it by «--value» option.

Module can search objects by mask, dictionary and by combination \(mask + dict\).

Module working in «raw» and «selenium» modes.

