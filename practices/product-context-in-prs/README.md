# Product context in every PR

Every pull request carries a short note on why the product changed, and that note ends up in git history, where it stays next to the code for as long as the code lives.

## The problem

How many times have you worked on a mature product and found that no one knows why a feature was built the way it was?

You dig up the original PRD, then realize it only tells half the story. Every bug fix and small improvement since then got written up in a ticket or some doc, and slowly the reasoning goes hazy. The people who made those calls have moved on, and no one quite remembers.

I've seen this happen across several products now. It's a real source of pain, and worse, it blindsides you when you plan a change, because you can't see what it might break.

The code is the one thing that's still true a year later. So the why should live right beside it, inside each change.

## The practice

Every PR description has a **Product context** section. Keep it to about 150 words:

- **User problem:** what the person using the product was running into.
- **Options considered:** the other ways we could have solved it.
- **Why this one:** what tipped the call, and what we gave up.
- **What we learned:** anything that surprised us while building or testing.

Open questions are optional. If the discussion ran long, put it in a decision record and link to it from the note.

Then merge with squash, with the repo set so the squash commit message is the PR title and description. The note becomes the commit message.

## Why the description and not a comment

I learned this one the hard way. I started out writing these notes as PR comments, and only later realized that comments never leave GitHub.

PR comments and descriptions sit in GitHub's database, attached to the PR page. Clone the repo, move it to another host or run `git log`, and they're nowhere to be seen. A commit message is different. It's part of git history, it travels with every clone, and it shows up in `git log` and `git blame` with no GitHub page to open.

So six months later, anyone, or any agent, can run `git blame` on a line and read why it exists. That second reader matters more every month. An agent that reads the why before touching the code is far less likely to "fix" something that was deliberate.

## How it's gone for me

Every pull request on Bot Portal carries one of these notes, more than ninety so far. Reading them back, they work like a diary of every product call I made, and a few have already turned into articles.

Engineers have done a version of this for a long time. Google's code review guide and the Linux kernel's patch rules both ask every change to say why it was made. What's usually missing is the product side of that why: the user problem, the options and what we learned. That's the gap this practice fills.

## Things to watch

- **It's permanent.** Whatever goes in the description stays in history, including if the repo goes public later. Never put secrets, tokens, customer names or private data in it.
- **Fix it before you merge.** The commit message is written at merge time, so later edits to the description don't carry over. Re-read it and make sure it matches what actually shipped.
- **Keep it short.** Agent-written notes can run long. The word cap keeps `git log` readable, and `git log --oneline` still shows only the title.
- **Comments still stay behind.** Anything said in comments after the PR was opened lives only on GitHub. If it changed the decision, fold it into the description.

## Set it up

1. Copy [pull_request_template.md](pull_request_template.md) into your repo as `.github/pull_request_template.md`.
2. Run the one-time squash setting from [setup-prompt.md](setup-prompt.md).
3. Paste the prompt in [setup-prompt.md](setup-prompt.md) into your coding agent, or add it to your `CLAUDE.md` or `AGENTS.md`, so every PR it opens follows the practice.
