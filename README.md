# motlabs.github.io

📚 [GitHub Pages](https://pages.github.com/) powered [motlabs](https://github.com/motlabs) Blog, with [Jekyll](http://jekyllrb.com) and [Kiko-plus](https://aweekj.github.io/Kiko-plus/)


## Getting Started (on MacOS)
- please contribute installation method for other OS.

#### 1. Install [Homebrew](https://brew.sh/)

```bash
workspace$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

#### 2. Install Ruby

```bash
workspace$ brew install ruby
```

#### 3. Install [Jekyll](https://jekyllrb.com/docs/installation/) and Plugins

```bash
workspace$ sudo gem install jekyll
workspace$ sudo gem install jekyll-paginate
workspace$ sudo gem install jekyll-admin
workspace$ sudo gem install jekyll-seo-tag
```
Note that gem may require ruby version update.
```bash
workspace$ \curl -sSL https://get.rvm.io | bash -s stable
workspace$ rvm install ruby-2.x.x
workspace$ rvm use ruby-2.x.x --default
```

#### 4. Clone Repository

```bash
workspace$ git clone https://github.com/motlabs/motlabs.github.io.git
```

#### 5. Serve

```bash
workspace$ cd motlabs.github.io/
workspace/blog$ jekyll serve
```

```bash
Configuration file: workspace/motlabs.github.io/_config.yml
            Source: workspace/motlabs.github.io
       Destination: workspace/motlabs.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
                    done in 0.408 seconds.
 Auto-regeneration: enabled for 'workspace/motlabs.github.io'
    Server address: http://127.0.0.1:4000
  Server running... press ctrl-c to stop.
```

#### 6. Open [http://127.0.0.1:4000](http://127.0.0.1:4000) to see what happens!

## New Blog Post with [typora.io](https://typora.io)

```
[For the first time] 
1. Sign up `https://ko.gravatar.com/` and fill up you profile.
2. Upload your profile image.
3. Generate your Hash code from your email address by http://www.miraclesalad.com/webtools/md5.php
4. Open _config.yml, fill up your author information
5. Send pull request to the master branch.
```
1. Create `YYYY-MM-DD-Your-Blog-Title.md` under `_posts/`

2. Write, save, and check on [http://127.0.0.1:4000](http://127.0.0.1:4000)

3. Create new feature branch from `develop`, commit, push and send PR to `develop`

4. After PR Review and final checking, post will be merged into `master` branch

5. [Jekyll](http://jekyllrb.com) will automatically compile blog into [https://motlabs.github.io/](https://motlabs.github.io/)

## Troubleshooting

Buy @jwkanggist a cup of coffee and everything will be fine 🎉

---

## [Kiko-plus](https://aweekj.github.io/Kiko-plus/) License

Take a closer look later

> Open sourced under the [Apache License 2.0](LICENSE.md).
>
> <3
