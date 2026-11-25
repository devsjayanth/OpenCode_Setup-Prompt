# OpenCode_Setup-Prompt

Set up my complete global OpenCode environment (~/.config/opencode/) using ONLY 100% free, local, zero-API-key tools so all token-saving plugins, proven skill sets, local persistent memory, self-learning loops, and a Master Orchestrator Skill work together cleanly without conflicts.

Execute the following steps in order:

### 1. INSTALL CORE LOCAL PLUGINS & CLI TOOLS (NO API KEYS / NO ACCOUNTS)
- **CodeGraph (Local AST Navigation MCP):** Run `npm i -g @colbymchenry/codegraph` and register it as a local MCP server in `~/.config/opencode/opencode.json`.
- **RTK (Local Shell Output Filter):** Install RTK (via `brew install rtk` or the official install script from https://github.com/rtk-ai/rtk) and run `rtk init -g --opencode`. (Do NOT install `opencode-snip` so shell hooks do not conflict.)
- **Caveman (Local Output Compression):** Run `npx -y github:JuliusBrussee/caveman -- --only opencode` to install the global OpenCode plugin and rules.
- **Local Persistent Memory & Context Compression Plugins:** Add `"opencode-agent-memory@latest"`, `"openslimedit@latest"`, and `"@tarquinen/opencode-dcp@latest"` to the `"plugin"` array in `~/.config/opencode/opencode.json` (do NOT install cloud `opencode-supermemory` since I want zero external accounts/APIs).

### 2. INSTALL PROVEN SKILL SETS (GLOBAL `~/.config/opencode/skills/` or `~/.agents/skills/`)
- **Obra Superpowers (SDLC, TDD, Debugging, Subagents, Skill Authoring):** Fetch and follow the official OpenCode installation instructions at `https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md`.
- **Beautiful Rust (`rust-best-practices`, `rust-review`, `rust-port`):** Install globally via `npx -y skills add morganlinton/BeautifulRust -g -a opencode` (or clone `https://github.com/morganlinton/BeautifulRust` and copy `skills/*` into `~/.config/opencode/skills/`).
- **Proven Python Skill Set (`python-best-practices`):** Install globally via `npx -y skills add ludo-technologies/python-best-practices -g -a opencode` (covering PEP 8/20, strict typing, Pydantic, asyncio, ruff, mypy, pytest, and uv).
- **Local Self-Learning & Self-Improvement Skill (`self-improving-agent`):** Create `~/.config/opencode/skills/self-improving-agent/SKILL.md` with proper YAML frontmatter so the agent automatically logs user corrections, failed commands, and recurring patterns into local `.learnings/` markdown files (`LEARNINGS.md`, `ERRORS.md`, `FEATURE_REQUESTS.md`), updates `opencode-agent-memory` blocks, and promotes proven rules into `AGENTS.md`.

### 3. CREATE THE MAIN SKILLS ORCHESTRATOR (`~/.config/opencode/skills/master-orchestrator/SKILL.md`)
Create `~/.config/opencode/skills/master-orchestrator/SKILL.md` with proper YAML frontmatter (`name: master-orchestrator`, clear `description` so OpenCode auto-invokes it on non-trivial tasks) that enforces this exact local-only workflow:
1. **Local Recall & Orient (Low-Token):** Read local `opencode-agent-memory` blocks and `.learnings/` for project conventions and past lessons, and use `CodeGraph` instead of broad file reads to map symbols and dependencies.
2. **Plan & Gate (Superpowers):** For new features or multi-file changes, trigger Superpowers' `brainstorming` -> `writing-plans` -> `using-git-worktrees` -> `subagent-driven-development` (or `executing-plans`). For bugs, enforce `systematic-debugging`.
3. **Domain Execution:**
   - When touching `.rs` or `Cargo.toml`, automatically load `rust-best-practices` (and `rust-review` before finishing, plus `rust-port` when migrating code).
   - When touching `.py` or `pyproject.toml`, automatically load `python-best-practices` (enforcing `uv`, `ruff`, `mypy`, `pytest`, and strict type hints).
4. **Verify & Compress:** Enforce Superpowers' `verification-before-completion`, keep outputs terse via Caveman rules, rely on RTK for shell filtering and DCP/OpenSlimedit for context pruning.
5. **Self-Learn & Persist Locally:** After any user correction, failed command, or completed milestone, log reusable insights via `self-improving-agent` into `.learnings/`, persist durable project facts in `opencode-agent-memory` blocks, and use Superpowers' `writing-skills` to turn repeated workflows into new local skills.

### 4. UPDATE GLOBAL RULES (`~/.config/opencode/AGENTS.md`)
Append a concise directive to `~/.config/opencode/AGENTS.md` (preserving existing Caveman/Superpowers entries):
"On every task, coordinate through the `master-orchestrator` skill: check local `opencode-agent-memory` and `.learnings/` first, navigate code via `CodeGraph`, follow `superpowers` TDD/debugging workflows, apply `BeautifulRust` or `python-best-practices` by language, log corrections via `self-improving-agent`, and enforce `Caveman`, `RTK`, `OpenSlimedit`, and `DCP` to aggressively minimize tokens."

### 5. VERIFY & REPORT
Run `opencode plugin list`, list all installed skill folders in `~/.config/opencode/skills/` and `~/.agents/skills/`, and print the final `~/.config/opencode/opencode.json` and `~/.config/opencode/AGENTS.md` so I can confirm everything is active and 100% local.
