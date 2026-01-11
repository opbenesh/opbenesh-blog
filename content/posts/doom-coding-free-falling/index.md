+++
date = '2026-01-11T02:16:16+02:00'
draft = false
title = 'My Unexpected Descent into Doom Coding (or: How I Built a Spotify Tracker App Using My Phone)'
tags = ['coding', 'spotify', 'ai', 'claude', 'doom-coding', 'python']
summary = 'How I built a Spotify release tracker on my phone using Claude Code and vibes.'
[cover]
    image = "result-readme.jpg"
    alt = "Esh Tracker README"
    caption = "Esh Tracker in action"
    relative = true
+++

Hosting a weekly "new metal" show at [KZRadio](https://www.kzradio.net/shows/esh) (hello, shameless plug) means I have an ever-renewing deadline for finding new stuff to play, and Spotify's own Release Radar misses 70% of the good stuff. So I built this over the weekend:

I wanted to revitalize my legacy Spotify release tracker project for a while now, but obviously ain't nobody got time for this sort of things these days.

**THAT ALL CHANGED** when I read a Hacker News article titled ["Stop Doom Scrolling, Start Doom Coding"](https://github.com/rberg27/doom-coding) (amazing term!). 

> I'm skipping forward a bit, but turns out that these days, the LLMs allow you to spin up on-demand sandboxes for their coding services, which you can then use to vibe code **ON YOUR FREAKING PHONE.** 

But if I'm already vibe coding, I might as well **auto-approve** agent code runs, meaning that I definitely don't want the setup running on my local machine (or even a VM on the same network). So on Friday morning I created an empty GitHub repo, and after a weekend of vibe-Clauding on the go (is this a thing? this should be a thing), I had a fully working app—complete with an AI-generated logo!

```bash
$ esh-tracker track --artist="Turnstile" --since 2025-10-01

  🎵 Turnstile - Dream Logic
     Album: Dream Logic - Single
     Released: 2025-11-14
     URL: https://open.spotify.com/track/4cPd7A7...
```

And the most surprising thing was that building it was **SO. MUCH. FUN.** The **async** nature is so perfect for meaningless side-projects like these. I actually vibe-coded at the supermarket and while brushing my teeth. Listen, I love to debate the AI bubble doom scenarios as much as the next guy, but please - you have to try it out. You'll REALLY enjoy it. I promise. I liked it so much I'm writing this blog post at 3am for god's sake.

I'm going to write a web version of the tracker one day, but feel free to early-adopt at `pip install esh-tracker` (or just check out the [GitHub repository](https://github.com/opbenesh/esh-tracker)).

***

## 🛠️ The Deep Dive: How to Doom Code

If you want to try this yourself (and you should), here is my current playbook for mobile-first vibe coding:

### 1. The Setup
*   **Create an empty, private GitHub repo.**
*   **Spin up Claude on your phone**, go to the "Code" tab.
*   **Authorize the GitHub integration** and pick your repo.
*   **Doom code!** Iterate, iterate, iterate.

    ![Claude Code Interaction](claude-interaction.jpg)

### 2. Best Practices for Mobile Agents
*   **Optional, but highly recommended:** Brainstorm your planned app with your favorite non-coding LLM (like o1 or Sonnet) and ask it to create a spec.
*   **Keep an `AGENTS.md` (or `CLAUDE.md`) file** for instructions. The agents read it before proceeding—it's the perfect place for project priorities, environment details, and "Core Values".
*   **TDD is your best friend.** Ask the agent to create tests for every single possible scenario. It's the only way to truly know if a task is done when you're not hovering over the terminal.
*   **One conversation per topic.** Start a session, give it a few related tasks, review/merge the PR, and move on. Both you and the agent will stay focused.

### 3. Staying Async
*   **Keep a `TODO.md` file.** This is a super async process. Rate limits, kids needing attention, or your stew getting burnt—the `TODO.md` ensures that resuming tasks (perhaps even with a different agent) is always seamless.

***

## 💭 Assorted Thoughts

* **The Setup Paradox**: The "official" doom-coding guide suggests local Claude Code + Tailscale + Android terminal. But for true freedom, **on-demand sandboxes** (like Claude's native Code tab) are the way to go. No local dependencies, no battery drain.
* **The Interaction Model**: Auto-approve completely changes your relationship with the agent. Instead of closely supervising every `rm`, the whole thing becomes truly **async**. 
* **Jevons Paradox in Coding**: You'd think async coding would give you free time for non-coding tasks (like making dinner). Instead, it just allows you to perform *more coding tasks* at the same time. I ended up more obsessed than ever.
* **Beyond Code**: These agents are surprisingly good at non-coding data tasks. Research and analysis feel like a natural next step—dump your CSVs in a repo and let the agent crunch them.

***

## 📚 Further Reading

*   **The Original Inspiration**: ["Stop Doom Scrolling, Start Doom Coding"](https://github.com/rberg27/doom-coding) by rberg27.
*   **Simon Willison**: Another major inspiration—check out ["The year of programming on my phone"](https://simonwillison.net/2025/Dec/31/the-year-in-llms/#the-year-of-programming-on-my-phone) from his excellent 2025 recap.
