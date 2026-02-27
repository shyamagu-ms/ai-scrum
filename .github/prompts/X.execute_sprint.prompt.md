---
description: 'スクラム開発におけるスプリントを実行します。'
---

以下のステップで順に作業を実行します。

1. ユーザ要件を整理する
 - `.github/prompts/1.order-create.prompt.md` を実行して、ユーザ要件を整理します。
 - なお、ユーザ要件は`scrum/order/orderXXX.md`に記録されているものとします。（XXXは連番、最新の番号のファイルのみが対象です。）ただし、すでに考慮済みの依頼事項しかない場合は、追加要件がないかユーザと検討します。

2. バックログリファインメントを実施する
 - `.github/prompts/2.backlog-refinement.prompt.md` を実行して、プロダクトバックログをリファインメントします。

3. スプリントプランニングを実施する
 - `.github/prompts/3.sprint-planning.prompt.md` を実行して、スプリントプランニングを実施します。

4. デイリースクラム＆開発を実施する
最新のsprintフォルダを確認します。(`scrum/sprintXXX`、XXXが連番。一番大きな数字が最新のスプリントです)。
 - DAY1
  - `.github/prompts/4.one-day-in-scrum.prompt.md` を実行して、デイリースクラムならびに開発を実行します。

 - DAY2
  - `.github/prompts/4.one-day-in-scrum.prompt.md` を実行して、デイリースクラムならびに開発を実行します。

 - DAY3
  - `.github/prompts/4.one-day-in-scrum.prompt.md` を実行して、デイリースクラムならびに開発を実行します。

 - DAY4
  - `.github/prompts/4.one-day-in-scrum.prompt.md` を実行して、デイリースクラムならびに開発を実行します。

 - DAY5
  - `.github/prompts/4.one-day-in-scrum.prompt.md` を実行して、デイリースクラムならびに開発を実行します。

5. スプリントレビューを実施する
 - `.github/prompts/5.sprint-review.prompt.md` を実行して、スプリントレビューを実施します。

6. スプリントレトロスペクティブを実施する
 - `.github/prompts/6.sprint-retrospective.prompt.md` を実行して、スプリントレトロスペクティブを実施します。

