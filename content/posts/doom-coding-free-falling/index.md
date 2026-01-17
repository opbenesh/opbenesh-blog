---
title: "my unexpected descent into doom coding"
date: 2026-01-11T02:16:16+02:00
draft: false
tags: ["coding", "spotify", "ai", "claude", "doom-coding", "python"]
summary: "How I built a Spotify release tracker on my phone using Claude Code and vibes."
author: "Ben Esh"
ShowPostNavLinks: true
---

> **TL;DR:** I built a fully working Spotify release tracker app over a weekend—entirely from my phone—using Claude Code. Here's how, plus tips for async "doom coding" on the go.

Hosting a weekly "new metal" show at KZRadio ([shameless plug](https://www.kzradio.net/shows/esh)) means I have an ever-renewing deadline for finding new stuff to play, and Spotify's own Release Radar misses 90% of the good stuff. I wanted to revitalize my legacy Spotify release tracker project for a while now, but obviously ain't nobody got time for this sort of thing these days.
 Except - I do have lots of free time in between other tasks, I just usually end up doom-scrolling HackerNews instead. Which is how I discovered the following gem: ["Stop Doom Scrolling, Start Doom Coding"](https://github.com/rberg27/doom-coding), coins "doom-coding" as the act of mindlessly vibe-coding on your phone.

So on Friday morning I created an empty GitHub repo, and after a weekend of vibe-Clauding on the go (is this a thing? this should be a thing), I had a fully working app.

<pre style="background:#1a1a1a; color:#0f0; padding:1em; border-radius:8px; font-family:monospace; overflow-x:auto;">
<code>$ esh-tracker track --artist="Turnstile" --since 2025-10-01

  🎵 Turnstile - Dream Logic
     Album: Dream Logic - Single
     Released: 2025-11-14
     URL: https://open.spotify.com/...</code>
</pre>

And the most surprising thing was that building it was **SO. MUCH. FUN.** The async nature is so perfect for meaningless side-projects like these. I actually vibe-coded at the supermarket and while brushing my teeth. Listen, I love to debate the AI bubble doom scenarios as much as the next guy, but please - you have to try it out. Pick a hobby project idea, and just give it a go:

*   Create an empty, private GitHub repo.
*   Spin up Claude on your phone, go to the Code tab
*   Authorize the GitHub integration and pick your repo
*   Iterate!

{{< figure src="result-readme.jpg" caption="The final result: a polished, auto-updating README for the project, generated and maintained entirely via mobile coding." width="50%" >}}

That's it - welcome to the hype train!

{{< figure src="claude-interaction.jpg" caption="A typical Claude Code interaction on mobile—reviewing code changes while waiting for the bus." width="50%" >}}

## Pro tips

*   Optional, but highly recommended: Brainstorm your planned app with your favorite non-coding LLM and ask it to create a spec.
*   Keep a `CLAUDE.md` file for instructions. Claude reads it before proceeding, so that's a good place to put important stuff about your project, priorities, and environment. Think of it like the "Our Core Values" document you never opened at your previous job!
*   This is a super async process. Rate limits, bus inspectors asking for that QR code, your stew getting burnt, etc. Keep a `TODO.md` file and ask Claude to update it, so that resuming tasks (perhaps even with another agent or environment) is always easy.
*   TDD FTW. Ask Claude to create tests for EVERY SINGLE POSSIBLE SCENARIO, and remind it to run them every once in a while. This is a great way to help the agent understand whether its task is truly done.
*   One surprising side effect of the async manner is that you can either use your newly free time for non-coding tasks (e.g. making dinner), or you can use it for performing *other coding tasks* (hello Jevons paradox!). I ended up spending most of my weekend on this.
*   One conversation per topic. Start a session, give it a few related tasks, review and merge the PR, and move on. Both you and the agent will concentrate better in this model. Learned anything interesting in this session? Great! Update `CLAUDE.md`.
*   Also - you _can_ actually use these things for non-coding tasks. Data analysis and research feels like a natural next step - put all your csvs file in a GitHub repo and let it run.

## Cloud or self-hosted?

The original Doom Coding post actually suggests a local Claude Code + Tailscale + Android terminal, but you'd have to solve sandboxing/isolation in order to auto-approve agent suggestions. This is why I recommend starting with cloud-based agents like Claude Code, Google Jules or OpenAI's Codex for a batteries-included remote-first experience.

## Further reading

1. [**"Stop Doom Scrolling, Start Doom Coding"**](https://github.com/rberg27/doom-coding) — The original article that started this whole adventure.
2. [**Simon Willison: "The year of programming on my phone"**](https://simonwillison.net/2025/Dec/31/the-year-in-llms/#the-year-of-programming-on-my-phone)  — Simon's 2025 recap includes a fantastic section on mobile-first coding that was a major inspiration.
