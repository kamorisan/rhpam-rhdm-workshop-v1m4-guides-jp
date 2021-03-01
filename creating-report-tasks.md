# タスクレポートの作成

*データソース* と *データセット* の設定後、レポートを作成することができます。まず、タスクのレポートを作成します。

Red Hat Process Automation Manager 7 は、プロセスやタスクのフォームを構築する際にも使用される新しいフォームモデラー技術を使用して、レポートを構築します。
このプラットフォームは、ページ内のフォームで利用できる膨大な数のレポートのコンポーネントを提供します。
さらに、レポートコンポーネントは他のフォームモデラーコンポーネントと簡単に組み合わせることができ、ユーザーはリッチなレポートページやインターフェースを構築することができます。

レポートは、Business Centralワークベンチで、**ページ** として作成されます。我々はまず、レポートを定義することができるページを設定する必要があります。

1. *メニュー* -> *設計* -> *ページ* に移動し、画面中央の *新規ページ* ボタンをクリックします。
    - 名前: `active-tasks-report`
    - スタイル: `流動`
![Create New Page]({% image_path pages-new-page.png %}){:width="600px"}
1. レポートページのエディターが開きます。
2. *コンポーネント* パレットを確認します。コンポーネントには、*コア* 、*ナビゲーション* 、*レポート* の3種類があります。
3. *レポート* コンポーネントパレットを開きます。*レポート* メニューには、*バー* 、*円（パイ）* 、*Line* 、*メーター* 、*マップ* などのさまざまなレポートコンポーネントがあることを確認してください。
4. *コア* メニューから、*HTML* コンポーネントをページの上部にドラッグします。これにより、*HTMLエディタ* が開きます。
![Create Page Add HTML Component]({% image_path dashboard-html-component.png %}){:width="600px"}
6. *HTMLエディタ* で テキストを中央に揃え、*太字* フォントを有効にし、*h1 (大きなタイトル)* を選択します。`Active Task Report` と記入し、*OK* をクリックします。
![Create Page Edit HTML Component]({% image_path dashboard-html-component-editing.png %}){:width="600px"}
7. *レポート* コンポーネントから、*円（パイ）* をページ上にドラッグします。
![Create Page Pie Chart Component]({% image_path dashboard-pie-chart.png %}){:width="600px"}
8. *新規ディスプレイヤー* の設定ページで、*データ* タブをクリックして、`active_tasks_per_owner` データセットを選択します。次に、*カテゴリ* ドロップダウンリストで `actualowner` を選択し、*OK*をクリックします。
![Create Page Edit Pie Chart Component]({% image_path dashboard-pie-chart-edit.png %}){:width="600px"}
9. ページをもう少し魅力的にしたいので、画面右上のレポートタイトルの横にロゴを追加します。*コア* コンポーネントから、*HTML* コンポーネントをページ上にドラッグし、ページタイトルの横に配置します。*HTMLエディタ* で、*イメージの挿入* をクリックします。開いたフォームで、以下のURLを画像 `https://upload.wikimedia.org/wikipedia/commons/b/b0/Beatles_logo.svg` に指定し、*OK* をクリックします。*ここにhtmlを追加してください...* のテキストを削除します。
![Create Page Image Component]({% image_path dashboard-image-url.png %}){:width="600px"}
10. このエディタでは、HTMLソースコードを直接変更することで、高度な整形も可能です。この画像を小さくしてみましょう。`表示の切り替え` をクリックします。画像タグにwidthパラメータを追加します: `width="200px"`  `<img width="200" alt="" src="https://upload.wikimedia.org/wikipedia/commons/b/b0/Beatles_logo.svg">` のようになります。表示を元に戻すと、画像が小さくなっているのが確認できます。*OK* をクリックします。
![Create Page Resize Image Component]({% image_path dashboard-image-source-edit.png %}){:width="600px"}
11. レポートのタイトルとロゴのコンポーネントのサイズがほぼ同じになりました。ロゴが右上に配置されるように、コンポーネントのサイズを変更することができます。マウスをコンポーネントの間に移動し、矢印が表示されたらクリックして、タイトルコンポーネントのサイズを大きくし、画像コンポーネントのサイズを小さくします。レポートのレイアウトに満足できるまで、これを繰り返してみてください。
12. 画面上部の `保存` ボタンをクリックしてページを保存します。
13. 円グラフの上にカーソルを置くと、より多くの情報が表示されます。

The page should somewhat look like this:

![Create Report Tasks]({% image_path create-report-tasks.png %}){:width="600px"}

We will now demonstrate how different reporting components can interact with each other when they use the same *Data Set*. To demonstrate this we will add a metric component that sums the number of tasks and a list that shows the actual tasks.

1. From the *Reporting* components, drag the *Metric* component onto the page, next to the pie chart.
![Create Dashboard Metric Component]({% image_path dashboard-metric-component.png %}){:width="600px"}
2. In the *New Displayer* configuration page, click on the *Data* tab and select the *active_tasks_per_owner* Data Set and click on *Ok*.
![Create Dashboard Metric Edit Component]({% image_path dashboard-metric-component-edit.png %}){:width="600px"}
3. Make the *Metric* component a bit smaller.
4. From the *Reporting* components, drag the *Table* component on to the page and place it under the pie chart component.
![Create Dashboard Table Component]({% image_path dashboard-table-component.png %}){:width="600px"}
5. In the *New Displayer* configuration page, click on the *Data* tab and select the *active_tasks_per_owner* Data Set and click on *Ok*.
![Create Dashboard Table Edit Component]({% image_path dashboard-table-component-edit.png %}){:width="600px"}
6. Save the page by clicking on the *Save* button on the top of the screen.

To demonstrate the filter functionality of the *Data Set* and the components that use it, click on "John's" tasks in the pie-chart. This will enable the filter on the *Data Set*, which dynamically changes the other reporting components that use the same data. Som the *Metric* component now shows the sum of John's tasks, and the table component now only shows tasks of which John is the owner.

We can also select a second user, for example "George", to filter just the tasks owned by John and George. Note how the other components adapt to the filters.

Finally, the filters can be cleared by either clicking in the pie-chart, or removing the items from filter row at the top of the component.

![Create Report Tasks 2]({% image_path create-report-tasks-2.png %}){:width="600px"}
