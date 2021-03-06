---

copyright:
  years: 2015, 2017
lastupdated: "2017-7-12"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}

# Git ソース管理と連携するようにローカル・クライアントをセットアップする
{: #git_local}


GitHub、GitHub Enterprise、または Git Repos and Issue Tracking のリポジトリーにあるソース・コードを、ローカルで、または Eclipse Orion Web IDE で管理したり処理したりできます。ローカルで作業するには、Git コマンド・ライン・インターフェースなどの Git クライアントを使用してリポジトリーを複製し、任意のエディターを使用してコードを編集します。Eclipse で作業する場合は、バージョン管理用の EGit プラグインをインストールできます。

## コマンド・ラインからの Git プロジェクトの複製


## 始めに
{: #git_before_clone}

1. ブラウザー以外から Git サーバーにアクセスするには、認証用に個人用アクセス・トークンか SSH 鍵を作成する必要が生じることがあります。以下の表に、認証のセットアップに必要な作業が示されています。

| Git タイプ| HTTPS のセットアップ| HTTPS で使用するもの|  SSH のセットアップ|
|:-----------|:-------------|:------------|:-------------|
| Git Repos and Issue Tracking (git.ng.bluemix.com)| [個人用アクセス・トークン](/docs/ContinuousDelivery/git_working.html#create_pat)| Git Repos and Issue Tracking のユーザー名 (IBM id ではない) と個人用アクセス・トークン| [SSH 鍵の構成](/docs/ContinuousDelivery/git_working.html#create_ssh)|
| Public GitHub (github.com)| 個人用アクセス・トークンは不要、ただしセットアップして使用することも可能| GitHub のユーザー名とパスワード、GitHub のユーザー名と個人用アクセス・トークン、またはユーザー名として指定する個人用アクセス・トークンのみ| [GitHub の SSH 鍵の構成](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)|
| GitHub Enterprise| [個人用アクセス・トークン](/docs/services/ghededicated/index.html#gheded_getting_started#ghe_auth)| GitHub Enterprise のユーザー名 (IBM id ではない) と個人用アクセス・トークン| [GitHub Enterprise の SSH 鍵の構成](/docs/services/ghededicated/index.html#gheded_getting_started#ghe_auth)|

**注**: SSH を使用する場合は、すべての Git サーバーで単一の鍵を再利用できます。前述のリンクで説明されているように、鍵を作成するか見つけ、それを各サーバーで構成します。鍵をパスフレーズと一緒に作成すると、その鍵の使用時に、このパスフレーズを入力するよう求められます。

2. Git コマンド・ラインを使用する場合は、以下のようにします。

    a. Git がインストールされているかどうかを確認します。コマンド・ラインで `git version` と入力します。Git がインストールされている場合は、バージョン番号が表示され、作業を開始できます。

    b. Git がインストールされていない場合は、[Git の Web サイトに進みます ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://git-scm.com/downloads){: new_window}。

    c. ご使用のオペレーティング・システム用のバージョンをダウンロードしてインストールします。デフォルトのインストール値を受け入れることができます。


### プロジェクトの複製
{: #git_clone}

Web IDE を使用せずに任意のデスクトップ・ツールを使用してリポジトリーのコンテンツにアクセスできるように、Git リポジトリーを複製してプロジェクト・ファイルのローカル・コピーを作成します。

1. ツールチェーンの概要ページから、複製対象のリポジトリーのカードをクリックします。

2. リポジトリーの URL を収集します。

   a. GitHub で、**「Clone or download」**をクリックします。HTTPS を使用するには、**「Use HTTPS」**を選択します。SSH を使用するには、**「Use SSH」**をクリックします。クリップボード・アイコンをクリックして URL をコピーします。

   b. Git Repos and Issue Tracking で、**「HTTPS」**または**「SSH」**を選択し、フィールド内に URL をコピーします。

3. コマンド・ラインを開きます。

4. Git リポジトリーのローカル・コピーを格納するディレクトリーに移動します。

5. `git clone` と入力し、URL を貼り付け、Enter キーを押します。

6. 認証を求められたら、前述の表で定義されているとおりに、該当する情報を入力します。


ダウンロードが完了すると、リポジトリー内にローカル・バージョンのファイルが格納されます。Git の使用法について詳しくは、[Git の資料 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")]](http://git-scm.com/doc){: new_window} を参照してください。


## Eclipse と EGit プラグインを使用してリポジトリーにアクセスする
{: #git_egit}

ソース管理に Git を使用するプロジェクトがあり、Eclipse を使用している場合は、EGit プラグインを使用して Eclipse からリポジトリーを管理できます。EGit をインストールして構成する手順については、
[EGit チュートリアル ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")]](http://eclipsesource.com/blogs/tutorials/egit-tutorial/){: new_window} を参照してください。Git Repos and Issue Tracking を使用しており、問題が生じている場合は、[Git Repos and Issue Tracking](git_working.html#git_local) を参照してください。

## IBM Eclipse Tools を使用した開発
{: #git_eclipse_tools}

IBM Eclipse Tools for Bluemix には、Eclipse 環境にインストールして IDE と Bluemix を統合できるプラグインが用意されています。

このツールを使用すると、以下のタイプのファイルとサーバーを Eclipse IDE または IBM WebSphere&reg; Application Server Developer Tools (WDT) から直接 Bluemix サーバーにデプロイできます。

* JavaScript ファイル
* WAR (Web アーカイブ) ファイル
* EAR (エンタープライズ・アーカイブ) ファイル
* Liberty Profile のパッケージ・サーバー

さらにデプロイメントの一部として、サービスを作成してアプリにリンクしたり、環境変数を定義したりすることもできます。IBM Eclipse Tools について詳しくは、[IBM Eclipse Tools for Bluemix を使用したアプリのデプロイ](../../manageapps/eclipsetools/eclipsetools.html)を参照してください。
