# XML-reports

It may be useful for automatization. Every modules has «--xml-report» options where you can specify path to report without extension. Example: «--xml-report /tmp/test». In this case, WS create files /tmp/test-result.xml, /tmp/test-errors.xml и /tmp/test-progress.xml. It was scan results, errors and progress information respectively. 

File -result.xml has next format:

```text
<root>
    <results>
        <item>
..
        </item>
        <item>
...
        </item>
</root>
```

Different modules has different structure of  tag. You can see it by start module with this option.

Format of -errors.xml:

```text
<root>
    <errors>
        <error>
            <text>some error</text>
            <trace>...</trace>
            <timestamp>1557102331</timestamp>
        </error>
        ...
    </errors>
</root>
```

Errors stop logging when their count getting bigger when 1000.

Format of -progress.xml:

```text
<root>
    <progress>
        <count_now>9000</count_now>
        <full_count>71746</full_count>
        <percent_done>12.54</percent_done>
        <time_now>35s</time_now>
        <time_left>3m 54s</time_left>
        <speed>272.45</speed>
    </progress>
</root>
```

File refresh every time when WS flush in cli progress string. Here:

* count\_now — items checked at this moment 
* full\_count — all items count 
* percent\_done — percent of done items 
* time\_now — WS work time from start 
* time\_left — work time left 
* speed — work speed, objects in seconds

