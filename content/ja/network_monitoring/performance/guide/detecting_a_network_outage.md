---
title: ネットワーク停止の検出
kind: ガイド
aliases:
  - /ja/network_performance_monitoring/guide/detecting_a_network_outage/
---
ネットワークの停止は、多くの場合、インフラストラクチャー、アプリケーション、またはコンテナの問題に偽装されているため、検出が困難です。地域のネットワークパフォーマンスまたは依存しているサードパーティのエンドポイントのパフォーマンスを可視化しないと、サードパーティまたはクラウドの地域の停止を検出するのに数時間かかる場合があり、最終的には顧客に影響を与える可能性があります。

ネットワークパフォーマンスモニタリング (NPM) を使用すると、ネットワークの停止を数分で検出できます。プロセスメトリクス、トレース、ログ、インフラストラクチャーメトリクスとともにネットワークフローデータを分析することにより、問題の根本について推測することを回避し、代わりに除去プロセス (以下の手順を参照) を使用して、ネットワークの停止が発生しているかどうかを判断できます。

## 基底のインフラストラクチャーに過負荷がかかるトラフィック

NPM メトリクスを使用して、ソースエンドポイントが大量のトラフィックを送信しているのか、宛先エンドポイントに多数のオープン接続を確立しているのかを確認します。障害のある依存関係 (たとえば、高レイテンシーの依存関係) を選択する場合、サイドパネルのグラフを使用して、このようなトラフィックの急増を見つけることができます。この急増は、受信アプリケーションを圧迫して (TCP の場合) すべての接続に応答できなくなり、パケット損失が増加し、TCP レイテンシーが増加する可能性があります。

{{< img src="network_performance_monitoring/guide/detecting_a_network_outage/npm-metrics.png" alt="基底のインフラストラクチャーのトラフィックの過負荷">}}

## 基底のインフラストラクチャーの CPU の過剰消費

一方、クライアントまたはサーバーエンドポイントのいずれかのリソースの過剰消費は、両者間の通信不良の原因になる可能性があります。サイドパネルの **Processes** タブで、ソースエンドポイントまたは宛先エンドポイントのいずれかで実行されているプロセスにビューのスコープを設定して、基底のホストまたはコンテナのパフォーマンスを低下させ、ネットワーク呼び出しに応答する能力を低下させている可能性のある重いソフトウェアを見つけます。この場合、基底のホストが熱くなり、アプリケーションのレイテンシーが発生しているかどうかを知ることに加えて、それが熱くなっている理由を知る必要があります。プロセスメトリクスをコマンドでグループ化すると、CPU およびメモリリソースを消費している特定のワークロードを特定できるため、この粒度が得られます。

{{< img src="network_performance_monitoring/guide/detecting_a_network_outage/processes.png" alt="基底のインフラストラクチャーの CPU の過剰消費">}}

## コード内のアプリケーションエラー

ネットワークエラーとレイテンシーは、クライアント側のアプリケーションエラーによっても発生する可能性があります。たとえば、アプリケーションがループ上で不必要に接続を生成している場合、それに依存するエンドポイントを圧迫し、ダウンストリームアプリケーションとネットワークの問題につながる可能性があります。NPM の **Traces** タブまたは APM Traces の **Network** タブを使用し、アプリケーションリクエストエラーを探して、これが当てはまるかどうかを判断します。

{{< img src="network_performance_monitoring/guide/detecting_a_network_outage/traces.png" alt="コード内のアプリケーションエラー">}}

これらの手順のいずれも根本原因につながるものではなく、特定のリージョン、アベイラビリティーゾーン、またはサードパーティドメインエンドポイントを対象とする依存関係のエラーとレイテンシーが発生している場合は、ネットワークの停止が発生しています。この場合、関連するプロバイダーに連絡して、問題を報告して解決することができます。