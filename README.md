# motlabs.github.io

📚 [GitHub Pages](https://pages.github.com/) powered [motlabs](https://github.com/motlabs) Blog, with [Jekyll](http://jekyllrb.com) and [Poole](http://getpoole.com) based [Lanyon](https://github.com/poole/lanyon)


## Getting Started (on MacOS)

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
```
Note that gem may require ruby version update.
```bash
workspace$ \curl -sSL https://get.rvm.io | bash -s stable
workspace$ rvm install ruby-2.x.x
workspace$ rvm use ruby-2.x.x --default
```

#### 4. Clone Repository

```bash
workspace$ git clone https://github.com/motlabs/motlabs.github.io
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

1. Create `YYYY-MM-DD-Your-Blog-Title.md` under `_posts/`

2. Write, save, and check on [http://127.0.0.1:4000](http://127.0.0.1:4000)

3. Create new feature branch, commit, push and send PR

4. After PR Review, post will be merged into `master` branch

5. [Jekyll](http://jekyllrb.com) will automatically compile blog into [https://motlabs.github.io/](https://motlabs.github.io/)

## Troubleshooting

Buy @jwkanggist a cup of coffee and everything will be fine 🎉

---

## [Lanyon](https://github.com/poole/lanyon) License

Take a closer look later

> Open sourced under the [MIT license](LICENSE.md).
>
> <3
