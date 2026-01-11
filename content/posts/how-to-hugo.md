---
title: "Set Up Your Hugo + GitHub Blog In 5 Minutes"
date: 2026-01-11T03:47:48+02:00
draft: false
tags: ["hugo", "automation", "ai", "tutorial"]
summary: "A guide to setting up a Hugo/GitHub blog and automating it with AI agents."
---

I literally done this an hour ago, so might as well document my learning for future generations!

#### **1. Core Prerequisites**

Open a terminal, install `hugo`

```bash
brew install hugo
```

Also, make sure you have a GitHub account!

#### **2. Initialize the Project**

Create the directory structure and initialize the repository. Replace `my-blog` with a better name.

```bash
hugo new site my-blog
cd my-blog
git init
```

#### **3. Theme Installation**

Pick a hugo theme - I use PaperMode:

```bash
git clone --depth=1 https://github.com/adityatelange/hugo-PaperMod themes/PaperMod
echo 'theme = "PaperMod"' >> hugo.toml
```

#### **4. Basic Config**

Update `hugo.toml` with your specific details.

* **baseURL**: `https://[your-github-username].github.io/`
* **theme**: `PaperMod`

#### **5. Deployment Automation (GitHub Actions)**

1. `mkdir -p .github/workflows`
2. `touch .github/workflows/hugo.yaml`
3. Paste the official [Hugo GitHub Action YAML](https://gohugo.io/host-and-deploy/host-on-github-pages/#step-4) into the file.
4. Navigate to **Settings > Pages** on GitHub.
5. Change **Build and deployment > Source** to **"GitHub Actions"**.

---

### Bonus: AI!

To minimize manual overhead, use an LLM agent (like Claude Code) to handle metadata and maintenance.

Instead of manually writing front matter, prompt the agent:

> "Review `content/posts/new-post.md`. Generate a 2-sentence summary for the `description` field and suggest 5 relevant `tags` based on the content. Update the file front matter directly."

> "Read `README.md` from [insert favorite project here] repo and my last three blog posts. Update `content/about.md` to reflect my current focus."

Use the agent as a CI gatekeeper before you push:

> "Check all files in `content/posts/`. Ensure `draft` is set to `false` for completed posts, verify all internal links work, and ensure images are correctly referenced in the `/static` folder. If everything is correct, commit with the message 'Release: [Post Title]' and push to main."

Or even better, create a CLAUDE.md file for your blog repo and let it roll:

```markdown
# Project Rules
- Always use PaperMod-compatible front matter.
- Tags should be lowercase.
- Summaries should be under 160 characters for SEO.
- Run `hugo server` to validate builds before suggesting a push.
```

Happy blogging :)
