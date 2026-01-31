---
title: "til: link capturing in obsidian with macrodroid"
date: 2026-01-31T23:43:36+02:00
draft: false
tags: ["obsidian","macrodroid"]
summary: "Easy save-for-later link capturing for Obsidian on Android"
author: "Ben Esh"
---

I'm migrating my save-for-later system to [Obsidian](https://obsidian.md/). I've used Notion databases for this in the past, but Obsidian is basically a Markdown frontend and doesn't have an out-of-the-box equivalent. This is what happens when you just share links to the Obsidian app in Android:

> https://strangestloop.io/essays/things-that-arent-doing-the-thing
> https://writethatblog.substack.com/p/simon-willison-on-technical-blogging
> https://openai.com/index/inside-our-in-house-data-agent/

Works, but I can immediately think of 3 major issues:
* New links are added to the end of the file, so the most recent links are at the bottom
* Marking articles as read is clunky
* Raw URLs don't tell you much at a glance

Fortunately, what Obsidian lacks in features, it shines in interoperability - which is why we can use a separate app to handle link capturing. There are several apps that fit the bill, here's how you do it with [MacroDroid](https://play.google.com/store/apps/details?id=com.arlosoft.macrodroid), a simple but powerful IFTTT-style Android toolkit.

Here's how I set it up:

1. Open MacroDroid and create a new Macro
2. Set the Trigger to `Text Shared to MacroDroid` (optionally filter with regex `^http.*` to only capture URLs)
3. Add the Action `Write to File`
4. For `Filename`, locate your Obsidian vault and choose your input file
5. For `Enter text`, use `- [ ] [{shared_text_subject}]({shared_text})\n` — MacroDroid will replace `{shared_text_subject}` with the page title and `{shared_text}` with the URL
6. Choose `Prepend to file` so newest links appear at the top
7. Save the Macro and share a link to MacroDroid (not Obsidian!)

Give it a go - here's how the same list would look now:

> - [ ] [Inside OpenAI's in-house data agent](https://openai.com/index/inside-our-in-house-data-agent/)
> - [x] [Simon Willison on Technical Blogging - by Cynthia Dunlop](https://writethatblog.substack.com/p/simon-willison-on-technical-blogging)
> - [x] [Things That Aren't Doing the Thing](https://strangestloop.io/essays/things-that-arent-doing-the-thing)

Much better! There's plenty more we could do here (tags, archives, cleanup macros), but personally I'm quite happy with this for now. In the spirit of [aggressive self-awareness](/posts/workflow-awareness/) - these are problems I don't have yet.