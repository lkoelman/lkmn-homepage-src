# GitHub Pages Documentation

https://guides.github.com/features/pages/


--------------------------------------------------------------------------------
# Hugo

## Documentation

https://gohugo.io/documentation/

## GitHub Pages support

https://gohugo.io/hosting-and-deployment/hosting-on-github/

```sh
# First create the remote repositories
# - github.com/username/mysite-src.git
# - github.com/username/username.github.io

# Initialize static files repository
mkdir mysite-static mysite-src && cd mysite-static
git init .
echo "# mysite.github.io" >> README.md && git add . && git commit -m "Initial commit"
git remote add origin https://github.com/lkoelman/lkoelman.github.io.git
git push -u origin master

# Initialize source repository
cd ../mysite-src
git init .

# Create submodule for static files (build outputs) in directory 'public'
git submodule add -b master https://github.com/username/username.github.io.git public
# Create submodule for the theme you are using in themes/theme-name
git submodule add https://github.com/matcornic/hugo-theme-learn.git themes/hugo-theme-learn
# Make sure it is up to date
git submodule update

# Build your site and inspect it
hugo && hugo serve

# Push source repository
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/username/mysite-src.git
git push -u origin master

# Push static files repository
cd public
git add .
git commit -m "Initial site build"
git push origin master
```

## Customizing structure

TODO, also see theme's README


## Customizing Look

- clone a theme in the `themes/` directory of your site
- use the theme
    + just for one run: `hugo server -t theme-name`
    + when building site: `hugo -t theme-name`
    + permanently: add `theme: theme-name` to `config.toml`

## Quick Start

```sh
hugo new site my-site
cd my-site

# install a theme by cloning it into /themes
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
hugo -t theme-name

# Create a page
hugo new posts/my-post.md # path relative to content/

# Build website and serve it
hugo server

# Deploy to GitHub. Pushes built website (contents of output/)
# to GITHUB_DEPLOY_BRANCH and source to GITHUB_SOURCE_BRANCH in conf.py
nikola github_deploy
```

[1]: https://getnikola.com/handbook.html#customizing-your-site
[2]: https://getnikola.com/handbook.html#getting-extra-themes

## Theme: hugo-theme-learn

[theme homepage with example site and config](https://github.com/matcornic/hugo-theme-learn)