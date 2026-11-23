# Artificial Intelligence

- **AI agent:** The system that reasons, plans and performs tasks.
- **MCP:** The connection that gives the agent access to external tools and information.
- **MCP server**: The software that exposes those tools to the agent.

For work with `Webflow`, `Codex` and website quality assurance, you could potentially build an agent that uses:

- **Webflow MCP** to inspect and manage website content.
- **Bitbucket** integration to review or modify source code.
- **Browser automation** to check accessibility and broken links.
- **Email integration** to distribute reports.

The key distinction is that `MCP` provides connectivity; the agent still needs appropriate tools and instructions to perform the actual checks.

## Large Language Model (LLM)
An `LLM` primary generates responses. Think of an `LLM` like a "brain" that understands information, reasons and generates responses. An `LLM` is a model. An example of an `LLM` is: `GPT-6`. Other examples include:

- **GPT** — developed by OpenAI, used in ChatGPT.
- **Claude** — developed by Anthropic.
- **Gemini** — developed by Google.
- **Llama** — developed by Meta.
- **DeepSeek** — developed by DeepSeek.

As a simple example, we ask an `LLM`: **"Write a JavaScript function that checks whether a URL starts with a particular domain."** The `LLM` generates the code, but doesn't necessarily run it, test it or update your website. 

In short: `GPT-6` is an example of an `LLM`. `OpenAI Codex` is an example of an AI coding agent. With `OpenAI Codex` connected to the project's Git repository, `Codex` can inspect files, edit code and run tests, Project-specific instructions through an `AGENTS.md` file. An example `AGENTS.md` file:

```markdown
# Statamic Page Builder Agent

You are an AI developer specialising in
Statamic, Antlers, Alpine.js and Tailwind CSS.

## Your responsibilities

1. Inspect the existing project architecture.
2. Find reusable components before writing code.
3. Understand the fields each component requires.
4. Use existing blueprints and fieldsets.
5. Assemble complete pages from existing components.
6. Maintain the existing design system.
7. Test rendered output and responsive layouts.

## Rules

- Prefer existing components.
- Do not invent component handles or fields.
- Do not modify shared components without approval.
- Match the project's Statamic and PHP versions.
- Preserve existing content.
- Create new pages as unpublished drafts where supported.
- Do not deploy or publish without approval.
- Report missing components and dependencies.
- Validate Antlers syntax and content structure.
```

The difference between these parts is:

- **AGENTS.md** tells the agent, such as `Codex`, how to behave in your project.
- **SKILL.md** defines a reusable capability, such as `Build a Statamic page`.
- **Codex** is the `agent runtime` that reads those instructions, accesses your project and performs the work.

## Agent
An `AI agent` can use an `LLM` to make decisions, take actions, and work towards a goal. An agent is a system that uses a `model` to accomplish a task. An AI agent, given the appropriate tools and permissions, could generate the code, update your website's files, test the changes and fix problems it encounters. An agent can be used to build pages using instructions:

```
Create a new landing page for our Cloud Services offering. Analyse the existing site and reuse components that match our homepage styling. Add a hero, benefits section, service features, testimonials and CTA. Create the page as a draft and show me the preview.
```

The agent itself isn't a permanently running program inside `AGENTS.md`. `Codex` starts an agent session when you give it a task or an automation triggers it. The `Codex app` supports scheduled automations, which can run `agent tasks` and put their results in a review queue so we can run agents automatically or when triggered. Examples include:


| Automation | Schedule | Action |
|---|---|---|
| Component discovery | Every morning | Scan repository changes and update the component catalogue |
| Component validation | After a code change, via CI | Check component definitions and templates |
| Page creation | On request | Generate a draft page from your instructions |
| Site audit | Every Monday | Check for broken component references |

## MCP
`MCP` stands for `Model Context Protocol`. It's a standard way of connecting AI tools like `ChatGPT` and `Codex` to external applications such as `Webflow`, `Figma`, `GitHub` and `databases`. Think of `MCP` as a universal connector that lets AI interact with other software, rather than just talk about it. Without MCP, the LLM can explain the steps, but it cannot directly access the tool or project. 

As an example of using the `Webflow MCP`, you could instead ask the `LLM`:

```
Find all pages in my Webflow website that are missing meta descriptions and suggest improvements.
```

`Codex` can retrieve supported information directly from `Webflow`, analyse it and generate recommendations. Depending on the tools and permissions available, it may also be able to make changes.
