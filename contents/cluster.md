# clusterの開発
2022年6月から2024年9月まで、フリーランスとして[cluster](https://cluster.mu)の開発に参画していました。  
主に操作キャラクターまわりの開発を行っていました。  

このページでは、clusterで私が開発した主な機能を紹介します。

# mocopiでのトラッキング
当時、SONYさんから[mocopi](https://www.sony.jp/mocopi)という比較的廉価なモーションキャプチャシステムが登場したため、それに対応するための開発を行いました。  
詳細につきましては、私が書いた[技術記事](https://tech-blog.cluster.mu/entry/2023/05/18)を御覧いただけますと幸いです。  

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr"><a href="https://twitter.com/hashtag/cluster?src=hash&amp;ref_src=twsrc%5Etfw">#cluster</a> v2.73をリリースしました🎉<br><br>・OSC Tracker による mocopi 対応が正式リリース！<br>・Quest版で、クラスターコインを購入する際に Meta Quest ストア の決済システムを利用するようになりました<br><br>▼詳しい情報はこちらから！<a href="https://t.co/TZ2h6A5ouI">https://t.co/TZ2h6A5ouI</a> <a href="https://t.co/OOYEMmlazB">pic.twitter.com/OOYEMmlazB</a></p>&mdash; cluster公式∞ (@cluster_jp) <a href="https://twitter.com/cluster_jp/status/1655450302143926273?ref_src=twsrc%5Etfw">May 8, 2023</a></blockquote>

# 操作キャラクターのモーション追加
当時、操作キャラクターのモーションは1種類のみでしたが、よりアバターに似合うモーションを選べるようにするため、タイプAとタイプBを追加しました。  
モーションデザイナーやPdMと連携してプロトタイプを作って手触りを確認しつつ、UI担当やサーバー担当とも協力して開発を進めました。  

<div class="ratio ratio-16x9 mb-3">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/RQW5U5_NWyM?si=fabyyG5OozokvfCy" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

[リリースノート](https://note.com/cluster_official/n/ne148d79e61cb)

# 操作キャラクターのモーション追加・刷新
当時、clusterはゲーム的な方向性を目指していたこともあり、操作キャラクターのモーションを追加・刷新しました。  
こちらもモーションデザイナーやPdMと連携してプロトタイプを作って手触りを確認しつつ、開発を進めました。

<div class="ratio ratio-16x9 mb-3">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/lzmpS9P2Lcw?si=QNLJsMoi4dzjL6Rq" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

[リリースノート](https://note.com/cluster_official/n/n33d840c2a73d)

# 11点トラッキング対応
VR環境のclusterでは、VR機器を用いることでフルボディトラッキングを行うことができます。  

当時のclusterでは、3点トラッキングと6点トラッキングが可能でしたが、より正確なトラッキングが求められていました。  
そこで、トラッキング機能を改修することで、3点、6点、8点、10点、11点のトラッキングに対応しました。  

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr"><a href="https://twitter.com/hashtag/cluster?src=hash&amp;ref_src=twsrc%5Etfw">#cluster</a> v2.62をリリースしました🎉<br><br>・PC版VRモードが11点までのトラッキングに対応！<br>・設定でマイクとは別の系統で音声を出力可能に（2/14のCluster Creator Kitアップデート後に利用できます）<br>・PC版アプリのログイン後ページデザインを刷新！<br><br>▼詳しい情報はこちら！<a href="https://t.co/04CxNUKfug">https://t.co/04CxNUKfug</a></p>&mdash; cluster公式∞ (@cluster_jp) <a href="https://twitter.com/cluster_jp/status/1624982793255284736?ref_src=twsrc%5Etfw">February 13, 2023</a></blockquote>
