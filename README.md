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

- `npm run npm start:dev`で起動成功！！→ 結論、 @nestjs/cli が環境でも起動できる！！

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