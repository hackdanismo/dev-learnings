# MCP (Model Context Protocol)
`MCP (Model Context Protocol)` is a standard way for AI models - `ChatGPT`, `Claude`, `Gemina` and many others - to talk to tools, data, and services. It is a way for `LLMs (Large Language Models)` to access external systems. This avoids the need to create custom integrations for each model or tool.

An `MCP` sits between the `LLM` the application and the external tool/service. To think of an `MCP` is to imagine it being like a `USB-C` for `AI tools`, one standard, many connections.

Examples of what an `MCP` can be used for:

+ `Read files`
+ `Query databases`
+ `Call APIs (Application Programming Interface)`
+ `Trigger Workflows`
+ `Interact with internal systems`

The `MCP servers` are not created by the companies that own or run the `LLMs`, such as: `Anthropic (Claude)` or `OpenAI (ChatGPT)`, but instead an `MCP` is created by a third-party, such as `Webflow`, or a developer. The `LLMs` simply use the `MCP servers`.

+ [Webflow MCP](#webflow-mcp)

## Webflow MCP
The documentation for the `Webflow MCP Server` can be found [here](https://developers.webflow.com/mcp/reference/overview). The installation instructions are [here](https://developers.webflow.com/mcp/reference/getting-started).

The `Webflow MCP Server` connects AI tools directly to a `Webflow` project. A prompt can be given to an `AI agent` or `LLM` to update designs, manage site data, and work with the CMS directly from within the selected `AI environment`. 

To begin, the `AI` tool is configured. The `MCP server` is added to: `Claude Desktop`, `Claude Code`, `Cursor`, or `Windsurf`.
