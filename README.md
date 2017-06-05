UI Recorder
=======================

![logo.png](https://raw.github.com/alibaba/uirecorder/master/logo.png)

[![NPM version](https://img.shields.io/npm/v/uirecorder.svg?style=flat)](https://www.npmjs.com/package/uirecorder)
[![License](https://img.shields.io/npm/l/uirecorder.svg?style=flat)](https://www.npmjs.com/package/uirecorder)
[![NPM count](https://img.shields.io/npm/dm/uirecorder.svg?style=flat)](https://www.npmjs.com/package/uirecorder)
[![NPM count](https://img.shields.io/npm/dt/uirecorder.svg?style=flat)](https://www.npmjs.com/package/uirecorder)

UI Recorder is a zero cost UI test case recorder like [Selenium IDE](http://docs.seleniumhq.org/projects/ide/).

UI Recorder is more powerful than Selenium IDE!

UI Recorder is easy to use.

1. Official Site: [http://uirecorder.com/](http://uirecorder.com/)
2. Language Switch: [English](https://github.com/alibaba/uirecorder/blob/master/README.md), [简体中文](https://github.com/alibaba/uirecorder/blob/master/README_zh-cn.md), [繁體中文](https://github.com/alibaba/uirecorder/blob/master/README_zh-tw.md)
3. Change log: [CHANGE](https://github.com/alibaba/uirecorder/blob/master/CHANGE.md)
4. Video Tutorial：[PC中文教程](http://v.youku.com/v_show/id_XMTY4NTk5NjI4MA==.html)

Features
================

1. Support all user operation: key event, mouse event, alert, file upload, drag, svg, shadow dom
2. Support mobile native APP(Android, iOS) recorde, powered by macaca: [https://macacajs.com/](https://macacajs.com/)
3. No interference when recording: the same as self test
4. Record test file saved in local
5. Support kinds of expect: val,text,displayed,enabled,selected,attr,css,url,title,cookie,localStorage,sessionStorage
6. Support powerful var string
7. Support common test case: one case call another
8. Support parallel test
9. Support i18n: en, zh-cn, zh-tw
10. Support screenshots after each step
11. Support HTML report & JUnit report
12. Support multi systems: Windows, Mac, Linux
13. Test file base on NodeJs: [jWebDriver](http://jwebdriver.com/)

Screenshots
================

![shot1](https://raw.github.com/alibaba/uirecorder/master/screenshot/shot1.png)

![shot2](https://raw.github.com/alibaba/uirecorder/master/screenshot/shot2.png)

![shot3](https://raw.github.com/alibaba/uirecorder/master/screenshot/shot3.png)

![shot4](https://raw.github.com/alibaba/uirecorder/master/screenshot/shot4.png)

Video demo
================

![video1](http://wx1.sinaimg.cn/mw1024/7f3afc78gy1fdf5gass5rg20sg0g0kjo.gif)

![video2](http://wx2.sinaimg.cn/mw1024/7f3afc78gy1fdf5hb8anig20sg0g0u12.gif)

Quick start
================

Install
--------------------------

1. Install NodeJs (version >= v7.x)

    > [https://nodejs.org/](https://nodejs.org/)

    > `sudo chown -R $(whoami) $(npm config get prefix)/{lib/node_modules,bin,share}` (Mac, Linux)

2. Install chrome

    > [https://www.google.com/chrome/](https://www.google.com/chrome/)

3. Install UI Recorder

    > `npm install uirecorder mocha -g`

PC record
---------------------------

1. Init test project

    > Create new folder

    > `uirecorder init`

2. Start record test case

    > edit hosts file

    > `uirecorder sample/test.spec.js`

3. Start WebDriver Server

4. Run test case

    > Run all case: `source run.sh` ( Linux|Mac ) or `run.bat` ( Windows )

    > Run single case: `source run.sh sample/test.spec.js` ( Linux|Mac ) or `run.bat sample/test.spec.js` ( Windows )

5. Get reports & screenshots

    > ./reports/index.html

    > ./reports/index.xml (JUnit)

    > ./reports/index.json

    > ./screenshots/

Mobile record
---------------------------

1. Install & start macaca server:

    > Install macaca: [http://macacajs.com/](http://macacajs.com/)

    > Connect your mobile or open emulator

    > `macaca server --port 4444`

2. Init test project

    > Create new folder

    > `uirecorder init --mobile`

3. Start record test case

    > `uirecorder --mobile sample/test.spec.js`

4. Run test case

    > Run all case: `source run.sh` ( Linux|Mac ) or `run.bat` ( Windows )

    > Run single case: `source run.sh sample/test.spec.js` ( Linux|Mac ) or `run.bat sample/test.spec.js` ( Windows )

5. Get reports & screenshots

    > ./reports/index.html

    > ./reports/index.xml (JUnit)

    > ./reports/index.json

    > ./screenshots/

QA
================

How to debug test code
----------------

1. Install [Visual Studio Code](https://code.visualstudio.com/) & open Visual Studio Code
2. Open the project root folder by vs code
3. Open test file, add break point
4. press `F5` key to start, press `F10` key to run next line

How to deploy WebDriver Server
----------------

1. How to run selenium standalone server?

    > `npm run server`

2. Selenium Grid: [https://github.com/SeleniumHQ/selenium/wiki/Grid2](https://github.com/SeleniumHQ/selenium/wiki/Grid2)
3. F2etest: [https://github.com/alibaba/f2etest](https://github.com/alibaba/f2etest)

How to change webdriver host & port by env temporary, debug for local?
----------------

1. `export webdriver=127.0.0.1:4444` or `set webdriver=127.0.0.1:4444` (Windows)

Tip: port is not required, For example: `export webdriver=127.0.0.1`

How to dock Jenkins?
----------------

1. Add commands

        source ./install.sh
        source ./run.sh

2. Add reports

    > [JUnit](https://wiki.jenkins-ci.org/display/JENKINS/JUnit+Plugin): `reports/index.xml`

    > [HTML](https://wiki.jenkins-ci.org/display/JENKINS/HTML+Publisher+Plugin): `reports/index.html`

How to filter unstable path
----------------

1. Because some attribute values are random or unstable, we can't record a stable CSS selector
2. We can filter the attributes with a blacklist. You can type `uirecorder init` and then input the blacklist from the command line

Tip: blacklist is a regex, you can use it like this: `/attr_\d+/`

How to record common test case?
----------------

1. Record `commons/login.mod.js`
2. Record `sample/test.spec.js`

    1. please input `login.mod.js` in recorder start page or jump test case in page
    2. After `login.mod.js` loaded, then recorder other steps

3. `source run.sh` ( Linux|Mac ) or `run.bat` ( Windows )

How to record file upload?
----------------

1. UI Recorder only support native file compont, no support for Flash
2. direct click `<input type="file">` or click `<button role="upload">Upload file</button>`, the placeholder button must mark as `upload` with `role` or `data-role`
3. File must save to `uploadfiles/` directory

How to use vars
----------------

edit config.json

    {
        "recorder": {
            ...
        },
        "webdriver": {
            ...
        },
        "vars": {
            "productId": "123456",
            "productName": "mp3"
        }
    }

1. start with url: `http://xxx.com/product?id={{productId}}`
2. add new var with tool panel
3. update var with tool panel
4. jump url with tool panel: `http://xxx.com/product?id={{productId}}`
5. insert vars string with tool panel: `{{productName}}` or `aaa{{productName}}bbb`
6. expect to var string: `{{productName}}` or `aaa{{productName}}bbb`

Tip: All var string also support js template string, For example: `{{productName}}, ${new Date().getTime()}, ${parseInt(testVars.a)+parseInt(testVars.b)}`


How to add hover multiple or add expect after a hover?
----------------

1. Press down `Ctrl` or `Command` button
2. Click `Add Hover` Button, enter hover mode
3. Release `Ctrl` or `Command` button
4. Click the dom you want to hover (can add multiple)
5. Click `Add Expect` Button
6. Click the dom you want to expect
7. Press `Esc` button or click `End Hover` Button, exit hover mode

How to expect the value after js eval in front browser?
----------------

1. `Add Expect`, select type `jscode`
2. sync mode: `return document.title`
3. function mode:

        function(){
            var str = "aaa";
            return str;
        }

4. async mode:

        function(done){
            setTimeout(function(){
                done(123);
            }, 100);
        }

How to hide doms before expect?
----------------

1. `uirecorder init`
2. Input css selector when init `Hide before expect`
3. `uirecorder start`
4. UIRecorder will hide matched doms before expect, then you can expect the dom behind the mask div

How to record option click?
----------------

Some steps is not very important, but occasionally displayed, this steps will expect to success always.

1. Press 'Alt' button
2. Click the target DOM

Can't do when recording
----------------

1. don't change url in location bar
2. don't change focus by TAB key
3. don't use dblclick, WebDriver no support
4. don't select text by mouse, WebDriver no support
5. don't focus to background window manualy
6. don't click useless DOM, only record key steps

How develop test friendly code?
----------------

1. please dont't use random id or name
2. please name a id for DOM area
3. add label for form
4. please listen click event instead of mousedown

How to set udid to mobile test?
----------------

1. `export devices=xxx1,xxx2` (windows: `set devices=xxx1,xxx2`)
2. `source run.sh` ( Linux|Mac ) or `run.bat` ( Windows )

How to save raw cmds json?
----------------

1. `uirecorder start --raw`
2. After test saved, then you can get 2 files: `sample/test.spec.js`, `sample/test.spec.json`

Other Tips
----------------

1. Mac system: localhost must place in hosts

License
================

HTMLHint is released under the MIT license:

> The MIT License
>
> Copyright (c) 2016 - 2017 alibaba.com
>
> Permission is hereby granted, free of charge, to any person obtaining a copy
> of this software and associated documentation files (the "Software"), to deal
> in the Software without restriction, including without limitation the rights
> to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
> copies of the Software, and to permit persons to whom the Software is
> furnished to do so, subject to the following conditions:
>
> The above copyright notice and this permission notice shall be included in
> all copies or substantial portions of the Software.
>
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
> IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
> FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
> AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
> LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
> OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
> THE SOFTWARE.

Thanks
================

* jWebDriver: [https://github.com/yaniswang/jWebDriver](https://github.com/yaniswang/jWebDriver)
* colors: [https://github.com/Marak/colors.js](https://github.com/Marak/colors.js)
* commander: [https://github.com/tj/commander.js](https://github.com/tj/commander.js)
* inquirer: [https://github.com/sboudrias/Inquirer.js](https://github.com/sboudrias/Inquirer.js)
* async: [https://github.com/caolan/async](https://github.com/caolan/async)
* chai: [https://github.com/chaijs/chai](https://github.com/chaijs/chai)
* mocha-parallel-tests: [https://github.com/yandex/mocha-parallel-tests](https://github.com/yandex/mocha-parallel-tests)
* Mochawesome: [https://github.com/adamgruber/mochawesome](https://github.com/adamgruber/mochawesome)
