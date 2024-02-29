# Quick Start for OutSystems 

OutSystems をこれから使う方に向けた、アプリケーション開発を体験できるクイックスタートです。

## 成果物
タスクを作成・編集・削除できるシンプルなタスク管理アプリケーションが完成します。<br/>
一覧画面と詳細画面という2画面構成です。

![image](https://github.com/katajunn/OutSystems/assets/120441205/fdfc839c-bc6f-428b-8fc9-aaf79fced506)

本チュートリアルは Service Studio の Help メニューから「Build an App in 5 min tutorial」を選択することで、ガイドのウィザードを起動できます。
Service Studioのメニューから実施するチュートリアルはモバイルアプリですが、こちらではReactive Web Appバージョンで作成していきます。

## 事前準備
OutSystems PE(Personal Environment) アカウント作成 ※無償<br/>
このページの「無料版ダウンロード」ボタンより作成頂けます。
https://www.ctc-g.co.jp/solutions/outsystems/

## Service Studio の起動
1. 事前準備でインストールした OutSystems の開発環境（Service Studio）を起動します。

![image](https://github.com/katajunn/OutSystems/assets/120441205/dadad98f-7c12-4584-b9e7-268d1a73834b)

2. 事前準備で作成した PE 環境へログインします。

![image](https://github.com/katajunn/OutSystems/assets/120441205/240a57c5-ab1f-416b-b3c3-eac9f3469f7d)
![image](https://github.com/katajunn/OutSystems/assets/120441205/6af8ac62-f8b9-4554-bed0-7c0d9e6dae07)

3. このような画面になれば Service Studio の起動は完了です！

![image](https://github.com/katajunn/OutSystems/assets/120441205/1b6c2bbe-9a10-42a7-8f64-ca7f8b5ce06b)

## タスク管理アプリケーションの実装

OutSystems で実装をする場合、以下の2つを作成する必要があります。
* Application
  * モジュールをまとめた単位で OutSystems 独自の用語。複数のモジュールを内包することができる。一般用語の"アプリケーション"と混同しがちなため、英語で表記します。
  * Java でいうと EAR のような存在。
* Module
  * Web アプリケーションや共通処理の実装成果物。
  * Java でいうと WAR や JAR のような存在。

それでは、それぞれについて進めていきましょう！

### 新規 Application の作成

1. Service Studioで [New Application] をクリックします。

![image](https://github.com/katajunn/OutSystems/assets/120441205/1dec0788-359e-49ea-87ce-43d276783f64)

2. [From scratch] を選択して [Next] ボタンをクリックします。<br/>
※今回はスクラッチで（＝ゼロから）開発しますが、予め用意したテンプレートをベースに実装を開始することも可能です。

![image](https://github.com/katajunn/OutSystems/assets/120441205/fb291814-d8e6-44d4-b137-8e0a8d7b3b29)

3. [Reactive Web App] を選択して [Next] ボタンをクリックします。<br/>
Reactive Web App とはレスポンシブな Single Page Application のことを意味しています。

![image](https://github.com/katajunn/OutSystems/assets/120441205/cdb70ec2-ab99-43f8-a045-8aab43a4d87b)

4. 任意の Application 名を設定します。ここでは [TODOList] としていますが、好きな文字列で大丈夫です。Application 名を設定したら [Create App] ボタンをクリックします。<br/>
ここではデフォルト選択されている色（毎回変わります）から変えていませんが、好きな色やアイコンも設定して頂いてももちろん OK です。

![image](https://github.com/katajunn/OutSystems/assets/120441205/aaf1d276-9b70-41c1-9a0a-0b23212ecba8)

5. このような画面になれば Application の作成は完了です！

![image](https://github.com/katajunn/OutSystems/assets/120441205/a9e24e08-2ab1-4e98-8b90-2c5d137e688b)

### モジュールの開発

OutSystemsでは、アプリケーションというプロジェクトの中に、モジュールと呼ばれるプログラムの実態がぶら下がる形でアプリケーションが構成されます。

* モジュールについてもっと知りたい方は[こちら](https://success.outsystems.com/ja-jp/Documentation/11/Developing_an_Application)をご覧ください。

1. ここでは、Reactive Web Appとしてアプリを開発するので、実装するモジュールのタイプが [Reactive Web App] となっていることを確認し [Create Module] ボタンをクリックします。

![](./images/009.png)

UI（画面）を作成するにあたり、画面から操作する対象のデータモデルを作成します。これはデータベースとテーブルにあたるものです。
OutSystemsでは、UIを作成するアプローチとして、スクラッチから作成、テンプレートをベースに作成、データモデルから自動生成、といった大きく3つの方法が存在します。
今回は、この中のデータモデルから自動生成する方法をやっていきましょう。これは通常スキャフォールディングと呼ばれます。

2. 今回のアプリで使う[データモデルの定義ファイル](./resources/TutorialResource.xlsx)を手元にダウンロードします。

定義ファイルはExcelで、内容はこのようになっています。
![](./images/010.png)

3. Service StudioのDataタブを選択し [Database] を右クリック、メニューから [Import New Entities from Excel...] を選択します。

![](./images/011.png)

4. 先程の手順で手元にダウンロードしたExcelファイルを選択し、Improtします。

![](./images/012.png)
![](./images/013.png)

5. Service StudioのDatabaseの下に [Task] という名前のエンティティ（データベースのテーブル）と、必要最低限のCRUDの処理（メソッド）が作成されていることが確認できます。

![](./images/014.png)

6. スキャフォールディングの機能を使ってUI（画面）を作成します。 Service Studioのワークスペースが [MainFlow] になっていることを確認します。 [Data] タブから先程作成した [Task] エンティティをワークスペース上へドラッグドロップします。

![](./images/015.png)

7. 画面が2つ作成され、線でつながれていることが確認できます。この2つの画面は、Taskエンティティを元に、そのデータの一覧画面（リスト画面）と詳細画面（編集・新規登録画面）になります。 OutSystemsではエンティティのデータ内容を自動認識して、一覧画面と詳細画面を自動で作成し、ボタン押下時の処理（データベースへのデータ更新、取得など）も自動で実装してくれます。

![](./images/016.png)

8. 画面を確認します。それぞれの画面はダブルクリックでレイアウトを確認することができます。 必要であれば、自分好みにカスタマイズすることも可能です。

一覧画面のレイアウト編集モード
![](./images/017.png)

詳細画面のレイアウト編集モード
![](./images/018.png)

## アプリケーションのパブリッシュ

OutSystemsでは、ローカルマシン上のService Studioで作成したアプリケーションを、パブリッシュすることでロジックチェック→ビルド/コンパイル→実行環境へのデプロイまで一気に行ってくれます。
本チュートリアルを実施しているタイミングでは、おそらくみなさんはPersonal Environment（PE）という無料アカウントをお使いだと思います。PEの場合は、アプリケーションのデプロイ先はOutSystemsが提供しているOutSystemsクラウドになります。
スタンダードライセンス、エンタープライズライセンスをお使いの場合は、任意のクラウドインフラやオンプレにOutSystems環境を構築することで、そちらへアプリケーションをデプロイすることが可能です。

1. Servie Studio上の [1Click Publish] ボタンをクリックします。

![](./images/019.png)

2. 全てのパブリッシュプロセスが完了すると、対象のアプリケーションがAvailableになったことをお知らせするメッセージがServie Studio上に表示されます。

![](./images/020.png)

3. Servie Studio上の [1Click Publish] ボタンが青色の [Open in browzer] ボタンに変わっているので、これをクリックします。

![](./images/021.png)

4. ブラウザが開き、作成したアプリケーションが表示されました。

一覧画面
![](./images/022.png)

編集画面（詳細画面）
![](./images/023.png)

新規登録画面（詳細画面）
![](./images/024.png)

## さいごに
おつかれさまでした。これでOutSystemsを使い始めるためのチュートリアルは完了です。 すでに基本は学びましたので、応用編としていろいろなアプリ作成を試してみてください。
OutSystemsでは、定期的にJump Startというハンズオンワークショップを行っていますので、ご興味ある方はこちらもチェックしてみてくださいね！

[OutSystems Jump Start - Japan](https://www.outsystems.com/ja-jp/events/jump-start/apac/japan/)


また、社内向けなど個別にハンズオンワークショップや、OutSystemsを使ったハッカソンをご希望の方は以下までご連絡ください！

### 萩野たいじ
Developer Advodate/Community Manager at OutSystems
taiji.hagino@outsystems.com
[Twitter](https://twitter.com/taiponrock)
[LinkedIn](https://www.linkedin.com/in/taiponrock/)
