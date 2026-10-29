# 0.8.9候補の設定画面例

2026-10-29、現行0.8.9/code35のアプリ自身のViewをAndroid 13/API33の一時エミュレーターで描画し、PNGとして保存した。実端末の写真ではない。独立したHTMLや描画し直したモックではなく、同じ `SetupActivity` の画面である。

| ファイル | 表示内容 |
| --- | --- |
| `business.png` | Android 13以降の「業務で読み取る準備」上部 |
| `business-bottom.png` | 同画面を下へスクロールした例。「ユーザー補助を開く」と制限時の案内ボタン |
| `restricted-help.png` | 制限付き設定のヘルプ上部。普段のキーボードとアプリ一覧の説明 |
| `restricted-help-bottom.png` | 同ヘルプ下部。「アプリ一覧を開く」と、解除後にユーザー補助へ戻る説明 |
| `settings-home.png` | 設定一覧上部。390×844dpのネイティブ表示例 |
| `settings-home-bottom.png` | 設定一覧下部。任意の自動切替と業務の読み取りが別の設定である例 |

画面例では業務連携は未設定、自動切替はOFF。設定済みの表示や制限解除の成功を示す画像ではない。端末の設定アプリ・「︙」メニュー・本人確認画面は撮影しておらず、PINなどの個人情報は含まない。実端末による導入結果は `VALIDATION.md` の実機記録を参照する。

生成には次の計測用テストを使用し、2件とも成功した。

- `InitialSetupNativeTest#android13BusinessStepOffersNormalKeyboardBeforeTryingServiceAndRestrictionRecovery`
- `SetupActivityTest#referenceImagesDrawActualNativeViewsAt390By844DpAndNormalText`

後者はアプリ自身のViewを390×844dpで測定・配置して描画する既存の画像出力機能。前者の画面は1080×2148pxのアプリ内容領域で、下部画像は描画直前に同じScrollViewをスクロールしている。余白の切除や画像編集はしていない。

画像出力の追加はAndroidテスト内だけで、本体のコード・配布APKに変更はない。撮影に使ったエミュレーターは終了し、実端末は操作していない。
