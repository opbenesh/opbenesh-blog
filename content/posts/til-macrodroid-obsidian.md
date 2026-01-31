---
title: "til: link capturing in obsidian with macrodroid"
date: 2026-01-31T23:43:36+02:00
draft: false
tags: ["obsidian","macrodroid"]
summary: "Easy save-for-later link capturing for Obsidian on Android"
author: "Ben Esh"
---

I'm currently deliberating migrating my personal knowledge base from Notion to Obsidian. I plan to post about this in more details later, but the tl;dr is that these things only work when they're seamless, and the frustratingly slow Notion app is anything but. But while Notion is apparently too powerful for its in good, Obsidian is a basically a Markdown frontend and doesn't natively support a "database"/smart list concept. You could create an `Articles.md` file and use Android's share-to-app feature, but the result will be a simple newline-separated, old-to-new sorted list of URLs:

```
https://strangestloop.io/essays/things-that-arent-doing-the-thing
https://writethatblog.substack.com/p/simon-willison-on-technical-blogging
https://openai.com/index/inside-our-in-house-data-agent/
```

I can immediately think of 3 simple enhancements I'd like to have here:
* Checklist - marking items as Read is a must, the strikeout formatting is a nice bonus
* Reverse order - the current method appends links to the end of the file, but until we add a cleanup/archive method the top will likely contain the least relevant articles
* Link titles - wouldn't it be nice to see the article title instead of the raw URL?
Fortunately, what Obsidian lacks in features, it UNKNOWN in interoperability. Again, local storage markdown frontend. Which is why we can use a separate app to handle link capturing. Here's how you do it with MacroDroid, a simple but powerful IFTTT-style Android toolkit:

1. Create an empty Obsidian file for link-capturing
2. Open MacroDroid
3. Create a new Macro, and configure it as follows:
	1. The Trigger ("when"): `Text Shared to Macrodroid`. I used a dead-simple `^http.*` regex for filtering.
	2. The Action ("what"): `Write to File`.
		1. `Filename`: Locate your Obsidian folder and choose your input file. 
		2. `Enter text`: use `- [ ] [{shared_text_subject}]({shared_text})\n`
		3. Finally, choose `Prepend to file`
	3. Save the new Macro
That's it! Next time you want to save a link, share it to MacroDroid rather than to Obsidian, and watch the magic happens!
Here's how the sample list from above might look like now:

> - [] [Inside OpenAI’s in-house data agent
](https://openai.com/index/inside-our-in-house-data-agent/)
> - [x] [Simon Willison on Technical Blogging - by Cynthia Dunlop](https://writethatblog.substack.com/p/simon-willison-on-technical-blogging)
> - [x] [Things That Aren't Doing the Thing](https://strangestloop.io/essays/things-that-arent-doing-the-thing)