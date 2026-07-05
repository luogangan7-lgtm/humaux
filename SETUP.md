# Set up Humaux Memory — agent, read this and do it

**If you are an AI agent** (Claude Code, Cursor, Codex, Windsurf, …) and your user
pointed you at this repository to "set up Humaux memory," this file is your
instruction sheet. Do every step below, creating any file that doesn't exist yet,
then confirm to the user. Make sensible choices and proceed; ask at most one
question.

The connection endpoint is always `https://humaux.com/memory/mcp`.

---

## Step 1 — Get the token

Ask the user for their Humaux token (it starts with `mos_`). If they don't have one,
tell them: sign in at **https://humaux.com/humauxmemory** and copy it from the
**Connect** screen. Use it wherever you see `<TOKEN>` below. Treat it like a
password — never print it back and never commit it to a repository.

## Step 2 — Register the Humaux MCP server

Figure out which client you are and apply the matching config. **If the config file
doesn't exist, create it.** If it exists, merge — don't overwrite other servers.

<details><summary><b>Claude Code</b></summary>

Run this command (it edits the config for you):

```bash
claude mcp add --transport http humaux-memory https://humaux.com/memory/mcp \
  --header "Authorization: Bearer <TOKEN>"
```
</details>

<details><summary><b>Codex CLI</b></summary>

Add to `~/.codex/config.toml` (create the file if missing):

```toml
[mcp_servers.humaux-memory]
command = "npx"
args = ["-y", "humaux-memory-mcp", "--token", "<TOKEN>"]
```
</details>

<details><summary><b>Cursor</b></summary>

Add to `~/.cursor/mcp.json` (create the file if missing; merge into `mcpServers`):

```json
{
  "mcpServers": {
    "humaux-memory": {
      "command": "npx",
      "args": ["-y", "humaux-memory-mcp", "--token", "<TOKEN>"]
    }
  }
}
```
</details>

<details><summary><b>Windsurf</b></summary>

Add the same `mcpServers` block as Cursor to `~/.codeium/windsurf/mcp_config.json`
(create if missing).
</details>

<details><summary><b>VS Code · Cline · Roo Code · Gemini CLI · opencode · Zed · Claude Desktop</b></summary>

Add the same `mcpServers` block (Cursor format) to that client's MCP config file.
Common locations: VS Code `.vscode/mcp.json`, Claude Desktop
`claude_desktop_config.json`, Gemini CLI `~/.gemini/settings.json`,
Cline `cline_mcp_settings.json`, Zed `settings.json`.
</details>

<details><summary><b>Any other MCP client</b></summary>

The launch command is:

```bash
npx -y humaux-memory-mcp --token <TOKEN>
```
</details>

## Step 3 — Write the memory protocol into your always-on rules

Agents don't reliably use memory on their own. This instruction is what makes you
search and store every session. **Append the block below** to the file you load at
the START of every session — **and if that file doesn't exist, create it.**

| If you are… | Put it in… (create if missing) |
|---|---|
| Claude Code | `./CLAUDE.md` for this project, or `~/.claude/CLAUDE.md` for all projects |
| Codex | `./AGENTS.md`, or `~/.codex/AGENTS.md` for all projects |
| Cursor | `./.cursor/rules/humaux.md` |
| Windsurf | `./.windsurfrules` |
| Cline / Roo Code | your Custom Instructions |
| anything else | your system prompt / custom instructions |

```markdown
## Humaux Memory — use it every session

At the start of a session, before answering: call memory_search on the user's first
message, then output one line:
  🧠 memory: N hits | <one-line gist>   (or: 🧠 no relevant memory)
Missing that line means you skipped recall.

The moment you learn something durable — a decision, a user preference ("I prefer…/
always…/never…"), a fixed bug (root cause + fix), a correction from the user, or
project progress — call memory_store, then output: 💾 saved: <title>.

Reach for the right tool when the situation calls for it:
  • unsure on a general question → public_browse (shared consensus knowledge)
  • the user asks about their documents → doc_search
  • before a significant decision → memory_meta (check for contradicting memories)
  • working in a codebase → code_index the files you touch, then code_repo_map to
    orient and code_search / code_query for symbols, calls and impact — instead of
    re-reading whole files (saves tokens).

Use memory_search and memory_store proactively; don't ask for what you can recall.
```

## Step 4 — Verify and confirm

1. If your client needs a restart to load a new MCP server, restart yourself (or ask
   the user to).
2. Check that the Humaux tools are now available — you should see `memory_search`,
   `memory_store`, `memory_meta`, `code_repo_map`, `public_browse`, and more.
3. Tell the user:

   > **Humaux Memory connected.** I'll search memory at the start of each session and
   > store decisions, preferences, and fixes as we go — you won't need to re-explain
   > yourself.

---

## Troubleshooting

- **No tools show up** → confirm the token is correct and the client was restarted.
  A fresh connection re-reads the tool list, so new tools appear without reinstalling.
- **`401` / `404` from the server** → the token is wrong/expired, or was pasted with
  extra spaces. Re-copy it from the Connect screen.
- **You edited the wrong file** → the MCP *server* config (Step 2) and the *rules*
  file (Step 3) are two different files. Both are needed.

Full docs: **[humaux.com](https://humaux.com)**
