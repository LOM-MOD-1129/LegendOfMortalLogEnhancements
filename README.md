# 活俠傳 ログ出力拡張MOD

Steam版『活俠傳 / Legend of Mortal』のログ表示・操作を補助する非公式MOD。

バージョン：**2.1.0**

## 主な機能

- ゲーム標準の数値変動ログへ変更前後の値を追記。例：`鍛造 +10（40 → 50）`
- 能力値は補正と上限・下限を反映した値を表示。
- 各勢力の向心値は「好感度」と表記。唐門自身の「団結」は変更なし。
- ホイール上でログ表示、会話中のホイール下で文章送り。行動選択中は下ホイールで文章を送らない。
- 右スティックの履歴スクロール速度を5段階で調整。十字キー上下でも履歴を操作可能。

## 対応環境

- ゲーム：Steam版『活俠傳 / Legend of Mortal』 v1.0.6001.0
- OS：Windows（確認環境：Windows 11）
- BepInEx：6.0.0-be.692（32-bit Mono）

## ダウンロード・導入

このリポジトリの **Releases → Latest**（URL末尾`/releases/latest`）のAssetsから、
`LegendOfMortalLogEnhancements.zip`をダウンロードして展開。

1. BepInEx 6を導入し、ゲームを終了。
2. 展開した`LegendOfMortalLogEnhancements`フォルダーを、ゲームの`BepInEx/plugins/`へコピー。
3. 更新時は同名のDLLを上書き。同じMODのDLLを複数の場所へ配置しないこと。

```text
BepInEx/plugins/LegendOfMortalLogEnhancements/LegendOfMortalLogEnhancements.dll
```

ZIP内の`README_JP.txt`にも導入・基本操作・主な設定を記載。更新内容は[変更履歴](CHANGELOG.md)を参照。
配布ZIPのSHA-256は同じリリースに添付された`SHA256.txt`を参照。
Assetsの`Source code (zip)`・`Source code (tar.gz)`はリポジトリの自動アーカイブで、MODの配布ZIPとは別物。

## 操作と設定

| 操作 | 動作 |
|---|---|
| ホイール上 | ログを開く |
| ホイール下 | 会話中の文章送り。行動選択中は文章を送らない |
| 右クリック | ログを閉じる |
| 右スティック／十字キー上下 | 履歴をスクロール。十字キーは長押しで連続移動 |

ゲームパッドでのログの開閉は、ゲーム標準の操作に従う。

ゲームの環境設定画面で、「MOD設定」の「ログ出力拡張」を選択。
変更はすぐに反映・保存。
項目は「表示・記録」「操作」の順に並び、下の項目へスクロール可能。

設定ファイルで変更する場合は、初回起動後にゲームを終了し、`BepInEx/config/lom.jp.log.enhancements.cfg`を編集。設定ページを開いている間はファイル変更も自動で反映。MOD全体の有効・無効（`General.Enabled`）、入力の判定量・最小間隔・調査用ログと追加記録の設定は、ファイルでのみ変更可能。

`true`は有効、`false`は無効。各項目は表のセクション内に記載し、変更後にゲームを起動。

### 全体・表示・記録

| セクション | 項目 | 初期値 | 説明 |
|---|---|---|---|
| `[General]` | `Enabled` | `true` | MOD全体の補助機能。無効にしてもゲーム標準のログ記録・表示は継続。 |
| `[Display]` | `IncludeBeforeAfterValues` | `true` | 数値変動ログへ`（変更前 → 変更後）`を追記。無効にしても、許可された追加記録そのものは停止しない。 |
| `[Logging]` | `LogPlayerStats` | `true` | 能力値・各勢力の好感度と人数の前後値表示、および許可された追加記録。 |
| `[Logging]` | `LogRelationships` | `true` | 人物好感度の前後値表示、および許可された追加記録。 |

記録設定を無効にしてもゲーム標準の記録は継続し、既存の履歴は削除しない。技能・特性の前後値表示は`Enabled`と`IncludeBeforeAfterValues`に従う。

### 操作

| セクション | 項目 | 初期値 | 説明 |
|---|---|---|---|
| `[Input]` | `EnableLogControls` | `true` | ホイールでログを開く操作、右クリックで閉じる操作、背後入力の抑制・復旧、ゲームパッドのスクロール補助。ゲーム標準のログ開閉操作は変更しない。 |
| `[Input]` | `WheelUpOpensLog` | `true` | ホイール上でログを開く。`EnableLogControls`が有効な場合に適用。 |
| `[Story]` | `WheelDownAdvances` | `true` | 会話中のホイール下で文章送り。`EnableLogControls`とは個別に切替可能。 |
| `[Input]` | `ScrollThreshold` | `0.1` | ホイール操作を受け付ける入力の蓄積量。大きいほど反応しにくくなる。実際の判定には最低`0.01`を使用。ログ画面内の移動量の設定ではない。 |
| `[Input]` | `MinimumIntervalSeconds` | `0.08` | ホイール操作を受け付ける最小間隔（秒）。大きいほど連続操作が遅くなる。実際の判定は`0～1`秒の範囲。 |
| `[Input]` | `GamepadLogScrollLevel` | `5` | 右スティックの履歴スクロール速度。`1`=10%、`2`=25%、`3`=50%、`4`=75%、`5`=標準。マウスの速度は変更なし。 |
| `[Input]` | `DpadLogScrollLevel` | `3` | 十字キー上下の1回の移動量。`0`=追加操作無効、`1`=表示枠の5%、`2`=10%、`3`=25%、`4`=50%、`5`=100%。長押しで連続移動。右スティックとは独立設定。 |

右スティック・十字キーの補助は`Enabled`と`EnableLogControls`がともに有効な場合に適用。

### 不具合調査用

| セクション | 項目 | 初期値 | 説明 |
|---|---|---|---|
| `[Debug]` | `EnableDiagnosticLogging` | `false` | BepInExのログへ切り分け用情報を出力。通常は無効のまま使用。 |
| `[Debug]` | `DiagnosticLogLevel` | `Info` | `Error`=エラーのみ、`Info`=エラーと通常の診断情報、`Trace`=さらに詳細な情報。`EnableDiagnosticLogging`が有効な場合に適用。`Trace`は出力量が多いため調査時のみ使用。 |

<details>
<summary>隠しパラメータの追加記録（任意・ネタバレ注意）</summary>

`LogHiddenParameters`は初期状態では設定ファイルに表示されず、未記載時は`false`扱い。必要な場合だけ、既存の`[Logging]`セクション内へ次の行を追記。

```ini
LogHiddenParameters = true
```

| 値 | ゲーム標準の記録に加える内容 |
|---|---|
| `false`（未記載時） | 追加記録なし。ゲーム標準の記録への前後値表示のみ。 |
| `true` | 「料理」（`cook`）と「心変わり」（`change-heart`）の変化を追加記録。 |

追加記録には`Enabled`と`LogPlayerStats`も有効にする必要あり。`IncludeBeforeAfterValues`を無効にすると、追加行にも前後値は付かない。
追加記録はセーブに保存されず、ロード後には残らない。無効へ戻す場合は追記した行を削除するか`false`へ変更。

</details>

## 履歴について

標準ログは最大300件で、ゲーム側の仕様に従って保存。  
このMODの前後値と追加記録は通常の場面転換では保持し、ロード後には残らない。  
過去の変更や取得できなかった値には前後値を付けない。

## 注意・削除

- 非公式MODのため、利用環境や他MODとの組み合わせによって正常に動作しない場合がある。導入前にセーブデータのバックアップを推奨。
- 日本語化MOD以外の他MODとの併用は動作保証の対象外。

ゲーム終了後に`BepInEx/plugins/LegendOfMortalLogEnhancements`を削除。
設定も不要なら`BepInEx/config/lom.jp.log.enhancements.cfg`を削除可能。

## ライセンス

[MIT License](LICENSE)。配布ZIPにも同内容の`LICENSE.txt`を同梱。
ゲーム本体と第三者の著作物へ本MODのライセンスが適用されるものではない。
