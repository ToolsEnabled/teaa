# TEAA

TEAA (ToolsEnabled Agent Architecture) provides Fleet, ToolsEngine, and Knowledge through one local MCP connection.

**Alpha status:** TEAA `0.5.0-alpha.6` is an alpha release. Interfaces and behavior may change between releases.

## Install the free launch release

The release assets are published on the [TEAA GitHub releases](https://github.com/ToolsEnabled/teaa/releases):

- Linux x64: `teaa-0.5.0-alpha.6-linux-x64.tar.gz`
- Native Windows x64: `teaa-0.5.0-alpha.6-windows-x64.zip`
- Checksums: `SHA256SUMS`

### Linux

Download the Linux archive and `SHA256SUMS` into one directory, then run:

```sh
sha256sum -c --ignore-missing SHA256SUMS
tar -xzf teaa-0.5.0-alpha.6-linux-x64.tar.gz
cd teaa-0.5.0-alpha.6-linux-x64
./install.sh
```

### Native Windows

Download the Windows zip and `SHA256SUMS`. In PowerShell, run `Get-FileHash .\teaa-0.5.0-alpha.6-windows-x64.zip -Algorithm SHA256` and compare the result with the Windows zip line in `SHA256SUMS`. Extract the zip, open Command Prompt in the extracted `teaa-0.5.0-alpha.6-windows-x64` folder, and run:

```bat
install.cmd
```

Node.js 22.19 or newer and Python 3.11 or newer are required on both systems. Git is required for Knowledge repository operations. Python does not have to be on `PATH`: set `knowledge.command` and `knowledge.args` in the TEAA settings as [SETUP.md](SETUP.md#python-runtime-for-knowledge) describes. After installation, create or choose an absolute project folder and run:

```text
teaa setup --folder <absolute-project-folder> --actor local --no-browser --workers
teaa doctor
teaa config --server-json
```

Register the JSON from `teaa config --server-json` as a stdio MCP server in your client. See [TEAA SETUP.md](https://github.com/ToolsEnabled/teaa/blob/main/SETUP.md) for first-run details.

## Source installation

This repository holds the TEAA 0.5.0-alpha.6 source, but it is not an installable tree. Install from the release archives above. The installers (`install.sh`, `scripts/install.cmd`) install a packaged release: they verify the archive's `release-manifest.json`, and the archive also carries the staged runtimes listed in its `vendor/manifest.json` (Fleet, ToolsEngine with its Node.js dependencies, and Knowledge). This checkout contains the component sources but not those files, so `./install.sh` run here stops with an error about `release-manifest.json`.

To run the tests from a checkout, use Node.js 22.19 or newer, Python 3.11 or newer and Git, and run `npm test`. Tests that run setup with the bundled runtime need the staged runtimes from a release archive and fail in a bare checkout.

See [SETUP.md](SETUP.md) for configuration and first-run details.

## Report a problem or get help

- **Something broken or confusing:** [open an issue](https://github.com/ToolsEnabled/teaa/issues/new/choose) and pick **Report a problem**. Include the version that `teaa doctor` shows and the steps to reproduce. Never paste passwords, tokens, API keys or private keys.
- **An idea:** open an issue and pick **Suggest an improvement**.
- **Your toolsenabled.ai account or the hosted service:** email support@toolsenabled.ai.
- **A security problem:** report it privately as the [security policy](https://github.com/ToolsEnabled/.github/blob/main/SECURITY.md) describes, never in a public issue.
