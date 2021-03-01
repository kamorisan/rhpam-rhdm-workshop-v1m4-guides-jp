# データセットの作成

これで *データソース* が定義されたので、*データセット* を作成することができます。

Process Automation Manager 7の *データセット* は、サポートされているプロバイダによって利用されるデータのセットを定義します。
プロバイダは、Java Bean、CSVファイル、データベーステーブルやSQLクエリ、またはElasticSearchクエリにすることができます。
プロバイダからデータを取得することとは別に、*データセット* は、データのキャッシングやフィルタリングのような機能も提供します。

1. 右上の歯車アイコンをクリックして `設定` 画面に移動します:
![Business Central Settings]({% image_path business-central-settings.png %}){:width="600px"}
2. `データセット` タイルをクリックします。
![Business Central Dataset Settings]({% image_path business-central-dataset.png %}){:width="600px"}
3. *データセットエクスプローラ* 画面で、*新しいデータセット* ボタンをクリックします。
4. プロバイダーのタイプは **SQL** を選択します。
![Business Central Dataset New Settings]({% image_path business-central-dataset-new.png %}){:width="600px"}
5. *データセット作成ウィザード* では、以下の設定を入力します:  
    - 名前: `active_tasks_per_owner`  
    - データソース: `PAM-Workshop-Reporting`  
    - スキーマ: (空欄)  
    - ソース: **クエリー** を選択し、以下のSQLクエリを使用します:  
    `select id, status, actualowner FROM task WHERE status = 'active'`  
6. *テスト* ボタンをクリックします。これでクエリが実行され、結果のプレビューが表示されます。
![Business Central Dataset New Test]({% image_path business-central-dataset-new-test.png %}){:width="600px"}
7. テストが成功したら、`次へ` ボタンをクリックして、*データセット* を保存します。
![Business Central Dataset New Test]({% image_path business-central-dataset-next.png %}){:width="600px"}

The configured query simply selects all the tasks that are active and their owners.

We now have a simple *Data Set* that can be used to create a report, which we will do in the next step of this scenario. Let's first create some additional *Data Sets* that we can use in our reporting pages.

We will now create the DataSet of our customer satisfaction.

1. In the *Data Set Explorer* screen, click again on the *New Data Set* button.
2. Select the *SQL* provider type.
3. In the *Data Set Creation Wizard*, provide the following configuration:  
    - Name: `customer_satisfaction`  
    - Data Source: `PAM-Workshop-Reporting`  
    - Schema: (leave empty)  
    - Source: enable *Query* and use the following SQL Query:  
<pre class="file" data-target="clipboard">
select *, (case
                    when satisfactionscore <= 50 then '0-50'        
                    when satisfactionscore > 50 and satisfactionscore <= 55 then '50-55'
                    when satisfactionscore > 55 and satisfactionscore <= 60 then '55-60'
                    when satisfactionscore > 60 and satisfactionscore <= 65 then '60-65'
                    when satisfactionscore > 65 and satisfactionscore <= 70 then '65-70'
                    when satisfactionscore > 70 and satisfactionscore <= 75 then '70-75'
                    when satisfactionscore > 75 and satisfactionscore <= 80 then '75-80'
                    when satisfactionscore > 80 and satisfactionscore <= 85 then '80-85'
                    when satisfactionscore > 85 and satisfactionscore <= 90 then '85-90'
                    when satisfactionscore > 90 and satisfactionscore <= 95 then '90-95'
                    when satisfactionscore > 95 and satisfactionscore <= 100 then '95-100'
                    else 'other'
              end) as satisfactionscore_range
    from customer_satisfaction
    order by satisfactionscore_range
</pre>
6. Click on the *Test* button. This will execute the query and show a preview of the result.
7. When the test is successful, click on the *Next* button and save the *Data Set*.

We have now defined two DataSets, let's build some reports.
