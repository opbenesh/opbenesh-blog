# AGENTS.md

## Important Guidelines

- **IMPORTANT**: Whenever you discover something that you didn't know about this environment, about referenced APIs or used tools, append it to `AGENTS.md`.
- **IMPORTANT**: Please maintain the `README.md` file after any significant changes to ensure documentation stays synchronized with the content.
- **IMPORTANT**: Commit changes after completing major features or refactoring steps to ensure work is backed up and synchronized.
## Automation Workflows

### Automate Metadata & Tags
- **Prompt**: "Review `content/posts/new-post.md`. Generate a 2-sentence summary for the description field and suggest 5 relevant tags based on the content. Update the file front matter directly."

### Automate the "About" Page
- **Prompt**: "Read `README.md` from my Spotify Tracker repo and my last three blog posts. Update `content/about.md` to reflect my current focus on metal music and mobile development."

### Pre-Flight Review & Post
- **Prompt**: "Check all files in `content/posts/`. Ensure `draft` is set to `false` for completed posts, verify all internal links work, and ensure images are correctly referenced in the `/static` folder. If everything is correct, commit with the message 'Release: [Post Title]' and push to `main`."

## Project Rules
- **Themes & Plugins**: Always use `git submodule add` for external themes/dependencies.
- **GitHub Tasks**: Prefer the `gh` CLI for repo-level management (linking, actions, creating repos).
- **Front Matter**: Always use PaperMod-compatible front matter.
- **Metadata**: Tags must be lowercase; summaries should be < 160 chars for SEO.
- **Validation**: Run `hugo server` or check for build errors before pushing.
- **Pre-Push Check**: Ensure `draft` is set to `false` for published posts and all internal links/images are verified.

## Cover Image Design Principles

All blog post cover images should follow this consistent visual style:

### Technical Specifications
- **Dimensions**: 1200x300px (4:1 aspect ratio banner format)
- **Background**: Dark (#0a0a0a / nearly black)
- **Primary Color**: Neon green (#00ff88 / rgb(0, 255, 136))
- **File Format**: PNG
- **Location**: Page bundle (`content/posts/[post-name]/cover.png`)

### Design Guidelines
- **Layout**: Icon(s) on left side (starting ~80px from left edge), bold title text starting ~280px from left
- **Icons**: Simple geometric shapes representing the post topic (satellite dish for doom-coding, gopher for Hugo, etc.)
- **Typography**: Large, bold sans-serif font (~100pt), neon green color
- **Style**: Minimalist, clean, modern aesthetic with strong contrast
- **Consistency**: All covers should feel like part of the same brand family

### Front Matter Configuration
```toml
[cover]
image = "cover.png"
alt = "[Descriptive alt text]"
relative = true
```

### Creation Tips
- Use simple geometric primitives (circles, triangles, rectangles) for icons
- Keep icons outlined (stroke only) rather than filled for consistency
- Text should be concise (2-4 words max) and clearly readable
- Maintain ~8-10px stroke width for icon outlines
- Test visibility on both light and dark backgrounds (though primarily viewed on dark)

#### Discoveries
- **Images**: Prefer Page Bundles (matching the `index.md` location) or the `assets` folder for blog images to support Hugo's image processing, though the `/static` folder remains the default for raw assets.
