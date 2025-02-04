# GCPでのゲームサーバーのホスティング
友達と遊ぶゲームでサーバーをホスティングする必要があったため、GCPを用いて環境を構築しました。  
また、GASを使って簡単なWebページを作り、誰でもいつでもサーバーを起動できるようにしました。

更に、サーバーとの通信を監視し、一定時間通信がない場合は自動でサーバーをシャットダウンするようにし、無駄な料金が掛からないようにしました。

<figure class="figure">
  <img class="figure-img img-fluid" src="./assets/dist/img/game_server_on_gcp/screenshot.png">
  <figcaption class="figure-caption text-center">GASで作ったWEBページのスクリーンショット</figcaption>
</figure>

# 開発動機
- 誰でもいつでも起動できるゲームサーバーが欲しかったため
- 当時、仕事でGCPを触っており、自分で環境構築をゼロからやってみたかったため
- 価格的にも、ゲームサーバーのホスティング専用サービスを使うより安価だったため

# 制作時期
- 2024年2月 PalWorld
- 2021年2月 Valheim

# 使用技術
- 環境: [GCP](https://cloud.google.com), [GAS](https://developers.google.com/apps-script?hl=ja)
  - [GCE](https://cloud.google.com/products/compute?hl=ja), [Cloud Monitoring](https://cloud.google.com/monitoring?hl=ja), [Cloud Functions](https://cloud.google.com/functions)
- OS: Linux
- 言語: HTML, JavaScript, CSS

# 技術解説
- GCEでLinuxマシンをホストし、その中でゲームサーバーを起動するようにしました
- Cloud Moniringでゲームサーバーへの通信を監視し、一定時間通信がない場合、Cloud Functionsを経由してGCEをシャットダウンするようにしました
- GASでWebページを作り、そこからGCEの起動とゲームサーバーのIPアドレス取得ができるようにしました

# 苦労した点
- ポートの許可設定や、権限設定まわりで苦労しました
- 分からないことが出てくるたび、ドキュメントや解説記事を探して解決しました
