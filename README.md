# Readme

This repository should outline a minimal example with [rails 6.1](https://github.com/rails/rails) and
[refinerycms](https://github.com/refinery/refinerycms), which fails while reloading code (in development).

It is a fresh rails project initialized with `rails _6.1.7.2_ new .`. RefineryCMS has been added to the Gemfile:

```Gemfile
# …

gem 'refinerycms', github: 'refinery/refinerycms'
```

To trigger the error, load/use the `Refinery::Page` class, reload and load the class again:

```sh
echo 'Refinery::Page; reload!; Refinery::Page' | rails c
# >
# Running via Spring preloader in process 408055
# Loading development environment (Rails 6.1.7.2)
# Switch to inspect mode.
# Refinery::Page; reload!; Refinery::Page
# Reloading...
# ~/.asdf/installs/ruby/3.2.0/lib/ruby/gems/3.2.0/bundler/gems/refinerycms-aee49a603860/pages/lib/refinery/pages/finder.rb:62:in `<module:Pages>': superclass mismatch for class FinderByTitle (TypeError)
```
