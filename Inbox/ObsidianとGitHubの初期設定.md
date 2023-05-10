[Obsidianで作成したMDファイルをGitのリポジトリで管理する - Qiita](https://qiita.com/xle_quality/items/7b386972c99bcc92bd6e)

以下のモノが必要になる
-   Git
-   GitHub Desktop
-   Obsidian

GitHub DesktopでRepositoryを作成する

Fileタブより、New repository...を選択

Create a new repository画面が表示されるので
-   Name... Repositoryの名前を入力
-   Local Path... ローカルディスク上の任意のフォルダを選択してください。後ほど、このローカルフォルダをObsidianのVault（プロジェクト）として指定します。  （今回は、Documentsに設定した）（設定したフォルダに、リポジトリの名前のフォルダが作られる）
- ほか設定項目は現状無視でOK
を記入してRepositoryを作成します

Repositoryを作成すると、以下のような画面に遷移しますので、Publish repositoryをクリックします。


Obsidian Gitを入れて、Obsidianの設定のホットキーに移動して、以下を設定する
-   Obsidian Git: Commit all changes = Ctrl + Shift + C
-   Obsidian Git: Pull = Ctrl + Shift + P
-   Obsidian Git: Push = Ctrl + Shift + S

