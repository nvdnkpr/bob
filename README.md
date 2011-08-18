Bob
---

A minimalistic build script for Node.js libs, also a deploy and startup script for Express apps.

Overview
--------

Bob provides standard build targets (clean, lint, test, package, deploy, stop,
start, status, restart) for Node.js libs/apps following certain conventions.

Installation
------------

    npm install -g bob

Config
------

Bob reads package.json file, properties under "app" are optional.

    {
        "name": "myproject",
        "version": "0.0.1",
        "app": {
            "src": {
                "dir": "/path/to/myproject/mysrc"
            }
            "deploy": {
                "host": "myremotehost",
                "port": 22,
                "dir": "/remote/path/to/myproject"
            }
        }
    }

Usage
-----
    
Run Bob.

    cd /path/to/myproject
    bob target1 target2 target3 ...
    
Targets
-------

Build

    clean:
    Delete build/
    
    lint:
    Run `nodelint` against all .js files under ./ and custom files configured in app.build.lint if any
    
    test:
    Run `vows` against all .js files under test/
    
    package:
    Create a .tar.gz package of the source at build/package/

Deploy

    deploy:
    Deploy the package to app.deploy.host:app.deploy.port at app.deploy.dir
    
    deploy-r:
    Deploy the package and then remotely restart the app

Startup

    start-dev:
    Start the app in development mode
    
    start-prd:
    Start the app in production mode
    
    stop:
    Stop the app
    
    restart-dev:
    Stop the app, then start it in development mode
    
    restart-prd:
    Stop the app, then start it in production mode
    
    status:
    Display the status of the app, whether it's running or not
