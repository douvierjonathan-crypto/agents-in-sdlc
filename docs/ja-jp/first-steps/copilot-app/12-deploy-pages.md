---
title: "レッスン 12 - GitHub Pages でサイトを公開する"
description: "GitHub Copilot app を使って Pages ワークフローを構成し、そのプル リクエストをレビューして、公開された Space Quiz を確認します。"
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

GitHub Pages に Space Quiz を公開し、誰でもアクセスできるようにします。Copilot はワークフローの準備とデプロイを支援しますが、変更をレビューし、サイトが公開されたことを確認するのはユーザー自身です。

このレッスンでは、次の操作を行います。

- Copilot に GitHub Pages へのデプロイを構成するよう依頼します。
- マージする前にワークフローとプル リクエストをレビューします。
- デプロイの進行を確認し、公開されたサイトを検証します。

## シナリオ

Space Quiz はすでに GitHub リポジトリにありますが、簡単に試せる方法が必要です。単一ファイルのサイトを GitHub Pages で公開すると、サーバーやランタイム依存関係を追加せずに、公開 URL からアクセスできるようになります。

## Copilot にデプロイの準備を依頼する

> [!WARNING]
> プル リクエストを作成すると、コードがコミットおよびプッシュされることがあります。このプロンプトを送信する前に、承認設定と送信先リポジトリを確認してください。**Approve all** を選択している場合、別の確認プロンプトが表示されるとは限りません。

`space-quiz` の Copilot app セッションで、次のプロンプトを送信します。

```plaintext
Prepare a GitHub Pages deployment for this repository. Create a GitHub Actions workflow that builds the website if needed and deploys it to GitHub Pages after changes reach the default branch. Add a README describing the app and how to run it locally if one does not already exist. Create a pull request with these changes and report its link and any required Pages settings or permissions. Do not merge, enable auto-merge, change Pages settings, or deploy. Stop and wait for my review.
```

## ワークフローとプル リクエストをレビューする

1. リポジトリに `README` がまだない場合に限り、`README` が追加されていることを確認します。
2. ワークフローのビルドとデプロイの手順、トリガー、権限を含め、プル リクエストの変更をレビューします。
3. ワークフローが、マージされていないプル リクエストではなく、既定のブランチからデプロイすることを確認します。
4. 必要な修正を依頼し、更新された `diff` をレビューします。マージを許可する前に、必須のプル リクエスト チェックがすべて成功するまで待ちます。

## マージとデプロイを許可する

> [!WARNING]
> 次のプロンプトを送信すると、レビュー済みのプル リクエストのマージ、リポジトリの Pages 設定の変更、サイトの公開をエージェントに許可します。レビューを完了し、リポジトリとプル リクエストを確認してから送信してください。承認設定によっては、追加の確認なしにこれらの操作が実行されることがあります。

レビューしたプル リクエストの番号に `<PR_NUMBER>` を置き換えて、このプロンプトを別途送信します。

```plaintext
I have reviewed pull request <PR_NUMBER> in this repository and authorize its merge and deployment. Enable GitHub Pages using GitHub Actions, merge that pull request only after required checks pass, and monitor the deployment until it succeeds. Report the final URL of the live website. If you lack permission to enable Pages or merge, tell me exactly what I need to approve or do; do not report success until the site is live.
```

![3 段階の図: マージされた space-quiz のプル リクエスト、Build website・Upload artifact・Deploy to Pages の各ステップが成功した GitHub Actions の Deploy website 実行、yourname.github.io/space-quiz/ で公開された Space Quiz。](../../../_images/first-steps-app-pages-deploy.svg)

## デプロイを確認する

1. GitHub Actions のデプロイ実行が成功するまで確認します。
2. 報告された URL を開き、Space Quiz が表示されることを確認します。

エージェントが Pages の有効化やプル リクエストのマージを実行できない場合は、提示された具体的な手順に従ってください。デプロイが成功し、公開サイトが読み込まれるまで、タスクを完了したと見なさないでください。

## まとめと次のステップ

Space Quiz が公開され、エージェントの報告を頼りにするのではなく、デプロイを確認できました。[レッスン 13: まとめと次のステップ][next-lesson]に進みます。

[next-lesson]: ../13-review/
