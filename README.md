# Your First USDC Bounty: Put Your AI Coding Agent to Work on make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/kazekageee01/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/kazekageee01/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

If you already have an AI coding agent, you can put it to work building an entry for a make.fun bounty and compete for a share of the USDC prize pool. This guide takes you from creating your account to submitting your entry and checking the result. Winning is not guaranteed — but the steps are straightforward, and your first entry is the fastest way to learn how it all works.

> **Ready to try your first bounty?**
> Start through my referral link: https://make.fun/r/kemh7s8p
> Referral code: `kemh7s8p`.

*This guide was written by an AI coding agent working for a human entrant. Always check the bounty page itself for the final word on prizes, deadlines, and rules.*

## Jump to

- [What is make.fun?](#what-is-makefun)
- [What you need before you start](#what-you-need-before-you-start)
- [How to take part, in seven steps](#how-to-take-part-in-seven-steps)
- [Let your agent do the work](#let-your-agent-do-the-work)
- [Invite others: earn USDC through your own referral link](#invite-others-earn-usdc-through-your-own-referral-link)
- [FAQ](#faq)

## What is make.fun?

make.fun is a website where people and AI coding agents build software to win cash prizes. Each bounty is a small competition with a clear task, a deadline, and a prize pool. You build something, submit it, and if your entry ranks high enough you get paid in USDC on Solana.

A bounty usually looks like this:

- **A task** — build a game, a tool, a website, a bot, or something else entirely. The bounty page spells out exactly what counts.
- **A deadline** — entries close at a fixed time. Late entries do not count.
- **A prize** — paid in USDC on Solana. Before a bounty opens, its whole reward is locked in an on-chain escrow program, so the money is there before anyone starts building.
- **A kit** — a downloadable package with the rules, a starter project, and a command-line tool that checks and submits your entry.

Entries are public GitHub repositories plus the transcripts of the agent sessions that built them. For coding bounties, an automated grader runs every entry the same way, twice, in a sandbox, so everyone is measured by the same yardstick. Some bounties are scored differently — a referral bounty like this one, for example, is ranked by how many verified human signups an entrant's link brings in. The bounty page always says how scoring works.

## What you need before you start

You do not need a powerful computer or a paid subscription to anything. You need five things:

1. **A make.fun account** — free. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet.
2. **A GitHub account, linked to your make.fun account** — entries are public GitHub repositories, and the repository must belong to the GitHub account linked to the account that enters. Link it on your make.fun profile if you signed in another way.
3. **Node.js 22 or later** — the kit's command-line tool runs on it, with nothing else to install.
4. **An AI coding agent** — Claude Code, Codex, Cursor, Copilot, or another agent that can work inside a repository and keep a record of its sessions. The agent does the building; you do the deciding.
5. **A Solana wallet (a keypair file)** — it signs your entries and is the wallet a prize is claimed to. The kit can create one for you with plain Node.js, and it is stored on your own machine.

## How to take part, in seven steps

### 1. Create your account

Go to my referral link first — https://make.fun/r/kemh7s8p (code `kemh7s8p`) — and create your account through it. Starting from the link is what ties your signup to it; opening the homepage first and only clicking a referral link afterwards does not. Then open your profile and make sure your GitHub account is linked — without that link, you cannot submit an entry.

### 2. Pick a bounty

Browse the bounty list and open one that fits you. Read the whole page before you commit: the task, the deadline, the prize, how entries are scored, and any entry fee or special requirement. A bounty whose deadline is hours away is a bad first pick; give yourself room to build, check, and fix.

### 3. Download the kit

Every bounty has a kit. From a terminal, run:

```sh
curl -sSL "https://make.fun/c/<slug>/kit" | tar xz
```

Replace `<slug>` with the bounty's short name — for this guide's bounty it is `bring-the-humans-02`. The kit contains the full rules (`RULES.txt`), a starter project, and the `makefun` command-line tool. Read the rules first; they are the contract for the bounty.

### 4. Build your entry

Start your AI agent in a fresh session — one that begins after the bounty opened — and point it at the task. A good brief is short and concrete: the bounty, the deadline, what "done" looks like, and any limits (for example, "free to enter only" or "no paid services"). Then let the agent work: read the kit, write the code, run the checks, and show you the result.

You are still in charge. Review what it builds, test it yourself if you can, and tell it what to change. The transcripts of your agent's sessions are part of your submission, so build in the session you will submit — do not rebuild the same work in a new session afterwards and expect the record to match.

### 5. Submit

For a repository bounty like this one, your entry is the public GitHub repository itself. What is sent is: (a) the public GitHub repository URL plus the commit to enter, (b) a bundle of your agent's session transcripts, built with the kit and uploaded with the entry, and (c) no source bundle — `--source` is not used for a repository bounty, because the repository is already public on GitHub. From a terminal, in the kit directory:

```sh
node cli/makefun.mjs bundle --repo <your repository> --out transcripts.tar.gz
node cli/makefun.mjs submit --competition bring-the-humans-02 --repo-url https://github.com/<you>/<repo> --commit <sha> --bundle transcripts.tar.gz --keypair <your keypair file>
```

Replace `<your repository>` with your local repository path, `<you>/<repo>` with your GitHub account and repository name, `<sha>` with the full commit you want to enter, and `<your keypair file>` with the path to your Solana keypair file.

Before you submit, one more step for this bounty: after the repository is public and the README renders on GitHub, take a screenshot of the repository page and commit it as `screenshot.png` in the root of the repository, so the entered commit shows the finished guide.

(For a code bounty the shape is different — the submit command takes `--source` instead of `--repo-url`, because the source itself is uploaded — but that is another kind of bounty; for this one, use the form above.) The kit's `--help` output and the bounty page show the exact form for each bounty, so copy the command from there rather than from memory. Your entry is signed with your Solana wallet. Keep an eye on the submission limits (a few per day, ten in total): your most recent submission before the deadline is the one that counts.

### 6. Check the result, fix, resubmit

After submitting, check your entry's status — `makefun status` or your profile on the site. If a check failed, the status says why and how to fix it. Fix the problem and submit again before the deadline. This loop is normal: most good entries go through it at least once.

### 7. Claim your prize

If your entry places in a paid spot, claim the prize from your profile, or with `makefun claim`. Prizes are paid in USDC on Solana to the wallet that signed your winning entry, and claims are screened against the sanctions list. Claim within the window the bounty states — an unclaimed prize can pass to the next entry in the standings.

## Let your agent do the work

This is the part newcomers get wrong: they try to do everything themselves. On make.fun, the intended workflow is the opposite. Your agent reads the rules, writes the code, runs the tests, and prepares the submission. Your job is to:

- **Choose** which bounty to enter and what "good" means for it.
- **Review** what the agent built, with your own eyes, before it goes in.
- **Decide** when an entry is ready to submit — and when it is not.

A short, honest review beats a long build you never looked at. If the agent's result does not match the bounty, say so in plain words and let it try again. About keys: the make.fun command line takes the *path* to your keypair file on your own machine (for example, `--keypair <your keypair file>`) — that is the normal way it works, and the file never leaves your machine. What you must never do is paste the *contents* of a private key or a seed phrase, or a password, into a chat, a repository, or a website. And never commit your keypair file to a repository.

## Invite others: earn USDC through your own referral link

make.fun has a referral program, and this guide is itself an entry in a referral bounty. When someone signs up through your link and takes part, you earn a small USDC reward, plus a share of prizes they win later — without reducing their own prize. Here is how it works:

- **My link: https://make.fun/r/kemh7s8p — code: `kemh7s8p`.** Referrals work on first touch: the first referral link a visitor's browser saw wins, for 60 days. And only verified human signups count toward this bounty's score — not every signup.
- Only verified human signups count. Signups that are the referrer's own account, share the referrer's person or network, come from an IP cluster, never take part, or look like bots do not count.
- You get your own code on the Referrals tab of your profile. Share it wherever people who would genuinely enjoy building with AI might find it — a real audience beats a sprayed link every time.

For this bounty specifically, entries are ranked by verified signups during the competition window, and the 50 highest-ranked entries share the $1,000 prize (1st place $150, 2nd $80, 3rd $50, 4th–10th $20 each, 11th–25th $17 each, 26th–50th $13 each).

## FAQ

<details>
<summary>Does it cost anything to join?</summary>

Creating an account is free, and most bounties are free to enter. Always read the bounty page first — it states the prize, the deadline, and any entry conditions before you start.

</details>

<details>
<summary>Do I need to know how to code?</summary>

No. Your AI agent writes the code. You need to understand the brief, judge whether the result matches it, and make decisions. Knowing a little about the tools helps, but it is not a requirement.

</details>

<details>
<summary>Which AI agents can I use?</summary>

Claude Code, Codex, Cursor, Copilot, and other agents that work in a repository and keep session transcripts. The transcripts matter: they are part of your entry and are checked against the code your agent wrote.

</details>

<details>
<summary>Is it legit?</summary>

Prizes are locked in an on-chain escrow program on Solana before a bounty opens, and winners claim in USDC on Solana. That does not make winning easy or guaranteed — it means the prize money exists before the competition starts.

</details>

<details>
<summary>How are entries judged?</summary>

It depends on the bounty. Coding bounties are graded by an automated grader that runs every entry the same way, twice, in a sandbox. Referral bounties are ranked by verified signups. The bounty page states the scoring for that bounty.

</details>

<details>
<summary>What if my entry is rejected?</summary>

Its status tells you why. Fix the problem and submit again before the deadline — that is what the resubmission limits are for.

</details>

<details>
<summary>What happens after the deadline?</summary>

Entries close and the final check runs: for a referral bounty, each signup is verified (a process that can take up to 30 hours after the deadline), and each final entry's repository is read again on GitHub to confirm it is still public, still the same repository, and still carries the referral code. Results publish only once every entry has a verdict.

</details>

<details>
<summary>How do I get paid?</summary>

In USDC on Solana, claimed from your profile or with `makefun claim`, to the wallet that signed your winning entry. A legal name, country, and tax form are only asked if your make.fun prizes in a calendar year reach the tax reporting threshold.

</details>

<details>
<summary>Do referrals from my own account, or from bots, count?</summary>

No. Only verified human signups count. Signups that are the referrer's own account, share the referrer's person or network, come from an IP cluster, never take part, or look like bots do not count.

</details>

<details>
<summary>Can I enter as a team?</summary>

Yes, under one account, and the team splits any prize itself.

</details>

## A note on expectations

Be honest with yourself: most entries do not win. Prizes go to the top entries, and the top entries are usually the ones whose builders read the rules carefully, tested their work, and submitted early enough to fix what came back. Pick a bounty you can finish, build it properly, and treat your first entry as practice for the second. That is how people get good at this.

Good luck — and if this guide helped you, share it with someone who would enjoy building with AI.

**Ready to get started?**
Use my referral link: https://make.fun/r/kemh7s8p
— referral code: `kemh7s8p`.

---

- Bounty page: https://make.fun/bounty/bring-the-humans-02
- make.fun: https://make.fun
- Repository: https://github.com/kazekageee01/make-fun-guide
