# \[M\] FormBruter

### Common description

Module using for forms bruteforce. In «raw» mode requests sends by POST method. In «selenium» mode bruteforce doing according to target site logic. Passwords getting from dictionary.

### Attack configuration

Config for bruteforce in «raw» mode is POST params with markers «^USER^» and «^PASS^» on relevant places. Result string put in «--conf-str» param. Examples: 

* login=^USER^&password=^PASS^ 
* {"login":"^USER^","pwd":"^PASS^"}

After marker string must contains tab-symbol \(\t\). And after that, put there CSS selector of element. Example:

```text
^USER^ #user 
^PASS^ #pass 
^SUBMIT^ #submit
```

With this configuration WS put login in text field id=user, password go to text field id=pass. After that WS will click by element id=submit.

### Options

{% hint style="info" %}
Params «-conf-file», «--conf-str» - you must specify one of them. Params «--true-phrase», «--false-phrase», «--false-size» too.
{% endhint %}

