# データソースの作成

レポートページを構築する前に、まず、レポートがレンダリングするデータを提供する **データソース** を定義して作成する必要があります。

Process Automation Manager 7 のデータセットは、Java Beans、CSV、SQLなど様々なデータプロバイダを利用することができます。
この例では、SQLプロバイダを利用したデータセットを使用します。

今回のシナリオでは、**クレジットカードのチャージバック申請** のユースケースのタスクデータと顧客満足度データを格納したデータベースを用意しました。
このデータベースは、OpenShift環境で稼働している事前に提供されたPostgreSQLデータベースです。

* Host: `postgresql.labs-infra.svc.cluster.local`
* Port: `5432`
* User: `postgres`
* Password: `postgres`
* Database:  `postgres`

Business Centralでは、このデータを使用して新しい **データソース** を作成し、後で **データセット** として使用できるようになります

新しい **データソース** を作成する前に、まず、データベース用の正しいドライバをインストールする必要があります。

---
**NOTE**

Process Automation Manager 7 は、プラットフォームの構成設定に応じて、MariaDB、MySQL、PostgreSQLのための事前に提供されたデータベースドライバを提供することができます。
お使いのバージョンに既に設定済みのPostgreSQLドライバが付属している場合は、ドライバを追加するステップをスキップすることができます。

---

1. 右上の歯車アイコンをクリックして `設定` 画面に移動します:
![Business Central Settings]({% image_path business-central-settings.png %}){:width="600px"}
2. `データソース` タイルをクリックします。
![Business Central Datasource Settings]({% image_path business-central-settings-datasource.png %}){:width="600px"}
3. *Drivers* セクションで、*+ Add Driver* をクリックします。
4. *新規ドライバー* で、以下の値を入力し、*完了* をクリックします:
    - Name: `PostgreSQL`  
    - ドライバークラス名: `org.postgresql.Driver`  
    - グループ ID: `org.postgresql`  
    - アーティファクト ID: `postgresql`  
    - バージョン: `9.4.1212.jre7`  

![Business Central New Driver]({% image_path business-central-settings-datasource-driver.png %}){:width="600px"}

次に、PostgreSQLデータベースに接続する *データソース* を作成します。

1. *データソース* 画面で、画面左側の *+ Add DataSource*  をクリックすると、*新規データソース追加フォーム* が開きます。
2. 以下の値を記入してください:
    - Name: `PAM-Workshop-Reporting`  
    - 接続 URL: `jdbc:postgresql://postgresql.labs-infra.svc.cluster.local:5432/postgres`  
    - ユーザー: `postgres`  
    - Password: `postgres`  
    - ドライバー: `PostgreSQL`  
3. `テスト接続` をクリックして設定をテストし、問題なければ`完了` をクリックする。
![Business Central New Datasource]({% image_path business-central-settings-add-datasource.png %}){:width="600px"}

![Business Central Test New Datasource]({% image_path business-central-settings-datasource-test-connection.png %}){:width="600px"}

データソースを作成したので、その内容を調べてみましょう。

1. 先ほど作成した `PAM-Workshop-Reporting` データソースをクリックして開きます。
2. パネル上部の *コンテンツの閲覧* ボタンをクリックします。これにより、データソースの *スキーマ* が開きます。
3. `public` スキーマの `開く` ボタンをクリックします。
![RHPAM Enablement Dataset Explore]({% image_path pam-enablement-dataset-explore.png %}){:width="600px"}
4. データベースの `public` スキーマには2つのテーブルがあります。1つは、クレジットカードのチャージバック申請案件のオープンタスクと完了タスクを含む `task` テーブルであり、もう1つは、クレジットカードのチャージバック申請案件に関連する顧客満足度の情報を含む `customer_satisfaction` テーブルです。
5. `task` テーブルの横にある `開く` ボタンをクリックして、テーブルの内容を調べます。
6. *public* スキーマページに戻り、`customer_satisfaction` テーブルの横にある `開く` ボタンをクリックして、テーブルの内容を調べます。

これで、PostgreSQL *データソース* への接続を作成したので、レポートをレンダリングするために使用する *データセット* を定義することができます。