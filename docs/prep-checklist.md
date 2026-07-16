# Prep Checklist

Working backwards from flagship day. The theme: nothing on screen you haven't seen on screen before.

**Flagship:** A Day on the Tools with Lamb Dog (T-0)
**Stream:** Judgement Day (T+3 weeks)

## T-3 weeks

- [ ] Lock the date, book the Teams event, recording on by default
- [ ] Post announcement + launch the kill list (comms-pack.md)
- [ ] Seed the kill list with 3-4 of your own targets
- [ ] Create the `clothes-boots-motorcycle` repo (private for now), drop in the README skeleton
- [ ] Decide the three salvo tasks and stage demo assets:
  - `~/demo/salvo-feature`: repo + pre-written one-paragraph spec for Mad Skills
  - `~/demo/salvo-audit`: fresh clone of a real mid-size OSS repo for Recky
  - Sanitised deck staged in OneDrive for Cowork deck-reviewer
- [ ] Tag `demo-start` on each demo repo

## T-2 weeks

- [ ] **Dry run #1: full session, recorded, alone.** Purpose: timings and `[VERIFY]` replacements, not polish
- [ ] Watch the recording at 1.5x hunting ONLY for leaks: client names, tenant IDs, email subjects, notification popups, browser tabs, shell history, statusline content, recent-files lists, terminal titles
- [ ] Fix every leak structurally, not by "remembering not to": separate browser profile, demo-only directories, OS-level notifications off in the presenting profile
- [ ] Pre-run the three salvo tasks end-to-end; commit outputs to `demo-complete` branches (break-glass)
- [ ] Record the pre-records:

| Clip | Target length | Notes |
|---|---|---|
| Kimble pipeline end-to-end | 3-4 min raw | Played at 1.5x with live narration |
| Wispr voice demo | 45 sec | Voice demos die live |
| Dotfiles fresh-WSL2 timelapse | 20 sec | Cold machine to working |

- [ ] Cut teaser 1 (azrl 30-second clip) from dry-run footage, post it

## T-1 week

- [ ] **Dry run #2: full session with an audience of one** (trusted colleague, ideally grad-brained). Their job: flag every moment they got lost or bored
- [ ] Ruthless cut pass: anything that blew its time box in both dry runs moves to the Judgement Day overflow list
- [ ] Finalise the Rules slide (the only slide)
- [ ] Goodie-bag repo: PROMPTS.md done, bootstrap script tested in a clean container, `kimble/` scripts sanitised and README'd, repo flipped to internal-visible
- [ ] Recruit and brief the chat wingman: park questions, surface the good ones at segment breaks, drop links on cue
- [ ] Post teaser 2

## T-2 days

- [ ] Post final reminder
- [ ] Verify vm-always, Tailscale, and all demo repos from the actual presenting machine on the actual network
- [ ] Charge everything. Test the actual mic. Headset over speakers.

## Session day (T-30 min)

Run the pre-flight block in run-sheet.md, plus:

- [ ] Close Outlook, Slack, and everything with a badge; only the meeting stays open
- [ ] WezTerm presenting profile: 18pt+, quiet statusline, high-contrast theme (recordings crush low contrast)
- [ ] Windows Focus Assist ON
- [ ] Second device joined as an attendee so you see what they see
- [ ] Break-glass branches confirmed one last time
- [ ] Pre-records cued, volume checked THROUGH the meeting (share system audio test)

## During

- Hard stops per segment. Run-sheet timings are commitments, not suggestions. Overflow goes to Judgement Day; say so out loud and move on.
- Live demo dies: one retry maximum, then break-glass branch, one self-deprecating line, keep moving. Never debug live in the flagship. Debugging live is Judgement Day's entire personality.
- Say the two-speed lines. You'll want to skip them when running hot. Don't.

## T+1 day

- [ ] Chapter the recording (timestamps in comms-pack.md), post the follow-up
- [ ] Cut 2-3 sub-60-second promo clips: cold open, azrl flip, Kimble fill
- [ ] Triage the kill list: shortlist for Judgement Day, pre-clone anything needed
- [ ] Book the TryNet recurring invite
- [ ] Log every chat question into `docs/faq.md` in the goodie bag

## Judgement Day prep (T+2 weeks onward)

- [ ] Kill list triage 3 days out: winners locked, repos pre-cloned, feasibility sanity-checked
- [ ] Two backup requests pre-scoped in case a live one dead-ends in 10 minutes
- [ ] Chat wrangler nominated (you cannot code and moderate)
- [ ] Rise of the Machines block: visible on-screen task list so drop-ins know what's running
- [ ] Post the block schedule announcement (comms-pack.md)

## Data hygiene (the non-negotiables)

- No client tenant names, IDs, or data on screen at any point. Demo directories use `client-a` / `velrada-x` style names.
- `az account show` output comes from lab tenants only (velradalab / velradaip), never client tenants.
- Kimble pre-record: sandbox engagement or blur; the evidence pack is client activity data.
- Fresh shell history in every demo shell; `env` grep for secrets before going live.
- Browser: dedicated presenting profile, zero saved sessions to client portals, bookmarks bar hidden.
- The dry-run-recording leak hunt is the control that actually works. Do it both times.
