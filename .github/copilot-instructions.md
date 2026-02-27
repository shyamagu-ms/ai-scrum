# Copilot カスタムインストラクション

このリポジトリはスクラム開発をAIエージェントで運用するプロジェクトです。

## プロジェクト構成

```
scrum/                          # スクラム成果物
└── order/                      # エンドユーザサイドの要求事項や依頼事項
│   └── orderXXX.md             # 個別の要求事項ファイル（XXXは連番。常に最新のみを確認する）
├── product_goal.md             # プロダクトゴール
├── product_backlog.csv         # プロダクトバックログ（PBI一覧、CSV形式）
├── definition_of_done.md       # 完成の定義（DoD）
├── impediment_log.csv          # 障害物ログ（CSV形式）
├── velocity.csv                # ベロシティ記録（CSV形式）
└── sprintXXX/                  # スプリント別フォルダ（sprint001, sprint002, ...）
    ├── sprint_backlog.md       # スプリントバックログ（ゴール・PBI・タスク）
    ├── sprint_planning.md      # スプリントプランニング記録
    ├── sprint_review.md        # スプリントレビュー記録
    ├── sprint_retrospective.md # スプリントレトロスペクティブ記録
    └── daily_scrum.md          # デイリースクラム記録（日次追記）

project/
├── front/                      # フロントエンドのソースコード（あれば）
├── back/                       # バックエンドAPIサーバのソースコード（あれば）
├── infra/                      # インフラ関連の成果物（あれば）
├── docs/                       # ドキュメント関連の成果物
├── sql/                        # SQL関連の成果物（あれば）
必要に応じてフォルダ構造は適宜分割                          
```

## 全体ルール

- 全ての成果物は **日本語** で記述すること
- CSVファイルの列構造を変更しないこと。また文字コードはUTF-8としてExcelで文字化けしないようにする。
- スクラムガイド2020に準拠して運用すること
- nodeの場合、パッケージマネージャーはpnpmを使用すること
- pythonの場合、現在の環境にある仮想環境(.venv)を使用すること
