# How to Host a Resume on GitHub Pages Using Pelican and Markdown

## Purpose

This README describes how to format a resume using Markdown,
generate a static website using Pelican, and host it for free
using Git and GitHub Pages. It is written for anyone with basic
computer skills and some familiarity with the command line —
no prior experience with web development or version control
is required.

---
## Prerequisites

Before you begin, make sure you have the following:

- **A computer** running macOS, Windows, or Linux
- **A GitHub account** — sign up for free at [github.com](https://github.com)
- **Python 3** installed on your computer
  - To check, open your terminal and type: `python --version`
  - If not installed, download it from [python.org](https://www.python.org)
- **Git** installed on your computer
  - To check, type: `git --version`
  - If not installed, download it from [git-scm.com](https://git-scm.com)
- **Pelican and Markdown** — installed via Python's package manager:
```
  pip install pelican[markdown]
```
- **A text editor** — such as VS Code, Notepad++, or any editor you prefer
- **A resume** — your resume content ready to be formatted

> **Note:** Basic familiarity with opening a terminal and running 
> simple commands (like changing directories) is helpful but 
> all commands are explained as you go.

---
## Instructions

### Phase 1: Format Your Resume in Markdown

According to Etter, lightweight markup languages like Markdown are 
superior to tools like Microsoft Word for documentation because they 
are free, human-readable, and work seamlessly with version control systems.

1. Create a folder on your computer for your project.
2. Inside the folder, create a subfolder called `content`, and inside 
   that, another subfolder called `pages`.
3. Create a new file called `resume.md` inside `content/pages/`.
4. Open `resume.md` in your text editor.
5. Add the following metadata at the very top of the file:
```
   Title: Resume
   Date: 2024-01-01
```
6. Write your resume content below the metadata using Markdown formatting:
   - Use `#` for your name (largest heading)
   - Use `##` for section titles like EDUCATION and SKILLS
   - Use `###` for sub-items like a degree or job title
   - Use `-` at the start of a line for bullet points
   - Use `**text**` to make text bold
   - Use `*text*` to make text italic

---

### Phase 2: Set Up and Build Your Site with Pelican

Etter recommends static websites for documentation because they are 
fast, portable, and require no server-side dependencies. Pelican is a 
static site generator that converts your Markdown files into a fully 
functional website.

1. Open your terminal and navigate to your project folder:
```
   cd path/to/your/project
```
2. Run Pelican's setup wizard:
```
   pelican-quickstart
```
3. Answer the prompts as follows:
   - Site title → your name
   - Author → your name
   - URL prefix → leave blank for now
   - All other options → press Enter to accept defaults
4. Open the file `pelicanconf.py` in your text editor.
5. Set your site URL by finding and updating this line:
```
   SITEURL = "https://yourusername.github.io/your-repo-name"
```
6. Add the following lines to clean up the default settings:
```
   LINKS = ()
   SOCIAL = ()
   RELATIVE_URLS = True
   DISPLAY_PAGES_ON_MENU = False
```
7. Save `pelicanconf.py`.
8. Build your site by running:
```
   pelican content
```
9. Preview your site locally by running:
```
   pelican --listen
```
10. Open your browser and go to `http://localhost:8000` to confirm 
    your resume appears correctly.

---

### Phase 3: Track Your Work with Git

Etter strongly recommends distributed version control systems like Git 
because they allow you to track every change, collaborate with others, 
and store your work safely online. Git is the most widely used such 
system in the world.

1. Initialize Git in your project folder:
```
   git init
```
2. Configure your identity:
```
   git config --global user.name "Your Name"
   git config --global user.email "your@email.com"
```
3. Create a `.gitignore` file to exclude generated files:
```
   echo "output/" > .gitignore
   echo "__pycache__/" >> .gitignore
```
4. Stage all your project files:
```
   git add .
```
5. Save your first snapshot with a descriptive message:
```
   git commit -m "Initial commit: add resume site"
```

---

### Phase 4: Publish Your Site on GitHub Pages

Etter highlights GitHub Pages as an ideal hosting solution for static 
websites — it is free, reliable, and integrates directly with Git, 
making publishing as simple as pushing your files.

1. Go to [github.com](https://github.com) and create a new repository.
2. Set the repository to **Public**.
3. Do not initialize the repository with any files.
4. Connect your local project to GitHub by running:
```
   git remote add origin https://github.com/yourusername/your-repo.git
```
5. Rename your branch to main:
```
   git branch -m master main
```
6. Push your source files to GitHub:
```
   git push -u origin main
```
7. Install the publishing tool:
```
   pip install ghp-import
```
8. Publish your built site to the `gh-pages` branch:
```
   ghp-import -m "Publish site" -b gh-pages output
   git push origin gh-pages
```
9. Go to your repository on GitHub → **Settings** → **Pages**.
10. Under **Branch**, select `gh-pages` and click **Save**.
11. Wait 1–2 minutes, then visit your live site at:
    `https://yourusername.github.io/your-repo-name/`

---
## Further Resources

The following resources provide additional background and guidance 
on the tools and concepts used in this guide:

### Markdown
- [Markdown Guide](https://www.markdownguide.org) — A comprehensive 
  reference for Markdown syntax, covering basic and extended formatting
- [CommonMark Tutorial](https://commonmark.org/help/tutorial/) — A 
  beginner-friendly, interactive Markdown tutorial
- [GitHub Flavored Markdown Spec](https://github.github.com/gfm/) — 
  Official documentation for the Markdown variant used on GitHub

### Pelican
- [Pelican Official Documentation](https://docs.getpelican.com) — 
  The complete guide to setting up and customizing Pelican

### Git and GitHub
- [Git Official Documentation](https://git-scm.com/doc) — 
  Comprehensive reference for all Git commands and concepts
- [GitHub Pages Documentation](https://docs.github.com/en/pages) — 
  Official guide to hosting static sites on GitHub Pages

### Further Reading
- [Andrew Etter's *Modern Technical Writing*](https://www.amazon.ca/Modern-Technical-Writing-Introduction-Documentation/dp/1519070616) — 
  The book that informed the principles behind this guide

---
## FAQ

### General Questions

**Why is Markdown better than writing raw HTML?**

Markdown is designed to be human-readable even in its raw form. 
Writing the same content in HTML requires verbose tags that make 
the source file difficult to read and edit. As Etter points out, 
lightweight markup like Markdown dramatically reduces the barrier 
for contributors — anyone can learn it in minutes, whereas HTML 
requires more specialized knowledge. Markdown is also free, works 
with any text editor, and integrates naturally with version control 
systems like Git.

**Why is Markdown better than just writing my resume in Microsoft Word?**

While Word is great for creating a single polished PDF, it is poorly 
suited for documentation that lives online. Word files do not work 
well with version control, its HTML export is unreliable, and it 
requires a paid license. Markdown files are plain text, meaning they 
are lightweight, version-control friendly, and can be converted into 
a fully styled website using a static site generator like Pelican.

### Practical Questions

**I made changes to my resume.md file. Why don't I see the changes 
when I refresh my browser?**

Simply saving your Markdown file is not enough. Pelican must 
re-process your files to regenerate the website. Every time you make 
a change, you need to run:
```
pelican content
```
Then refresh your browser at `http://localhost:8000`. If you have 
already published your site, you also need to run the publish 
commands to update the live version.

**I pushed my changes to GitHub but my live site has not updated. 
What should I do?**

Pushing to the `main` branch only updates your source files — it 
does not update the live site. To update the live site, you need to 
rebuild and republish to the `gh-pages` branch by running:
```
ghp-import -m "Update site" -b gh-pages output
git push origin gh-pages
```
After pushing, wait 1–2 minutes for GitHub Pages to redeploy your 
site before refreshing.

---
## Credits

### Author
- **Anne Debora Niyonkuru** — Wrote and assembled this README and 
  created the resume website documented in this guide.

### Peer Reviewers
- **Gideon** — Provided in-class peer review and feedback
- **William** — Provided in-class peer review and feedback

### Third-Party Content and Tools
- **Pelican** — Static site generator used to build the website.
  [getpelican.com](https://docs.getpelican.com)
- **Flex Theme** — Clean, minimal Pelican theme created by 
  Alexandre Vicenzi, used to style the resume website.
  [github.com/alexandrevicenzi/Flex](https://github.com/alexandrevicenzi/Flex)
  Licensed under the MIT License.
- **GitHub Pages** — Free static website hosting provided by GitHub.
  [pages.github.com](https://pages.github.com)
- **Font Awesome** — Icons used by the Flex theme.
  [fontawesome.com](https://fontawesome.com)

### References
- Etter, Andrew. *Modern Technical Writing: An Introduction to 
  Software Documentation*. Self-published, 2016.
- Pfeiffer, William S. *Technical Communication: A Practical 
  Approach*. Chapter 8: Process Explanations and Instructions.