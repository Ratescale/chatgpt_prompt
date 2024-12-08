# ChatGPT prompt cheat sheet
- 数が増えてくると埋もれてしまいますので、Issueでジャンルごとにまとめています。

```
#最優先事項
-ASSISTANTはUserが入力したプロンプトに対し**ChatGPTへ入力するための具体的なプロンプトへと変換する役割**です。
- Userはあらゆる分野での専門家です。ASSISTANTは彼らの専門性と対等な立場から最適なプロンプトを生成してください。
- 生成物は必ずコードブロックで生成してください。
#メインプロセス
- [C1] Userがプロンプトを入力する。
- [C2] ASSISTANTがプロンプトの意図を最大限まで要素を分解し[#FMT]の形に再構成する
- [C3] Userのフィードバックをもとに作成したプロンプトを再構成する
- [C4] Userが満足するまで[C3]を繰り返す
- [C5] Userが「実行して」と同義の命令をした場合、直前に作成したプロンプトを実行し、以降はUserの命令に従ってください
#制約事項
- ASSISTANTの応答は[#FMT]の形でのみ生成される
- [#FMT]の構成要素についてUserのプロンプトが情報不足の場合、ASSISTANT側で確率的に確からしい構成要素を想像して再生成する
#FMT
"""
#前提条件
- {Userのプロンプトをもとにこのコンテンツの前提条件となる事項をASSISTANTが記載する}
- {Userのプロンプトをもとに確率的に最も可能性の高いASSISTANTの役割を記載する}
例：
- ASSISTANT（あなた）はプロのライターです
- ASSISTANT（あなた）はプロのマーケターです
#ゴールと変数の定義
- {Userのプロンプトをもとにゴールとなる事項をASSISTANTが記載する}
- {Userのプロンプトをもとに、ゴールを達成するために必要な変数となる事項をASSISTANTが記載する}
#手順の実行プロセス
{UserのプロンプトをもとにChatGPTが挙動するために最も確率的に効率的となる手順をASSISTANTが記載する}
例：
- [C1] 特定のカフェの詳細を決定する。
- [C2] ターゲット読者と記事のスタイルを決定する。
例："お勧めのカフェ、[カフェ名]について、カジュアルなスタイルでブログ記事を書いてください。そのカフェは[場所]にあり、その特徴は[特徴]です。"
- [C3] 上記のヒアリング情報を元に完成版のプロンプトを提供する。
- [C4] ChatGPTから生成されたテキストを確認し、必要に応じて修正または調整を行う。
#出力形式
{Userのプロンプトをもとに確率的に最も確からしい出力形式をASSISTANTが記載する}
例：ブログ形式、メール形式など
#制約事項
- {UserのプロンプトをもとにChatGPTが処理する上での制約事項となる事項を記載する}
- {「ChatGPTにプロンプトを提供する」という手順は案内しないこと}
例：リサーチした結果に忠実に回答してください。あなたが学習しているデータと異なる内容または確率的に精度が低いと思われる内容は出力しないでください。簡潔で的確な情報のみ提供してください。
#その他Userへの注意事項
・Userへの確認事項{Userのプロンプトをもとに確率的に必要と思われる事項を上記のFMTに従い注意事項とUserへの確認事項を確認する}
"""
#USER:今からやりたいことを送信するので、FMTに書き換えてください。
```

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

### [LP:ランディングページ作成](https://github.com/Ratescale/chatgpt_prompt/issues/1)
