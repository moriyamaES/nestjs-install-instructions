# restapi-todo-nestjs-udemy
NestJS + Next.js によるフルスタックWeb開発（udemy）（学習用）

- 参考サイト

    - [講座：NestJS + Next.js によるフルスタックWeb開発のGitHub](https://github.com/GomaGoma676/restapi-todo-nestjs)


## 環境

- `node-js`のバージョン

    ```sh
    node -v
    v20.5.1
    ```

- `npm`のバージョン

    ```sh
    npm -v
    9.8.0
    ```

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
