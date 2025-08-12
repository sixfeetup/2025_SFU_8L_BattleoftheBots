---
title-prefix: Six Feet Up
pagetitle: "Battle of the Bots: AI Agent Showdown"
author: Calvin Hendryx-Parker, Travis Frisinger
author-meta:
    - Calvin Hendryx-Parker
    - Travis Frisinger
date: SFU_8L 2025
date-meta: 2025
keywords:
    - Python
    - AI
    - Agents
    - Code
---

# Battle of the Bots: {.r-fit-text data-background="images/1.png"}
## AI Agent Showdown
#### Calvin Hendryx-Parker, CTO, Six Feet Up
#### Travis Frisinger, Technical Director of AI, 8th Light

---

# AI Coding Assistants {.r-fit-text data-background="images/2.png"}
## The New Pair-Programming Partners {.r-fit-text}

### Rapid Evolution over the last year:

> More than 97% of respondents reported having used AI coding tools at work
>
> -- [Github AI in Software Survey](More than 97% of respondents reported having used AI coding tools at work at some point)

---

# Why This Matters {.r-fit-text data-background="images/9.png"}

- AI coding assistants are transforming how we build software
- Choosing the right tool can mean the difference between frustration and flow
- Let’s find out which one delivers for real-world developers!

---

# The Contenders {data-background="images/3.png"}

- Aider
- Goose
- Claude Code
- Cursor
- Devin


::: notes
- Aider: Git-integrated assistant that understands entire codebases and can commit changes
- Goose: Specialized in API development with strong documentation capabilities
- Claude Code: Anthropic's CLI tool with advanced context awareness and precise refactoring capabilities
- Cursor: Editor-integrated solution enabling real-time collaborative coding and debugging
- Devin: ...

From basic code completion to full-fledged pair programmers in just one year
:::

---

# What is AI Agent? {data-background="images/4.png"}

An AI agent is a system that can:

- Perceive its environment through tools/APIs
- Make decisions autonomously
- Take actions to achieve specific goals
- Learn from interactions and feedback
- Chain multiple operations together

---

# Agents Continued {data-background="images/4.png"}

Key characteristics:

- Tool use capabilities (file system, web search, code execution)
- Planning and reasoning about complex tasks
- Persistent memory within a session
- Self-improvement through feedback loops

---

# What is MCP? {data-background="images/6.png"}

![](images/Model%20Context%20Protocol%20Diagram.png){.r-stretch .r-frame .r-center}

::: notes
The Model Context Protocol is an open standard that enables developers to build
secure, two-way connections between their data sources and AI-powered tools. The
architecture is straightforward: developers can either expose their data through
MCP servers or build AI applications (MCP clients) that connect to these
servers.
:::

---

# MCP Examples {data-background="images/8.png"}

- A [suite of specialized MCP servers](https://github.com/awslabs/mcp) for AWS:
    - Saves the cost of having all the AWS docs in your own context
- Use [Playwright from your AI Tools](https://github.com/microsoft/playwright-mcp)
    - Control a browser and grab the context from various web pages

---

# In practice {data-background="images/8.png"}

- Connect your AI assistant to AWS MCP servers
- Ask natural language questions about AWS services
- Get contextually accurate answers based on latest documentation
- Generate AWS CLI commands, CloudFormation templates, or IAM policies
- Troubleshoot AWS-specific issues with current best practices

---

# DEMO: The Prompt {data-background="images/4.png"}

> This project was bootstrapped with scaf and has a NextJS frontend in the `frontend` dir and a Django backend in the `backend` dir.
>
> The scaf template only supports a GraphQL API. Refactor the app to use a REST API.

---

# Tool introduction: Aider {.r-fit-text data-background="images/9.png"}

- Developed by Paul Gauthier
- Open-source ([GitHub: paul-gauthier/aider](https://github.com/paul-gauthier/aider))
- Supports multiple LLM models (OpenAI GPT-4, Claude, Llama)
- Semi-agentic with git integration
- No MCP support currently
- Supports `/voice` interactions
- Use Multiple Models in the same session

---

# DEMO: Aider {data-background="images/5.png"}

- Specify conventions in CONVENTIONS.md
- Use different models for architect and edit mode simultaneously
- Use external editor with `/editor`
- Run commands and add to output with `/run`
- Show cost with `/tokens`
- Clear context with `/clear`
- Start with `--lint-command` and `--test-command` run your test suite after
  each time the AI edits your code
 
---

# Tool introduction: Goose {.r-fit-text data-background="images/2.png"}

- Developed by Block Inc. (formerly Square)
- Open-source ([GitHub: block/goose](https://github.com/block/goose))
- Supports multiple LLM models (OpenAI, Claude, Ollama)
- Fully agentic with integrated tooling
- Supports [MCP](https://block.github.io/goose/docs/getting-started/using-extensions#mcp-servers)
- Supports OpenRouter! (<https://openrouter.ai>)

---

# DEMO: Goose {data-background="images/9.png"}

- Specify conventions in `.goosehints`:
  Global: `~/.config/goose/.goosehints`
  Local: `.goosehints`
- Session support:
  Start a session: `goose session -n rest-api`
  Exit a session: type exit
  Resume session: `goose session -r rest-api`
- Permission Modes:
  Completely Autonomous / Manual Approval / Smart Approval / Chat Only
- Clear context by exiting `/exit`
 
---

# Tool introduction: Claude Code {.r-fit-text data-background="images/10.png"}

- Developed by [Anthropic](https://www.anthropic.com/claude)
- Proprietary model and tooling
- Uses only Claude models (Claude 3 Opus/Sonnet/Haiku)
- Fully agentic with reasoning capabilities
- Supports MCP (Model Context Protocol)

---

# DEMO: Claude Code {data-background="images/6.png"}

- Allow tools: `claude config add allowedTools "Bash(git:*),Bash(cat:*),Bash(grep:*)"`
- Specify conventions in CLAUDE.md
- Doesn't use git to commit changes. TIP: Ask it to "Review the staged changes
  with `git diff --staged` and git commit using conventional commit standard"
- Show cost with `/cost`
- Compact and clear context with `/compact` and `/clear`

---

# Tool introduction: Cursor {.r-fit-text data-background="images/1.png"}

- Developed by Cursor team (acquired by Anthropic)
- Proprietary editor with open-source components
- Supports both OpenAI and Anthropic models
- Fully agentic with project navigation
- Supports [MCP](https://docs.cursor.com/context/model-context-protocol)

---

# DEMO: Cursor {data-background="images/8.png"}

- Specify conventions in Cursor Rules: ./cursor/rules
  https://docs.cursor.com/context/rules-for-ai
- Ask Cursor to setup a `.cursor-guildeline.json`

---

# Agentic Coding Models {data-background="images/1.png"}

![](images/aider_leaderboar.png)


---

# Tool Comparison {.r-fit-text data-background="images/4.png"}

| Tool   | Open Source | MCP Support | Agentic | Models Supported       |
|--------|-------------|-------------|---------|------------------------|
| Aider  | Yes         | No          | Semi    | Bring your own         |
| Claude | No          | Yes         | Full    | Claude Models          |
| Cursor | No          | Yes         | Full    | OpenAI, Claude, Gemini |
| Goose  | Yes         | Yes         | Full    | Bring your own         |
| Devin  |           |           |     |       |

---

# Key Takeaways {.r-fit-text data-background="images/3.png"}

- No single assistant is best for every workflow
- MCP is enabling richer, more context-aware coding
- Open source tools are catching up fast
- Try several and see what fits your style!

---

# Talk To Us  {.r-fit-text data-background="images/1.png"}

📩 <calvin@sixfeetup.com>  
🤝 <https://linkedin.com/in/calvinhp>  
🦋 [@calvinhp.com](https://bsky.app/profile/calvinhp.com)  


📩 <tfrisinger@8thlight.com>  
🤝 <https://linkedin.com/in/travis-frisinger>  
🦋 [@tmfrisinger.bsky.social](https://bsky.app/profile/tmfrisinger.bsky.social)  
