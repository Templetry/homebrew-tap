# Templetry Homebrew tap

Install the [Templetry](https://github.com/Templetry) CLI and MCP server on macOS or Linux:

```sh
brew install Templetry/tap/templetry
```

You get `templetry` and `templetry-mcp` on your PATH. Update with `brew upgrade templetry`.

Prefer no package manager? The engine ships a script that does the same thing:

```sh
curl -fsSL https://raw.githubusercontent.com/Templetry/engine/main/install.sh | sh
```

## How the formula stays current

`Formula/templetry.rb` is **generated, never hand-edited** — eight hashes across four platforms is exactly what a person gets wrong once, silently, until somebody's install fails an integrity check.

[`bin/update.sh`](bin/update.sh) reads the latest [engine release](https://github.com/Templetry/engine/releases), takes the hashes from its own `SHA256SUMS`, rewrites the formula and commits only if the version moved. It runs daily, and the engine's release can fire it immediately through `repository_dispatch`.

Every push installs the formula on both macOS and Linux and runs its test, which renders a real template and checks the output — so a green tick here means the thing installs and works, not that the file parses.
