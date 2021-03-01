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
11. レポートのタイトルとロゴのコンポーネントのサイズがほぼ同じになりました。ロゴが右上に配置されるように、コンポーネントのサイズを変更することができます。マウスをコンポーネントの間に移動し、`←` 、もしくは `→` 矢印が表示されたらダブルクリックして、タイトルコンポーネントのサイズを大きくし、画像コンポーネントのサイズを小さくします。レポートのレイアウトに満足できるまで、これを繰り返してみてください。
12. 画面上部の `保存` ボタンをクリックしてページを保存します。
13. 円グラフの上にカーソルを置くと、より多くの情報が表示されます。

作成したページは以下のようになっているはずです:

![Create Report Tasks]({% image_path create-report-tasks.png %}){:width="600px"}

ここでは、異なるレポートコンポーネントが同じ *データセット* を使用するときに、どのように相互作用するかを示します。
これを実証するために、タスクの数を合計するメトリックコンポーネントと、実際のタスクを表示するリストを追加します。

1. *レポート* コンポーネントから、*メトリック* コンポーネントをページ上の円グラフの下にドラッグします。
![Create Dashboard Metric Component]({% image_path dashboard-metric-component.png %}){:width="600px"}
2. *新規ディスプレイヤー* 画面で、*データ* タブをクリックして、`active_tasks_per_owner` データセットを選択し、`OK`をクリックします。
![Create Dashboard Metric Edit Component]({% image_path dashboard-metric-component-edit.png %}){:width="600px"}
3. *メトリック* コンポーネントのサイズを調整して小さくしてください。
4. *レポート* コンポーネントから、*テーブル* コンポーネントをページ上にドラッグし、円グラフコンポーネントの下に配置します。
![Create Dashboard Table Component]({% image_path dashboard-table-component.png %}){:width="600px"}
5. *新規ディスプレイヤー* 画面で、*データ* タブをクリックして、`active_tasks_per_owner` データセットを選択し、`OK` をクリックします。
![Create Dashboard Table Edit Component]({% image_path dashboard-table-component-edit.png %}){:width="600px"}
6. 画面上部の `保存` ボタンをクリックしてページを保存します。

*データセット* とそれを使用するコンポーネントのフィルタ機能を実演するには、円グラフの `John` タスクをクリックします。
これにより、*データセット* のフィルタが有効になり、同じデータを使用する他のレポートコンポーネントが動的に変更されます。
これにより、*メトリック* コンポーネントには *John* のタスクの合計が表示され、テーブルコンポーネントには *John* が所有者であるタスクのみが表示されるようになりました。

*John* と * George* が所有するタスクだけをフィルタリングするために、2番目のユーザ、例えば "George "を選択して追加することもできます。
他のコンポーネントがどのようにフィルタに適応するかに注目してください。

円グラフ内をクリックするか、コンポーネントの上部にあるフィルターの行から項目を削除することで、フィルターをクリアすることができます。

![Create Report Tasks 2]({% image_path create-report-tasks-2.png %}){:width="600px"}
