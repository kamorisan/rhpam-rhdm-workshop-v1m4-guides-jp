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

1. Go to the “Settings” screen by clicking on the gear icon in the upper right corner:
![Business Central Settings]({% image_path business-central-settings.png %}){:width="600px"}
2. Click on the *Data Sources* tile.
![Business Central Datasource Settings]({% image_path business-central-settings-datasource.png %}){:width="600px"}
3. In the *Drivers* section, click on *+ Add Driver*.
4. In the *New driver* from, entering the following values and click on *Finish*:
    - Name: `PostgreSQL`  
    - Driver Class Name: `org.postgresql.Driver`  
    - Group Id: `org.postgresql`  
    - Artifact Id: `postgresql`  
    - Version: `9.4.1212.jre7`  

![Business Central New Driver]({% image_path business-central-settings-datasource-driver.png %}){:width="600px"}

Next, we can create the *DataSource* that connects to our PostgreSQL database.

1. In the *Data Sources* screen, click on *+ Add DataSource* on the left-hand side of the screen, which will open the *New data source form*.
2. Fill in the following values:
    - Name: `PAM-Workshop-Reporting`  
    - Connection URL: `jdbc:postgresql://postgresql.labs-infra.svc.cluster.local:5432/postgres`  
    - User: `postgres`  
    - Password: `postgres`  
    - Driver: `PostgreSQL`  
3. Click on `Test Connection` to test the setup and if the test is OK, click on `Finish`
![Business Central New Datasource]({% image_path business-central-settings-add-datasource.png %}){:width="600px"}

![Business Central Test New Datasource]({% image_path business-central-settings-datasource-test-connection.png %}){:width="600px"}

Now that we've created the DataSource, we can explore its content.

1. Click on the *PAM-Workshop-Reporting* DataSource that we've just created.
2. Click on the *Browse content* button at the top of the panel. This will open the *Schemas* of the datasource.
3. Click on thew *Open* button of the `public` schema.
![RHPAM Enablement Dataset Explore]({% image_path pam-enablement-dataset-explore.png %}){:width="600px"}
4. The `public` schema of our database contains two tables. One `task` table which contains the open and completed tasks of our credit-card dispute cases, and a `customer_satisfaction` table which contains information of the customer satisfaction related to our credit-card dispute cases.
5. Click on the *Open* button next to the `task` table and explore the table's content.
6. Go back to the *public* schema page and click on the *Open* button next to the `customer_satisfaction` table and explore the table's content.

Now that we've created a connection to our PostgreSQL *DataSource* we can define the *DataSets* that we will use to render our reports.
creating-datasets.mdcreating-datasets.md
