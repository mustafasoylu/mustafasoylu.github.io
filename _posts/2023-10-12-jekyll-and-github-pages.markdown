---
# layout: post
title: "Jekyll and GitHub Pages"
date: 2023-10-12 13:44:31 +0200
categories: posts
---

## Install ruby and jekyll to local user

Install environment manager for ruby, rbenv. It is pyenv equivalent of pyenv.

```bash
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
source ~/.bashrc

git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
# install the latest version
rbenv install 3.2.2
rbenv global 3.2.2
```

Install bundler and jekyll libraries.

```bash
gem install bundler
gem install jekyll
```

## Create a repository

Create a repository named your_github_username.github.io

## Create a jekyll project and connect to github

```bash
jekyll new github-page
cd github-page
git init
git add .
git commit -m "initial commit"
```

Add github as remote repository.

```bash
git remote add origin https://github.com/mustafasoylu/mustafasoylu.github.io.git
git branch -M main
git push -u origin main
```

## Update Gemfile

1. Open `Gemfile` file.
2. Comment out line with `gem "jekyll", "~> 4.3.2"` using #.
3. Add below line to next line in `Gemfile.` 228 is current [GITHUB-PAGES-VERSION](https://pages.github.com/versions/)

```Gemfile
gem "github-pages", "~> GITHUB-PAGES-VERSION", group: :jekyll_plugins
```

4. Save and close `Gemfile` file.
5. Run `bundle install` in terminal.
6. Run `bundle add webrick` to try the code on your local machine.

## Run you local server

Run `bundle exec jekyll serve` to see your pages.
You can update index.md and about.md, commit and push them to the repository.

## Serve in GitHub Pages

Before doing anything, GitHub pages settings were done automatically for me. If it does not work, you can check [here](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site) to have correct settings.

## Use modernist theme

1. Add bundle for remote-theme with `bundle add jekyll-remote-theme`.
2. Add below lines to `_config.yml` file. If there is a `theme` line, comment it out. If plugins line exists, add `jekyll-remote-theme` to the list.

```yaml
# Build settings
# theme: minima
remote_theme: pages-themes/modernist
plugins:
  - jekyll-remote-theme
```

3. Comment out or delete layout lines in any markdown file's in the front matter.

```yaml
---
# layout: home
title: Home
permalink: /
---
```
