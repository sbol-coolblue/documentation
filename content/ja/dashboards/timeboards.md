---
title: タイムボードレイアウト
kind: documentation
aliases:
  - /ja/graphing/dashboards/timeboard/
  - /ja/dashboards/timeboard/
further_reading:
  - link: /dashboards/template_variables/
    tag: ドキュメント
    text: テンプレート変数を使用してダッシュボードの機能を強化
  - link: /dashboards/sharing/
    tag: ドキュメント
    text: Datadog以外とグラフを共有
  - link: /dashboards/widgets/
    tag: ドキュメント
    text: すべてのウィジェットをダッシュボードで体験できます
---
タイムボードでは、ダッシュボード全体を定刻またはリアルタイムで自動レイアウトにより表示します。通常、トラブルシューティング、共同作業、一般データの調査に使用します。

[ダッシュボードレイアウト][1]からタイムボードレイアウトに切り替えるには、歯車メニューの `Pick Layout` を使用して `Automatic` を選択します。

{{< img src="dashboards/auto-layout.png" alt="ダッシュボードの自動レイアウトオプション"  style="width:70%;">}}

## 検索

### イベント

左上の **Search...** リンクをクリックしてイベントのオーバーレイを設定し、**Events** を選択、検索ボックスに[クエリ][2]を入力します。これにより、設計時に追加されたイベントのオーバーレイと置き換わり、タイムボードの全グラフに適用されます。イベントの発生状況がオーバーレイで時系列グラフ上に表示され、右側にはイベントの一覧が表示されます。

{{< img src="dashboards/timeboard/events_overlay.png" alt="イベントのオーバーレイ"  style="width:75%;">}}

### ログ

左上の **Search...** リンクをクリックしてログのオーバーレイを設定し、**Logs** を選択、検索ボックスに[クエリ][3]を入力します。時系列グラフ上にログの頻度がオーバーレイで表示され、右側にはイベントの一覧が表示されます。

## グラフメニュー

ダッシュボード上で時系列グラフをクリックすると、オプションメニューが開きます。

| オプション                 | 説明                                                   |
|------------------------|---------------------------------------------------------------|
| スナップショットを送信          | グラフのスナップショットを作成および送信します。                     |
| 相関関係のあるメトリクスを検索| APM サービス、インテグレーション、ダッシュボードの相関関係を検索します。 |
| View in full screen    | グラフを[全画面モード][4]で表示します。                     |
| カーソルをロック            | ページに配置されたカーソルをロックします。                         |
| View related processes | グラフ参照範囲の[ライブプロセス][5]ページへジャンプします。   |
| View related hosts     | グラフ参照範囲の[ホストマップ][6]ページへジャンプします。         |
| View related logs      | グラフ参照範囲の[ログエクスプローラー][7]ページへジャンプします。     |
| 関連トレースを表示    | グラフ参照範囲の[トレース][8]パネルに入力します。           |
| 関連プロファイルを表示  | グラフ参照範囲の[プロファイリング][9]ページへジャンプします。        |
### ログ検索クエリ

**View related logs** の検索クエリは、下記のパラメーターを使用して定義します。

* **タイムフレーム**: 選択したデータポイントを中心に置き、グラフの時間枠を使用して選択したポイントの前後のデータを表示します。
* **インテグレーションプレフィックス**: メトリクスがインテグレーションから派生しっている場合、Datadog は同じインテグレーション名で `source`  属性にフィルターを掛けます。
* **タグ**: グラフで使用されるタグ (*template variable*、*split by*、*filter by*) はすべて、自動的に検索クエリに追加されます。

## ヒントとコツ

- ウィジェットアイコンをクリックして、ドラッグせずにダッシュボードに追加します (キーボードショートカットの `N` と `shift+N` でも可能)
- ウィジェットの左下または右下のサイズ変更ハンドルをダブルクリックして、隣接する空のスペースを即座に埋めます
- なげなわツールを使用するには、空のスペースをクリックしてドラッグします
- 複数のウィジェットを選択すると、一括アクションを含むアクションメニューが表示されます
- `cmd+G` または `ctrl+G` を押して、選択したウィジェットをグループ化します 
- ダッシュボードヘッダーの歯車メニューを使用して、ダッシュボード上のすべてのグループを開いたり折りたたんだりします

## その他の参考資料

{{< partial name="whats-next/whats-next.html" >}}

[1]: /ja/dashboards/dashboard
[2]: /ja/events/#event-query-language
[3]: /ja/logs/search_syntax/
[4]: /ja/dashboards/widgets/#full-screen
[5]: https://app.datadoghq.com/process
[6]: https://app.datadoghq.com/infrastructure/map
[7]: https://app.datadoghq.com/logs
[8]: /ja/tracing/
[9]: /ja/tracing/profiler/