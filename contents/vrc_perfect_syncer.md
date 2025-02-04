# VRC PerfectSyncer
VRC PerfectSyncerは、VRChatでパーフェクトシンクを実現するためのツールです。  

<div class="ratio ratio-16x9 mb-3">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/SDk3bwNRlCQ?si=VQ_N70eIvplNaHYj" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

# 開発動機
- VRChatでOSCというプロトコルが使えるようになったため、技術的挑戦も兼ねて、それを用いたツールを作りたくなったため
  - 顔のトラッキングについてはKeyboardStuvioでの経験があったので、サッと作れそうだった

# リリース時期
2022年2月 ([booth](https://booth.pm/ja/items/3687658))

# 技術解説
VRC PerfectSyncerは、以下の2つのツールから構成されます。
- アバターをセットアップする SetUpper
- OSCでアバターを制御する Client

SetUpperでセットアップしたアバターをVRChatにアップロードし、そのアバターに対してClientからOSCを送ることにより、表情を制御します。

技術的な詳細については[説明記事](https://qiita.com/VRNatsuVR/items/761124985e5fcf16f599)を書いていますので、そちらをご参照いただけますと幸いです。

# 使用技術
- 環境: Unity
- 言語: C#
