# dit

### Aliases for common tools, making them easier to use in a consistent way to increaese productivity.

Dit is a just shell script that glues development tools together by allowing short-hand and/or squashed commands to save time and increase productivity. Using docker containers means you don't need to worry about dependencies and can get on with coding 💻 

## Installation

### Pre-requisites

- Docker
- Git

### Homebrew
```sh
brew install abnegate/repo/dit
```

## Core Tools

- [Docker](https://docker.com)
- [Git](https://git-scm.com)

### Secondary tools
- [Composer](https://getcomposer.org)
- [Gradle](https://gradle.org)
- [NPM](https://www.npmjs.com)
- [PyPI](https://pypi.org)
- [RubyGems](https://rubygems.org)
- [SwiftPM](https://www.swift.org/package-manager/)
- [Yarn](https://yarnpkg.com)

## Usage

```
    dit branch                  Print the current branch.
    dit build <options>         Build the current project.
    dit commit <message>        Commit the current branch.
    dit down <options>          Bring the current project down.
        -v, --volumes           Remove volumes
    dit diff <options>          Print the diff of the current branch.
    dit help                    Print this message.
    dit info                    Display project status using lazydocker.
    dit install                 Install the current project dependencies (supports composer, npm, yarn, rubygems, pypi, swiftpm).
    dit pull <options>          Pull the current branch.
    dit push <options>          Push the current branch.
    dit reup <options>          Bring the current project down then back up.
        -v, --volumes           Remove volumes (splattable)
        -b, --build             Build the project before bringing it up (splattable)
        -d, --detach            Detach from the project after bringing it up (splattable)
    dit restart <options>       Restart the current project, or a specific container.
    dit reinstall               Reinstall the current project dependencies (supports composer, npm, yarn, rubygems, pypi, swiftpm).
    dit run <command>           Run a command on a container instance.
        -g, --global <image>    Run a command on a global image.
    dit save <message>          Commit and push current changes.
    dit sh <options>            Spawn a shell on a container instance.
        -g, --global <image>    Spawn a shell on a global image.
    dit swap <branch>           Swap to a new branch, bringing the current project down and back up.
        -v, --volumes           Remove volumes (splattable)
        -s, --stash             Stash the current branch before swapping (splattable)
        -a, --apply             Apply the stash after swapping (splattable)
        -p, --pull              Pull the new branch after swapping
        -n, --no-up             Do not bring the project up after swapping
        -i, --reinstall         Reinstall the project dependencies after swapping (supports composer, npm, yarn, rubygems, pypi, swiftpm)
    dit up <options>            Bring the current project up.
        -b, --build             Build the project before bringing it up (splattable)
        -d, --detach            Detach from the project after bringing it up (splattable)
        -r, --recreate          Recreate the container before bringing it up (splattable)
        -c, --cleanup           Cleanup orphans from project before bringing it up (splattable)

```

## Examples

```
# Get current branch
  dit branch
  dit br
  
# Bring the current project down including volumes
  dit down --volumes
  dit d -v
  
# Install project dependencies
  dit install
  dit i
  
# Clean install dependencies of one type
  dit reinstall composer
  dit ri c
  
# Bring project down including volumes, then build before bringing back up, then detach
  dit reup --build --detach --volumes
  dit reup -bdv
  
# Restart the project
  dit restart
  dit res

# Run 'ls' on a container named 'container'
  dit run container ls
  dit r container ls
  
# Run 'echo hi' on a new container using the 'composer' image
  dit run 'echo hi' -g composer
  dit r 'echo hi' -g composer
  
# Spawn a shell on a new container using the 'alpine' image
  dit sh -g alpine
  
# Spawn a shell on a container named 'container'
  dit sh container
  dit sh container

# Bring the current project down including volumes, then stash the current changes, then checkout git branch named 'dev', then pull the latest changes, then apply the stashed changes, then reinstall project dependencies, then bring the project up.
  dit swap dev --volumes --stash --apply --pull --reinstall
  dit s dev -vsa -p -i
  
# Build the project, then bring it up recreating containers and removing orphans, then detach
  dit up --build --detach --recreate --clean
  dit u -bdr
```

## Contributing

All contributions welcome!

## License

This repository is available under the [MIT License](./LICENSE).
