# React/Vue.js環境構築 for mac

## エディタの準備
### Visual Studio Code(VSCode)のインストール
アプリをダウンロードして実行  
https://code.visualstudio.com/download  

### VSCodeのプラグイン
VSCode本体の機能はシンプルだが、プラグインをインストールすることで機能を増やせる作りになっている  
VSCodeを起動し、左のタブからExtentionsからインストールできる  

- 日本語サポート  
[Visual Studio Code [vsCode] 日本語化](https://qiita.com/ntkgcj/items/e77331932c7983dea830)  

- eslintサポート  
javascriptの構文チェックのツール  
https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint  
[ESLintをプログラミングエディタで使う「Visual Studio Code編」](https://blog.htmlhifive.com/2018/01/17/eslint-vscode/)  

- prettierサポート  
javascriptのファイルフォーマットのツール  
https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode  
[VSCodeで自動整形ツールのprettierで自動フォーマットされるようにする](https://qiita.com/sifue/items/dd1fdc538df69aedd1da)  

- Vue.jsサポート  
.vueファイルをうまく扱うためのツール  
https://marketplace.visualstudio.com/items?itemName=octref.vetur  
[Vue.jsをVSCodeで書く時はVeturを入れてjsconfig.jsonを書こう](https://qiita.com/nyallpo/items/c50909926e465fabdb55)  

- その他のプラグインやTIPSなど  
[VSCodeで爆速コーディング環境を構築する(主にReactJS向け設定)](https://qiita.com/teradonburi/items/c4cbd7dd5b4810e1a3a9)  
[macOS で Visual Studio Code を使うためのアレコレ (2019/03/28)](https://qiita.com/satokaz/items/6a6a0d9b6489ec2d1803)  
[VSCodeのオススメ拡張機能 24 選 (とTipsをいくつか)](https://qiita.com/sensuikan1973/items/74cf5383c02dbcd82234)  


## gitとgithubの準備
### gitのインストール
macのインストールは3パターンあり、どれかでいい  
[Git のインストール 〜Git をMacにインストールしよう〜](https://tracpath.com/bootcamp/git-install-to-mac.html)  

- コマンドライン・デベロッパ・ツールをインストール  
- ダウンロードしてインストール  
- homebrewでインストール  

### gitクライアントのインストール
gitのログを見たり、コミットしたりする時に使うツール  

- SourceTreeを使う  
https://www.sourcetreeapp.com/  
[Gitクライアント! SourceTree の使い方 ～GUIでGitを使おう～](https://tracpath.com/bootcamp/learning_git_sourcetree.html)  
***アカウントの登録は必須*** 、もちろん無料ではある  

- vscodeのgitプラグインを使う  
[Visual Studio CodeでGitを利用する (1/3)](https://www.atmarkit.co.jp/ait/articles/1507/21/news017.html)  

- gitコマンドで頑張る  

### githubの準備
#### アカウント登録と、公開鍵の作成/登録
[GitHubのアカウント登録からリポジトリ操作まで](https://qiita.com/muneo/items/1321bf8cdb21178a73e2)  
アカウントを作成したら、ローカルで公開鍵/秘密鍵を作り、githubのアカウントへ登録する  
`git@github.com~~~` のアクセス方式では、鍵を使って認証するので、  
githubに鍵を登録してなければ、認証失敗する  

#### gitクライアントからgithubへの接続を確認
自分のアカウントでリポジトリ作ればテストし放題なので、必ずpull〜commit〜pushの手順を確認する  
認証まわりでうまくいかないことが多い  
[SourceTreeとGithubでGitの練習環境をつくる](https://qiita.com/naoki85/items/4f44601f1365c18035f4)  
[GitHubとSourceTreeを使って簡単にGitの開発手順を説明するよ！](https://high-programmer.com/2018/08/30/github_sourcetree_flow/)  

#### Organizationsに追加してもらう
業務のリポジトリが見れるように、権限追加を依頼する  


## nodeの準備
ローカルでビルドするために必要  

### nvm(node version manager)のインストール
プロジェクトごとにnodeのversionをわけることが多いので、  
まずはnodeのversionを選択できるようにする  

#### インストール
homebrewでインストール、またはshでインストールする  
[nvmをHomebrewでインストールしてみました](http://furudate.hatenablog.com/entry/2015/02/06/003422)  
[nvm + Node.js + npmのインストール](https://qiita.com/sansaisoba/items/242a8ba95bf70ba179d3)  

#### .bash_profile追記
`.bash_profile(または.bashrc)` の追記を忘れないこと  
追記を忘れると、ターミナル再起動時にnvm,nodeが参照できない状態になる  

```
export NVM_DIR=~/.nvm
source $(brew --prefix nvm)/nvm.sh
```

#### node8.10.0のインストールとversionの固定
```
nvm install 8.10.0
nvm use 8.10.0
nvm alias default 8.10.0
```

alias defaultの設定を忘れると、ターミナル再起動時に指定が初期設定に戻る  
`node -v` で `v8.10.0` が表示されれば完了  


## プロジェクトの読み込み
### githubからのclone
gitクライアントによる  

### 開発ブランチの切り替えと、新規ブランチの作成
開発ブランチ（またはmasterブランチ）を元に、新しい開発用のブランチを作成し、作業をする  
[【連載Git入門 第3回】SourceTreeでGitを始めよう！ブランチを切ってみよう](https://naichilab.blogspot.com/2014/01/git-3sourcetreegit.html)  
***どのブランチを元にするかは、必ず確認する***  

### プロジェクトの初期準備
clone後、ローカルのプロジェクトのルートディレクトリにて、  
`npm install` すると、必要なライブラリがインストールされ、開発の準備はほぼ完了  
ビルドを実行し(やり方はプロジェクトにより異なる)、動作確認をする  

