# api documentation for  [daemon (v1.1.0)](https://github.com/indexzero/daemon.node#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-daemon.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-daemon) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-daemon.svg)](https://travis-ci.org/npmdoc/node-npmdoc-daemon)
#### Add-on for creating *nix daemons

[![NPM](https://nodei.co/npm/daemon.png?downloads=true)](https://www.npmjs.com/package/daemon)

[![apidoc](https://npmdoc.github.io/node-npmdoc-daemon/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-daemon_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-daemon/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-daemon/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-daemon/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Roman Shtylman",
        "email": "shtylman@gmail.com"
    },
    "bugs": {
        "url": "https://github.com/indexzero/daemon.node/issues"
    },
    "contributors": [
        {
            "name": "Pedro Teixeira",
            "email": "pedro.teixeira@gmail.com"
        },
        {
            "name": "Charlie Robbins",
            "email": "charlie.robbins@gmail.com"
        },
        {
            "name": "James Halliday",
            "email": "mail@substack.net"
        },
        {
            "name": "Zak Taylor",
            "email": "zak@dobl.com"
        },
        {
            "name": "Daniel Bartlett",
            "email": "dan@f-box.org"
        },
        {
            "name": "Charlie McConnell",
            "email": "charlie@charlieistheman.com"
        },
        {
            "name": "Josh Holbrook",
            "email": "josh@nodejitsu.com"
        },
        {
            "name": "Arthur",
            "email": "arthur@norgic.com",
            "url": "Slashed"
        }
    ],
    "dependencies": {},
    "description": "Add-on for creating *nix daemons",
    "devDependencies": {
        "after": "0.6.0",
        "mocha": "1.8.1"
    },
    "directories": {},
    "dist": {
        "shasum": "6c5102c81db0be856fc9008fc2c935b398864ae8",
        "tarball": "https://registry.npmjs.org/daemon/-/daemon-1.1.0.tgz"
    },
    "engines": {
        "node": ">= 0.8.0"
    },
    "homepage": "https://github.com/indexzero/daemon.node#readme",
    "main": "./index.js",
    "maintainers": [
        {
            "name": "indexzero",
            "email": "charlie.robbins@gmail.com"
        },
        {
            "name": "avianflu",
            "email": "charlie@charlieistheman.com"
        },
        {
            "name": "shtylman",
            "email": "shtylman@gmail.com"
        }
    ],
    "name": "daemon",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+ssh://git@github.com/indexzero/daemon.node.git"
    },
    "scripts": {
        "test": "mocha --ui qunit test/*.js"
    },
    "version": "1.1.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module daemon](#apidoc.module.daemon)
1.  [function <span class="apidocSignatureSpan"></span>daemon (script, args, opt)](#apidoc.element.daemon.daemon)



# <a name="apidoc.module.daemon"></a>[module daemon](#apidoc.module.daemon)

#### <a name="apidoc.element.daemon.daemon"></a>[function <span class="apidocSignatureSpan"></span>daemon (script, args, opt)](#apidoc.element.daemon.daemon)
- description and source-code
```javascript
daemon = function (script, args, opt) {

    opt = opt || {};

    var stdout = opt.stdout || 'ignore';
    var stderr = opt.stderr || 'ignore';

    var env = opt.env || process.env;
    var cwd = opt.cwd || process.cwd;

    var cp_opt = {
        stdio: ['ignore', stdout, stderr],
        env: env,
        cwd: cwd,
        detached: true
    };

    // spawn the child using the same node process as ours
    var child = child_process.spawn(process.execPath, [script].concat(args), cp_opt);

    // required so the parent can exit
    child.unref();

    return child;
}
```
- example usage
```shell
...

## api

### daemon()

Respawn the process (self) as a daemon. The parent process will exit at the point of this call.

### daemon.daemon(script, args, opt)

Spawn the 'script' with given 'args' array as a daemonized process. Return the 'child' process object.

opt can optionally contain the following arguments:
* stdout (file descriptor for stdout of the daemon)
* stderr (file descriptor for stderr of the daemon)
* env (environment for the daemon) (default: process.env)
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
