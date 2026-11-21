# このスキルへのフィードバック

スキルを使った後、ルールや雛形が合わなかった点を記録する。同じ種類が 2 回出たら `SKILL.md`、`references/`、`templates/` を直す。編集はユーザーの承認を得てから PR で行う。サービス固有の例外は、ここではなく、そのサービスの ARCHITECTURE.md に書く。

| 日付 | 案件(概要) | 段階 | 種類 | 内容 | 対応 |
| --- | --- | --- | --- | --- | --- |
| 2026-10-26 | よろずや(スキルシート) | 構造 | ギャップ | 検証のスキーマのファイル名の決まりがなく、`career.ts` や `sheet-file.ts` のように役割が名前から分からなかった | `references/principles.md` の命名に `<名前>.schema.ts` を足した |
| 2026-11-21 | よろずや | ハーネス | ツールの変化 | `make release-version ARGS=minor` の push で、pre-push フックの make に `ARGS` が MAKEFLAGS で引き継がれ、検査が失敗した | `templates/harness/lefthook.yml` のフックの make で、値を渡す変数を空にした |
| 2026-11-21 | よろずや | ハーネス | ギャップ | README の版の表記やバッジの数など、正本の写しが手で直され、正本とずれた | `references/quality-gates.md` に、正本と写しの食い違いを止める検査を推奨として足した |
| 2026-11-21 | よろずや | ハーネス | ギャップ | Storybook の静的ビルドが CI で組み立てられておらず、サーバー専用のモジュールで壊れても気づけなかった | `references/quality-gates.md` の CI のビルドのステージに、Storybook の静的ビルドを含めた |
| 2026-11-21 | よろずや | テスト | ギャップ | E2E が `networkidle` の時点で数えて読み込み中の表示を拾い、ラベルの部分一致で別の欄に入力したまま通っていた | `references/testing-strategy.md` の「AI 駆動開発での注意」に足した |
| 2026-11-21 | legacy-to-add | 構造 | ギャップ | 昇格の優先順位が型から始まり、設計で誤りそのものをなくす選択肢と、ルールと強制手段の対応表がなかった | `templates/harness/docs/feedback/LESSONS.md` に「設計でなくす」と対応表を足した |

種類: ギャップ(ルールがない)、曖昧(解釈が分かれた)、不適合(合わなかった)、繰り返される例外、ツールの変化(雛形が現行版で動かない)

見直しの観点:
- 判定で決めきれなかったケースはないか。後で段階を昇格・降格したか。その条件は ADR の見直し条件と一致したか
- 雛形の設定が現行版のツールで動いたか(oxlint のルール名、oxfmt の設定、dependency-cruiser のオプション)
- 対象リポジトリの `docs/feedback/LESSONS.md` から昇格したルールのうち、他の案件でも使えるものはないか。あれば `templates/harness/` に取り込む
