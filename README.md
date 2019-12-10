# Laptop

Laptop is a script to set up a macOS laptop for web and mobile development.

It can be run multiple times on the same machine safely.
It installs, upgrades, or skips packages
based on what is already installed on the machine.

## Requirements

We support:

- macOS Mavericks (10.9)
- macOS Yosemite (10.10)
- macOS El Capitan (10.11)
- macOS Sierra (10.12)
- macOS High Sierra (10.13)
- macOS Mojave (10.14)

Older versions may work but aren't regularly tested.
Bug reports for older versions are welcome.

## Install

Download the script:

```sh
curl -o- -L https://raw.githubusercontent.com/adhawk/dev-machine/master/install | bash
```

## What it sets up

macOS tools:

- [Homebrew] for managing operating system libraries.

[homebrew]: http://brew.sh/

Unix tools:

- [Universal Ctags] for indexing files for vim tab completion
- [Git] for version control
- [The Silver Searcher] for finding things in files
- [Watchman] for watching for filesystem events
- [Zsh] as your shell

[universal ctags]: https://ctags.io/
[git]: https://git-scm.com/
[ripgrep]: https://github.com/BurntSushi/ripgrep
[watchman]: https://facebook.github.io/watchman/
[zsh]: http://www.zsh.org/

GitHub tools:

- [Hub] for interacting with the GitHub API

[hub]: http://hub.github.com/

Image tools:

- [ImageMagick] for cropping and resizing images

Programming languages, package managers, and configuration:

- [ASDF] for managing programming language versions
- [Bundler] for managing Ruby libraries
- [Node.js] and [NPM], for running apps and installing JavaScript packages
- [Ruby] stable for writing general-purpose code
- [Yarn] for managing JavaScript packages

[bundler]: http://bundler.io/
[imagemagick]: http://www.imagemagick.org/
[node.js]: http://nodejs.org/
[npm]: https://www.npmjs.org/
[asdf]: https://github.com/asdf-vm/asdf
[ruby]: https://www.ruby-lang.org/en/
[yarn]: https://yarnpkg.com/en/

It should take less than 15 minutes to install (depends on your machine).

## Customize in `~/.laptop.local`

Your `~/.laptop.local` is run at the end of the Laptop script.
Put your customizations there.
For example:

```sh
#!/bin/sh

brew bundle --file=- <<EOF
brew "go"
EOF

fancy_echo "Cleaning up old Homebrew formulae ..."
brew cleanup
brew cask cleanup
```

Write your customizations such that they can be run safely more than once.
See the `mac` script for examples.

Laptop functions such as `fancy_echo` and
`gem_install_or_update`
can be used in your `~/.laptop.local`.

## Contributing

Edit the `mac` file.
Document in the `README.md` file.
Follow shell style guidelines by using [ShellCheck] and [Syntastic].

```sh
brew install shellcheck
```

[shellcheck]: http://www.shellcheck.net/about.html
