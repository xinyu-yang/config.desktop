# Debian Desktop Migration Checklist

[x] 1. Create a separate working copy from `/home/xinyu/config.sh` into a new desktop repo directory so the current server-oriented repo stays untouched.

[x] 2. Reconnect that new working copy to `git@github.com:xinyu-yang/config.desktop.git` and confirm it is an independent git repo before changing files.

[x] 3. Audit the current files and split them into:
   - portable settings to keep,
   - server-specific settings to remove,
   - Debian KDE desktop settings to add.

[x] 4. Refactor the `run` bootstrap script to remove fish support completely.
   This includes deleting fish config handling and any fish-related bootstrap logic.

[x] 5. Refactor the `run` bootstrap script to remove proxy support completely.
   This includes deleting `setproxy`, proxy aliases, and proxy-related shell defaults.

[x] 6. Change shell defaults to match this Debian KDE machine.
   Set the terminal default to `konsole` instead of `st`.

[x] 7. Align browser settings with the actual machine.
   Use `microsoft-edge.desktop` for XDG desktop associations and `microsoft-edge` for the shell `BROWSER` variable.

[x] 8. Review the remaining login-shell environment and remove stale server assumptions.
   In particular, reevaluate `TERM="tmux-256color"` and keep only XDG and PATH settings that still make sense on Debian desktop.

[x] 9. Keep Neovim and other useful tools only where they still fit the desktop workflow.
   Prefer configuring already-installed tools instead of reinstalling or compiling them.

[x] 10. Replace source-build behavior with Debian-friendly behavior where possible.
    For tools like `tmux`, prefer existing system packages and skip unnecessary install steps.

[x] 11. Improve installer safety and idempotency.
    Ensure rerunning the script does not duplicate shell blocks, overwrite files silently, or break existing desktop configs.

[x] 12. Update the README so the repo clearly documents:
    - target system: Debian 13 KDE desktop,
    - what is managed,
    - what was intentionally removed from the old setup,
    - prerequisites and safe usage.

[x] 13. Verify the adapted repo locally.
    Run shell syntax checks, review diffs, and confirm the new bootstrap behavior is consistent before committing.

[ ] 14. Commit the desktop-specific changes in the new repo with a clear message.

[ ] 15. Push the finished result to `git@github.com:xinyu-yang/config.desktop.git`.
