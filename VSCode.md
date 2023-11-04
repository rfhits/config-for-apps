# VSCode

[toc]

## 选中文字插入超链接

在 markdown 文件中选中文字，按下 `Ctrl + K`，插入超链接。

```json
{
        "key": "ctrl+k",
        "command": "editor.action.insertSnippet",
        "when": "editorTextFocus && editorLangId == 'markdown'",
        "args": {
            "snippet": "[$TM_SELECTED_TEXT](${1:link})$0"
        }
}
```
