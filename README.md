# restapi-todo-nestjs-udemy
NestJS + Next.js によるフルスタックWeb開発（udemy）（学習用）

- 参考サイト

    - [講座：NestJS + Next.js によるフルスタックWeb開発のGitHub](https://github.com/GomaGoma676/restapi-todo-nestjs)


## 環境

1. `nodejs`のインストール

    ```sh
    sudo dnf install nodejs
    メタデータの期限切れの最終確認: 0:13:26 前の 2023年10月21日 14時54分05秒 に実施しました。
    依存関係が解決しました。
    =====================================================================================================================================================================================================================================
    パッケージ                                           アーキテクチャー                           バージョン                                                                      リポジトリー                                  サイズ
    =====================================================================================================================================================================================================================================
    インストール:
    nodejs                                               x86_64                                     1:20.5.1-1.module_el8+641+80a1645e                                              appstream                                      14 M
    弱い依存関係のインストール:
    nodejs-docs                                          noarch                                     1:20.5.1-1.module_el8+641+80a1645e                                              appstream                                      10 M
    nodejs-full-i18n                                     x86_64                                     1:20.5.1-1.module_el8+641+80a1645e                                              appstream                                     8.2 M
    npm                                                  x86_64                                     1:9.8.0-1.20.5.1.1.module_el8+641+80a1645e                                      appstream                                     2.8 M

    トランザクションの概要
    =====================================================================================================================================================================================================================================
    インストール  4 パッケージ

    ダウンロードサイズの合計: 35 M
    インストール後のサイズ: 174 M
    これでよろしいですか? [y/N]: y
    パッケージのダウンロード:
    (1/4): nodejs-full-i18n-20.5.1-1.module_el8+641+80a1645e.x86_64.rpm                                                                                                                                  2.3 MB/s | 8.2 MB     00:03    
    (2/4): npm-9.8.0-1.20.5.1.1.module_el8+641+80a1645e.x86_64.rpm                                                                                                                                       1.2 MB/s | 2.8 MB     00:02    
    (3/4): nodejs-docs-20.5.1-1.module_el8+641+80a1645e.noarch.rpm                                                                                                                                       1.2 MB/s |  10 MB     00:08    
    (4/4): nodejs-20.5.1-1.module_el8+641+80a1645e.x86_64.rpm                                                                                                                                            1.1 MB/s |  14 MB     00:12    
    -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
    合計                                                                                                                                                                                                 2.7 MB/s |  35 MB     00:12     
    トランザクションの確認を実行中
    トランザクションの確認に成功しました。
    トランザクションのテストを実行中
    トランザクションのテストに成功しました。
    トランザクションを実行中
    scriptletの実行中: npm-1:9.8.0-1.20.5.1.1.module_el8+641+80a1645e.x86_64                                                                                                                                                       1/1 
    準備             :                                                                                                                                                                                                             1/1 
    インストール中   : nodejs-docs-1:20.5.1-1.module_el8+641+80a1645e.noarch                                                                                                                                                       1/4 
    インストール中   : nodejs-full-i18n-1:20.5.1-1.module_el8+641+80a1645e.x86_64                                                                                                                                                  2/4 
    インストール中   : npm-1:9.8.0-1.20.5.1.1.module_el8+641+80a1645e.x86_64                                                                                                                                                       3/4 
    インストール中   : nodejs-1:20.5.1-1.module_el8+641+80a1645e.x86_64                                                                                                                                                            4/4 
    scriptletの実行中: nodejs-1:20.5.1-1.module_el8+641+80a1645e.x86_64                                                                                                                                                            4/4 
    検証             : nodejs-1:20.5.1-1.module_el8+641+80a1645e.x86_64                                                                                                                                                            1/4 
    検証             : nodejs-docs-1:20.5.1-1.module_el8+641+80a1645e.noarch                                                                                                                                                       2/4 
    検証             : nodejs-full-i18n-1:20.5.1-1.module_el8+641+80a1645e.x86_64                                                                                                                                                  3/4 
    検証             : npm-1:9.8.0-1.20.5.1.1.module_el8+641+80a1645e.x86_64                                                                                                                                                       4/4 

    インストール済み:
    nodejs-1:20.5.1-1.module_el8+641+80a1645e.x86_64    nodejs-docs-1:20.5.1-1.module_el8+641+80a1645e.noarch    nodejs-full-i18n-1:20.5.1-1.module_el8+641+80a1645e.x86_64    npm-1:9.8.0-1.20.5.1.1.module_el8+641+80a1645e.x86_64   

    完了しました!
    ```

1. `node-js`のバージョン

    ```sh
    node -v
    v20.5.1
    ```

1. `npm`のバージョン

    ```sh
    npm -v
    9.8.0
    ```

1. `npx`のバージョン

    - `nodejs`と一緒にインストールされる模様

    ```sh
    npx -v
    9.8.0
    ```

1. `@nestjs/cli`をグローバルでインストール

    ```sh
    sudo npm i -g @nestjs/cli
    45 packages are looking for funding
    run `npm fund` for details
    ```

1. グローバルインストールの確認

    ```sh
    npm ls -g
    /usr/local/lib
    └── @nestjs/cli@10.1.18
    ```

<del>
- `npx npm new --help`コマンドを実行したところ、`npm@10.2.1`が必要とされたため、インストール

1. `npm@10.2.1`をインストール

    ```sh
    npx npm new --help
    Need to install the following packages:
    npm@10.2.1
    Ok to proceed? (y) y
    Unknown command: "new"

    To see a list of supported npm commands, run:
    npm help
    ```
</del>

## NextJS の環境構築の条件

- `npm`を使用。`yarn`は使用しない。
- TyprScriptの使用を強制する

    - 、[このサイト](https://zenn.dev/shiro12/scraps/a0bc323f925625)より、

        ```
        nest new実行時 --strict とすれば厳密な機能セットを備えた新しい TypeScript プロジェクトを作成できる
        ```

- このため、NestJsのプロジェクトは、以下のコマンドで作成する

    ```sh
    nest new <プロジェクト名> -p npm --strict
    ```

    - `help`を確認

    ```sh
    nest new -help
    Usage: nest new|n [options] [name]

    Generate Nest application.

    Options:
    --directory [directory]                 Specify the destination directory
    -d, --dry-run                           Report actions that would be performed without writing out results. (default: false)
    -g, --skip-git                          Skip git repository initialization. (default: false)
    -s, --skip-install                      Skip package installation. (default: false)
    -p, --package-manager [packageManager]  Specify package manager.
    -l, --language [language]               Programming language to be used (TypeScript or JavaScript) (default: "TypeScript")
    -c, --collection [collectionName]       Schematics collection to use (default: "@nestjs/schematics")
    --strict                                Enables strict mode in TypeScript. (default: false)
    -h, --help                              Output usage information.
    ```

## NestJSのプロjクト作成

1. ホームディレクトリに移動

    ```sh
    cd ~
    ```

1. プロジェクト`nestjs-samle-01`を作成

    ```sh
    nest new nestjs-samle-01 -p npm --strict
    ⚡  We will scaffold your app in a few seconds..

    CREATE nestjs-samle-01/.eslintrc.js (663 bytes)
    CREATE nestjs-samle-01/.prettierrc (51 bytes)
    CREATE nestjs-samle-01/README.md (3340 bytes)
    CREATE nestjs-samle-01/nest-cli.json (171 bytes)
    CREATE nestjs-samle-01/package.json (1956 bytes)
    CREATE nestjs-samle-01/tsconfig.build.json (97 bytes)
    CREATE nestjs-samle-01/tsconfig.json (541 bytes)
    CREATE nestjs-samle-01/src/app.controller.spec.ts (617 bytes)
    CREATE nestjs-samle-01/src/app.controller.ts (274 bytes)
    CREATE nestjs-samle-01/src/app.module.ts (249 bytes)
    CREATE nestjs-samle-01/src/app.service.ts (142 bytes)
    CREATE nestjs-samle-01/src/main.ts (208 bytes)
    CREATE nestjs-samle-01/test/app.e2e-spec.ts (630 bytes)
    CREATE nestjs-samle-01/test/jest-e2e.json (183 bytes)

    ✔ Installation in progress... ☕

    🚀  Successfully created project nestjs-samle-01
    👉  Get started with the following commands:

    $ cd nestjs-samle-01
    $ npm run start

                                                                                                                    
                                                                                                        Thanks for installing Nest 🙏
                                                                                                Please consider donating to our open collective
                                                                                                    to help us maintain this package.
                                                                                                                    
                                                                                                                    
                                                                                            🍷  Donate: https://opencollective.com/nest
    ```


- 作成されたフォルダの内容を確認

    ```sh
    ll ~/nestjs-samle-01/
    合計 352
    -rw-rw-r--   1 kazuhiro kazuhiro   3340 10月 21 15:59 README.md
    -rw-rw-r--   1 kazuhiro kazuhiro    171 10月 21 15:59 nest-cli.json
    drwxrwxr-x 478 kazuhiro kazuhiro  16384 10月 21 16:00 node_modules
    -rw-rw-r--   1 kazuhiro kazuhiro 316872 10月 21 16:00 package-lock.json
    -rw-rw-r--   1 kazuhiro kazuhiro   1956 10月 21 15:59 package.json
    drwxrwxr-x   2 kazuhiro kazuhiro    119 10月 21 15:59 src
    drwxrwxr-x   2 kazuhiro kazuhiro     50 10月 21 15:59 test
    -rw-rw-r--   1 kazuhiro kazuhiro     97 10月 21 15:59 tsconfig.build.json
    -rw-rw-r--   1 kazuhiro kazuhiro    541 10月 21 15:59 tsconfig.json
    ```

- プロジェクトをビルドする

    - `nest`コマンドのヘルプを確認

    ```sh
    nest --


- `npm`のヘルプを確認

    ```sh
    npm --help
    npm <command>

    Usage:

    npm install        install all the dependencies in your project
    npm install <foo>  add the <foo> dependency to your project
    npm test           run this project's tests
    npm run <foo>      run the script named <foo>
    npm <command> -h   quick help on <command>
    npm -l             display usage info for all commands
    npm help <term>    search for help on <term>
    npm help npm       more involved overview

    All commands:

        access, adduser, audit, bugs, cache, ci, completion,
        config, dedupe, deprecate, diff, dist-tag, docs, doctor,
        edit, exec, explain, explore, find-dupes, fund, get, help,
        help-search, hook, init, install, install-ci-test,
        install-test, link, ll, login, logout, ls, org, outdated,
        owner, pack, ping, pkg, prefix, profile, prune, publish,
        query, rebuild, repo, restart, root, run-script, search,
        set, shrinkwrap, star, stars, start, stop, team, test,
        token, uninstall, unpublish, unstar, update, version, view,
        whoami

    Specify configs in the ini-formatted file:
        /home/kazuhiro/.npmrc
    or on the command line via: npm <command> --key=value

    More configuration info: npm help config
    Configuration fields: npm help 7 config

    npm@9.8.0 /usr/lib/node_modules/npm
    ```

1. `package.json`の`scripts`を確認

    ```sh
    $ cat ~/nestjs-samle-01/package.json 
    {
    "name": "nestjs-samle-01",
    "version": "0.0.1",
    "description": "",
    "author": "",
    "private": true,
    "license": "UNLICENSED",
    "scripts": {
        "build": "nest build",
        "format": "prettier --write \"src/**/*.ts\" \"test/**/*.ts\"",
        "start": "nest start",
        "start:dev": "nest start --watch",
        "start:debug": "nest start --debug --watch",
        "start:prod": "node dist/main",
        "lint": "eslint \"{src,apps,libs,test}/**/*.ts\" --fix",
        "test": "jest",
        "test:watch": "jest --watch",
        "test:cov": "jest --coverage",
        "test:debug": "node --inspect-brk -r tsconfig-paths/register -r ts-node/register node_modules/.bin/jest --runInBand",
        "test:e2e": "jest --config ./test/jest-e2e.json"
    },
    "dependencies": {
        "@nestjs/common": "^10.0.0",
        "@nestjs/core": "^10.0.0",
        "@nestjs/platform-express": "^10.0.0",
        "reflect-metadata": "^0.1.13",
        "rxjs": "^7.8.1"
    },
    "devDependencies": {
        "@nestjs/cli": "^10.0.0",
        "@nestjs/schematics": "^10.0.0",
        "@nestjs/testing": "^10.0.0",
        "@types/express": "^4.17.17",
        "@types/jest": "^29.5.2",
        "@types/node": "^20.3.1",
        "@types/supertest": "^2.0.12",
        "@typescript-eslint/eslint-plugin": "^6.0.0",
        "@typescript-eslint/parser": "^6.0.0",
        "eslint": "^8.42.0",
        "eslint-config-prettier": "^9.0.0",
        "eslint-plugin-prettier": "^5.0.0",
        "jest": "^29.5.0",
        "prettier": "^3.0.0",
        "source-map-support": "^0.5.21",
        "supertest": "^6.3.3",
        "ts-jest": "^29.1.0",
        "ts-loader": "^9.4.3",
        "ts-node": "^10.9.1",
        "tsconfig-paths": "^4.2.0",
        "typescript": "^5.1.3"
    },
    "jest": {
        "moduleFileExtensions": [
        "js",
        "json",
        "ts"
        ],
        "rootDir": "src",
        "testRegex": ".*\\.spec\\.ts$",
        "transform": {
        "^.+\\.(t|j)s$": "ts-jest"
        },
        "collectCoverageFrom": [
        "**/*.(t|j)s"
        ],
        "coverageDirectory": "../coverage",
        "testEnvironment": "node"
    }
    }
    ```

1. パッケージの保存先フォルダに移動

    ```sh
    cd ~/nestjs-samle-01
    ```

1. 作成したプロジェクトをビルドする

    ```sh
    npm run build
    > nestjs-samle-01@0.0.1 build
    > nest build
    ```

1. 作成されたフォルダの内容を確認

    - `dist`フォルダが作成されている

    ```sh
    ll ~/nestjs-samle-01/
    合計 356
    -rw-rw-r--   1 kazuhiro kazuhiro   3340 10月 21 15:59 README.md
    drwxrwxr-x   2 kazuhiro kazuhiro   4096 10月 21 16:39 dist
    -rw-rw-r--   1 kazuhiro kazuhiro    171 10月 21 15:59 nest-cli.json
    drwxrwxr-x 478 kazuhiro kazuhiro  16384 10月 21 16:00 node_modules
    -rw-rw-r--   1 kazuhiro kazuhiro 316872 10月 21 16:00 package-lock.json
    -rw-rw-r--   1 kazuhiro kazuhiro   1956 10月 21 15:59 package.json
    drwxrwxr-x   2 kazuhiro kazuhiro    119 10月 21 15:59 src
    drwxrwxr-x   2 kazuhiro kazuhiro     50 10月 21 15:59 test
    -rw-rw-r--   1 kazuhiro kazuhiro     97 10月 21 15:59 tsconfig.build.json
    -rw-rw-r--   1 kazuhiro kazuhiro    541 10月 21 15:59 tsconfig.json
    ```

1. ビルドしたアプリを実行する


    ```sh
    npm run start
    > nestjs-samle-01@0.0.1 start
    > nest start

    [Nest] 48145  - 2023/10/21 16:49:37     LOG [NestFactory] Starting Nest application...
    [Nest] 48145  - 2023/10/21 16:49:37     LOG [InstanceLoader] AppModule dependencies initialized +21ms
    [Nest] 48145  - 2023/10/21 16:49:38     LOG [RoutesResolver] AppController {/}: +44ms
    [Nest] 48145  - 2023/10/21 16:49:38     LOG [RouterExplorer] Mapped {/, GET} route +4ms
    [Nest] 48145  - 2023/10/21 16:49:38     LOG [NestApplication] Nest application successfully started +4ms
    ```

1. 別ターミナルで`curl`でアクセスし、疎通を確認

    ```sh
    curl http://10.1.1.201:3000
    Hello World!
    ```

1. もう一度ビルドしてみる → バージョンは変らない

    ```sh
    npm run build
    > nestjs-samle-01@0.0.1 build
    > nest build
    ```

1. `ctrl+C`で停止

1. `Hello World!` から`こんにちわ`に変更する（再ビルドでバージョンが変わるかを確認）

    ```sh
     cat src/app.service.ts 
    import { Injectable } from '@nestjs/common';

    @Injectable()
    export class AppService {
        getHello(): string {
        return 'こんにちわ';
        }
    }
    ```

    - バージョンは変わらない

    ```sh
    npm run build
    > nestjs-samle-01@0.0.1 build
    > nest build
    ```

1. `package.json`内のバージョンを`0.0.2`に変えて、ビルドしてみた

    ```sh
        "name": "nestjs-samle-01",
        "version": "0.0.2",
    ```

    - バージョンが変わった → アプリのバージョンは`package.json`で管理している

    ```sh
    npm run build
    
    > nestjs-samle-01@0.0.2 build
    > nest build
    ```
1. 気持ち悪いの`package-lock.json`内のバージョンも`0.0.2`にかえる


## 作成したプロジェクトをGitHubにpushする

1. ローカルの`git`ディレクトリに移動する

    ```sh
    cd ~/nestjs-samle-01/
    ```

1. `~/nestjs-samle-01`をローカルでコッミトする。

    ```sh
    git add .
    ```

    ```sh
    git commit -m "リポジトリの作成"
    ```

1. ルートのブランチ名を`master`から`main`に変更

    ```sh
    git branch 
    * master
    ```

    ```sh
    git branch -m master main
    ```

    ```sh
    git branch 
    * main
    ```

1. GitHub上に`README`無しのリポジトリを以下のURLで作成する

    - https://github.com/moriyamaES/nestjs-samle-01.git

        - GitHubのリポジトリ名は、NestJsのプロジェクト名に合わせる

1. リモートリポジトリを名前を`origin`で作成

    ```sh
    git remote add origin https://github.com/moriyamaES/nestjs-samle-01.git
    ```

1. リモートリポジトリ`origin`に`manin`ブランチを作成し、`push`する

    ```sh
    git push --set-upstream origin main
    Enumerating objects: 20, done.
    Counting objects: 100% (20/20), done.
    Delta compression using up to 3 threads
    Compressing objects: 100% (20/20), done.
    Writing objects: 100% (20/20), 83.30 KiB | 4.16 MiB/s, done.
    Total 20 (delta 0), reused 0 (delta 0), pack-reused 0
    To https://github.com/moriyamaES/nestjs-samle-01.git
    * [new branch]      main -> main
    branch 'main' set up to track 'origin/main'.
    ```

1. 以下のコマンドを実行し、`origin/HEAD`を作成 

    ```sh
    git remote set-head origin main

    ```

1. `git`のログを確認する

    ```sh
    git log --graph --oneline --all
    bb89d78 (HEAD -> main, origin/main, origin/HEAD) リポジトリの作成
    ````

## GitHubから`clon`したプロジェクトのソースをビルドする

1. ローカルの`git`リポジトリを削除する

    ```sh
    cd ~/
    ```

    ```sh
    sudo rm -rf nestjs-samle-01/
    ```
1. GitHubからプロジェクトのソースを`clone`する

    ```
    git clone https://github.com/moriyamaES/nestjs-samle-01.git
    Cloning into 'nestjs-samle-01'...
    remote: Enumerating objects: 20, done.
    remote: Counting objects: 100% (20/20), done.
    remote: Compressing objects: 100% (20/20), done.
    remote: Total 20 (delta 0), reused 20 (delta 0), pack-reused 0
    Receiving objects: 100% (20/20), 83.30 KiB | 4.16 MiB/s, done.
    ```

1. `clone`の結果を確認する

    ```sh
    ll nestjs-samle-01
    -rw-rw-r-- 1 kazuhiro kazuhiro   3340 10月 21 18:08 README.md
    -rw-rw-r-- 1 kazuhiro kazuhiro    171 10月 21 18:08 nest-cli.json
    -rw-rw-r-- 1 kazuhiro kazuhiro 316872 10月 21 18:08 package-lock.json
    -rw-rw-r-- 1 kazuhiro kazuhiro   1955 10月 21 18:08 package.json
    drwxrwxr-x 2 kazuhiro kazuhiro    119 10月 21 18:08 src
    drwxrwxr-x 2 kazuhiro kazuhiro     50 10月 21 18:08 test
    -rw-rw-r-- 1 kazuhiro kazuhiro     97 10月 21 18:08 tsconfig.build.json
    -rw-rw-r-- 1 kazuhiro kazuhiro    541 10月 21 18:08 tsconfig.json
    ```

1. `clone`したプロジェクトのフォルダに移動

    ```sh
    cd nestjs-samle-01
    ```

1. `clone`したプロジェクトをビルドする（エラー発生）

    - エラーが発生した

    ```sh
    npm run build

    > nestjs-samle-01@0.0.2 build
    > nest build

    src/app.controller.ts:1:33 - error TS2307: Cannot find module '@nestjs/common' or its corresponding type declarations.

    1 import { Controller, Get } from '@nestjs/common';
                                    ~~~~~~~~~~~~~~~~
    src/app.module.ts:1:24 - error TS2307: Cannot find module '@nestjs/common' or its corresponding type declarations.

    1 import { Module } from '@nestjs/common';
                            ~~~~~~~~~~~~~~~~
    src/app.service.ts:1:28 - error TS2307: Cannot find module '@nestjs/common' or its corresponding type declarations.

    1 import { Injectable } from '@nestjs/common';
                                ~~~~~~~~~~~~~~~~
    src/main.ts:1:29 - error TS2307: Cannot find module '@nestjs/core' or its corresponding type declarations.

    1 import { NestFactory } from '@nestjs/core';
                                ~~~~~~~~~~~~~~

    Found 4 error(s).
    ```

1. `nom`でモジュールをインストールする


    ```sh
    npm install
    
    added 700 packages, and audited 701 packages in 14s

    119 packages are looking for funding
    run `npm fund` for details

    found 0 vulnerabilities
    ```

1. `clone`したプロジェクトをビルドする（成功！！）

    ```sh
    npm run build

    > nestjs-samle-01@0.0.2 build
    > nest build
    ```

1. ビルドしたアプリを実行する

    ```sh
    npm run start

    > nestjs-samle-01@0.0.2 start
    > nest start

    [Nest] 51372  - 2023/10/21 18:23:26     LOG [NestFactory] Starting Nest application...
    [Nest] 51372  - 2023/10/21 18:23:26     LOG [InstanceLoader] AppModule dependencies initialized +20ms
    [Nest] 51372  - 2023/10/21 18:23:26     LOG [RoutesResolver] AppController {/}: +21ms
    [Nest] 51372  - 2023/10/21 18:23:26     LOG [RouterExplorer] Mapped {/, GET} route +4ms
    [Nest] 51372  - 2023/10/21 18:23:26     LOG [NestApplication] Nest application successfully started +3ms
    ```

1. 別ターミナルで`curl`でアクセスし、疎通を確認

    ```sh
    curl http://10.1.1.201:3000
    こんにちわ
    ````

<del>
## NextJS の環境構築

- 参考サイト

    - [【npm】npmコマンド一覧（野良サイト）](https://qiita.com/P-man_Brown/items/db1c9f13ab34dcf97993)

- `yarn` をグローバルインストール

    ```sh
    sudo npm i -g yarn
    
    added 1 package in 2s
    ```

- `@nestjs/cli`をグローバルインストール

    ```sh
    sudo npm i -g @nestjs/cli
    [sudo] kazuhiro のパスワード:

    added 263 packages in 25s

    44 packages are looking for funding
    run `npm fund` for details
    ```

- グローバルインストールの確認

    ```sh
    npm ls -g
    /usr/local/lib
    ├── @nestjs/cli@10.1.18
    └── yarn@1.22.19
    ```

## NestJsのプロジェクト作成

- 以下のコマンドを実行

    ```sh
    cd ~/restapi-todo-nestjs-udemy/
    ```

<del>
    ```sh
    nest new api-lesson
    ⚡  We will scaffold your app in a few seconds..

    ? Which package manager would you ❤️  to use? yarn
    CREATE api-lesson/.eslintrc.js (663 bytes)
    CREATE api-lesson/.prettierrc (51 bytes)
    CREATE api-lesson/README.md (3347 bytes)
    CREATE api-lesson/nest-cli.json (171 bytes)
    CREATE api-lesson/package.json (1951 bytes)
    CREATE api-lesson/tsconfig.build.json (97 bytes)
    CREATE api-lesson/tsconfig.json (546 bytes)
    CREATE api-lesson/src/app.controller.spec.ts (617 bytes)
    CREATE api-lesson/src/app.controller.ts (274 bytes)
    CREATE api-lesson/src/app.module.ts (249 bytes)
    CREATE api-lesson/src/app.service.ts (142 bytes)
    CREATE api-lesson/src/main.ts (208 bytes)
    CREATE api-lesson/test/app.e2e-spec.ts (630 bytes)
    CREATE api-lesson/test/jest-e2e.json (183 bytes)

    ✔ Installation in progress... ☕

    🚀  Successfully created project api-lesson
    👉  Get started with the following commands:

    $ cd api-lesson
    $ yarn run start

                                                    
                                    Thanks for installing Nest 🙏
                            Please consider donating to our open collective
                                    to help us maintain this package.
                                                    
                                                    
                        🍷  Donate: https://opencollective.com/nest
                                                    

    ```




- `tsconfig.json`を以下のように修正

    - 変更の意図は以下

        - `"noImplicitAny": true`→型無しをエラーにする
        - `"strict": true`→ TypeScriptとする？

    ```diff
    diff -u tsconfig.json.2310151743 tsconfig.json
    --- tsconfig.json.2310151743    2023-10-15 17:44:12.791492000 +0900
    +++ tsconfig.json       2023-10-15 17:41:10.944492000 +0900
    @@ -13,9 +13,10 @@
        "incremental": true,
        "skipLibCheck": true,
        "strictNullChecks": false,
    -    "noImplicitAny": false,
    +    "noImplicitAny": true,
        "strictBindCallApply": false,
        "forceConsistentCasingInFileNames": false,
    -    "noFallthroughCasesInSwitch": false
    +    "noFallthroughCasesInSwitch": false,
    +    "strict": true
    ```
</del>

- ここで、[このサイト](https://zenn.dev/shiro12/scraps/a0bc323f925625)より、

    ```
    nest new実行時 --strict とすれば厳密な機能セットを備えた新しい TypeScript プロジェクトを作成できる
    ```

- とのことであるため、先の作成したプロジェクトフォルダは削除し、再作成する。

    ```sh
    rm -rf ~/restapi-todo-nestjs-udemy/api-lesson
    ```

    ```sh
    cd ~/restapi-todo-nestjs-udemy/
    ```

- `--strict`として再作成

    ```sh
    nest new api-lesson --strict
    ⚡  We will scaffold your app in a few seconds..

    ? Which package manager would you ❤️  to use? yarn  ★yarnを選択
    CREATE api-lesson/.eslintrc.js (663 bytes)
    CREATE api-lesson/.prettierrc (51 bytes)
    CREATE api-lesson/README.md (3347 bytes)
    CREATE api-lesson/nest-cli.json (171 bytes)
    CREATE api-lesson/package.json (1951 bytes)
    CREATE api-lesson/tsconfig.build.json (97 bytes)
    CREATE api-lesson/tsconfig.json (541 bytes)
    CREATE api-lesson/src/app.controller.spec.ts (617 bytes)
    CREATE api-lesson/src/app.controller.ts (274 bytes)
    CREATE api-lesson/src/app.module.ts (249 bytes)
    CREATE api-lesson/src/app.service.ts (142 bytes)
    CREATE api-lesson/src/main.ts (208 bytes)
    CREATE api-lesson/test/app.e2e-spec.ts (630 bytes)
    CREATE api-lesson/test/jest-e2e.json (183 bytes)

    ✔ Installation in progress... ☕

    🚀  Successfully created project api-lesson
    👉  Get started with the following commands:

    $ cd api-lesson
    $ yarn run start

                                                    
                                    Thanks for installing Nest 🙏
                            Please consider donating to our open collective
                                    to help us maintain this package.
                                                    
                                                    
                        🍷  Donate: https://opencollective.com/nest
    ```

- `--strict`をしていない場合（ここでは、`api-lesson-2`）としていない場合(ここでは、`api-lesson`)との`tsconfig.json`の違いは以下
- とりあえす、 `--strict`を使用した場合でハンズオンを事項していく

    - `"noImplicitAny": true`→型無しをエラーにする

    ```sh
    $ diff -u  ~/restapi-todo-nestjs-udemy/api-lesson-2/tsconfig.json ~/restapi-todo-nestjs-udemy/api-lesson/tsconfig.json 
    --- /home/kazuhiro/restapi-todo-nestjs-udemy/api-lesson-2/tsconfig.json 2023-10-15 18:15:23.429492000 +0900
    +++ /home/kazuhiro/restapi-todo-nestjs-udemy/api-lesson/tsconfig.json   2023-10-15 18:09:32.849492000 +0900
    @@ -12,10 +12,10 @@
        "baseUrl": "./",
        "incremental": true,
        "skipLibCheck": true,
    -    "strictNullChecks": false,
    -    "noImplicitAny": false,
    -    "strictBindCallApply": false,
    -    "forceConsistentCasingInFileNames": false,
    -    "noFallthroughCasesInSwitch": false
    +    "strictNullChecks": true,
    +    "noImplicitAny": true,
    +    "strictBindCallApply": true,
    +    "forceConsistentCasingInFileNames": true,
    +    "noFallthroughCasesInSwitch": true
    ```




## NestJaのポート番号を修正

- `~/restapi-todo-nestjs-udemy/api-lesson/src/main.ts`を以下のように変更し、ポート番号を`3000`から`3005`に変更する

    ```diff
    $ diff -u main.ts.231015184139 main.ts
    --- main.ts.231015184139        2023-10-15 18:41:39.380492000 +0900
    +++ main.ts     2023-10-15 18:41:59.909492000 +0900
    @@ -3,6 +3,6 @@
    
    async function bootstrap() {
    const app = await NestFactory.create(AppModule);
    -  await app.listen(3000);
    +  await app.listen(3005);
    }
    bootstrap();
    ```

## NestJsでAPサーバを起動（yarn を使用：講座通り）

- 以下のコマンドを実行

    ```sh
    cd ~/restapi-todo-nestjs-udemy/api-lesson/
    ```

    ```sh
    yarn start:dev
    ```

- 別ターミナルで以下のコマンドを実行

    - 正常起動を確認

    ```sh
    curl http://10.1.1.201:3005
    Hello World!
    ```

## NestJsのAPサーバを起動（mpn を使用）→ 失敗（ `yarn`で作成した`NestJs`のプロジェクトは`npm`では実行できない模様）

    ```sh
    cd ~/restapi-todo-nestjs-udemy/api-lesson/
    ```

    ```sh
    npm start:dev
    Unknown command: "start:dev"

    Did you mean one of these?
        npm run start:dev # run the "start:dev" package script
        npm run start:debug # run the "start:debug" package script

    To see a list of supported npm commands, run:
    npm help
    ```
- `yarn`で作成した`NestJs`のプロジェクトは`npm`では実行できない模様

# NextJS の環境構築（npmのみを使用、yarnは使用しない　場合の検証）

- グローバルインストールした`yarn`をアンインストール 

    - [【npm】npmコマンド一覧（野良サイト）](https://qiita.com/P-man_Brown/items/db1c9f13ab34dcf97993)


    ```sh
    sudo npm un yarn -g
    [sudo] kazuhiro のパスワード:

    removed 1 package in 491ms
    ```

- グローバルインストールの確認

    ```sh
    npm ls -g
    /usr/local/lib
    └── @nestjs/cli@10.1.18
    ```
## NestJsのプロジェクト作成（npmを選択）

- 以下のコマンドを実行

    ```sh
    cd ~/restapi-todo-nestjs-udemy/
    ```

- `--strict`として作成

    ```sh
    nest new api-lesson-npm --strict
    ⚡  We will scaffold your app in a few seconds..

    ? Which package manager would you ❤️  to use? npm ★npmを選択
    CREATE api-lesson-npm/.eslintrc.js (663 bytes)
    CREATE api-lesson-npm/.prettierrc (51 bytes)
    CREATE api-lesson-npm/README.md (3340 bytes)
    CREATE api-lesson-npm/nest-cli.json (171 bytes)
    CREATE api-lesson-npm/package.json (1955 bytes)
    CREATE api-lesson-npm/tsconfig.build.json (97 bytes)
    CREATE api-lesson-npm/tsconfig.json (541 bytes)
    CREATE api-lesson-npm/src/app.controller.spec.ts (617 bytes)
    CREATE api-lesson-npm/src/app.controller.ts (274 bytes)
    CREATE api-lesson-npm/src/app.module.ts (249 bytes)
    CREATE api-lesson-npm/src/app.service.ts (142 bytes)
    CREATE api-lesson-npm/src/main.ts (208 bytes)
    CREATE api-lesson-npm/test/app.e2e-spec.ts (630 bytes)
    CREATE api-lesson-npm/test/jest-e2e.json (183 bytes)

    ✔ Installation in progress... ☕

    🚀  Successfully created project api-lesson-npm
    👉  Get started with the following commands:

    $ cd api-lesson-npm
    $ npm run start

                                                
                                Thanks for installing Nest 🙏
                        Please consider donating to our open collective
                                to help us maintain this package.
                                                
                                                
                        🍷  Donate: https://opencollective.com/nest
    ```

- APサーバが使用するポート番号を確認 → 3000

    ```sh
    cat ~/restapi-todo-nestjs-udemy/api-lesson-npm/src/main.ts 
    import { NestFactory } from '@nestjs/core';
    import { AppModule } from './app.module';

    async function bootstrap() {
    const app = await NestFactory.create(AppModule);
    await app.listen(3000);
    }
    bootstrap();
    ```

- `npm`で起動

<del>
- `npm npm start:dev`では起動できない

    ```sh
    cd ~/restapi-todo-nestjs-udemy/api-lesson-npm/
    ```

    ```sh
    npm start:dev
    npm start:dev
    Unknown command: "start:dev"

    Did you mean one of these?
        npm run start:dev # run the "start:dev" package script
        npm run start:debug # run the "start:debug" package script

    To see a list of supported npm commands, run:
    npm help 
    ```
</del>

- `npm run npm start:dev`で起動成功！！

    ```sh
    cd ~/restapi-todo-nestjs-udemy/api-lesson-npm/
    ```

    ```sh
    npm run start:dev
    ````

- 別ターミナルでレスポンスを確認

    ```sh
    curl http://10.1.1.201:3000
    Hello World!
    ```

- 結論、ここまでなら`yarn`をインストールしなくとも`NestJs`を起動できる

# NextJS の環境構築（ @nestjs/cli がなくとも良いかを検証）→ 結論できない


## @nestjs/cli のアンインストール

    ```sh
    sudo npm un @nestjs/cli -g
    [sudo] kazuhiro のパスワード:

    removed 263 packages in 2s
    ```

- グローバルインストールの確認

    ```sh
    npm ls -g
    /usr/local/lib
    └── (empty)
    ```

## NestJsのプロジェクト作成（npmを選択、 @nestjs/cli 無し）→ 結論できない

    ```sh
    cd ~/restapi-todo-nestjs-udemy/
    ```

- `--strict`として作成　→ @nestjs/cli 無し ではできない

    ```sh
    nest new api-lesson-no-nest --strict
    bash: /usr/local/bin/nest: そのようなファイルやディレクトリはありません

## NestJsのプロジェクト作成（npmを選択、 @nestjs/cli 無し）→ 結論、 @nestjs/cli が環境でも起動できる

    ```sh
    npm ls -g
    /usr/local/lib
    └── (empty)
    ```

- `npm run npm start:dev`で起動成功！！→ 結論、 @nestjs/cli がない環境でも起動できる！！

    ```sh
    cd ~/restapi-todo-nestjs-udemy/api-lesson-npm/
    ```

    ```sh
    npm run start:dev
    ````

- 別ターミナルでレスポンスを確認

    ```sh
    curl http://10.1.1.201:3000
    Hello World!
    ```


# NestJs のプロジェクトをGitHubの初回push する手順（1回目）

- NestJs のプロジェクトは自動で、`.git` ファイルと`README.md`ファイルを作成している
- このため、NestJs のプロジェクトをGitpubへ初回Pushする場合以下の手順が必要
1. GitHUbにリポジトリを、`README`無しでリポジトリを作成する

    - GitHubのリポジトリ名は、NestJsのプロジェクト名と同じとした方がよいと思われる

    - ここでは、リポジトリ名（を含むURL）を以下とした

    https://github.com/moriyamaES/api-lessen-udemy'

2. ローカルのgitリポジトリに移動し、以下のコマンドを実行する

    ```git
    git add .
    ```
    
    ```git
    git commit -m "create repository"
    ```

    ```sh
    [kazuhiro@localhost ~/api-lesson-udemy (master)]
    $ git remote add origin https://github.com/moriyamaES/api-lessen-udemy
    ```
    
    ```sh
    git push --set-upstream origin master
    Enumerating objects: 23, done.
    Counting objects: 100% (23/23), done.
    Delta compression using up to 3 threads
    Compressing objects: 100% (23/23), done.
    Writing objects: 100% (23/23), 95.76 KiB | 4.79 MiB/s, done.
    Total 23 (delta 2), reused 0 (delta 0), pack-reused 0
    remote: Resolving deltas: 100% (2/2), done.
    To https://github.com/moriyamaES/api-lessen-udemy
    * [new branch]      master -> master
    branch 'master' set up to track 'origin/master'.
    ```

    - NextJsがローカルのブランチ名がデフォルトで`master`となっているため、`push`する前に、ローカルのブランチ名を`main`に変えた方がよいと思われる。

    - NextJsのプロジェクトは、`.gitignore`でソースファイルのみアップするように成ってる模様

# NestJs のプロジェクトをGitHubの初回push する手順（２回目）

- １回目の手順を修正しながら、`api-lesson-npm-udemy`のリーモートリポジトリをGitHub上に作成する。

1. `~/api-lesson-npm-udemy`をローカルでコッミトする。

    ```sh
    cd ~/api-lesson-npm-udemy/
    ```

    ```sh
    git add .
    ```

    ```sh
    git commit -m "リポジトリの作成"
    ```

1. 現在のローカルブランチのカレントを確認

    ```sh
    git branch 
    * master   
    ```

1. ルートのブランチ名を`master`から`main`に変更

    ```sh
    git branch -m master main
    ```

    ```sh
    git branch 
    * main
    ```

1. リモートリポジトリを

- NestJs のプロジェクトは自動で、`.git` ファイルと`README.md`ファイルを作成している
- このため、NestJs のプロジェクトをGitpubへ初回Pushする場合以下の手順が必要

1. GitHUbにリポジトリを、`README`無しでリポジトリを作成する

    - GitHubのリポジトリ名は、NestJsのプロジェクト名と同じとした方がよいと思われる

    - ここでは、リポジトリ名（を含むURL）を以下とした

    https://github.com/moriyamaES/api-lessen-npm-udemy.git

1. リモートリポジトリを名前を`origin`で作成

    ```sh
    git remote add origin https://github.com/moriyamaES/api-lessen-npm-udemy.git
    ```

    ```sh
    git push --set-upstream origin main
    Enumerating objects: 20, done.
    Counting objects: 100% (20/20), done.
    Delta compression using up to 3 threads
    Compressing objects: 100% (20/20), done.
    Writing objects: 100% (20/20), 82.70 KiB | 3.06 MiB/s, done.
    Total 20 (delta 0), reused 0 (delta 0), pack-reused 0
    To https://github.com/moriyamaES/api-lessen-npm-udemy.git
    * [new branch]      main -> main
    branch 'main' set up to track 'origin/main'.
    ```

git log --graph --oneline 
* cb21c78 (HEAD -> main, origin/main) リポジトリの作成

- `git log`を確認

    - `origin/HEAD`が無い 

    ```sh
    git log --graph --oneline 
    * cb21c78 (HEAD -> main, origin/main) リポジトリの作成 
    ```

- `push`してみる

    ```sh
    `git push`
    ``````
    ```sh
    git log --graph --oneline --all
    * 22024ea (HEAD -> main, origin/main) READMEを修正
    * cb21c78 リポジトリの作成
    ```    

    - `origin/HEAD`が無い状態が解消されない


- 以下のコマンドを実行し、`origin/HEAD`を作成 

    ```sh
    git remote set-head origin main
    ```

    - `origin/HEAD`が作成された 
    
    ```sh
    git log --graph --oneline --all
    * 22024ea (HEAD -> main, origin/main, origin/HEAD) READMEを修正
    * cb21c78 リポジトリの作成
    ```

# "api-lesson-npm-udemy" にて、"Hello World" を "こんちわ"に変更した後、GitHubにpush後、ローカールでcloneしたソースで "api-lesson-npm-udemy"をビルドし、"こんちわ"が表示されることかを検証する

## 環境構築

1. `@nestjs@cli`をインストール

    ```sh
    sudo npm i -g @nestjs/cli
    [sudo] kazuhiro のパスワード:

    added 263 packages in 24s

    44 packages are looking for funding
    run `npm fund` for details
    ```

1. インストール済の確認

    ```sh
    npm ls -g
    /usr/local/lib
    └── @nestjs/cli@10.1.18
    ```

## 検証の実施

1. ソースファイルを変更

    ```diff
    git diff ./src/app.service.ts
    diff --git a/src/app.service.ts b/src/app.service.ts
    index 927d7cc..ddd4ce3 100644
    --- a/src/app.service.ts
    +++ b/src/app.service.ts
    @@ -3,6 +3,6 @@ import { Injectable } from '@nestjs/common';
    @Injectable()
    export class AppService {
    getHello(): string {
    -    return 'Hello World!';
    +    return 'こんちわ';
      }
    }    
    ```

1. APサーバを起動し、"こんちわ"の表示を確認

    ```sh
     cd ~/api-lesson-npm-udemy/
    ```

    ```sh
    npm run start:dev
    ```

1. ローカルのソースをGitHubにpush

    - 別ターミナルで以下のコマンドを実行

    ```sh
    curl http://10.1.1.201:3000
    こんちわ
    ```

    - サーバを停止

1. 修正したソースをGitHubにプッシュ

    ```sh
     git commit -am "service.tsを修正"
    ```

    ```sh
    git push
    ```

    ```sh
    * 3a17c19 (HEAD -> main, origin/main, origin/HEAD) service.tsを修正
    * 22024ea READMEを修正
    * cb21c78 リポジトリの作成
    ```
    
1. ローカルのリポジトリフォルダを削除

    ```sh
    cd ~
    ```

    ```sh
    m -rf api-lesson-npm-udemy/
    ```

1. ローカルにリモートリポジトリを`clone`

    ```sh
    cd ~
    ```

    ```sh
    git clone https://github.com/moriyamaES/api-lessen-npm-udemy.git
    Cloning into 'api-lessen-npm-udemy'...
    remote: Enumerating objects: 27, done.
    remote: Counting objects: 100% (27/27), done.
    remote: Compressing objects: 100% (23/23), done.
    remote: Total 27 (delta 5), reused 26 (delta 4), pack-reused 0
    Receiving objects: 100% (27/27), 83.25 KiB | 936.00 KiB/s, done.
    Resolving deltas: 100% (5/5), done.
    ```

1. ローカルのリポジトリにて、プロジェクトをビルド

    ```sh
     cd ~/api-lessen-npm-udemy/
    ```

    ```sh
    npm run start:dev
    ```    


    
<del>    ```sh
    cd ~
    ```

    ```sh
    nest new api-lesson-npm -p npm
    ⚡  We will scaffold your app in a few seconds..

    CREATE api-lesson-npm/.eslintrc.js (663 bytes)
    CREATE api-lesson-npm/.prettierrc (51 bytes)
    CREATE api-lesson-npm/README.md (3340 bytes)
    CREATE api-lesson-npm/nest-cli.json (171 bytes)
    CREATE api-lesson-npm/package.json (1955 bytes)
    CREATE api-lesson-npm/tsconfig.build.json (97 bytes)
    CREATE api-lesson-npm/tsconfig.json (546 bytes)
    CREATE api-lesson-npm/src/app.controller.spec.ts (617 bytes)
    CREATE api-lesson-npm/src/app.controller.ts (274 bytes)
    CREATE api-lesson-npm/src/app.module.ts (249 bytes)
    CREATE api-lesson-npm/src/app.service.ts (142 bytes)
    CREATE api-lesson-npm/src/main.ts (208 bytes)
    CREATE api-lesson-npm/test/app.e2e-spec.ts (630 bytes)
    CREATE api-lesson-npm/test/jest-e2e.json (183 bytes)

    ✔ Installation in progress... ☕

    🚀  Successfully created project api-lesson-npm
    👉  Get started with the following commands:

    $ cd api-lesson-npm
    $ npm run start

                                                
                                Thanks for installing Nest 🙏
                        Please consider donating to our open collective
                                to help us maintain this package.
                                                
                                                
                    🍷  Donate: https://opencollective.com/nest
                                                

    ```
</del>

1. APサーバを起動し、"こんちわ"の表示を確認

</del>