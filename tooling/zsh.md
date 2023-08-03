# Matee Wiki - Tooling - zsh

## Intro
- Since macOS 10.15 (Catalina), zsh is a default shell in Terminal
- There are various configuration files such as `.zshenv` / `.zshrc` / `.zlogin` / `.zprofile`
- TLDR: Use `.zshenv` for things you need in non-interactive shells and `.zshrc` for things you need only in interactive shells

## `.zshenv`
- `.zshenv` is sourced on all invocations of the shell, unless the -f option is set
- It should contain commands to set the command search path, plus other important environment variables
- `.zshenv` should not contain commands that produce output or assume the shell is attached to a tty

## `.zshrc`
- `.zshrc` is sourced in interactive shells
- It should contain commands to set up aliases, functions, options, key bindings, etc.

## `.zlogin`
- `.zlogin` is sourced in login shells
- It should contain commands that should be executed only in login shells
- `.zlogin` is not the place for alias definitions, options, environment variable settings, etc.

## `.zprofile`
- `.zprofile` is similar to `.zlogin`, except that it is sourced before `.zshrc`
- `.zprofile` is meant as an alternative to `.zlogin` for ksh fans
- The two are not intended to be used together although this could certainly be done if desired

## Resources
- https://scriptingosx.com/2019/06/moving-to-zsh/
- https://tanguy.ortolo.eu/blog/article25/shrc
- https://zsh.sourceforge.io/Intro/intro_3.html
