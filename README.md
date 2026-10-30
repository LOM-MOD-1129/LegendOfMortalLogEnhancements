# 活俠傳 Log Enhancements

Steam版『活俠傳 / Legend of Mortal』のログ表示・操作を補助する非公式MOD。

現在の配布版：**2.0.2**

## 主な機能

- ゲーム標準の数値変動ログへ変更前後の値を追記。例：`鍛造 +10（40 → 50）`
- 能力値は補正と上限・下限を反映した値を表示。
- 各勢力の向心値は「好感度」と表記。唐門自身の「団結」は変更なし。
- ホイール上でログ表示、会話中のホイール下で文章送り。行動選択中は下ホイールで文章を送らない。
- 右スティックの履歴スクロール速度を5段階で調整。十字キー上下でも履歴を操作可能。

## 対応環境

- Steam版『活俠傳 / Legend of Mortal』v1.0.6001.0
- Windows 11
- BepInEx 6.0.0-be.692

それ以前のゲーム版は非対応。ゲーム更新後はMODの対応状況を確認すること。

## ダウンロード・導入

[2.0.2の配布ZIP](https://github.com/LOM-MOD-1129/LegendOfMortalLogEnhancements/releases/download/v2.0.2/LegendOfMortalLogEnhancements-2.0.2.zip)をダウンロードして展開。

1. ゲームを終了。
2. 展開した`LegendOfMortalLogEnhancements`フォルダーを、ゲームの`BepInEx/plugins/`へコピー。
3. 更新時は同名のDLLを上書き。

```text
BepInEx/plugins/LegendOfMortalLogEnhancements/LegendOfMortalLogEnhancements.dll
```

詳しい操作・設定はZIP内の`README_JP.txt`を参照。
配布ZIPのSHA-256は[ハッシュ一覧](https://github.com/LOM-MOD-1129/LegendOfMortalLogEnhancements/releases/download/v2.0.2/SHA256.txt)、更新内容は[変更履歴](CHANGELOG.md)を参照。
Assetsの`Source code (zip)`・`Source code (tar.gz)`はリポジトリの自動アーカイブで、MODの配布ZIPとは別物。

## 設定

初回起動後にゲームを終了し、`BepInEx/config/lom.jp.log.enhancements.cfg`を編集。

- `GamepadLogScrollLevel`：右スティックの履歴スクロール速度。1=10%、2=25%、3=50%、4=75%、5=標準。初期値5。マウスの速度は変更なし。
- `DpadLogScrollLevel`：十字キー上下の移動量。0=無効、1=表示枠の5%、2=10%、3=25%、4=50%、5=100%。初期値3。長押しで連続移動。

ログ操作・文章送り・前後値表示なども個別に切替可能。一部の追加記録は任意の手動設定で有効化する。詳細はZIP内の説明書を参照。

## 履歴について

標準ログは最大300件で、ゲーム側の仕様に従って保存。  
このMODの前後値と追加記録は通常の場面転換では保持し、ロード後には残らない。  
過去の変更や取得できなかった値には前後値を付けない。

## 注意・削除

非公式MODのため、利用環境や他MODの組合せによって正常に動作しない場合がある。導入前にセーブデータのバックアップを推奨。  
削除する場合はゲーム終了後に`BepInEx/plugins/LegendOfMortalLogEnhancements`を削除。

## ライセンス

[MIT License](LICENSE)。配布ZIPにも同内容の`LICENSE.txt`を同梱。
