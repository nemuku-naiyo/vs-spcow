# VS.スプカウ

暴走した電脳スプカウを、うーちーが救う。円形ステージで戦う3Dボスバトル。

> 「みんなと遊びたい」――1匹のスプカウが作ったプログラムが暴走し、街に巨大なスプカウを生み出しつづけている。
> うーちーはソフトクリーム光線で、巨大スプカウたちを浄化してきた。けれど今夜のスプカウは、なにかがちがう。
> うーちーは、スプカウを救えるのか？

## 遊ぶ

ブラウザで `index.html` を開くだけで遊べます（スマホ・PC対応）。
GitHub Pages で公開する場合は、このフォルダをリポジトリに置いて Pages を有効にしてください。

### 操作

| | スマホ | PC |
|---|---|---|
| 周回（左右） | 左右パッド（指をすべらせて切り替え） | ← → / A D |
| ジャンプ（空中で長押しでジェット） | ジャンプ | スペース / ↑ / W |
| 連射（その場で足を止める） | 連射（長押し） | J / Z / Enter |
| 一時停止 | タイム表示をタップ | Esc / P |

動いている間は、弱い弾が自動で出ます。

## ファイル構成

```
index.html        ゲーム本体（モデル・テクスチャ・効果音・BGMをすべて内蔵した1ファイル）
models/           3Dモデル（glTF）とテクスチャ
  uuchii_n64_200.glb / uuchii_tex_200.png   うーちー（215ポリゴン）
  spcow_boss.glb / spcow_boss_tex.png       スプカウ（439ポリゴン、表示時は10倍）
lib/              three.js を同梱する場所（three.min.js を置くとオフラインでも動く）
tools/            スプカウのモデルを作り直すためのPythonスクリプト
  spcow_build.py   形（ポリゴン）
  spcow_paint.py   テクスチャ
  spcow_export.py  glb / obj の書き出し（models/ へ）
  spcow_render.py  確認用の簡易レンダラー
.nojekyll         GitHub Pages でそのまま配信するための空ファイル
```

### モデルを作り直す

```
cd tools
python3 spcow_paint.py    # テクスチャ（spcow_tex.png）
python3 spcow_export.py   # ../models/ に glb・obj を書き出し
```

必要なもの：Python 3、numpy、Pillow。

## 使っているもの

- [three.js](https://threejs.org/) r128（MIT License）… `lib/three.min.js` があればそれを、なければCDNから読み込み
- 効果音・BGM はすべてブラウザの Web Audio でその場で合成（音声ファイルなし）

## 記録

ベストタイムなどの記録は、遊んだブラウザの中（localStorage）にだけ保存されます。
