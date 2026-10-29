# MCP client configuration

After setup, run `teaa config --server-json --actor local` to print the command and arguments for a local stdio MCP server. Add that configuration to your MCP client under the name `teaa`; TEAA does not edit client configuration automatically.

The gateway exposes Fleet, ToolsEngine, and Knowledge tools together with the read-only `teaa_status` tool. Keep separate component entries only when you intend to run those components independently as well.

The actor value identifies local ownership; it is not a provider login. Enable workers and browser tools only when you need them.
