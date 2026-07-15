# Run Sheet

**Event 1:** A Day on the Tools with Lamb Dog (flagship, 60 min)
**Event 2:** Judgement Day (open workshop stream, half day, T+3 weeks)
**Tagline:** "Come with me if you want to ship."

Anything marked `[VERIFY]` is a best-guess command. Replace with real syntax during dry run #1.
Golden rule: every tool gets shown doing something real, or it gets cut.

---

# Part 1: The Flagship

Live on Teams, recorded, chaptered afterwards. Dedicated 1080p presenting window, terminal font 18pt+, notifications off, demo directories only.

## Segment overview

| Time | Segment | Purpose |
|---|---|---|
| 0:00 | Cold open | One command restores the world |
| 0:05 | Fire the salvo | Delegate first, type second |
| 0:12 | Invisible plumbing | Multi-tenant sanity (veteran mind-blow) |
| 0:22 | Plugins and daily drivers | 90 seconds each, live, doing something |
| 0:32 | Consultant crowd-pleasers | Kimble + Cowork (low-code bridge) |
| 0:42 | Harvest | Review discipline (credibility for sceptics) |
| 0:52 | Goodie bag + pitch | Rules slide, repo, Judgement Day plug |

## Pre-flight (T minus 30 min)

- [ ] Presenting profile active (font, statusline quiet mode, clean wallpaper)
- [ ] Fresh shell history in every demo shell: `history -c && rm ~/.bash_history`
- [ ] `env | grep -iE 'key|token|secret|pass'` returns nothing sensitive
- [ ] Demo repos reset: `git -C ~/demo/<repo> reset --hard demo-start && git clean -fd`
- [ ] Break-glass branches confirmed: `demo-complete` on each salvo repo
- [ ] Pre-recorded clips loaded, cued, audio tested (Kimble, Wispr)
- [ ] vm-always reachable: `ssh always echo ok`
- [ ] Tailscale up both ends: `tailscale status`
- [ ] Teams recording ON, chat wingman briefed
- [ ] Water

## 0:00-0:05 | Cold open: the day starts

**On screen:** blank desktop, one terminal.

```bash
herdr attach lambdog        # [VERIFY] your session-restore command
```

Sessions populate: PowerWorker, Unfurl, dvx, a client sandbox, multiple Claude Code panes. **Say nothing for ~30 seconds.** Then:

> "That's the day started. Everything you just saw come up, I'll unpack over the next hour. But first I'm putting some agents to work, because I don't start my day by typing code. I start it by delegating."

**Two-speed:** "New folks: your environment should be one command away. Veterans: this is herdr, my Rust tmux replacement. Keyboard protocol talk happens at Judgement Day."

**Fallback:** plain `tmux attach` to a pre-built session. Nobody will know except you.

## 0:05-0:12 | Fire the salvo

Kick off three real agent tasks live, then walk away. Harvested at 0:42.

**Task 1: Mad Skills feature build** (`~/demo/salvo-feature`)

```bash
cd ~/demo/salvo-feature && claude
> /rig "<pre-written one-paragraph feature spec>"   # [VERIFY] which phase you invoke
```

Narrate why a skill beats a mega-prompt. Keel, brace, rig, build, ship, berth: one sentence each, 60 seconds total.

**Task 2: Recky audit on an unfamiliar repo** (`~/demo/salvo-audit`, fresh clone of a real mid-size OSS repo)

```bash
cd ~/demo/salvo-audit && claude
> use the recky skill to audit this codebase and produce a handoff brief
```

> "I get dropped into unfamiliar codebases weekly. This is how I stop pretending I've read them."

**Task 3: Cowork deck review** (pre-staged sanitised deck in OneDrive). Runs in Cowork, not the terminal. Quietly plants the low-code flag early.

**Close:** "Three tasks running. I'm not going to watch them. That's the whole point. Back to them at quarter to."

**Two-speed:** "New folks: the prompts were short because the skills carry the process. Veterans: skills are versioned, reviewable, and PR-able, unlike your prompt library in Notepad."

**Fallback:** if a task errors on launch, acknowledge it ("that's real life") and defer to the break-glass branch at harvest. Do not debug live here.

## 0:12-0:22 | The invisible plumbing

**Demo 1: azrl per-directory credential isolation (the headline act)**

```bash
cd ~/demo/client-a && az account show --query '{sub:name, tenant:tenantId}' -o table
cd ~/demo/velrada-x && az account show --query '{sub:name, tenant:tenantId}' -o table
```

Context flips on `cd` alone. Pause, let it sink in. Then 60 seconds on how: azrl shim, per-directory config, SSH/WSL browser-callback bridge. 20 seconds of the TUI:

```bash
azrl dash    # [VERIFY]
```

> "Open source. Link's in the goodie bag. If you juggle more than one tenant, install it this afternoon."

**Demo 2: git-credential-ado across tenants**

```bash
cd ~/demo/client-a && git pull     # tenant A
cd ~/demo/velrada-x && git pull    # tenant B
```

One sentence on the helper. Depth goes to Judgement Day.

**Demo 3: Tailscale + vm-always**

```bash
ssh always    # show a Claude Code session already running on the VM
```

> "My dev machine follows me around. Laptop dies, phone hotspot, doesn't matter. Secrets live in Key Vault via managed identity, nothing on the laptop."

**Demo 4: dotfiles bootstrap** (30 sec). Show the repo and symlink installer; play the pre-recorded fresh-WSL2 timelapse rather than running it.

**Two-speed:** "New folks: auth pain is optional, the goodie bag has the fix. Veterans: azrl issues are open, PRs welcome."

**Timing discipline:** this segment WILL blow out. Hard stop at 0:22. Overflow goes to Judgement Day.

## 0:22-0:32 | Plugins and daily drivers

90 seconds each, live, doing something. Pick six, cut ruthlessly:

1. **claude-statusline**: what the fuel gauge is telling you right now (context, model, session state)
2. **Hooks (session-guard + Stop hook)**: trigger the Stop hook live by letting an agent try to pause mid-tasklist. "Deterministic guardrails beat hoping the model behaves."
3. **squiz**: one browser automation on a sanitised, pre-chosen page
4. **Wispr**: dictate a prompt into Claude Code. PRE-RECORDED. Voice demos die live.
5. **superpowers**: invoke one workflow, one sentence on methodology, point at obra's repo
6. **graphify** `[VERIFY scope]`: its single best trick

Honourable mentions, verbal only, 10 seconds: dvx, Blueprint Foundry, Dopamine Hit. "Judgement Day topics. Vote on the kill list."

**Two-speed:** "New folks: install the Day One tier only, or you'll drown. Veterans: the hooks are where the leverage is, steal mine."

## 0:32-0:42 | The consultant crowd-pleasers

**Demo 1: Kimble timesheet reconstruction** (PRE-RECORDED, narrated live at 1.5x). Full chain: M365 signals + git/Claude Code collectors, JSONL evidence pack, Cowork, Excel + kimble-import JSON, Chrome extension fills Kimble.

> "I stopped reconstructing my week from memory months ago. The evidence pack knows what I did better than I do."

End the clip on the filled timesheet. Pause for the chat reaction. There will be one.

**Demo 2: Cowork live** (short). Open Cowork, show the salvo deck-review finished or in flight. No terminal, no code, same agentic pattern, anyone in the business can use it.

> "If you left now with only this segment, you'd still save two hours a week. The terminal stuff is my day. This is everyone's day."

**Two-speed:** "New folks and non-devs: Cowork is your on-ramp, start here. Veterans: collector scripts are in the goodie bag, adapt them to your own evidence trail."

## 0:42-0:52 | Harvest

Return to the salvo in order:

1. **Feature build:** open the diff. Review out loud like a grad's PR. Accept something, reject something, show HOW you push back (corrective prompt, not rage-quit). If it produced slop, celebrate it: "This is why review is non-negotiable."
2. **Recky audit:** skim the handoff brief. Point at one thing you didn't know about the repo. "Forty minutes of unattended work I'd have spent an afternoon on."
3. **Deck review:** one-line callback to the Cowork segment.

**Plant the flags** (verbal, 2 min):

- Skills beat mega-prompts. Version your process, not your prose.
- Review agent output like a grad's PR. Trust is earned per-task, not granted per-tool.
- Determinism matters MORE in an agentic world: hooks, per-directory auth, dotfiles. The agents are non-deterministic, so nothing around them should be.
- Where I DON'T use agents: <your honest 2-3>.

**Fallback:** stalled task? Switch to `demo-complete`: "Here's the same run from yesterday." Zero shame, keep moving.

## 0:52-1:00 | Goodie bag, rules, and the pitch

**The only slide:** Lamb Dog's Rules of Agentic Coding (screenshot-bait):

1. Delegate first, type second.
2. Skills over mega-prompts. Version your process.
3. Review like it's a grad's PR.
4. One command from cold laptop to working world.
5. Auth pain is optional.
6. Make the environment deterministic so the agent doesn't have to be.
7. Cowork is the on-ramp. The terminal is the destination, not the entry fee.
8. If you can type it faster than you can review it, just type it.

**Then:**

- Goodie-bag repo link in chat: **clothes-boots-motorcycle**. "You arrived with nothing. Clone this and leave equipped. Day One tier tonight, that's the homework."
- Announce **Lamb Dog: Judgement Day**: date, drop-in format, kill list link. "You vote, I build it live."
- Announce TryNet fortnightly office hours.
- Invite Mad Skills contributions: "Build a skill, PR it in."

**Last line:**

> "None of this is magic. It's plumbing, habits, and review discipline. The agents are the easy part. Come with me if you want to ship."

---

# Part 2: Lamb Dog: Judgement Day

Half day, 10:00-15:00, drop-in like a Twitch stream. Published block schedule so people cherry-pick. Recorded and chaptered. Each block: 45 min content + 15 min buffer, self-contained, 60-second context reset at the top for fresh arrivals.

| Time | Block | Content |
|---|---|---|
| 10:00 | **Genisys** (setup from zero) | Fresh WSL2 to working agentic setup. The grad block. Slow, welcoming, questions encouraged. Yes, named after the bad one. It's a fresh install, it fits. |
| 11:00 | **Skynet Core** (deep plumbing) | azrl internals, git-credential-ado, multi-tenant CLI profiles, Tailscale + vm-always + Key Vault. The veteran block. |
| 12:00 | **Rise of the Machines** (lunch lurk) | Agents grinding a real backlog item while I eat. Camera on the terminal, mic mostly off. Genuinely soothing viewing. |
| 13:00 | **The Kill List** (requests #1) | Top-voted requests, built live, unrehearsed, honest debugging. |
| 14:00 | **Dark Fate** (bring your broken thing) | Attendees screen-share a real problem; we set agents on it together. |
| 14:45 | **Hasta La Vista** (wrap) | What got built, links, TryNet plug, Mad Skills PR invite. "Hasta la vista, backlog." |

## Judgement Day prep

- Triage the kill list 3 days out: shortlist winners, pre-clone repos, sanity-check feasibility. "Unrehearsed" means the coding, not the logistics.
- Two backup requests pre-scoped in case a live one dead-ends in 10 minutes.
- Nominate a chat wrangler. You cannot code and moderate.
- Rise of the Machines needs a visible task list on screen so drop-ins know what's running.

## Overflow list (flagship cuts land here, all vote-able on the kill list)

herdr keyboard protocol internals, dvx Dataverse MCP walkthrough, Dopamine Hit and spec-driven dev, Sudo architecture, local inference on the 4070 SUPER, CleverSwitch and monitor automation, Unfurl, war-room multi-agent orchestration.
