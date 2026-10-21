# .dotfiles

## tmux-claude (bin/)

tmux のウィンドウ構成と各ペインの Claude Code セッションを保存・復元する。

- 構成が変わるたびに自動保存し、tmux サーバー起動時に自動復元（`claude --resume <id>` で再開）
- Alacritty を開くと自動で `tmux new -A -s 0` に入る（.zshrc）
- 手動: `prefix + S` 保存 / `prefix + C-r` 復元
- Claude の会話IDの記録には `~/.claude/settings.json` に以下の hook が必要:

```json
"hooks": {
  "SessionStart": [{ "hooks": [{ "type": "command", "command": "tmux-claude-hook" }] }],
  "SessionEnd":   [{ "hooks": [{ "type": "command", "command": "tmux-claude-hook" }] }]
}
```
