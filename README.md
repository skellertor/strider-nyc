# strider-nyc

**Getting started**

1. ```cd strider```
2. ```npm install https://github.com/skellertor/strider-nyc.git --save```

**Description**

This plugin is currently under development.  Right now it runs coverage and unit tests.  It leverages [mocha](https://github.com/mochajs/mocha) and [nyc](https://github.com/istanbuljs/nyc).  By default it only looks in the ```test``` directory for unit tests.  It will run through every directory for coverage results unless specified in the package.json in the `nyc` stanza. 

You can specify which files/directories to include or exclude from coverage tests by including the following options. Just add the `nyc` stanza to the package.json of the project you want to test.

```json
{
  "nyc": {
    "include": [
      "src/**/*.js"
    ],
    "exclude": [
      "src/**/*.spec.js"
    ],
    "extension": [
      ".jsx"
    ]
  }
}
```

**Configuring for Strider-CD**

Currenty there are no configuration options for this plugin within strider.  Just add the plugin to your desired repo and click `enable` on the plugin tile.  If you used the default nodejs plugin to prepare, test, and deploy make sure you set the nodejs plugins `test command` to `no test command`.

**Output**

strider-nyc outputs the test result into the strider phaux terminal.  It also appends test results to the strider `job` object.  It is a top level object on the `job` object named `test_results`. It also appends a string value named `coverage_results`.  This is just a summary of the coverage results.  Lastly it appends a string labeled `coverage_results_url`.  This is a link to a detailed coverage description.  The `coverage_results_url` will only work if the repositories that were cloned live in the default loctation which is ```~/.strider/data/{{org}}-{{repo}}-{{branch}}/job-xxxxxxxxx```.  The original intentions of appending the results to the `job` object was to make it accessible to such plugins like strider-slack.

**TODO**

* Show results in alert box above strider faux terminal
