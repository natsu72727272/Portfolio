# 冬季バレンタリンピック～チョコ飛ばし複合～
冬季バレンタリンピック～チョコ飛ばし複合～ はUnity製のミニゲームです。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">オリンピックとヴァレンタインについて考えていたらゲームができていました。<br>それでは聴いて下さい。<br>「<a href="https://twitter.com/hashtag/%E5%86%AC%E5%AD%A3%E3%83%90%E3%83%AC%E3%83%B3%E3%82%BF%E3%83%AA%E3%83%B3%E3%83%94%E3%83%83%E3%82%AF%E3%83%81%E3%83%A7%E3%82%B3%E9%A3%9B%E3%81%B0%E3%81%97%E8%A4%87%E5%90%88?src=hash&amp;ref_src=twsrc%5Etfw">#冬季バレンタリンピックチョコ飛ばし複合</a>」<a href="https://t.co/yeBaHr3Q1k">https://t.co/yeBaHr3Q1k</a> <a href="https://t.co/j6fHCappvS">pic.twitter.com/j6fHCappvS</a></p>&mdash; なつ@VR (@VRNatsuVR) <a href="https://twitter.com/VRNatsuVR/status/1493150496483594240?ref_src=twsrc%5Etfw">February 14, 2022</a></blockquote>

# 開発動機
- 2022年2月、冬季オリンピックとバレンタインの時期が被ることに気付き、これをネタに何かしようと思い、技術的挑戦も兼ねてバカゲーを作ろうと思ったため

# リリース時期
2022年2月14日 ([unityroom](https://unityroom.com/games/valentalympic))  
(バレンタインの3日前に企画を思いつきましたが、なんとか3日で完成させて14日にリリースしました)

# 技術解説
このゲームには種目が4つありますが、実験的な設計として以下のような設計にしました
- 1つの種目をMVPパターンで表す
- Modelには入力とデータとロジックを集約し、Viewには表示に関するものを集約し、Presenterはそれを仲介する
- 基本的に情報の流れはModelからViewへの1方向のみ

<figure class="figure">
  <img class="figure-img img-fluid" src="./assets/dist/img/valentalympic/classes.png" style="width:600px">
  <figcaption class="figure-caption text-center">スケート種目の場合</figcaption>
</figure>

## 実装してみた感想
実際に実装してみて、「こういったミニゲームではギリギリ使えるが、実装の規模が大きくなると使えなさそう」という感想になりました。

### メリット
- 情報の流れをModelからViewへの1方向に限定しているので、実装がシンプルになる
  - 3日で完成させられたのは、この設計があったからかなと思っています

### デメリット
- Viewの情報をModel側で参照できないので、`GameObject`の`Transform`等を参照できない
  - なので、キャラクターを物理演算したり等はできない

# 使用技術
- 環境: Unity
- 言語: C#
- ライブラリ等
  - [Zenject](https://github.com/modesttree/Zenject), [UniRx](https://github.com/neuecc/UniRx), [UniTask](https://github.com/Cysharp/UniTask)

# 工夫した点
バカゲーなので、演出をとにかく勢いのある感じにしました。  
具体的には以下のような演出を行いました。

- スピードが上がるほど
  - スケート選手のアニメーションが速くなる
  - 集中線が激しくなる
  - チョコが入った箱のジェット噴射が大きくなる
  - チョコが入った箱の拡大縮小が速くなる
- いろんな効果音を鳴らして騒がしくする
  - 音割れすることもあるが、面白いので許容

こういった演出の効果があってか、実況してくれる人が現れたり、社内で一瞬流行ったりしたのは嬉しかったです。
