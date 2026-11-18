# lemon-paperplane-plugin-keymap-vscode

Lemon Paperplane 文件编辑器的 VS Code 快捷键方案（插件 id `keymap-vscode`）。商店插件（不内置，打进随 App 附带的离线商店）。

- keymaps/vscode-macos.json、keymaps/vscode-windows.json：Visual Studio Code 默认的 macOS / Windows 键位（⌘P 快速打开、⌘D 选中下一个、⇧⌘K 删除行、⌘K ⌘0 全部折叠…）。
- 没有业务逻辑：方案在 `plugin.json` 的 `contributes.keymaps` 里声明；这是纯声明插件：`plugin.json` 不写 `executable`，没有程序，内核从不启动进程。
- JSON 方案格式：`{"bindings": [{"key": "Cmd-d", "command": "deleteLine"}]}`，键名用 CodeMirror 写法（`Cmd`/`Ctrl`/`Alt`/`Shift`，不用 `Mod`，多键序列用空格分隔），`command` 取编辑器命令表 `lemon-paperplane-main/lemon-paperplane-main-editor/COMMANDS.md`。编辑器工程的 `npm test` 会检查方案里的命令都存在。
- module 方案由编辑器工程的 `node scripts/build-lang.mjs keymap-vscode` 生成（CodeMirror 运行时取自编辑器的 `window.cm`）。
