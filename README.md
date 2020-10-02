# Crash Course: Docs-as-Code

This repo contains an HTML5 template called [Stellar](https://html5up.net/stellar), built by [ajlkn](https://github.com/ajlkn/responsive-tools). We'll use this template as a stand-in for our project source code while learning a docs-as-code workflow.  

## Docs-as-code setup

- git
- A github.com account
- A text editor
- Command line terminal
- Hugo

We'll use Markdown to write documentation content. We'll also use the [gh-pages branch](https://gohugo.io/hosting-and-deployment/hosting-on-github/#deployment-of-project-pages-from-your-gh-pages-branch) to deploy the docs site to GitHub Project Pages. 

Having `gh-pages` as the source branch for GitHub Pages (separate from your main or other feature branches) allows you to keep your generate pages as well as docs site deployment history completely clean and separate from your "regular" app source code. You could also choose to keep the generated site pages (and commits) in the same main branch -- this probably just comes down to your preference.

## How to use this repository

This has been marked as a ["template" repository](https://docs.github.com/en/free-pro-team@latest/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template). 

1. Fork the repository
2. Clone the fork locally on your machine (copy the `main` branch **only**)
3. Build out the Hugo site/project within the repository
4. Commit changes to source code and push as desired
5. When ready to publish documentation, carry out a Hugo site build and push built pages up to fork on the gh-pages branch

A step-by-step guide for building the docs site is provided in the [crash-course.md](./crash-course.md) file.

## Resources

- [git worktree](https://git-scm.com/docs/git-worktree)
- [git submodule](https://www.git-scm.com/book/en/v2/Git-Tools-Submodules)