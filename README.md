# 顧客管理アプリ

新規開拓先の顧客情報・アプローチ記録を営業担当別に管理するWebアプリです。

- 今日やることのお知らせとワンタップ記録
- 毎月の定期アプローチカレンダー（未 → 済）
- 顧客一覧（担当・店名・住所・定期アプローチ、並べ替え・絞り込み、Excel/CSV一括取り込み、重複チェック）
- レポート（アプローチ → 購買担当接触 → アポ獲得 → 商談 → 成約 の段階表、営業別・都道府県別）

## しくみ

| 役割 | サービス |
|---|---|
| 画面 | GitHub Pages（`main` に push すると自動で公開） |
| データ保存・同期 | Firebase Firestore |
| ログイン | Firebase Authentication（メール / パスワード） |

## ファイル

| ファイル | 内容 |
|---|---|
| `index.html` | アプリ本体（画面・処理すべて） |
| `firebase-config.js` | Firebase の接続設定 |
| `firestore.rules` | データベースのアクセスルール（Firebase コンソールに貼り付けて使う） |
| `manifest.webmanifest`, `icons/` | スマホのホーム画面に追加したときの名前とアイコン |
| `.github/workflows/pages.yml` | GitHub Pages への自動公開 |

## ログインできる人を増やす・減らす

Firebase コンソール → Authentication → Users で追加・削除します。
アプリ側から新しいアカウントは作れません（Authentication → 設定 → ユーザーアクション で「作成（登録）を有効にする」をオフにしておくこと）。

## バックアップ

顧客一覧の「CSV出力」で、月1回程度パソコンに保存してください。
