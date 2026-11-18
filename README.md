# builder-notes

Most of us now build through agents. We describe the problem, they write the code, and the real job is deciding what's worth building and why.

As I've used these agents to build my own products, I've picked up habits that made a real difference. This repo is where I share them, especially for product thinkers who don't come from an engineering background. You don't need to learn software best practices first. Apply a practice here while you build, and you'll find yourself following those best practices along the way. I'm a product manager with a technical background, and it has given me a head start with coding agents. I'd like to pass some of that on.

## Practices

### Product context in every PR

I've worked on mature products where nobody could tell me why a feature worked the way it did. The PRD said one thing, years of bug fixes said another, and the people who made the calls had moved on. With agents it gets worse. An agent reads the code, not the history, and will happily "fix" something that was deliberate.

So every pull request I merge now carries a short product note: the user problem, what I considered, what I picked and why. It goes into the commit itself, so the reason sits next to the code forever. Close to a hundred of these notes later, they read like a diary of every product call I've made, and a few have already turned into articles.

[Set it up for yourself](practices/product-context-in-prs/)

## If you try one

Make it yours. If it breaks or you find a better way, open an issue. I'd genuinely like to know.

Find me on [X](https://x.com/far_and_close) and [LinkedIn](https://www.linkedin.com/in/saurabhmehta2/).
