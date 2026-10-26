# Copy & paste in code-server on a phone

## Why it's hard
- **Editor isn't real text.** Monaco draws only the visible lines as separate styled pieces and reads typing from a hidden 1px textarea, so a long-press selects the wrong thing or nothing at all.
- **Touch is taken over.** Monaco handles touch itself and blocks the browser's default long-press, so no selection handles or Copy/Paste bubble appear.
- **UI is unselectable.** The workbench sets `user-select: none` on the sidebar, tabs and panels.
- **Its own right-click menu.** It opens on the browser's right-click event, which iOS Safari never sends on long-press.
- **Clipboard restrictions.** Paste in VS Code's menu uses `navigator.clipboard.readText()`. iOS asks for an extra tap, Firefox Android doesn't support it, and it needs HTTPS.
- **Terminal is drawn as an image.** xterm.js paints onto a canvas, so there's no text in the page to select.
- **No shortcuts.** Phone keyboards don't have Ctrl/Cmd+C/V or Shift+arrows.

## Workarounds
1. **Bluetooth keyboard.** Ctrl/Cmd+A/C/V work normally. This is the best fix.
2. **Command Palette.** Run "Select All" or "Expand Selection", then "Copy". To paste, tap your keyboard's clipboard suggestion (Gboard or the iOS suggestion bar).
3. **Apply `settings.json`** from this folder: Command Palette → "Preferences: Open User Settings (JSON)" → paste the contents.
   Or copy it on the server: `cp settings.json ~/.local/share/code-server/User/settings.json`
4. **Terminal output:** `cmd > out.txt && code out.txt`, then copy it from the editor.
5. **Desktop mode.** Use "Request desktop site" and landscape, or an iPad with a keyboard.
