---
title: "setup your Hugo + GitHub blog in 5 minutes"
date: 2026-01-11T03:47:48+02:00
draft: false
tags: ["hugo", "automation", "ai", "tutorial"]
summary: "I literally did this an hour ago—here is how to set up a Hugo blog with PaperMod and delegate the maintenance to AI agents."
author: "Ben Esh"
---

I literally did this for myself an hour ago, so might as well document my learning for future generations!

## 1. Core prerequisites

Open a terminal, install `hugo` and the GitHub CLI (`gh`):
```bash
brew install hugo gh
```

**Authenticate with GitHub**:
```bash
gh auth login
```

## 2. Initialize and link

Create the directory structure, initialize Git, and **link it to GitHub**.

```bash
# replace [github-username] with your GitHub username
hugo new site [github-username].github.io
cd [github-username].github.io
git init

# Create the repo on GitHub
gh repo create [your-username].github.io --public --source=. --remote=origin
```

## 3. Theme installation

Pick a hugo theme - I use PaperMod:

```bash
git submodule add https://github.com/adityatelange/hugo-PaperMod themes/PaperMod
echo 'theme = "PaperMod"' >> hugo.toml
```

## 4. Basic config

Update `hugo.toml` with your specific details.

*   **baseURL**: `https://[github-username].github.io/`
*   **theme**: `PaperMod`

## 5. Create your first post

```bash
hugo new posts/my-first-post.md
```

## 6. Local preview

Before pushing, it's always good to see how it looks:
```bash
hugo server -D
```
Open `http://localhost:1313` to preview your site. The `-D` flag tells Hugo to include drafts.

## 7. Final push

Now that everything is configured and you have your first post, push it to GitHub:

```bash
git add .
git commit -m "Initial commit: Setup Hugo with first post"
git branch -M main
git push -u origin main
```

## 8. Deployment automation (GitHub Actions)

1.  `mkdir -p .github/workflows`
2.  `touch .github/workflows/hugo.yaml`
3.  Paste the official [Hugo GitHub Action YAML](https://gohugo.io/host-and-deploy/host-on-github-pages/#step-4) into the file.
4.  Navigate to **Settings > Pages** on GitHub.
5.  Change **Build and deployment > Source** to **"GitHub Actions"**.

That's it - you can now interact with your git repo using your favourite local/web IDE. GitHub will automatically publish a new version whenever you `git push`.

---

## Bonus: AI

Since the whole setup is Markdown-based, you can easily use a coding agent for metadata and maintenance. For example, instead of manually writing front matter, prompt the agent to:

> "Review `content/posts/new-post.md`. Generate a 2-sentence summary for the `description` field and suggest 5 relevant `tags` based on the content. Update the file front matter directly."

> "Check all files in `content/posts/`. Ensure `draft` is set to `false` for completed posts, verify all internal links work, and ensure images are correctly referenced in the `/static` folder."

Or even better, create an `AGENTS.md` file for your blog repo and let it roll:

```markdown
# Project Rules
- Always use PaperMod-compatible front matter.
- Tags should be lowercase.
- Summaries should be under 160 characters for SEO.
- Run `hugo server` to validate builds before suggesting a push.
```

Feel free to check out mine [here!](https://github.com/opbenesh/opbenesh.github.io/blob/main/AGENTS.md)

Happy blogging :)

