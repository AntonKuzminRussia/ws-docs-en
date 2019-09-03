# \[M\] ContentDiscovery

### Common description

Using for directory and files search based on popular names/exts dictionary and already known URLs.

Important. ContentDiscovery is dictionary generating wrap for DafsDict module. When dict is ready, WS start DafsDict module with same options \(which you run ContentDiscovery\). It mean, ContentDiscovery has logic and params of DafsDict. It has only two own params described below.

### Dictionary generation

In start of work module generate dictionary with creating words by next schemes:

1. Years from 2010 to current 
2. Names from base bases/content-discovery/base.txt in clear form and with extensions from param «--discovery-exts» 
3. Names from bases/content-discovery/tools-and-others.txt 
4. All combinations of letters \(lower case\) and digits with length 1 and 2 symbols \(mask ?l?d,1,2\). In clear form and with exts from «--discovery-exts»

If you specified already known URLs list in «--urls-file» params, names for search generating base on it too. Every URL split on parts \(/a/b/c =&gt; a, b, c\). Name of file counts with extension and without it \(/a/log.txt =&gt; a, log, log.txt\). For every part of URL WS generate variants by next schemes:

1. Clear form \(without modifications\) 
2. Backup names. Templates for it takes from bases/content-discovery/backup-schemas.txt. 
3. Variants with changed numbers in start and end of name. Description of this process you can find in «Generating names with digits» below. 
4. Variants with extensions from «--discovery-exts» param.

Remember, module make search only in concrete directory which you specify in «--template» param. URLs from «--urls-file» not go in work, only pieces of it \(like described upper\).

### Generating names with digits

If number in the beginning of the name, module generate variants with numbers from 1 to 9 at this place \(1admin =&gt; 2admin, 3admin, …, 9admin\). With digits in the end same logic \(admin1=&gt;admin2,...,admin9\). Names of files modifying before extensions \(admin1.php =&gt; admin2.php, …, admin9.php\).

If we has digits in both positions \(start and end\), module generate variants with one digit in both places \(1admin1 =&gt; 2admin2, 3admin3,…\).

In current time modifying only first and last digits in name. For example, in «12admin34.php» only 1 and 4 will be changed.

### Generating names with letters

If letter in the beginning of the name, module generate variants with all letters in same case at this place \(admin =&gt; bdmin, cdmin, …, zdmin\). With letter in the end, same logic \(admin =&gt; admia,...,admib\). Names of files modifying before extensions \(admin.php =&gt; admia.php, …, admiz.php\).

### Options

{% hint style="info" %}
All other options you may get in DafsDict docs
{% endhint %}

### Опции \(\* - обязательные\)

| Имя | По умолчанию | raw | selenium | Описание |
| :--- | :--- | :--- | :--- | :--- |
| --urls-file |  | Да | Да | Path to already known URLs list. Host of this URLs and target host may not be equal. |
| --discovery-exts | php,html,js,log,txt | Да | Да | Extensions list for names generation. |
