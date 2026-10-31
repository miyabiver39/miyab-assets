# miyab-assets

miyab-portal など自作アプリから参照する、**大きな静的ファイル（SoundFont・AIモデル・Wasm・サンプル素材など）の配信専用リポジトリ**。GitHub Pages で公開する。

配信URL: `https://miyabiver39.github.io/miyab-assets/`

## 運用ルール

* **公開リポジトリ**のため、再配布が許可されたファイルだけを置く。個人データ・非公開素材・鍵は絶対に置かない。
* 配布元のライセンスファイルを、必ず対象ファイルと同じディレクトリに同梱する。
* **一度公開したパスは不変**とする。内容を変えるときは `.../<バージョン>/` を新設し、既存パスは書き換えない（参照側のキャッシュ整合のため）。
* 大きなファイルをコミットした後に削除・差し替えしない（履歴にバイナリが残りリポジトリが肥大化する）。やり直しが必要なら新規パスに追加する。
* Git LFS は使わない（Pages は LFS の実体を配信できない）。
* 追加・変更したら `index.json`（マニフェスト）も更新する。参照側はこのマニフェストでサイズ・ハッシュを検証できる。

## GitHub Pages の制約

* 1ファイル 100 MB まで（Git の制限）。サイト全体は 1 GB 程度、帯域は月 100 GB 程度が目安。
* 全レスポンスに `Access-Control-Allow-Origin: *` が付与され、ブラウザから直接 `fetch` できる。
* ヘッダーの任意指定はできない（`Cache-Control` は約10分）。長期キャッシュは参照側の IndexedDB 等で行う。

## 収録ファイル

| パス | 内容 | ライセンス |
|---|---|---|
| `soundfonts/generaluser-gs/2.0.3/GeneralUser-GS.sf2` | GeneralUser GS 2.0.3（SoundFont, 約32MB）by S. Christian Collins | 独自ライセンス（音楽制作は私用・商用とも制限なし。同ディレクトリの `LICENSE.txt` を参照） |
| `soundfonts/musescore-general/0.2/MuseScore_General.sf3` | MuseScore_General 0.2（SoundFont, 約40MB） | MIT（FluidR3 由来。著作権表示は同ディレクトリの `LICENSE.md` に記載） |

出典:
* GeneralUser GS: https://github.com/mrbumpy409/GeneralUser-GS
* MuseScore_General: https://musescore.org/en/handbook/soundfonts-and-sfz-files
