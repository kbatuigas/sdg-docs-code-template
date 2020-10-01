## Setup

1. Navigate to template at [https://github.com/kbatuigas/sdg-docs-code-template](https://github.com/kbatuigas/sdg-docs-code-template)
2. Click "Fork"
3. Using the command line, clone the fork
```
git clone https://github.com/kbatuigas/sdg-docs-code-template.git
```
4. Add your fork as a remote
```
git remote add origin https://github.com/kbatuigas/sdg-course-docs-code.git
```

For the sake of a simple demo, these steps assume that you're doing all development work (including docs writing) on the `main` branch. You can try creating a feature branch if you like.

## Create a new Hugo site

1. Run this command within the _root_ directory of your local project:  
```
hugo new site docs
```  

This creates a new `docs` directory in your project code. `docs` will contain the "skeleton" of a new Hugo site (i.e. there is no content yet)  

2. Navigate to `docs`
```
cd docs
```
3. Add this to version history

```
git commit -m "Add Hugo site"
```
4. Add some content
    - In `docs`, run:
    ```
    hugo new get-started/index.md
    ```
    - Modify the .md file as desired
    - What happens if you run `hugo server -D`?
5. Add the [DocDock theme](https://docdock.netlify.app/)
```
git submodule add https://github.com/vjeantet/hugo-theme-docdock.git themes/docdock
```
6. Initialize the submodule
```
git submodule init
git submodule update
```
7. Add the theme to your site by adding this line to the `config.toml` file:
```
theme = "docdock"
```

You should now have a very basic site that you can view locally by running `hugo server`.

8. Push these changes to your remote fork
```
git push origin main
```

## Deploy to GitHub Pages

1. In `config.toml`, change the baseURL value to the URL of your project page, and make sure to save this with a commit.

    What happens if your value looks like this?: `<USERNAME>.github.io/<PROJECT>/`

2. When you're happy with how the site looks locally, do a build:
```
hugo
```
    
This creates a `public` directory that contains the generated static files for your docs site.
3. Add `public` to `.gitignore`
```
echo "public" >> .gitignore
```
4. Create a new orphan branch called `gh-pages`
```
git checkout --orphan gh-pages
git reset --hard
git commit --allow-empty -m "Init gh-pages branch"
```
5. Push `gh-pages` branch up to your remote fork
```
git push origin gh-pages
```
6. Check your fork GitHub pages settings. The Source should be set to the `gh-pages` branch and it should also provide the URL for your project pages.

7. Return to the `main` branch and add a worktree

```
git checkout main
rm -rf public
git worktree add -B gh-pages public origin/gh-pages
```
This will essentially remove your Hugo builds from your `main` branch and get the build history saved on the `gh-pages` branch instead.

8. Regenerate the site by running `hugo`
9. Push build up to remote fork:

cd public
git add --all
git commit -m "Publish and deploy"
git push origin gh-pages

Your project pages should be live in a short while at the URL provided in your remote Settings.

## When you want to update the published docs

1. Remove worktree
```
git checkout main
git worktree prune
```
2. Commit desired updates in `main` and push up to remote.
3. Add the worktree with the `gh-pages` branch again for the `public` subdirectory.
4. Remove contents of `public` and regenerate the site by doing a new build
```
rm -rf public
hugo
```
5. Switch to `gh-pages` branch, commit the new build, then push to remote
```
git checkout gh-pages 
git add --all
git commit -m "Build and deploy"
git push origin gh-pages
```