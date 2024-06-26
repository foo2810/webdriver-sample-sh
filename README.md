# Example of using webdriver with shell scripts

Example of using webdriver with shell scripts

In general, automated browsing is implemented using a webdriver wrapped in a library such as selenium.
However, for simple automation, browsing can also be automated with shell scripts.
This repository provides an example of shell script-based automated browsing.


## Preliminary 

This project uses firefox, [geckodriver](https://github.com/mozilla/geckodriver), and jq command.
The geckodriver is webdriver for firefox.

The samples in this repository are intended to work on Linux, but may be on other platforms as well.

First install firefox.
```
$ dnf install firefox jq
```

Next, obtain the webdriver binary from the geckodriver Github project.
In this example, version 0.34.0 is used.
```
$ curl -LO https://github.com/mozilla/geckodriver/releases/download/v0.34.0/geckodriver-v0.34.0-linux64.tar.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100 3173k  100 3173k    0     0  1941k      0  0:00:01  0:00:01 --:--:-- 5736k

$ tar -xf geckodriver-v0.34.0-linux64.tar.gz 

$ ls
fetch-html  firefox-headless  geckodriver  geckodriver-v0.34.0-linux64.tar.gz  LICENSE  README.md
```


## Example

`fetch-html` retrieves HTML source after executing javascript.
```
$ ls
fetch-html  firefox-headless  geckodriver  geckodriver-v0.34.0-linux64.tar.gz  LICENSE  README.md

$ ./geckodriver -b $(realpath firefox-headless) &> geckodriver.log &

$ ./fetch-html https://google.com
<html itemscope="" itemtype="http://schema.org/WebPage" lang="ja"><head><meta charset="UTF-8"><meta content="origin" name="referrer"><meta content="/images/branding/googleg/1x/googleg_standard_color_128dp.png" itemprop="image"><title>Google</title><script src="https://apis.google.com/_/scs/abc-static/_/js/k=gapi.gapi.en.iZZZ0XsR8bM.O/m=gapi_iframes,googleapis_client/rt=j/sv=1/d=1/ed=1/am=AAAQ/rs=AHpOoo_0-97nH_2IxP0suYF105-PdJv4zg/cb=gapi.loaded_0" nonce="I6owNRxCYzDvb2m0QJxIgQ" async="">
...
```


## License

These software may be freely used under the MIT License. See the LICENSE file for copyright information and license notice.

