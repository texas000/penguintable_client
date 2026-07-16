# 🐧 PenguinTable Client

A modern, privacy-first desktop database client with a built-in **Local AI** assistant.

![macOS](https://img.shields.io/badge/macOS-aarch64-blue) ![Version](https://img.shields.io/badge/version-1.0.0-green) ![Framework](https://img.shields.io/badge/Flutter-Dart-02569B)

## Features

- **Multi-Database Support** — PostgreSQL, MySQL, MariaDB, SQLite, and SQL Server (MSSQL)
- **Local AI Assistant** — Powered by Ollama / LM Studio. Runs 100% locally, so no data ever leaves your machine
- **AI-Assisted Query Writing** — Generate and refine SQL with natural language prompts
- **SSH Tunnel** — Connect securely through SSH with password or key-based authentication
- **Smart Query Editor** — SQL syntax highlighting with AI-assisted query writing
- **Data Grid** — Virtualized grid with multi-row selection and right-click copy (Markdown, JSON, CSV, HTML, INSERT)
- **Schema Browser** — Browse tables grouped by schema with instant search
- **ER Diagram View** — Visualize table relationships
- **Query History** — Revisit and re-run previous queries
- **Workspace Restore** — Open tabs and the active tab are restored per connection across restarts
- **Data Export** — Export query results to CSV, JSON, and more
- **Privacy-First** — Connection credentials are stored securely in the OS Keychain

## Tech Stack

- **Framework:** Flutter (Dart) — native desktop
- **State:** Riverpod
- **Database Drivers:** `postgres`, `mysql_client`, `sqflite` (SQLite), `mssql_connection` (FreeTDS)
- **SSH:** `dartssh2` tunneling
- **Credentials:** OS Keychain via `flutter_secure_storage`
- **AI:** Ollama / LM Studio (local inference)

## Download

Download the latest release from the [Releases](https://github.com/texas000/penguintable_client/releases) page.

### macOS Installation

1. Download `PenguinTable_1.0.0_arm64.dmg`
2. Open the DMG and drag **Penguin Table** to Applications
3. **Important:** Since the app is not notarized, macOS may show a warning. Run this in Terminal:
   ```sh
   xattr -cr "/Applications/Penguin Table.app"
   ```
4. Open Penguin Table from Applications

> **Note:** Currently available for Apple Silicon (M1/M2/M3/M4) Macs only.

## Local AI Setup

The AI assistant runs entirely on your machine. To enable it:

1. Install [Ollama](https://ollama.com/) or [LM Studio](https://lmstudio.ai/)
2. Pull a model (for example: `ollama pull llama3`)
3. Make sure the local inference server is running
4. Open the AI panel in PenguinTable and start writing queries in natural language

## Building from source

```sh
make run        # run locally (macOS); stages FreeTDS for MSSQL
make test       # run the test suite
make build-dmg  # build a release .app and package a distributable DMG
```

## Security

- Database passwords, SSH passwords, and SSH private-key contents are stored in the OS Keychain and never touch disk in plaintext
- Parameterized queries are used for schema/column introspection to prevent SQL injection
- `ORDER BY` generation escapes identifiers and whitelists sort direction to `ASC`/`DESC`
- A global error boundary handles uncaught errors gracefully

## License

Proprietary and commercial. See [LICENSE](LICENSE). All rights reserved.
