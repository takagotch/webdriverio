### webdriverio
---
https://github.com/webdriverio/webdriverio

```
mkdir webdriverio-test && cd webdriverio-test

curl -L https://github.com/mozilla/geckodriver/releases/download/v0.21.0/geckodriver-v0.21.0-linux64.tar.gz | tar xz

curl -L https://github.com/mozilla/geckodriver/releases/download/v0.21.0/geckodriver-v0.21.0-macos.tar.gz | tar xz

choco install selenium-gecko-driver

/path/to/binary/geckodriver --port 4444
./geckodriver --port 4444

npm install webdriverio

node test.js
npm i --save-dev @wdio/cli
./node_modules/.bin/wdio config

mkdir -p ./test/specs
touch ./test/specs/basic.js
./node_modules/.bin/wdio wdio.conf.js

npm install --save-dev @babel/core @babel/cli @babel/preset-env @babel/register
```

```js
$url = "https://github.com/mozila/geckodriver/releases/download/v0.21.0/geckodriver-v0.21.0-win64.zip"
$output = "geckodriver.zip"
$unzipped_file = "geckodriver"

[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12

Invoke-WebRequest -Uri $uri -OutFile $output

Expand-Archive $output -DestinationPath $unzipped_file
cd $unzipped_file

[System.Environment]::SetEnvironmentVariable("PATH", "$Env:Path,$pwd\geckodriver.exe", [System.EnvironmentVariableTarget]::Machine)


const { remote } = require('webdriverio');
(async () => {
  const browser = await remote({
    logLevel: 'error',
    path: '/',
    capabilities: {
      browserName: 'firefox'
    }
  });
  
  await browser.url('https://webdriver.io');
  
  const title = await browser.getTitle();
  console.log('Title was: ' + title);
  
  await browser.deleteSession();
}).catch((e) => console.error(e));


path: '/',

exports.config = {
  path: '/',
  
  runner: 'local',
}

const assert = require('assert');

describe('webdriver.io page', () => {
  it('should have the right title', () => {
    browser.url('https://webdriver.io');
    const title = browser.getTitle();
    assert.equal(title, 'WebdriverIO - Next-gen WebDriver test framework for Node.js');
  });
});


const { remote } = require('webdriverio');

(async () => {
  const browser = await remote({
    logLevel: 'trace',
    capabilities: {
      browserName: 'chrome'
    }
  })
  
  await browser.url('https://duckduckgo.com/')
  
  const inputElem = await browser.$('#search_form_input_homepage')
  
  const inputElem = await browser.$('#search_from_input_homepage')
  await inputElem.setValue('WebdriverIO')
  
  const inputElem = await brower.$('#search_form_input_homepage')
  await inputElem.setValue('WebdriverIO')
  
  const submitBtn = await brower.$('#search_button_homepage')
  await submitBtn.click()
  
  console.log(await browser.getTitle())
  
  await browser.deleteSession()  
})().catch((e) => console.error(e))


describe('DuckDuckGo search', () => {
  it ('search for WebdriverIO', () => {
    browser.url('https://duckduckgo.com/')
    
    $('#serch_form_input_homepage').setValue('WebdriverIO')
    $('#search_button_homepage').click()
    
    const title = browser.getTitle()
    console.log('Title is: ' + title)
  })
})

// wdio.conf.js
exports.config = {
  
  afterTest: (test) => {
    console.log(`Finished test "$(test.parent) - ${test.title}"`);
  }
}


module.exports = {
  presets: [
    ['@babel/preset-env', {
      targets: {
        node: 8
      }
    }]
  ]
}

before: function(){
  require('@babel/register');
},

mochaOpts: {
  ui: 'bdd',
  compilers: ['js:@babel/register'],
  require: ['./test/helpers/common.js']
},

before: funciton() {
  require('ts-node').register({ files: true });
},

mochaOpts: {
  ui: 'bdd',
  require: [
    'tsconfig-paths/register'
  ]
},

require("ts-node/register")
module.exports = require("wdio.conf.ts")

const config: WebdriverIO.Config = {
}
export { config }

import { Suite, Test } from "@wdio/mocha-framework"

const elem = $('h2.subheading a');
elem.click();

const link = $('=WebdriverIO');
console.log(link.getText());
console.log(link.getAttribute('href'));

const link = $('*=driver');
console.lo(link.getText());

const header = $('h1=Welcome to my Page');
console.log(header.getText());
console.log(header.getTagName());

const header = $('h1*=Welcome');
console.log(header.getText());

const classNameAndText = $('.someElem=WebdriverIO is the best');
console.log(classNameAndText.getText());

const idAndText = $('#elem=WebdriverIO is the best');
console.log(idAndTExt.getText());

const classNameAndPartialText = $('.someElem*=WebdriverIO');
console.log(classNameAndPartialText.getText());

const idAndPartialText = $('#elem*=WebdriverIO');
console.log(idAndPartialText.getText());

const classNameAndText = $('<my-element />');
console.log(classNameAndText.getText());

const paragraph = $('//BODY/P[2]');
console.log(paragraph.getText());

const parent = paragraph.$('..');
console.log(parent.getTagName());

const elem = $('elem')
elem.$(function () { return this.nextSibling.nextSibling })

const selector = 'ne UiSelector().text("Cancel").className("android.widget.Button")';
const Button = $(`android=${selector}`);
Button.click();

const selector = `UIATarget.localTarget().frontMostApp().mainWindow().buttons()[0]`;
const Button = $(`ios=${selector}`);
Button.click();


const selector = 'type == \'XCUIElementTypeSwitch\' && name CONTAINS \'Allow\'';
const Switch = $(`-ios predicate string:${selector}`);
Switch.click();

const selector = '**/XCUIElementTypeCell[`name BEGINSWITCH "D"`]/**/XCUIElementTypeButton';
const Button = $(`-ios class chain:${selector}`);
Button.click();

const elem = $('~my_accessibility_identifier');
elem.click();

$('UIATextField').click();
$('android.widget.DatePicker').click();


$('.row .entry:nth-child(1)').$('button*=Add').click();

import { multiremote } from 'webdriverio';

(async () => {
  const browser = await multiremote({
    myChromeBrowser: {
      capabilities: {
        browserName: 'chrome'
      }
    },
    myFirefoxBrowser: {
      capabilities: {
        browserName: 'firefox'
      }
    }
  });
  
  await browser.url('http://json.org');
  
  const elem = await browser.$('#someElem');
  await elem.click();
  
  await elem.myFirefoxBrowser.click();
});

export.config = {
  
  capabilities: {
    myChromeBrowser: {
      capabilities: {
        browserName: 'chrome'
      }
    },
    myFirefoxBrowser: {
      capabilities: {
        browserName: 'firefox'
      }
    }
  }
};

browser.url('http://chat.socket.io/');

browser.url('https://www.whatismybrowser.com/');

const elem = $('.string-major');
const result = elem.getText();

console.log(result.resultChrome);
console.log(result.resultFirefox);

myChromeBrowser.$('#message').setValue('Hi, I am Chrome');
myChromeBrowser.$('#send').click();

const firefoxMessage = myFirefoxBrowser.$$('.message')

firefoxMessages.waitForExist();

assert.true(
  firefoxMessages.map((m) => m.getText()).includes('Hi, I am Chrome')
)


// wdio.conf.js
var config = {}
if (process.env.CI) {
  config.user = process.env.SAUCE_USERNAME;
  config.key = process.env.SAUCE_ACCESS_KEY;
}
exports.config = config

exports.config = {

  runner: 'local',
  
  hostname: '0.0.0.0',
  port: 4444,
  path: '/wd/hub',
  
  user: 'webdriverio',
  key: 'xxxxxxxxxxxxxxxx',
  
  region: 'us',
  
  specs: [
    'test/spec/**'
  ],
  
  exclude: [
    'test/spec/multibrowser/**',
    'test/spec/mobile/**'
  ],
  
  maxInstances: 10,
  
  maxInstancesPerCapability: 10,
  
  capabilities: [{
    browserName: 'chrome',
    'goog:chromeOptions': {
    }
  }, {
    maxInstances: 5,
    browserName: 'firefox',
    specs: [
      'test/ffOnly/*'
    ],
    "moz:firefoxOptions": {
    }
  }],
  
  execArgv: [],
  
  logLevel: 'info',
  
  bail: 0,
  
  baseUrl: 'http://localhost:8080',
  
  waitforTimeout: 1000,
  
  filesToWatch: [
  ],
  
  framework: 'mocha',
  
  reporters: [
    'dot',
    ['allure', {
      outputDir: './'
    }]
  ],
  
  mochaOpts: {
    ui: 'bdd'
  },
  
  jasmineNodeOpts: {
    
    defaultTimeoutInterval: 5000,
    
    expectationResultHandler: function(passed, assertion){
    },
    
    grep: null,
    invertGrep: null
  },
  
  cucumberOpts: {
    require: [],
    backtrace: false,
    compiler: [],
    dryRun: false,
    failFast: false,
    format: ['pretty'],
    colors: true,
    snippets: true,
    source: true,
    profile: [],
    strict: false,
    tags: [],
    timeout: 20000,
    ignoreUndefineDefinitions: false,
  },
  
  onPrepare: funciton (config, capabilties) {
  },
  
  beforeSession: function (config, capabilities, specs) {
  },
  
  before: funciton(capabilities, specs) {
  },
  
  beforeSuite: function (suite) {
  },
  
  beforeHook: function () {
  },
  
  afterHook: function () {
  },
  
  beforeTest: function (test) {
  },
  
  beforeCommand: funciton (commandName, args) {
  },
  
  afterCOmmand: function(commandName, args, result, error) {
  },
  
  aftertest: funciton (test) {
  },
  
  afterSuite: function (suite) {
  },
  
  after; function (result, capabilities, specs) {
  },
  
  afterSession: function (config, capabilities, specs) {
  },
  
  onComplete: function (exitCode, config, capabilities, results) {
  },
  
  onReload: function(oldSessionId, newSessionId) {
  },
  
  beforeFeature: function (feature) {
  },
  beforeScenario: function (scenario) {
  },
  beforeStep: function (step) {
  },
  afterStep: function (stepResult) {
  },
  afterScenario: funciton (scenario) {
  },
  afterFeature: funciton (feature) {
  }
};
```

```
{
  browserName: 'chrome',
  browserVersion: '27.0',
  platformName: 'Windows 10'
}

reporters: [
  'dot',
  'spec',
  ['junit', {
    outputDir: ___dirname + '/reports',
    otherOption: 'foobar'
  }]
]

{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "*": [./*],
      "src/*": ["./src/*"]
    },
    "types": ["node", "webdriverio"]
  },
  "include": [
    "./src/**/*.ts"
  ]
}

{
  "compilerOptions": {
    "types": ["node", "@wdio/sync"]
  }
}


browserName: 'chrome',
version: '27.0',
platform: 'XP',
'tunnel-identifier': process.env.TRAVIS_JOB_NUMBER,
name: 'integration',
build: process.env.TRAVIS_BUILD_NUMBER
```


