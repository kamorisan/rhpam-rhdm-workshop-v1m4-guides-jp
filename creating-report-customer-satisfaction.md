# 顧客満足度レポートの作成

ここで、顧客満足度を可視化する2つ目のレポートを作成します。このために、先ほど作成した `customer-satisfaction` *データセット* を使用します。

このレポートでは、満足度スコアの範囲ごとの顧客満足度レポートの数を示す棒グラフを作成してみます。
すなわち、50%よりも低いスコアをコアとするすべてのスコアをカウントし、その後、5%の範囲ごとのスコアの数をカウントしています（例えば、50%～55%、55%～60%、60%～65%など）。

データセットで使用したクエリは、顧客満足度データをこれらの範囲のいずれかに既に分類していることに注意してください。

1. *メニュー* -> *設計* -> *ページ* に移動し、画面中央の *新規ページ* ボタンをクリックします。
    - **名前**: `customer-satisfaction-report`
    - **スタイル**: `流動`
2. レポートページのエディターが開きます。
3. *コア* メニューから、*HTML* コンポーネントをページの上部にドラッグします。これにより、*HTMLエディタ* が開きます。
4. *HTMLエディタ* で テキストを中央に揃え、*太字* フォントを有効にし、*h1 (大きなタイトル)* を選択します。`Customer Satisfaction Report` と記入し、*OK* をクリックします。
![Create Report Customer Satisfaction HTML]({% image_path dashboard-customer-satisfaction-html.png %}){:width="600px"}
5. *レポート* コンポーネントから、*バー* をページにドラッグします。*新規ディスプレイヤー* 画面で、*データ* タブをクリックして、`customer_satisfaction` データセットを選択します。
6. 次に、*カテゴリ* ドロップダウンリストで `satisfactionscore_range` を選択し、*シリーズ* セクションで `id`  セクションの `回数` を選択します。`OK`をクリックします。
![Create Report Customer Satisfaction Bar]({% image_path dashboard-component-bar-config.png %}){:width="600px"}
7. ページに *テーブル* コンポーネントを追加し、データプロバイダと同じ *データセット* を使用します。
8. 自由にコンポーネントを追加して、ページをカスタマイズしてみてください。

前回のレポートと同様に、棒グラフのバーを選択してデータのフィルタリングを有効にしてみてください。
テーブルのエントリがどのようにフィルタリングされるかに注目してください。

![Create Report Customer Satisfaction]({% image_path create-report-customer-satisfaction.png %}){:width="600px"}
