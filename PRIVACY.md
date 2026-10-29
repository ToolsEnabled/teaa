# Privacy and network behavior

TEAA keeps its configuration, Fleet state, ToolsEngine workspace data, and Knowledge repository in per-user locations. Provider credentials and conversations remain with the provider CLI or MCP client; TEAA does not copy them into the package. Uninstalling TEAA retains user settings and state.

Installation and setup run locally. TEAA configures no telemetry. At runtime, Fleet can contact the model endpoints selected by the operator. ToolsEngine can access websites requested through its tools. Knowledge contacts a Git remote only when the operator configures one and enables synchronization. Optional provider-tool discovery can query a package registry. The MCP client receives tool results and handles them under its own policies.
