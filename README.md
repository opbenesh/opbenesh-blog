# opbenesh-blog

A personal blog built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

## 🚀 Built With

- **Static Site Generator:** [Hugo](https://gohugo.io/)
- **Theme:** [PaperMod](https://github.com/adityatelange/hugo-PaperMod)

## 🛠️ Getting Started

To get a local copy up and running, follow these simple steps.

### Prerequisites

- **Hugo:** You need to have Hugo installed (Extended version recommended).
  - macOS: `brew install hugo`
  - Linux: `sudo snap install hugo`
  - Windows: `choco install hugo-extended`

### Installation

1.  Clone the repository:
    ```bash
    git clone --recurse-submodules https://github.com/opbenesh/opbenesh-blog.git
    cd opbenesh-blog
    ```
    *Note: The `--recurse-submodules` flag is important to download the theme.*

2.  If you already cloned without submodules:
    ```bash
    git submodule update --init --recursive
    ```

## 💻 Usage

### Run Local Server

To start the development server with live reload:

```bash
hugo server -D
```

Navigate to `http://localhost:1313/` in your browser.

### Create a New Post

To create a new markdown file for a blog post:

```bash
hugo new posts/my-new-post.md
```

This will create a new file in `content/posts/` with the default frontmatter.

### Build for Production

To build the static site (generates files in `public/`):

```bash
hugo
```

## 📂 Project Structure

- `content/`: Markdown files for your pages and posts.
- `themes/`: Contains the PaperMod theme submodule.
- `static/`: Static assets (images, CSS, JS) that are copied directly to the build.
- `layouts/`: Custom HTML layouts to override the theme.
- `hugo.toml`: Main project configuration file.
