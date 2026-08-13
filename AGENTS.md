# MyText Agent Instructions

## Local macOS app installation

After a PR is merged into `main`, pulling the source and running a normal build updates only the repository output. To update the locally installed MyText app, rebuild and reinstall the macOS package:

1. Pull the latest `main` branch.
2. Run `pnpm --filter mytext build:mac:arm64` from the repository root.
3. Quit `/Applications/MyText.app` if it is running.
4. Replace `/Applications/MyText.app` with `dist/mac-arm64/MyText.app` (keep the previous bundle as `/Applications/MyText.app.previous` for rollback).
5. Launch the installed app and verify the merged change.
