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
```

```
```


