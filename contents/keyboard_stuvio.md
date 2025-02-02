# KeyboardStuvio
<div class="ratio ratio-16x9 mb-3">
    <iframe src="https://www.youtube.com/embed/CguZWeJUuKs?si=axfc4pe0Ww9_rgqH&amp;start=17" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

※古い動画なのでアプリ名がVirtual Studioになっていますがご了承下さい

# これは何？
キーボードの演奏をWEBカメラでトラッキングし、アバターに反映させるアプリです。

# 開発動機
- VTuber等が気軽に演奏配信をできるようにしたかったため
- 当時、[MediaPipe](https://github.com/google-ai-edge/mediapipe)というソリューションが面白そうだったので、技術的挑戦も兼ねて使ってみたかったため

# リリース時期
2021年5月 ([booth](https://natsunatsu.booth.pm/items/2956377))

# KeyboardStuvioの技術的な概要
Keyboard Stuvioでは、Webカメラを含む外部とのデータ連携を実現するため、様々な技術を使っています。

全て説明すると長くなるため、概要を1枚図で紹介するだけに留めておきます。  
以下のように、多種多様なデータを扱っている点が特徴です。
<div class="ratio ratio-16x9 mb-3">
    <img src="./assets/dist/img/keyboard_stuvio/slide0.png">
</div>

# 使用技術
## アプリ本体
- 環境: Unity
- 言語: C#
- ライブラリ等
  - [Zenject](https://github.com/modesttree/Zenject), [UniRx](https://github.com/neuecc/UniRx), [UniTask](https://github.com/Cysharp/UniTask), [MessagePack-CSharp
](https://github.com/MessagePack-CSharp/MessagePack-CSharp), [VRM](https://github.com/vrm-c/UniVRM), Perfect Sync, [VMC Protocol](https://protocol.vmc.info/), [Aura 2](https://assetstore.unity.com/packages/tools/particles-effects/aura-2-volumetric-lighting-fog-137148), [Beautify](https://assetstore.unity.com/packages/vfx/shaders/fullscreen-camera-effects/beautify-3-advanced-post-processing-233073), [Enviro](https://assetstore.unity.com/packages/tools/particles-effects/enviro-sky-and-weather-33963), [I2 Localization](https://assetstore.unity.com/packages/tools/localization/i2-localization-14884), [OpenCVForUnity](https://assetstore.unity.com/packages/tools/integration/opencv-for-unity-21088), [UnityGLTF](https://github.com/KhronosGroup/UnityGLTF), [uLipSync](https://github.com/hecomi/uLipSync)

## LandmarkDetector (V1)
- 環境: Python embeddable package
- 言語: Python3
- ライブラリ等: MediaPipe
## LandmarkDetector (V2)
- 環境: Node.js, [Electron](https://www.electronjs.org/ja/)
- 言語: JavaScript
- ライブラリ等: MediaPipe, [face-api.js](https://github.com/justadudewhohacks/face-api.js)

# 苦労した点
## LandmarkDetectorのパフォーマンスの改善
- 最初は、実装の簡単さからPythonでMediaPipeを動かしていましたが、JavaScriptで動かした方がパフォーマンスが良い事がわかったため、JavaScriptへの移行を決断しました
- しかし、アプリの配布を考えるとJavaScriptが動作する環境ごと配布したかったため、Electronを使用してNode.js環境をパッケージングすることにしました
- [Electronはメインプロセスとレンダラープロセスに分けて実装する必要があり](https://www.electronjs.org/ja/docs/latest/tutorial/process-model)、「Pythonのコードを少し改変して移植」みたいな感じにはならず、ほぼ書き直しになったのが苦労した点です
- また、様々なnpmパッケージを利用して開発を進めましたが、「何故かメインプロセスだと使えるがレンダラープロセスだとエラーが出る」みたいな事がよくあり、そのたびに原因を調査して改修したり、代替パッケージを探す等したのも苦労した点です

## 座標系の変換
- Keyboard Stuvioには様々な座標系があるのですが、それらをうまく変換することに苦労しました
- 大きく分けて、Unityの座標系、OpenCVの座標系、MediaPipeの座標系([手](https://ai.google.dev/edge/mediapipe/solutions/vision/hand_landmarker/web_js?hl=ja#handle_and_display_results)、[全身](https://ai.google.dev/edge/mediapipe/solutions/vision/pose_landmarker/web_js?hl=ja#handle_and_display_results))があり、これらの変換に苦労しました
- 特に、回転の変換については理解が浅かったため、この[あたりの記事](https://qiita.com/drken/items/0639cf34cce14e8d58a5)を参考にして愚直に変換処理を実装しました
