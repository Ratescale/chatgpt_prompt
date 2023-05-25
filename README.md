# ChatGPT prompt cheat sheet
- 数が増えてくると埋もれてしまいますので、Issueでジャンルごとにまとめています。

### ゴールシークプロンプト
- ゴールシークプロンプトIssue https://github.com/Ratescale/chatgpt_prompt/issues/4
```
Prompt:
Output: Output only final deliverables
Feedback:
If feedback indicates that the prompt is correct, follow these steps to generate the output:
Read Output to understand the steps required to achieve the goal, with each step labeled from P1 to P#.
Read Output2 to understand the variables related to the goal, which may include (goal).
Read Output3 and redefine the goal using the variables defined in Output2. This will help you understand the goal more accurately and select the steps to execute.
Read Output4 and execute the steps from [P1] to [P#] one by one based on (content _details), recording the results in (01] to [0#].
Follow the execution steps provided in the prompt in the form of step commands. Use examples or bullet points to explain steps if necessary.
if an error occurs, refer to the results in Output4 to identify the cause and find a solution.
Once the execution is complete, check whether the goal has been achieved.
By following these steps, you can achieve the goal provided in this prompt. If the output is incorrect, revise the prompt based on the feedback and execute the same steps again.
[Output format]: Display
## Please check the final deliverable to confirm that the goal of generating the output has been achieved.
```

### プラグインを使用したプロンプト案
- [情報量が多い場合の情報収集](https://github.com/Ratescale/chatgpt_prompt/issues/6) https://github.com/Ratescale/chatgpt_prompt/issues/6

### [LP:ランディングページ作成](https://github.com/Ratescale/chatgpt_prompt/issues/1)

### テキストをChatGPTにインプットさせたい時に使うプロンプト
```
テキストを読み込んで欲しいので読み込めたら「はい」と回答して、他に何も言わないでください。
```

### 音声文字起こしから記事作成
```
このプロンプトに従って、音声ファイル（プレゼンテーションまたは対談）を文字起こししたテキストを元に簡単な記事を作成してください。以下のプロンプトの下に、文字起こしをしたテキストを貼り付けます。

プロンプト:
'音声ファイルから、以下の構成で約3000字程度の記事を作成してください:

タイトル: 内容の主題を表す短くてキャッチーなフレーズ
序論: 主要なトピックと議論のポイントを紹介する100-150字程度の概要
登場人物・スピーカー: スピーカーの専門知識と見解を説明する300-500字程度のパラグラフ（対談の場合）
内容のハイライト: 取り上げられた課題や解決策を詳細にまとめる1000-1200字程度のパラグラフ
インパクトのある発言: ハイライトやインパクトのある発言を引用形式で挙げる300-500字程度のパラグラフ
結論: 音声ファイルの目的やリスナーが得られる情報・学びを詳しくまとめる800-1000字程度のパラグラフ'
```

### 自然な表現に変更するプロンプト
```
"以下のプロンプトに従って、先ほど作成した記事をもう一度チャットGPTで自然な言葉遣いに修正し、客観的な記事に仕上げてください。各段落をプロンプトの下に貼り付けて、自然な言葉遣いで書き直すように指示してください。

プロンプト:
'以下の段落をもっと自然な言葉遣いで表現し、客観的な記事に仕上げてください:

【ここに段落を貼り付けてください】'
```
