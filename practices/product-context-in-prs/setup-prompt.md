# Setup prompt

Two parts: a one-time repo setting, and a prompt for your coding agent.

## 1. One-time repo setting

This makes every squash merge use the PR title and description as the commit message. Replace OWNER/REPO with your repo, and run it with the GitHub CLI as someone who can change the repo's settings:

```
gh api -X PATCH repos/OWNER/REPO -f squash_merge_commit_title=PR_TITLE -f squash_merge_commit_message=PR_BODY
```

Squash merging has to be allowed on the repo for this to matter. You can check both under the repo's Settings, in the Pull Requests section.

## 2. Prompt for your coding agent

Paste this into Claude Code or any coding agent, or add it to your `CLAUDE.md` or `AGENTS.md`:

```
From now on, the product reasoning for every change must end up in git history, not only on GitHub.

1. Every PR description has a "Product context" section, using the headings in .github/pull_request_template.md. Put it in the description itself, never in a separate PR comment.
2. Keep it to about 150 words: the user problem, the options we considered, why we picked this one, and what we learned. Write it from the conversation where the decision was made, and quote the person who made the call where you can. Put long discussion in a decision record and link to it.
3. Before merging, re-read the description and update it so it matches what actually shipped.
4. Merge with squash, so the PR title and description become the commit message.
5. Never put secrets, tokens, customer names or private data in a PR description. It becomes permanent history.
6. Optional backfill: for older PRs whose product reasoning sits only in comments or other docs, collect it into a docs/product-history.md file in one commit.
```
