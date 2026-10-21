# .dotfiles

## tmux-claude (bin/)

tmux のウィンドウ構成と各ペインの Claude Code セッションを保存・復元する。

- `prefix + S` 保存 / `prefix + C-r` 復元（`claude --resume <id>` で再開）
- 自動保存には `~/.claude/settings.json` に以下の hook が必要:

```json
"hooks": {
  "SessionStart": [{ "hooks": [{ "type": "command", "command": "tmux-claude-hook" }] }],
  "SessionEnd":   [{ "hooks": [{ "type": "command", "command": "tmux-claude-hook" }] }]
}
```
