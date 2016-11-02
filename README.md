
# Require is broken for `meteor npm link`

To reproduce:

```bash
$ cd meteorProj
$ meteor npm link ../npmPack
$ meteor
```

Get error:

```bash
W20161102-16:59:06.176(1)? (STDERR) Error: Cannot find module './foobar.js'
W20161102-16:59:06.177(1)? (STDERR)     at require (packages/modules-runtime.js:109:19)
W20161102-16:59:06.177(1)? (STDERR)     at meteorInstall.node_modules.npmPack.index.js (packages/modules.js:346:14)
W20161102-16:59:06.177(1)? (STDERR)     at fileEvaluate (packages/modules-runtime.js:181:9)
W20161102-16:59:06.178(1)? (STDERR)     at Module.require (packages/modules-runtime.js:106:16)
W20161102-16:59:06.178(1)? (STDERR)     at Module.Mp.import (/home/perfre/.meteor/packages/modules/.0.7.7.ljfope++os+web.browser+web.cordova/npm/node_modules/reify/lib/runtime.js:70:16)
W20161102-16:59:06.179(1)? (STDERR)     at meteorInstall.index.js (/home/perfre/workspace/ps/requireProblems/meteorProj/.meteor/local/build/programs/server/app/app.js:9:25)
W20161102-16:59:06.179(1)? (STDERR)     at fileEvaluate (packages/modules-runtime.js:181:9)
W20161102-16:59:06.180(1)? (STDERR)     at require (packages/modules-runtime.js:106:16)
W20161102-16:59:06.181(1)? (STDERR)     at /home/perfre/workspace/ps/requireProblems/meteorProj/.meteor/local/build/programs/server/app/app.js:17:1
W20161102-16:59:06.182(1)? (STDERR)     at /home/perfre/workspace/ps/requireProblems/meteorProj/.meteor/local/build/programs/server/boot.js:295:34
=> Exited with code: 1
```


## This works though:

To rollback:

```
$ cd ..
$ rm -rf */node_modules
```

Install the conventional way:

```bash
$ cd meteorProj
$ meteor npm install
$ meteor
...
=> Started proxy.                             
=> Started MongoDB.                           
I20161102-15:54:04.179(1)? { foo: 'bar' }     
=> Started your app.

=> App running at: http://localhost:3000/

```

My system:

```bash
$ meteor --version
Meteor 1.4.2
$ meteor npm --version
3.10.9
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

```
