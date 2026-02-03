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

+ [Setup Claude Code](#setup-claude-code)
+ [Webflow MCP](#webflow-mcp)
  + [Add Webflow MCP Server to Claude Code](#add-webflow-mcp-server-to-claude-code)

## Setup Claude Code
To install `Claude Code`, follow the installation instructions [here](https://github.com/anthropics/claude-code). To summarise, open the terminal and install `Claude Code`:

```shell
# macOS
$ curl -fsSL https://claude.ai/install.sh | bash

# macOS Homebrew
$ brew install --cask claude-code

# Windows
$ irm https://claude.ai/install.ps1 | iex
```

Once installed, check where `Claude Code` has been installed. This will confirm the path:

```shell
$ which claude
```

The `~/.local/bin` may need adding to the `PATH` (`zsh`). To do this, enter the following in the terminal and close/re-open the terminal:

```shell
$ echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
$ source ~/.zshrc
```

To verify that `Claude Code` has been installed, check the version:

```shell
$ claude --version
```

To start `Claude Code`:

```shell
$ claude
```

Once logged in, a `Claude Max` or `Pro` subsciption is required to connect to `Claude Code`. This is needed to use the `Webflow MCP Server`. When logging in, the account email will be required.

When `Claude Code` is running, to list the `MCP Servers` that have been configured:

```shell
$ /mcp list 
```

To provide access outside of the terminal, `Slack` can be used as there's a `Claude Code in Slack` path (`beta/research preview`) that lets people interact from threads/messages instead of a shell. This tends to be the lowest-friction “outside the terminal” option.

## Webflow MCP
The documentation for the `Webflow MCP Server` can be found [here](https://developers.webflow.com/mcp/reference/overview). The installation instructions are [here](https://developers.webflow.com/mcp/reference/getting-started).

The `Webflow MCP Server` connects AI tools directly to a `Webflow` project. A prompt can be given to an `AI agent` or `LLM` to update designs, manage site data, and work with the CMS directly from within the selected `AI environment`. 

To begin, the `AI` tool is configured. The `MCP server` is added to: `Claude Desktop`, `Claude Code`, `Cursor`, or `Windsurf`. The instructions for installing `Claude Code` are [here](https://github.com/anthropics/claude-code#installation).

### Add Webflow MCP Server to Claude Code
To add the `Webflow MCP Server` to `Claude Code`, enter the following terminal command inside of a folder where you want to run `Claude Code`:

```shell
$ claude mcp add --transport http webflow https://mcp.webflow.com/mcp
```

Once this command has been run, the output of the terminal will look like this:

```shell
Added HTTP MCP server webflow with URL: https://mcp.webflow.com/mcp to local config
File modified: /Users/danieljackson/.claude.json [project: /Users/danieljackson]
```

Once `Claude Code` is running, the `MCP Servers` configured can be listed:

```shell
$ /mcp list 
```

The `MCP Server` will need authentication:

<img width="578" height="402" alt="Screenshot 2026-02-03 at 14 29 49" src="https://github.com/user-attachments/assets/b787513c-7833-493e-8fab-fec42af4aea7" />

Click `Enter` to start the Authorisation process. A Browser window will open to connect to the `Webflow` instance and connect to the projects within:

<img width="1717" height="862" alt="Screenshot 2026-02-03 at 14 31 20" src="https://github.com/user-attachments/assets/d2c2ec22-f60f-40df-8b9a-cc12ce16420e" />

Once authorised, the terminal will confirm that `Claude Code` is now connected to `Webflow`:

<img width="576" height="406" alt="Screenshot 2026-02-03 at 14 31 42" src="https://github.com/user-attachments/assets/26ecf490-b7f6-458f-bb3d-8f3d76cb52f3" />

