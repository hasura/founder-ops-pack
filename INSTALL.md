# Installing the pack

Each skill is a folder under `skills/`. Copy the folders for the tool you use:

## Claude Code
- User-wide: copy skill folders into `~/.claude/skills/`
- Per-project: copy into `.claude/skills/` in the repo
- Agents: copy `agents/*.md` into `~/.claude/agents/` (or `.claude/agents/`)

## OpenAI Codex (CLI / IDE / app)
- User-wide: `~/.codex/skills/`
- Per-project: `.codex/skills/` (Codex also scans `.agents/skills/` up the repo tree)
- Invoke explicitly with `/skills` or `$skill-name`, or let description matching load them.

## Cursor
- Project-scoped only: copy skill folders into `.cursor/skills/` in each project.
- No global directory. Repeat per project.
- Invoke with `/skill-name` or let the agent auto-discover at startup.

## PromptQL
- Skills install as wiki pages. In a thread, upload the skill's `SKILL.md`
  and ask the agent to add it to the wiki as a page titled with the skill
  name. Approve the proposed wiki change when it appears. The skill then
  loads automatically in any thread where the topic comes up.
- Agents install as saved programs. In a thread, upload the agent playbook
  from `agents/` and ask the agent to save it as a saved program named
  after the agent (for example `fractional_cfo_lite`). Invoke it from any
  thread by name, or put it on a schedule. If the agent needs a task or
  inputs, create a named text artifact in the thread first (the program's
  README names it) and the program reads it on run.

## Gemini CLI, GitHub Copilot / VS Code, others
- These read the Agent Skills standard; check your tool's skills directory
  in its docs and copy the folders there.

## ChatGPT (consumer)
Consumer ChatGPT cannot install skill folders. Use the `chatgpt/` directory:
each skill's body is provided as a paste-ready `.txt`. Paste it into a
Project's instructions or at the top of a conversation.

## Verify the install
Ask your agent: "what skills do you have for running a monthly close?" It
should surface `monthly-close-runbook`. If not, check the folder path
matches your tool's skills directory exactly (folder name must match the
skill's frontmatter `name`).
