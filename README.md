# clothes-boots-motorcycle

> "I need your clothes, your boots and your motorcycle."
> The T-800, arriving with nothing, leaving fully equipped

The goodie bag from **A Day on the Tools with Lamb Dog**. You've arrived on a naked machine; this repo is how you leave equipped. Everything shown in the session, tiered so you don't drown. Do the Day One tier tonight. Ignore the rest until it's boring.

| Link | What |
|---|---|
| <recording link> | Session recording, chaptered |
| <kill list link> | Nominate targets for Lamb Dog: Judgement Day |
| <calendar link> | TryNet office hours, fortnightly |

---

## Day One (tonight, ~30 minutes)

The minimum viable setup. Nothing exotic.

**1. Claude Code.** Official install docs: https://code.claude.com/docs. WSL2 users: install inside WSL, not Windows-side. Trust me.

**2. Bootstrap the baseline config.**

```bash
git clone https://github.com/slamb2k/claude-dotfiles ~/.claude-dotfiles
cd ~/.claude-dotfiles && ./install.sh    # symlink-based, non-destructive
```

You get sensible Claude Code settings, the session-guard hooks, and statusline config. Read `install.sh` before running it. Always read install scripts. That's rule zero.

**3. Your first skill.**

```bash
# In any repo:
claude
> use the recky skill to explain what this codebase does
```

Recky: <repo link>. If you've ever been dropped into a repo and nodded along in standup while understanding nothing, this is for you.

**4. Read `PROMPTS.md` in this repo.** My actual daily prompt patterns. Short, boring, effective. Steal them.

**Stop here. Seriously. Use this for a week before adding anything else.**

## Week One (once Day One feels normal)

**azrl: per-directory credential isolation.** https://github.com/slamb2k/azrl

```bash
brew install slamb2k/tap/azrl    # <verify tap name>
```

`cd` into a client directory, you're in their tenant. `cd` out, you're not. If you touch more than one Azure tenant, this pays for itself on day one. Includes an SSH/WSL browser-callback bridge so device-code auth stops ruining your life.

**Hooks (the leverage point).** Installed via dotfiles; now go READ them:

| Hook | Trigger | Job |
|---|---|---|
| `session-guard.sh` | SessionStart | Environment sanity on every session |
| `session-guard-prompt.sh` | UserPromptSubmit | Pre-prompt checks |
| Stop hook | Stop | Prevents agents pausing mid-tasklist |

Hooks are how you make agent behaviour deterministic. Modify mine, or write your own.

**claude-statusline.**

```bash
brew install felipeelias/tap/claude-statusline
```

Context usage, model, session state at a glance. Your fuel gauge. You will stop blowing your context window mid-task.

**Cowork.** M365 Copilot Cowork is the same agentic pattern with zero terminal. Start with the deck-reviewer workflow from the session. Non-dev or dev-adjacent? This is your on-ramp: start HERE, not above.

**Wispr (voice input).** Dictating prompts beats typing them once your prompts get conversational. Feels ridiculous for two days, then you can't go back.

## When You're Ready (the deep end)

**Mad Skills: the dev process library.** Nautical-themed skill suite covering the delivery lifecycle: keel, brace, rig, build, ship, berth. The "skills beat mega-prompts" thesis made real: the process lives in versioned, reviewable skills, so your prompts stay short and your output stays consistent. <repo link>

Contribute. Build a skill for something you do weekly, PR it in. The library only works if it's ours, not mine.

**superpowers: spec-driven methodology.** https://github.com/obra/superpowers. Read Jesse Vincent's writing on it before installing. The methodology matters more than the plugin.

**squiz: browser automation plugin.** Agent-driven browser work, for anything web-portal-shaped with no API.

**git-credential-ado: multi-tenant Azure DevOps auth.** Custom credential helper for working across ADO orgs in different Entra tenants without the constant re-auth dance. In the dotfiles repo under `bin/`.

**Tailscale + a cloud dev VM.** Tailscale free tier is fine for a personal mesh. The pattern: always-on Azure VM, SSH alias, Claude Code sessions live there, secrets in Key Vault via managed identity. The laptop becomes a disposable window. Setup notes: `docs/dev-vm.md`.

**Kimble evidence-pack pipeline.** The timesheet chain from the session: collector scripts (M365 signals + git + Claude Code history), JSONL evidence pack, Cowork, Excel + kimble-import JSON, Chrome extension. Scripts in `kimble/` with a README; adapt the collectors to your own evidence trail. Hygiene note: the evidence pack contains your client activity. Treat it like client data, because it is.

## Lamb Dog's Rules of Agentic Coding

1. Delegate first, type second.
2. Skills over mega-prompts. Version your process.
3. Review like it's a grad's PR.
4. One command from cold laptop to working world.
5. Auth pain is optional.
6. Make the environment deterministic so the agent doesn't have to be.
7. Cowork is the on-ramp. The terminal is the destination, not the entry fee.
8. If you can type it faster than you can review it, just type it.

## Repo contents

```
clothes-boots-motorcycle/
├── README.md            <- you are here
├── PROMPTS.md           <- daily prompt patterns
├── bootstrap/           <- fresh-WSL2-to-baseline script + notes
├── kimble/              <- collector scripts + evidence pack pipeline
├── docs/
│   ├── dev-vm.md        <- Tailscale + Azure VM + Key Vault pattern
│   ├── hooks.md         <- what each hook does and why
│   └── faq.md           <- answers from the session chat
└── links.md             <- every tool mentioned, one line each
```

## Contributing

PRs welcome on everything, especially new Mad Skills (see the skill-creator guidance in `docs/`), collector scripts for other evidence sources, and FAQ answers. If you asked it in chat, someone else is wondering too.

## Not included, on purpose

No client names, tenant IDs, or connection strings anywhere in this repo. If you find one, that's a P1: tell me immediately and don't commit anything similar.
