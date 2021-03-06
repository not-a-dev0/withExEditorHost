EN | [JA](./README.ja.md)

[![Build Status](https://travis-ci.org/asamuzaK/withExEditorHost.svg?branch=master)](https://travis-ci.org/asamuzaK/withExEditorHost)
[![dependencies Status](https://david-dm.org/asamuzaK/withExEditorHost/status.svg)](https://david-dm.org/asamuzaK/withExEditorHost)
[![devDependency Status](https://david-dm.org/asamuzaK/withExEditorHost/dev-status.svg)](https://david-dm.org/asamuzaK/withExEditorHost?type=dev)
[![GitHub release](https://img.shields.io/github/release/asamuzaK/withExEditorHost.svg)](https://github.com/asamuzaK/withExEditorHost/releases)

# withExEditorHost

Native messaging host for browser extension *withExEditor*.
The browser interacts with the host via messages, and the editor is executed by this host.

* [withExEditor :: Add-ons for Firefox](https://addons.mozilla.org/addon/withexeditor/ "withExEditor :: Add-ons for Firefox")
* [withExEditor - Chrome Web Store](https://chrome.google.com/webstore/detail/withexeditor/koghhpkkcndhhclklnnnhcpkkplfkgoi "withExEditor - Chrome Web Store")

## Supported browsers

|Browser      |Windows|Linux  |Mac    |
|:------------|:-----:|:-----:|:-----:|
|Firefox      |   ✓   |   ✓   |   ✓   |
|Waterfox     |   ✓ *1|       |       |
|Chrome       |   ✓   |   ✓   |   ✓   |
|Chrome Canary|   ✓ *2|       |   ✓   |
|Chromium     |       |   ✓   |   ✓   |
|CentBrowser  |   ✓ *2|       |       |
|Kinza        |   ✓ *2|       |       |
|Opera        |   ✓ *2|       |   ✓ *2|
|Vivaldi      |   ✓ *2|   ✓   |   ✓   |

*1: Shares host with Firefox.
*2: Shares host with Chrome.

If your browser is not listed or OS for that browser is left blank, file an [issue](https://github.com/asamuzaK/withExEditorHost/issues "Issues · asamuzaK/withExEditorHost") for adding support.
When filing an issue, if you know [where to save the application manifest](https://developer.mozilla.org/en-US/Add-ons/WebExtensions/Native_messaging#App_manifest_location "Native messaging - Mozilla | MDN") in that browser, please let me know.

## Host setup

When setting up the host, disable withExEditor installed in the browser.

NOTE: If you are upgrading from host v2.x, you also need to run the following setup script. In addition, please delete all v2.x files.

Download a zip file for your OS from [Releases](https://github.com/asamuzaK/withExEditorHost/releases "Releases · asamuzaK/withExEditorHost"), after decompressing, save it in an arbitrary place under your home directory (for example, `C:\Users\XXX\withExEditorHost\`).

Next, open "cmd.exe" on Windows, "terminal" on Linux / Mac, change directory to where you saved withExEditorHost, execute the following command.

```
> cd path/to/withExEditorHost
> index setup
```

Then you will be asked which browser you want to setup the host for, so please enter the browser name from the list.

After that, you will be prompted for the following, please input as appropriate.

NOTE: If you are upgrading from host v2.x, it is not necessary to overwrite the editor setting.
You can choose `n` and exit.

* Enter editor path
* Enter command line options
  * NOTE: Quote the argument if it contains spaces or backslashes.
    For example: `-a -b "C:\Program Files"`

If config files are created successfully, enable withExEditor again.
The browser and the host get connected and the editor will be ready to use.

### Options

In the setup script you can specify some options.

#### -b --browser

To specify the browser, please use `-b` or `--browser` option.

```
> index setup --browser=firefox
```

#### -c --config-path

By default, configuration files are saved under user's home directory.
* Windows: `C:\Users\[UserName]\AppData\Roaming\withexeditorhost\config\`
* Mac: `~/Library/Application Support/withexeditorhost/config/`
* Linux: `~/.config/withexeditorhost/config/`

If you want to save configuration files in different location, use `--config-path` option.
Quote path if it contains spaces or backslashes.

```
> index setup --config-path="C:\Users\XXX\path\to\another\location"
```

#### Other options

See help for other options.

```
> index --help
```

***

## Host setup from source code

Note that [Node.js](https://nodejs.org/en/ "Node.js") v8.9.0 or higher is required to run the host from source code.

When setting up the host, disable withExEditor installed in the browser.

Download a zip file or tar.gz file of the source code from [Releases](https://github.com/asamuzaK/withExEditorHost/releases "Releases · asamuzaK/withExEditorHost"), after decompressing, save it in an arbitrary place under your home directory (for example, `C:\Users\XXX\withExEditorHost\`).
If you have a Github account, you can also clone and save the repository.

Next, open "cmd.exe" on Windows, "terminal" on Linux / Mac, change directory to where you saved withExEditorHost, execute the following command.

```
> cd path/to/withExEditorHost
> npm run setup
```

Then you will be asked which browser you want to setup the host for, so please enter the browser name from the list.

After that, you will be prompted for the following, please input as appropriate.

* Enter editor path
* Enter command line options
  * NOTE: Quote the argument if it contains spaces or backslashes.
    For example: `-a -b "C:\Program Files"`

If config files are created successfully, enable withExEditor again.
The browser and the host get connected and the editor will be ready to use.

### Options

In the setup script you can specify some options.

#### -b --browser

To specify the browser, please use `-b` or `--browser` option.

```
> npm run setup -- --browser=firefox
```

#### -c --config-path

By default, configuration files are saved under user's home directory.
* Windows: `C:\Users\[UserName]\AppData\Roaming\withexeditorhost\config\`
* Mac: `~/Library/Application Support/withexeditorhost/config/`
* Linux: `~/.config/withexeditorhost/config/`

If you want to save configuration files in different location, use `-c` or `--config-path` option.
Quote path if it contains spaces or backslashes.

```
> npm run setup -- --config-path="C:\Users\XXX\path\to\another\location"
```

#### Other options

For other options, see help

```
> node index --help
```

***

## Host setup from npm (Experimental)

[Node.js](https://nodejs.org/en/ "Node.js") v8.9.0 or higher is required.

When setting up the host, disable withExEditor installed in the browser.

Get host from [withexeditorhost - npm](https://www.npmjs.com/package/withexeditorhost) and install globally, move to installed path (for example, `C:\Users\XXX\AppData\Roaming\npm\node_modules\withexeditorhost`), then run the command for setup.

NOTE: The setup command is `node index setup`, not `npm run setup`.

```
> npm i -g withexeditorhost
> cd path/to/npm/node_modules/withexeditorhost
> node index setup
```

Then you will be asked which browser you want to setup the host for, so please enter the browser name from the list.

After that, you will be prompted for the following, please input as appropriate.

* Enter editor path
* Enter command line options
  * NOTE: Quote the argument if it contains spaces or backslashes.
    For example: `-a -b "C:\Program Files"`

If config files are created successfully, enable withExEditor again.
The browser and the host get connected and the editor will be ready to use.

### Options

In the setup script you can specify some options.

#### -b --browser

To specify the browser, please use `-b` or `--browser` option.

```
> node index setup --browser=firefox
```

#### -c --config-path

By default, configuration files are saved under user's home directory.
* Windows: `C:\Users\[UserName]\AppData\Roaming\withexeditorhost\config\`
* Mac: `~/Library/Application Support/withexeditorhost/config/`
* Linux: `~/.config/withexeditorhost/config/`

If you want to save configuration files in different location, use `-c` or `--config-path` option.
Quote path if it contains spaces or backslashes.

```
> node index setup --config-path="C:\Users\XXX\path\to\another\location"
```

#### Other options

For other options, see help

```
> node index --help
```
