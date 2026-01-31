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

Hosting a weekly "new metal" show at KZRadio ([shameless plug](https://www.kzradio.net/shows/esh)) means I have an ever-renewing deadline for finding new stuff to play, and Spotify's own Release Radar misses 90% of the good stuff. I wanted to revitalize my legacy Spotify release tracker project for a while now, but who's got time for that.

Except - I do have lots of free time in between other tasks, I just usually end up doom-scrolling HackerNews instead. Which is how I discovered the following gem: ["Stop Doom Scrolling, Start Doom Coding"](https://github.com/rberg27/doom-coding), coins "doom-coding" as the act of mindlessly vibe-coding on your phone.

{{< figure src="claude-interaction.jpg" caption="A typical Claude Code interaction on mobile." width="50%" >}}

So on Friday morning I created an empty GitHub repo, and after a weekend of mobile coding, I had a fully working app.

```bash
$ esh-tracker track --artist="Turnstile" --since 2025-10-01

  🎵 Turnstile - Dream Logic
     Album: Dream Logic - Single
     Released: 2025-11-14
     URL: https://open.spotify.com/...
```

And the most surprising thing was that building it was genuinely fun. The async nature is so perfect for meaningless side-projects like these. I actually vibe-coded at the supermarket and while brushing my teeth. Listen, I love to debate the AI bubble doom scenarios as much as the next guy, but please - you have to try it out. Pick a hobby project idea, and just give it a go:

*   Create an empty, private GitHub repo.
*   Spin up Claude on your phone, go to the Code tab
*   Authorize the GitHub integration and pick your repo
*   Iterate!

That's it - your repo is live.
{{< figure src="result-readme.jpg" caption="The final result: a polished, auto-updating README for [esh-tracker](https://github.com/opbenesh/esh-tracker), generated and maintained entirely via mobile coding." width="50%" >}}

## Pro tips

*   **Start with a spec**: Brainstorm your planned app with your favorite non-coding LLM and ask it to create a spec. Optional, but highly recommended.
*   **Track your progress**: This is a super async process. Rate limits, bus inspectors asking for that QR code, your stew getting burnt, etc. Keep a `TODO.md` file and ask Claude to update it, so that resuming tasks (perhaps even with another agent or environment) is always easy.
*   **TDD FTW**: Ask Claude to create tests for EVERY SINGLE POSSIBLE SCENARIO, and remind it to run them every once in a while. This is a great way to help the agent understand whether its task is truly done.
*   **Use an `AGENTS.md` file**: Agents read it before proceeding, so that's a good place to put important stuff about your project, priorities, and environment. Think of it like the "Our Core Values" document you never opened at your previous job!

Happy doom coding!