# TEAA

TEAA (ToolsEnabled Agent Architecture) provides Fleet, ToolsEngine, and Knowledge through one local MCP connection.

**Alpha status:** TEAA `0.5.0-alpha.5` is an alpha release. Interfaces and behavior may change between releases.

## Install the free launch release

The release assets are published on the [TEAA GitHub releases](https://github.com/ToolsEnabled/teaa/releases):

- Linux x64: `teaa-0.5.0-alpha.5-linux-x64.tar.gz`
- Native Windows x64: `teaa-0.5.0-alpha.5-windows-x64.zip`
- Checksums: `SHA256SUMS`

### Linux

Download the Linux archive and `SHA256SUMS` into one directory, then run:

```sh
sha256sum -c --ignore-missing SHA256SUMS
tar -xzf teaa-0.5.0-alpha.5-linux-x64.tar.gz
cd teaa-0.5.0-alpha.5-linux-x64
./install.sh
```

### Native Windows

Download the Windows zip and `SHA256SUMS`. In PowerShell, run `Get-FileHash .\teaa-0.5.0-alpha.5-windows-x64.zip -Algorithm SHA256` and compare the result with the Windows zip line in `SHA256SUMS`. Extract the zip, open Command Prompt in the extracted `teaa-0.5.0-alpha.5-windows-x64` folder, and run:

```bat
install.cmd
```

Node.js 22.19 or newer and Python 3.11 or newer are required on both systems. Git is required for Knowledge repository operations. After installation, create or choose an absolute project folder and run:

```text
teaa setup --folder <absolute-project-folder> --actor local --no-browser --workers
teaa doctor
teaa config --server-json
```

Register the JSON from `teaa config --server-json` as a stdio MCP server in your client. See [TEAA SETUP.md](https://github.com/ToolsEnabled/teaa/blob/main/SETUP.md) for first-run details.

## Source installation

From this checkout, run `./install.sh` on Linux or `scripts/install.cmd` on native Windows. Node.js 22.19 or newer and Python 3.11 or newer are required; Git is needed for Knowledge repository operations.

See [SETUP.md](SETUP.md) for configuration and first-run details.

## Report a problem or get help

- **Something broken or confusing:** [open an issue](https://github.com/ToolsEnabled/teaa/issues/new/choose) and pick **Report a problem**. Include the version that `teaa doctor` shows and the steps to reproduce. Never paste passwords, tokens, API keys or private keys.
- **An idea:** open an issue and pick **Suggest an improvement**.
- **Your toolsenabled.ai account or the hosted service:** email support@toolsenabled.ai.
- **A security problem:** report it privately as the [security policy](https://github.com/ToolsEnabled/.github/blob/main/SECURITY.md) describes, never in a public issue.
