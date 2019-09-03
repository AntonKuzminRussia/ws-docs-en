# Selenium

Scanning with Selenium using for bypass bot- and ddos-protections. Usually, at first site visit this protections run some javascript code which made some actions. For example, write some cookies or wait some time. If primitive bot get this page, it can`t run javascript and can`t get really site content. Selenium allow make all actions with real browser and successfully bypass this protections.

Selenium-mode enable by param «--selenium=1». In documentation of every module you may see does it works in this mode.

Also you can \(but must not\) specify param «--browser-wait-re». In this param you may put regex for detect in HTML page source code a signature for some waiting. For example, human action need \(solve captcha\), or some waiting need \("wait X secs, we check your browser"\). WS will wait until this match not disappear.

Content of this param you may detect very simple. Get some page of target host by primitive mechanism list cli curl or wget \(no browser\). If protection exists, in response you see this code. Take any phrase from it and put in param.

When you use selenium you must remember — selenium work require more time and system resources unlike simple multi-thread scan. Usual work by raw HTTP\(s\) in 10 threads «eat» small resources, but 10 selenium threads may get one-two GB of RAM because every thread it’s a full individual browser. By this reason in WS exists threads limit for selenium mode \(5 by default\). You can change it in config.ini, section «\[selenium\]», param «max\_threads».

For selenium mode WS use a Firefox browser. Path to it you must specify in config.ini, section «\[selenium\]», param «firefox\_path». By default it is «/usr/bin/firefox», but in your case it must be other.

By default you will see browsers because param «virtual\_display» in config.ini have value «0». So you may see a work process and stop/correct it if need. If you specify this param «1» - browsers will open in virtual display and you will not see it. This solution allow to start selenium-scanning on VDS without XWindows. You must remember what this work mode is very capricious and at this moment not fully tested. Better if you first test concrete scan in visible mode.

At current moment selenium-mode have some unpleasant features. In load page process browser load some third party elements — icons, scripts, fonts, etc. Sometimes this requests may freeze on loading stage or data transfer stage. Now this problem partially solved by disabling css, images and flash loading in config.ini \(see section Configuration\). But, this trouble may interfere for you. More one solve — param «timeout\_page\_load» in config.ini. It’s a page loading timeout for Firefox. By default it’s 15 seconds. But if every page will load 15 seconds, full scan time will very big. In this case you may put problem host in /etc/hosts with IP 127.0.0.1 \(if this host not target or you use proxy\).

And one important moment. In selenium-mode not work limit of response content size from config.ini «max\_size» and by mime-types.

