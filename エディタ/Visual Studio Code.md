## 設定
フィルターでみれる(右上のろうとのようなマーク)

- *Editor Unicode Highlight Include Comments*: **false**
- *Editor Unicode Highlight Include String*: **false**
- *Editor Suggest Selection Mode*: **never**（補完候補が選択されない状態にする）
- *Editor Snippet Suggestions*: **top**（スニペットを上に表示）
- *Editor Suggest Preview*: **✓**（提案の結果を薄く表示）

### キーボードショートカット
検索にユーザと入力でみれる

- *selectNextSuggestion*: **Tab**（タブで補完候補の選択を移動）
- *hideSuggestWidget*: **Enter**（Enterで補完リストを消す）
	Ctrl + shift + pでコマンドパレットを開き、
	Preferences: Open Keyboard Shortcuts (JSON)を選択。

```
{
    "key": "enter",
    "command": "hideSuggestWidget",
    "when": "suggestWidgetVisible && textInputFocus && !suggestWidgetHasFocusedSuggestion"
}
```
を書く