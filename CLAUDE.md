# 新規開拓ノート — 開発メモ

- 利用者は日本語話者の営業2名（篠原・天野）。画面の文言・説明はすべて日本語で書く。
- 構成はビルド不要の静的サイト。`index.html` 1ファイルに CSS と JS（ES module）が入っている。Firebase SDK は gstatic の ESM を直接 import。
- データ: Firestore `prospects/{id}`（顧客1社=1ドキュメント、アプローチ記録 `logs` 配列・定期アプローチ `recDays`/`done` を含む）と `settings/main`（`reps` 営業担当名、`targets` 月間目標）。
- 既存データとの互換を崩さない（フィールド名を変えるときは読み替えを入れる。例：`gyotai` は画面上「店名」、結果の旧値「担当者と話せた」「断り」は読み替えている）。
- レポートの段階表は会社数ベースで、先の段階に進んだ会社は手前の段階にも数える（右に行くほど同じか少なくなること）。
- `main` に push すると GitHub Actions で GitHub Pages に公開される。公開対象は workflow の「公開するファイルを集める」ステップに列挙したファイルのみ。新しいファイルを足したらそこにも追加する。
- 変更後は `node --check` で module スクリプトの構文を確認し、可能なら Playwright で表示を確認する。
