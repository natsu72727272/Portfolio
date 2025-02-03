# 桃鉄グラフメーカー
桃鉄グラフメーカーは、「桃太郎電鉄 〜昭和 平成 令和も定番!〜」の画面をOCRし、総資産のグラフを作成するアプリです。  

<blockquote class="twitter-tweet" data-media-max-width="560" data-theme="dark"><p lang="ja" dir="ltr">Switchの桃鉄の総資産画面をOCRしてグラフ作るアプリできた！！<br><br>こんな感じで、テレビに表示される総資産画面をスマホで撮るとグラフを作ってくれる。<br>(動画はAndroidのエミュを撮影したもの)<br><br>今は最低限の機能しかないけど近いうちに公開したい。<a href="https://twitter.com/hashtag/%E6%A1%83%E9%89%84?src=hash&amp;ref_src=twsrc%5Etfw">#桃鉄</a> <a href="https://twitter.com/hashtag/%E6%A1%83%E9%89%84%E3%82%AA%E3%83%B3%E3%83%A9%E3%82%A4%E3%83%B3?src=hash&amp;ref_src=twsrc%5Etfw">#桃鉄オンライン</a> <a href="https://t.co/8179VaaESP">pic.twitter.com/8179VaaESP</a></p>&mdash; なつ@VR (@VRNatsuVR) <a href="https://twitter.com/VRNatsuVR/status/1333088160608227328?ref_src=twsrc%5Etfw">November 29, 2020</a></blockquote>

# 開発動機
- 桃鉄シリーズは、年度の終わりにプレイヤー同士で総資産グラフを眺めて1年を振り返りつつワイワイするのが楽しいのですが、「桃太郎電鉄 〜昭和 平成 令和も定番!〜」リリース当時は総資産グラフが未実装だったため、技術的挑戦も兼ねて自作しようと思ったため

# リリース時期
2020年11月 (リリース後、割とすぐにゲーム本体に総資産グラフが実装されたため公開停止)

# 技術的な説明
Xamarin.Formsで作ったアプリから、Google Cloud Visionに写真を投げてOCRを行い、返された値を元にグラフを描画・保存しています。

# 使用技術
- 環境: ASP.Net, [Xamarin.Forms](https://dotnet.microsoft.com/ja-jp/apps/xamarin/xamarin-forms)
- 言語: C#
- ライブラリ等: [Google Cloud Vision](https://cloud.google.com/vision), [OxyPlot](https://oxyplot.github.io/)

# 工夫した点
- OCR結果から、「どの資産額がどのプレイヤーに紐づくのか」を解決する必要があるのですが、そもそもプレイヤー名が正しく読み取られていない場合があります
  - 例: 「太郎」が正しいプレイヤー名なのに、OCR結果が「大郎」になっている
- そういった場合でも問題なく紐づけができるように、文字列の類似度を比較し、最も類似度が高いプレイヤーと紐づけるロジックを実装しました
- これにより、多少OCR結果がブレた場合でも意図した紐づけができるようになりました

# 苦労した点
- 私がMVVMパターンを始めて触るということもあり、MVVMパターンの学習や実装に苦労しました
