---
title: "Set Your Hugo + GitHub Blog In 5 Minutes"
date: 2026-01-11T03:47:48+02:00
draft: false
tags: ["hugo", "automation", "ai", "tutorial"]
summary: "I literally did this an hour ago—here is how to set up a Hugo blog with PaperMod and delegate the maintenance to AI agents."
---

I literally done this an hour ago, so might as well document my learning for future generations!

#### **1. Core Prerequisites**

Open a terminal, install `hugo` and the GitHub CLI (`gh`):
```bash
brew install hugo gh
```

**Authenticate with GitHub**:
```bash
gh auth login
```

#### **2. Initialize and Link**

Create the directory structure, initialize Git, and **link it to GitHub**. 

> [!TIP]
> If you want your blog at the root (e.g., `username.github.io`), name your repository `[your-username].github.io`. Otherwise, name it `my-blog`.

```bash
hugo new site my-blog
cd my-blog
git init

# Link it to your GitHub account
gh repo create my-blog --public --source=. --remote=origin
```

#### **3. Theme Installation**

Pick a hugo theme - I use PaperMod:

```bash
git submodule add https://github.com/adityatelange/hugo-PaperMod themes/PaperMod
echo 'theme = "PaperMod"' >> hugo.toml
```

#### **4. Basic Config**

Update `hugo.toml` with your specific details. 

> [!CAUTION]
> **The baseURL must match your repository path.** If your repo is named `my-blog`, your baseURL must be `https://[username].github.io/my-blog/`. If you miss the subpath, your CSS will break and the site will look like raw text.

* **baseURL**: `https://[your-github-username].github.io/my-blog/`
* **theme**: `PaperMod`

#### **5. Create Your First Post (The "Draft" Trap)**

Hugo won't show anything unless there is content, and it won't publish anything marked as a draft.

```bash
# Create the file
hugo new posts/my-first-post.md
```

Open that file and change `draft: true` to **`draft: false`**. If you forget this, your site will be empty after deployment!

#### **6. Final Push**

Now that everything is configured and you have your first post, push it to GitHub:

```bash
git add .
git commit -m "Initial commit: Setup Hugo with first post"
git branch -M main
git push -u origin main
```

#### **7. Deployment Automation (GitHub Actions)**

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

---

Feel free to check out my vendor-independent [AGENTS.md](https://github.com/opbenesh/opbenesh-blog/blob/main/AGENTS.md) file!
