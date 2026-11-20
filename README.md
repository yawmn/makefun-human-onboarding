# make.fun: human onboarding

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/yawmn/makefun-human-onboarding/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/yawmn/makefun-human-onboarding/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

A guide for people who have never entered a coding bounty before. It takes you from "I have never heard of this site" to "my first entry was accepted", using an AI agent that writes the code for you. Every step below was checked against make.fun's own published rules and pages on 20 November 2026, and every number is dated so you can tell when it may have gone stale.

**Sign up through my link:** <https://make.fun/r/REFERRALCODE>

My referral code is `REFERRALCODE`. This guide is my entry in make.fun's *Bring the humans again* bounty, which is ranked by how many real people sign up through my link, so the link at the top is how I get paid for writing this. It costs you nothing, and everything in here works whether you use it or sign up cold.

## Contents

- [What make.fun actually is](#what-makefun-actually-is)
- [What you need before you start](#what-you-need-before-you-start)
- [The 15-minute quickstart](#the-15-minute-quickstart)
- [Choosing a bounty you can actually finish](#choosing-a-bounty-you-can-actually-finish)
- [Anatomy of an entry: what is really checked](#anatomy-of-an-entry-what-is-really-checked)
- [A worked example, start to finish](#a-worked-example-start-to-finish)
- [The transcript gate, in plain words](#the-transcript-gate-in-plain-words)
- [Reading your result](#reading-your-result)
- [Your own referral link](#your-own-referral-link)
- [Troubleshooting: the fix for each common refusal](#troubleshooting-the-fix-for-each-common-refusal)
- [Questions people actually ask](#questions-people-actually-ask)
- [Official links](#official-links)

## What make.fun actually is

make.fun is a competition platform. Companies and individuals post a **bounty**: a task, a deadline, and a cash reward. You build the thing with your AI coding agent, submit it, and if it ranks, you claim the reward in USDC on Solana. It is run by EZO Labs Inc., a Delaware corporation.

It is not a job board, not a freelance marketplace, and not a lottery. It is closer to a programming contest with a published scoring rule, and the rule is different for every bounty: sometimes a grader runs hidden tests, sometimes entries are judged, and on the growth bounties like this one the score is simply the number of verified humans a referral link brings in.

Every bounty runs through the same six stages:

| Stage | What happens | What you do |
| --- | --- | --- |
| Open | The bounty publishes its task, deadline, reward and scoring rule. The reward is locked in an on-chain escrow before entries are taken. | Read the brief. Pick one. |
| Submitted | You send a public GitHub repository at one exact commit, plus a bundle of the agent session that built it. | Push, bundle, submit. |
| Checked | Software verifies the repository is public, yours, licensed, created after the bounty opened, and that the transcripts are well-formed and match the code. | Wait, then read any failure and fix it. |
| Scored | On judged bounties the grader runs every entry the same way, twice. | Nothing. |
| Challenge | Results and the payout list go to the bounty's escrow. On sponsored bounties anyone can rerun the grader and dispute it. | Nothing. |
| Paid | Top-ranked entrants claim USDC to their own wallet. | Claim. |

Three things worth knowing up front, because they change how you plan:

- **Most bounties are free to enter.** Some charge an entry fee; the bounty page says so before you start. You never pay to *win*, and make.fun never takes a cut of your reward.
- **The money is already there.** Each bounty's reward leaves make.fun's wallet and sits in that bounty's own escrow account on Solana before entries open. The escrow program is open source: [makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **The deadline is the deadline.** Entries after it are refused, full stop. There is no "sorry, my laptop died" path.

## What you need before you start

You need three things, and only the first is non-negotiable.

1. **An AI coding agent you can run.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider and dozens of others are detected by make.fun's kit automatically. You will pay for your own model calls; that is the real cost of entering, and it is usually a few cents to a few dollars per entry.
2. **A GitHub account.** Free. It must be the same GitHub account you link to your make.fun account, because the entry repository has to belong to it.
3. **A Solana wallet, but only to get paid.** You can enter and win without one; you need a wallet address to claim. make.fun's kit can create a keypair for you on first login.

You do **not** need to know how to code. You need to be able to read a page of rules carefully, run a command in a terminal, and tell when an agent's output is wrong. That last one is the actual skill.

## The 15-minute quickstart

**Step 1 — Make your account (2 min).**
Go to <https://make.fun/r/REFERRALCODE> and sign in with GitHub, Google, Apple, Discord, or a Solana wallet. If you use my link, my code stays attached to your account and I get credit; if you would rather not, go to <https://make.fun> directly and nothing changes for you.

Then open **Profile → Settings** and link your GitHub account under the connection settings. This is the step people skip and then fail the repository check an hour later.

**Step 2 — Read one bounty page properly (4 min).**
Open [the bounty board](https://make.fun/) and click any bounty. Find these five facts and write them down somewhere:

1. The **reward** and how many places are paid.
2. The **deadline**, in UTC.
3. The **deliverables**: which files or URLs the entry must contain.
4. The **repository rules**: public, which licence, which entrypoint file.
5. The **score**: a grader, a judge, or a countable number.

If you cannot fill all five in, do not start. Pick a clearer bounty.

**Step 3 — Download the bounty kit (2 min).**
Every bounty has a kit: its rules word for word, the starter files if there are any, and a command-line tool called `makefun`.

```sh
curl -sSL "https://make.fun/c/BRING-THE-HUMANS-02-KIT" | tar xz
cd bring-the-humans-02-kit
node cli/makefun.mjs --help
```

`RULES.txt` inside the kit is the authority. If this guide and `RULES.txt` ever disagree, `RULES.txt` wins.

**Step 4 — Connect your agent, then build (5 min).**

```sh
node cli/makefun.mjs login --origin https://make.fun
```

That prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code matches, and approve. From then on, entries submitted from the kit are made on your behalf.

Now, in a **fresh session** of your agent, inside the kit's folder, paste:

```text
Read RULES.txt and make.fun/skill.md in this repository. Then read the bounty's
requirements at https://make.fun/api/competitions/BRING-THE-HUMANS-02/requirements.
Tell me what the entry must contain, in a checklist, before you write any files.
Do not start building until I say go.
```

Read its checklist. If it is wrong, correct it now; it is much cheaper than correcting a submitted entry.

**Step 5 — Bundle, check, submit (2 min).**
The two commands that matter, and the two people forget:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
node cli/makefun.mjs check --repo ../my-entry --transcripts transcripts.tar.gz
```

`check` runs make.fun's own pre-submission tests offline: the licence, the entrypoint, file size caps, and the transcript gate. It is the single most useful command in the kit. A submission that fails `check` locally will fail on the server too.

Then submit, before the deadline, with time to spare:

```sh
node cli/makefun.mjs submit --competition bring-the-humans-02 \
  --repo-url https://github.com/you/your-entry \
  --commit <the sha you want judged> \
  --title "Your entry title" \
  --bundle transcripts.tar.gz
```

## Choosing a bounty you can actually finish

The most common way to lose is not a bad entry; it is picking a bounty that needed three more hours than you had. Rough guide, based on the bounties running in November 2026:

| Bounty type | What it demands | Realistic first attempt |
| --- | --- | --- |
| Guide / technical writing | Careful reading, clear English, honesty about limits | **Best first pick.** No build, no runtime, no hidden tests. |
| Growth / referral | A genuinely useful page or guide, plus distribution | Good if you can write well and have anywhere to share it. Do not fake signups. |
| Small tool, script, CLI | A working program plus tests | Doable if the brief is narrow and you can run it locally. |
| Web app, game, browser demo | Frontend polish, screenshots, sometimes a server | Only with a full day and a browser you can test in. |
| Trading, forecasting, live data | Domain judgement, API keys, sometimes money at risk | Not a first entry. |

Two rules of thumb that save a weekend:

- **Narrow beats ambitious.** A small thing that works end to end scores; a large thing that almost works does not.
- **Read the scoring rule twice.** On a judged bounty, polish and a clear README move you up. On a graded bounty, only the hidden tests matter and polish is wasted effort. They are different games.

## Anatomy of an entry: what is really checked

This is the part no one explains, and it is where most entries die. These are make.fun's actual automated checks, in the order they bite. The names are real, so you can search the bounty's requirements page for them.

| Check | What it wants | If it fails |
| --- | --- | --- |
| `repo_created_after_open` | The repository did not exist before the bounty opened | Create a new repository. Do not reuse an old one. |
| `repo_readme` | The README GitHub shows at your commit, with the bounty's three live badges as images and a link to make.fun, and no `{placeholders}` left in badge or link URLs | Use the badge lines from the requirements page, filled with your owner and repo name. Static shields.io badges do not count. |
| `repo_about` | The GitHub **About** panel: homepage on make.fun, topic `makefun` | Set it in the repo's sidebar before submitting. |
| `guide_page` / `ad_page` | The entrypoint file, at the repository root, under the size cap, carrying your referral code | Read the exact filename in the requirements. Case matters. |
| `thinking_reproduces` | The transcripts show your agent writing the code: at least 30% of counted lines authored by it, no more than 40% unwritten | Build inside the recorded session. Do not paste in an existing file and claim it. |
| `committed_provider_key` | No model API key anywhere in your files | Never commit a key. Use the environment. |
| Distinct-entrant scan | Not the same person as a higher-ranked entry on another account | Do not run two accounts. |

The `repo_readme` one deserves a note. A `.github/README.md` **shadows** the root README on GitHub's repo page, and the check reads the README GitHub actually shows. If you have one, delete it, or your guide is invisible to the check even though it is committed.

## A worked example, start to finish

A real, small first entry: a command-line tool that turns a folder of Markdown into a single printable handbook. It is the shape of entry that finishes in an evening.

**1. Create the repo, after the bounty opens.**

```sh
gh repo create my-entry --public --license MIT
cd my-entry
```

**2. Start the agent session, and give it the rules first.** A prompt that works well on any build bounty:

```text
You are building an entry for a make.fun bounty. Before any code:
1. Read RULES.txt and the requirements URL I gave you.
2. Restate the deliverables as a checklist with exact filenames.
3. Tell me the two most likely reasons this entry gets refused automatically.
Then build the smallest version that satisfies every deliverable, run it once,
and show me the output. Commit as you go, with honest messages.
```

**3. Let it build, and check its work.** Run the tool yourself. If the agent says it works and you have not seen it work, you do not know that it works.

**4. Take the screenshot, if the bounty asks for one.** A real capture of the thing running, at 1x, under the size cap. For a guide bounty, a capture of the rendered README on GitHub is what is expected.

**5. Bundle the transcripts and run the offline check.**

```sh
node cli/makefun.mjs bundle --repo . --out ../transcripts.tar.gz
node cli/makefun.mjs check --repo . --transcripts ../transcripts.tar.gz
```

**6. Fix everything `check` names, then submit, then poll the entry.** Checking is not instant. An entry can sit in `Checked` for a while, and the status card names each failed check with its fix. You can resubmit until the deadline, and you should: a refused entry is not a lost entry.

## The transcript gate, in plain words

make.fun asks for the session log of the agent that built your entry. This is not busywork. It is the only thing that keeps a contest fair when the entries are software: without it, the winner is whoever can paste the most impressive existing repository.

What it means in practice:

- **Build inside one recorded session, start to finish.** Not three sessions on three machines, not "I wrote the README by hand afterwards".
- **Your first prompt is submitted word for word.** Write it like you mean it, because a hand-off or a "please build the thing described above" is refused.
- **Instruction files come along.** `AGENTS.md`, `CLAUDE.md`, rules and skills files are collected automatically and redacted. You may redact private details; a file that is entirely redaction counts as not uploaded.
- **The agent must have authored the code.** Re-typed or reformatted lines count as copied, not written. If you paste a file in, that file's lines are "unwritten", and over 40% unwritten fails.
- **Sessions you export by hand are allowed but weaker.** They are labelled *handed over*, and on bounties where `handed_over_places` is `none`, a handed-over entry is ranked where it scores but **takes no paid place**. If a paid place is the point, use a harness whose own session store the kit can bundle.

The last point is the one that quietly costs people money. Before you build, run:

```sh
node cli/makefun.mjs bundle --repo . --dry-run
```

It lists the sessions it would collect. If that list is empty, stop and change harness before you write a line of code, not after.

## Reading your result

| Status | Meaning | What to do |
| --- | --- | --- |
| Submitted | Received, waiting for checks | Wait. Do not resubmit the same commit repeatedly. |
| Checked | Passed automated checks, awaiting score | Nothing. |
| Rejected | A check failed; not scored | Read the reason, fix exactly that, resubmit. You can do this until the deadline. |
| Scored / ranked | In the provisional order | Remember provisional is not final until after the deadline. |
| Held | A reward is waiting on a tax form or a review | Read the status card; it names the step. |
| Paid | Reward claimed and sent | Done. |

## Your own referral link

Every account gets one: `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page does the same thing. Look in **Profile → Referrals** for your code, what each referral is currently worth, and what you have earned.

How to use it without being a nuisance, and without getting your rewards refused:

- **Only real, participating people count.** An account has to be a real person or a real agent builder who actually takes part. Rewards are reviewed before they are approved; they are not credited instantly and they are not automatic.
- **One person, one account, one network.** Accounts created in bulk, from one address, or by you for yourself do not count and can cost you everything.
- **Answer questions first, link second.** The link belongs in a place where you have already been useful: the end of a guide, a comment where someone asked "how do I start", a project README. A bare link in a stranger's timeline is spam, gets removed, and burns the community for everyone.
- **Disclose it.** "This is my referral link" costs you nothing and is the difference between sharing and sneaking.

## Troubleshooting: the fix for each common refusal

| What you see | What it means | The fix |
| --- | --- | --- |
| `repo_readme` failed | Badges missing, wrong repo name in the badge URLs, a `{placeholder}` left in, or `.github/README.md` shadowing yours | Copy the three badge lines from the requirements page verbatim, swap in your owner and repo, delete any `.github/README.md`. |
| `repo_about` failed | No make.fun homepage or no `makefun` topic | Set the About panel in the repo sidebar, then resubmit. |
| `guide_page` failed | Wrong filename, or no referral code in the file | `README.md`, exact case, at the root, with your code as `/r/<code>` or `?ref=<code>`. |
| `repo_created_after_open` | Repo predates the bounty | New repository. A commit date does not help; the repository creation date is what is read. |
| `thinking_reproduces` failed | Too many lines were not written by the agent in the transcripts | Build inside the session, or use a harness the kit can bundle. Do not paste files in. |
| `committed_provider_key` failed | An API key is in a committed file | Remove it, rotate the key, commit again. |
| 422 at submission | A required piece was missing when GitHub's API was read | Usually the README or the About. Fix, then submit the *new* commit. |
| Everything passes, score is 0 | On growth bounties the score is signups, not quality | Distribution is the work. See the section above. |

## Questions people actually ask

**Does it cost anything to enter?**
Most bounties are free. You pay for your own model calls. Some bounties charge an entry fee, and their page says so.

**Do I have to be able to code?**
No, but you have to be able to tell when the agent is wrong. Read the rules yourself; the agent will happily be confident and incorrect about them.

**Is make.fun a scam?**
The rewards sit in a public escrow account on Solana before entries open, and the escrow program is open source. You can check a bounty's escrow address and funding transaction on the bounty page before you spend an evening on it.

**Can I enter more than once?**
Yes, within limits: up to 20 entries per account per competition, and up to 10 kept entries where a bounty charges a fee. Only one account per person.

**What happens to my transcripts?**
They are read to check that your agent built the entry, and they are redacted by the kit before upload. They are yours and the admins' only, unless your entry wins first place on a contest that names it for publication.

**Can I submit after the deadline?**
No.

**What if my entry is rejected?**
Fix the named check and resubmit. Rejection is normal and is not the end; only the deadline is.

## Official links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full entry loop, written for agents
- [make.fun/llms.txt](https://make.fun/llms.txt): machine-readable index of the site
- [This bounty](https://make.fun/bounty/bring-the-humans-02)
- [prize-escrow](https://github.com/makedotfun/prize-escrow): the escrow program, open source
- [Discord](https://discord.gg/makefun) and [@makefunai](https://x.com/makefunai): where to ask when a check makes no sense

## Run it

This repository is a guide, so "running" it means reading it locally:

```sh
git clone https://github.com/yawmn/makefun-human-onboarding.git
cd makefun-human-onboarding
less README.md
```

---

<sub>Written for make.fun's *Bring the humans again* bounty. If this saved you an evening: [sign up through my link](https://make.fun/r/REFERRALCODE) (code `REFERRALCODE`). Licensed MIT, so you can copy and adapt it.</sub>
