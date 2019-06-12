# Node.js / JS / Typescript

Node.js is a JavaScript runtime built on Chrome's V8 JavaScript engine.

## Installation

### Using Homebrew

    $ brew install node

### Using Node Version Manager (nvm)

Download and install [nvm](https://github.com/creationix/nvm) by running:

    $ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.1/install.sh | bash

Then download Node and select your version by running:

    $ source ~/.bashrc        # source your bashrc/zshrc to add nvm to PATH
    $ command -v nvm          # check the nvm use message
    $ nvm install node        # install most recent Node stable version
    $ nvm ls                  # list installed Node version
    $ nvm use node            # use stable as current version
    $ nvm ls-remote           # list all the Node versions you can install
    $ nvm alias default node  # set the installed stable version as the default Node

See the [documentation](https://github.com/creationix/nvm#installation) for information.

## npm usage

To install a package:

    $ npm install <package> # Install locally
    $ npm install -g <package> # Install globally

To install a package and save it in your project's `package.json` file:

    $ npm install <package> --save

To see what's installed:

    $ npm list [-g]

To find outdated packages:

    $ npm outdated [-g]

To upgrade all or a particular package:

    $ npm update [-g] [<package>]

To uninstall a package:

    $ npm uninstall [-g] <package>

## Typescript

### Project Setup

```bash
# create project folder
mkdir sample-project
# initialize the npm repo
npm init -y
# initalize the typescript project within your repo (will generate the tsconfig that defines how the ts code is transpiled to js)
npx tsc --init
# install node types
npm i -D @types/node
```
### Develop Typescript Backend

As typescript is a transpiled language you develop your app like in this [example project](https://github.com/denseidel/ts-express-sample) / [more mature sample](https://github.com/aherve/typescript-express-docker). For a aws lambda sample follow [here](https://scotch.io/@nwayve/how-to-build-a-lambda-function-in-typescript
).

## Basics

* The basics are explained in the offical [Handbook](https://www.typescriptlang.org/docs/handbook/basic-types.html)
* Anotate existing npm packeges with types with a [delcaration file](https://basarat.gitbooks.io/typescript/docs/types/ambient/d.ts.html). You can use [dts-gen](https://medium.com/@jonjam/getting-started-with-typescript-type-definitions-1cda7094b8d2) to make it easier.
* How to export [modules](https://www.typescriptlang.org/docs/handbook/modules.html).