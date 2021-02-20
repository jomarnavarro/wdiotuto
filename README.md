  #WebdriverIO tutorial

  ##Installation instructions.

     Run the following commands in succession on a unixlike terminal.

* Install nvm
``` curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash```

* Make sure you add NVM's environment variables into the shell profile file

```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```
* Install your favorite version of node.  I chose 12.18.0.
```nvm install 12.18.0```

* cd into your repository folder
```cd ~/repo```

* make the project directory and cd into it.

```
mkdir <project_name>
cd <project_name>
```

* initialize the node project
```npm init```

Upon the prompts, input these answers:

package name: <project_name>
version: (1.0.0)
description: <project_description>
entry point: (index.js)
test command: node ./node_modules/.bin/wdio wdio.conf.js
git repository: empty
keywords: empty
author: <your_name>
license: (ISC)

* Install the following libraries:

```npm install webdriverio --save-dev```
```npm install @wdio/cli```

* Run the configuration for webdriverIO

```./node_modules/.bin/wdio config```

Enter the following options:

? Where is your automation backend located? On my local machine
? Which framework do you want to use? mocha
? Do you want to run WebdriverIO commands synchronous or asynchronous? sync
? Are you using a compiler? No!
? Where are your test specs located? ./test/specs/**/*.js
? Do you want WebdriverIO to autogenerate some test files? No
? Which reporter do you want to use? spec, dot
? Do you want to add a service to your test setup? selenium-standalone
? What is the base url? <project_url>

* Install the following libraries

```npm install chai --save-dev```
```npm install chai-webdriverio --save-dev```
```npm install local-runner --save-dev```

* open wdio.conf.js and navigate to the `beforeTest` section and remove comments.  Then include the following lines of code.

```
...
beforeTest: function (test, context) {
        const chai = require('chai')
        const chaiWebdriver = require('chai-webdriverio').default
        chai.use(chaiWebdriver(browser))
        global.assert = chai.assert
        global.should = chai.should
        global.expect = chai.expect
},
...
```

