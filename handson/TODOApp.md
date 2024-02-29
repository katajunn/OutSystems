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

### Application の作成

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

### Module の作成
前述のように、OutSystemsでは Application というものの中に Module と呼ばれるプログラムの実態をまとめる形式でアプリケーションを表現します。<br/>
ここからは、いよいよ Web アプリケーションを実装していきます。

1. 実装するモジュールのタイプが [Reactive Web App] となっていることを確認し [Create Module] ボタンをクリックします。<br/>
Module name はデフォルト（Application 名と一緒になる）のままでも変えても良いです。ここではデフォルトで進めます。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/a9e24e08-2ab1-4e98-8b90-2c5d137e688b)

2. このような画面になっていれば Module の新規作成は成功しています。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/86d72cf0-3d45-48df-bd1e-6fcc52045878)

3. まずはデータモデルから作成していきましょう。これは RDBMS におけるテーブルに該当します。
   Service Studio の右上あたりにある Dataタブを選択し [Database] を右クリック、メニューから [Add Entity] を選択します。
   
   ![image](https://github.com/katajunn/OutSystems/assets/120441205/b9b57540-a44b-4ab3-a56e-7e8121b46c4d)

4. Entity の名前を [Task] としてください。Entity を選択して F2 か、右下のプロパティの Name を編集することで入力可能です。<br/>
※赤いものが出ていますが、この後に解消するので問題ありません。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/bf98c0ae-4892-4674-9944-9a917906ed05)

5. ここまでで Entity（テーブル）を作成することができたので、次はその Entity に Attribute（カラム）を追加しましょう。<br/>
Attribute は Entity を右クリック、メニューから [Add Entity Attribute] を選択することで可能です。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/c851122d-7068-4bc3-b970-b7a11683e184)

6. 以下の 3 つの Attribute を作りましょう。Attribute Name は同じものにしてください。
   - タスクの概要：Description
   - タスクの期限：DueDate
   - タスクがアクティブかどうか：IsActive

7. このような状態になっていれば、Attribute の作成は完了です！次は UI を実装しましょう。
   
   ![image](https://github.com/katajunn/OutSystems/assets/120441205/c32c0285-94f8-4db2-87de-97e84a8a7428)

8. OutSystemsでは UI を実装するアプローチとして、以下の3つの方法が存在します。<br/>
今回は、この中の "データモデルから自動生成" の方法で実装します。OutSystems のドキュメントでは "Scaffolding" と呼ばれているものです。
   - スクラッチから作成
   - テンプレートをベースに作成
   - データモデルから自動生成

9. では Scaffolding をしましょう！[MainFlow] の部分に、先ほど作成した Task Entity をドラッグ&ドロップします。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/46f3b39c-739c-4424-aaac-cfbd2e5e6d3c)

10. 画面が2つ作成され、線でつながれていることが確認できます。この2つの画面は Task Entity を元に作成された、そのデータの一覧画面（リスト画面）と詳細画面（編集・新規登録画面）です。<br/>
エンティティのデータ内容を自動認識して一覧画面と詳細画面を自動で作成し、ボタン押下時の処理（データベースへのデータ更新、取得など）も自動で実装してくれるのが、データモデルからの自動生成機能だったのです。<br/>
※もちろん汎用性は低いですが、作成された画面を改修可能なのでゼロから画面を実装するより効率的なことが多いです

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/425d11d5-df99-4be5-8a79-d78a3334af90)

11. Interface -> MainFlow を展開すると、作成された画面が確認できます。<br/>
それぞれの画面はダブルクリックでレイアウトを確認することができます。自分好みにカスタマイズすることが可能です。
   - Taks: 一覧画面のレイアウト編集モード
     ![image](https://github.com/katajunn/OutSystems/assets/120441205/5953e907-34cc-4857-8654-0a3065e85616)
     
   - TaskDetail: 詳細画面のレイアウト編集モード
      ![image](https://github.com/katajunn/OutSystems/assets/120441205/17111b5e-ea0f-4006-83c3-8a074cb8f96d)

12. デフォルトでは、画面にアクセスする場合にログインを求める実装になっています。PE では認証情報は Service Studio で使用したものと同一です。<br/>
今回は認証を外す方法をご紹介します。Task 画面を選択し、右下の Roles の部分にある Anonymous をチェックすることで可能です。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/c23c83c8-0690-4375-b10a-07d0428ef74d)

13. 同様に、TaskDetail についてもチェックをしてください。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/6101b3d0-8a0f-41aa-98c6-10f11f535743)

14. 以上で、Module の作成は完了です！

## Publish
OutSystemsでは、ローカルマシン上の Service Studio で実装したものを ビルド、コンパイル、実行環境へのデプロイまで一気に行う機能があり、それを Publish と呼びます。<br/>
本チュートリアルを実施しているタイミングでは、おそらくみなさんは PE という実行環境を使用していると思います。PE は OutSystems が保有するクラウド環境に構築されています。<br/>
それでは、今まで皆さんが実装したものを Publish しましょう！

1. Servie Studio上の [Publish] ボタンをクリックします。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/8cccccdc-30c6-4fd7-b0f3-1d0feaff0634)

2. すると、左下に Publish の進捗が出てくるようになります。全てのプロセスが完了すると、対象のアプリケーションにアクセス可能になります。<br/>
この状態になれば正常に Publish が完了しています。<br/>
警告が出ていますが、Role を Anonymous にしていることで起きている事象です。認証を外すことは実アプリではないと思いますので、今回特有のこととご理解ください。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/0e138d18-a435-4e28-b5c0-1d06f0da8a07)

3. Servie Studio上の [Publish] ボタンが青色の [Open in browzer] ボタンに変わっているので、これをクリックします。<br/>
押下することで、この Module の "Home 画面" にアクセスすることができます。今回だと Task 画面ですね。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/d6eeed1a-ca51-47bd-ac62-c0a9321f9d1f)

4. ブラウザが開き、実装したアプリケーションが表示されました。タスクを作成したり、編集してみたりしてください！

   - 一覧画面（Task）
      ![image](https://github.com/katajunn/OutSystems/assets/120441205/aae22496-bbb5-44a2-bacb-b0300d39b256)
   - 新規登録画面（TaskDetail）
      ![image](https://github.com/katajunn/OutSystems/assets/120441205/2ca2f333-fedb-47c0-9a3a-c02a1bfea237)
   - 編集画面（TaskDetail）※データを1件以上作ると遷移可能
      ![image](https://github.com/katajunn/OutSystems/assets/120441205/73794278-e6f1-4783-8628-8ded0878b185)

5. 以上で、タスクを作成し、それらを一覧表示・編集できるアプリケーションを実装することができました！

## タスク管理アプリケーションの改修
余分なタスクは削除したい気持ちになったあなたは、削除機能を実装したいと考えました。OutSystems でアプリケーションを改修してみましょう！

1. 一覧画面にボタンを追加しましょう。Task 画面を開いて、一覧の Is Active あたりをクリックしてください。<br/>
すると画面上部に列を追加できそうなアイコンが出てきますので、右側に列を追加するものを押下してください。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/b8981ce1-16aa-4f18-8284-b0bc1f588a93)
   ![image](https://github.com/katajunn/OutSystems/assets/120441205/40aac038-3ed2-4aba-bbdb-a65f95de3a06)

2. 列が追加されたため、ボタンを配置します。Button をドラッグ&ドロップするとボタンを追加できます。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/7ff37473-1e0f-4944-a890-d89bb6c3e89b)
   ![image](https://github.com/katajunn/OutSystems/assets/120441205/2f352cf4-2155-4629-809d-81bafa604692)

3. 赤くなっていますね。これは "ボタンに処理がくっついていないよ" という状態なので Service Studio が "おかしいんじゃ？" と教えてくれている状態です。<br/>
そのため、ボタンに紐づく処理を実装していきましょう。その前に、Button という名称では何が何やらわからないため、ボタンの名前を変更しましょう。"Delete" とします。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/42479bd7-ed4d-4107-a69c-dd2686884186)

4. Delete ボタンをダブルクリックします。すると、DeleteOnClick という Client Action が作成されました。<br/>
OutSystems ではブラウザで実行されるクライアントロジックとサーバーで実行されるサーバーロジックの2種類を実装できますが、クライアントロジックのガワが作れらた状態です。<br/>
OutSystems ではロジックは全てこのようなフローで表現されます。フローにはまだ何もなく、つまりは何もしてくれない状態なため、特定の Task を削除する処理を実装していきます。 

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/fef66473-da45-4067-b543-8b7cbd95bec0)

5. まずは特定の Task を削除するために、DeleteOnClick に引数を追加します。<br/>
DeleteOnClick を右クリックし、[Add Input Parameter] を選択し、パラメーターの名称を [TaskId] とします。Data Type は Task Identifier になっていることを確認してください。<br/>
※ Task となっている場合は修正が必要です。Data Type のプルダウンから選択してください。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/76f818f6-2974-44af-8103-700d2a221373)

6. では、この TaskId を使って特定のタスクを削除する処理を実装しましょう。<br/>
Data タブで Task Entity を展開してください。OutSystems で Entity を作成すると、その Entity に対する CRUD 操作ができる処理が生成されます。<br/>
今回はその中から、"DeleteTask" というものを使います。"DeleteTask" をフローの上にドラッグ&ドロップします。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/45dd9f24-074b-4f9a-97bc-9c9acbd14d3f)

7. DeleteTask には引数が必要なので、先ほど DeleteOnClick で定義した TaskId を渡してあげます。<br/>
こうすることで、「DeleteOnClick に渡された引数を使って Task レコードを削除する」処理が実装できました。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/9ee73733-293e-42f2-b9f8-f18ffd49d2de)

8. ただまだボタンが赤いままですね。赤い原因を探りましょう。左下の Error などが書かれているタブをクリックするとエラーや警告の一覧を見ることができます。<br/>
その中で赤くなっているものをダブルクリックしてください。その原因となる箇所に飛んでくれます。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/f6f96e70-de8f-4cd7-bf97-a132a1e57ce6)

9. どうやら、「DeleteOnClick という処理は作ってその中身を実装したはいいものの、画面からそのボタンを押下するときに引数を渡していない」ことが原因だったようです。<br/>
画面上から値を渡してあげていなかったので、ちゃんと機能しないということを Service Studio が教えてくれていたんですね。<br/>
そうと分かればボタンへ値を渡してあげましょう。右下の TaskId のプルダウンから [GetTasks.List.Current.Task.Id] を選んでください。<br/>
これは「表示するために取得したタスクの一覧データから、タスクの Id を選択した」という意味です。Current は Iterator や Cursor のようなものです。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/57f5769d-7c58-4a0a-83a0-200c89457d6c)

10. ボタンが緑になりましたね。Publish して動作確認をしてみましょう。

11. しかし、何かが変です。タスクを作って Delete を押下してみても何も起こりません。でも画面をリフレッシュさせるとデータは消えているのでロジックは正しく動いていそうです。
   - Delete ボタン押下直後。データが消えていない。
      ![image](https://github.com/katajunn/OutSystems/assets/120441205/ceac3e21-733d-4025-9e02-642d0c01e95d)
   - リフレッシュ（F5等）後。データは消えている。
      ![image](https://github.com/katajunn/OutSystems/assets/120441205/9ea87099-9b10-40ff-a3d4-548fc00099bc)

12. 実は、先ほど実装した DeleteOnClick に足りないものがあったのです。確かにデータは削除しているのですが、その後に「データ取得処理をもう一度実行する」という処理がありませんでした。<br/>
ここにその処理を実装しましょう。左側から [Reflesh Data] をドラッグ&ドロップします。

   ![image](https://github.com/katajunn/OutSystems/assets/120441205/1ca96334-7b3a-477e-967a-2f4d682f1be1)

13. どれをもう一回するの？と聞かれるので、[GetTasks] を選択して [Select] を押下しましょう。これはタスク一覧画面を自動生成したときに一緒に作成された、Task Entity から一覧データを取得してくる処理です。

    ![image](https://github.com/katajunn/OutSystems/assets/120441205/d33a4e8e-41a7-4a63-a214-ce91d08ca998)

14. この状態でもう一度 Publish してみて動作を確認してください。今度はうまくいっているはずです。

## さいごに
これで QuickStart は完了です。 OutSystems は無償で様々な学習リソースを提供しているため、ぜひ色々なアプリ作成を試してみてください。
より高度な内容を学べる Jump Start というハンズオンワークショップも定期的に行っていますので、ご興味ある方はこちらもチェックしてみてくださいね！

[OutSystems Jump Start](https://www.ctc-g.co.jp/solutions/outsystems/service/hands-on/)
