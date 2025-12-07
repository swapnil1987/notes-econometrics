# Step-by-Step Setup Guide

Follow these steps to get your econometrics book online with GitHub Pages.

## Part 1: Install Required Software

### 1. Install Quarto

**Windows:**
- Download from https://quarto.org/docs/get-started/
- Run the installer
- Verify: Open terminal and type `quarto --version`

**Mac:**
```bash
brew install quarto
```

**Linux:**
```bash
# Download the .deb file from quarto.org
sudo dpkg -i quarto-*.deb
```

### 2. Install Python

- Download from https://python.org (3.8 or later)
- Or use Anaconda: https://anaconda.com

### 3. Install VS Code

- Download from https://code.visualstudio.com/
- Install the Quarto extension (search "Quarto" in Extensions)

### 4. Install Git

**Windows:**
- Download from https://git-scm.com/

**Mac:**
```bash
brew install git
```

**Linux:**
```bash
sudo apt-get install git
```

## Part 2: Set Up Your Book Locally

### 1. Extract the Template

Extract the `econometrics-book` folder to your desired location (e.g., `Documents/`).

### 2. Open in VS Code

- Open VS Code
- File → Open Folder → Select `econometrics-book`

### 3. Install Python Packages

Open terminal in VS Code (Terminal → New Terminal):

```bash
pip install -r requirements.txt
```

### 4. Preview Your Book

```bash
quarto preview
```

Your browser will open showing the book. Leave this running!

### 5. Make Your First Edit

- Open `_quarto.yml`
- Change `author: "Your Name"` to your actual name
- Change `repo-url` to your future GitHub URL
- Save the file
- Browser will auto-refresh!

## Part 3: Publish to GitHub

### 1. Create GitHub Account

If you don't have one: https://github.com/signup

### 2. Create New Repository

- Click the "+" in top-right → "New repository"
- Name: `econometrics-book` (or your choice)
- Set to **Public**
- Do NOT initialize with README (we already have one)
- Click "Create repository"

### 3. Update Your Book Configuration

In `_quarto.yml`, update line 22:
```yaml
repo-url: https://github.com/YOUR-USERNAME/econometrics-book
```

Replace `YOUR-USERNAME` with your actual GitHub username.

### 4. Initialize Git and Push

In VS Code terminal:

```bash
# Configure git (first time only)
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Initialize repository
git init
git add .
git commit -m "Initial commit: Econometrics book"

# Connect to GitHub (replace YOUR-USERNAME)
git remote add origin https://github.com/YOUR-USERNAME/econometrics-book.git

# Push to GitHub
git branch -M main
git push -u origin main
```

You may be asked to authenticate with GitHub.

### 5. Enable GitHub Pages

- Go to your repository on GitHub
- Settings → Pages (left sidebar)
- Under "Source", select: **GitHub Actions**
- Click Save

### 6. Wait for Deployment

- Click "Actions" tab in your repository
- You'll see "Publish Quarto Book" running
- Wait 2-3 minutes for completion (green checkmark)
- Your book is now live!

### 7. Visit Your Book

Go to: `https://YOUR-USERNAME.github.io/econometrics-book/`

🎉 **Congratulations!** Your book is online!

## Part 4: Daily Workflow

### Writing Content

1. Open VS Code
2. Run `quarto preview` in terminal (if not already running)
3. Edit `.qmd` files
4. See changes instantly in browser

### Publishing Updates

When ready to publish:

```bash
git add .
git commit -m "Describe your changes"
git push
```

Wait 2-3 minutes, then refresh your website. Done!

## Common Commands Reference

```bash
# Preview book locally
quarto preview

# Render without preview
quarto render

# Check status
git status

# See what changed
git diff

# Publish changes
git add .
git commit -m "Your message"
git push
```

## Troubleshooting

### Preview not working?
```bash
quarto check
```

### Python packages missing?
```bash
pip install -r requirements.txt
```

### Git authentication issues?
- Use GitHub's personal access token
- Or set up SSH keys: https://docs.github.com/en/authentication

### Build failing on GitHub?
- Check "Actions" tab for error messages
- Common: Python package missing → Add to `requirements.txt`

## Next Steps

1. Customize `index.qmd` with your course information
2. Fill in the placeholder chapters
3. Add your own chapters in `chapters/` folder
4. Update `_quarto.yml` to include new chapters
5. Add references to `references.bib`

## Getting Help

- Quarto docs: https://quarto.org/docs/books/
- Quarto community: https://github.com/quarto-dev/quarto-cli/discussions
- GitHub Pages: https://docs.github.com/en/pages

---

**Need help?** Create an issue on your GitHub repository!
