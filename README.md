# deb packaging for pyznap

This debian source package builds [pyznap](https://github.com/yboetz/pyznap/) natively on your build environment. It is managed with [git-buildpackage](https://wiki.debian.org/PackagingWithGit) and aims to be a pretty good quality debian source package. You can find the maintaining command summary in [debian/gbp.conf](debian/gbp.conf).

## Download prebuilt packages

Prebuild deb packages are available in the [releases section](https://github.com/dionysius/pyznap-deb/releases) for the latest Ubuntu LTS and Debian stable in various architectures (if applicable). They are automatically built in [Github Actions](https://github.com/dionysius/pyznap-deb/actions) and you can verify the signatures with this [signing-key](signing-key.pub).

## Requirements

- Installed `git-buildpackage` from your apt
- Installed build dependencies as defined in [debian/control `Build-Depends`](debian/control) (will notify you in the build process otherwise)
  - [`mk-build-deps`](https://manpages.debian.org/testing/devscripts/mk-build-deps.1.en.html) can help you automate the installation

## Packaging

- Clone with git-buildpackage: `gbp clone https://github.com/dionysius/pyznap-deb.git`
- Switch to the folder: `cd pyznap-deb`
- Build with git-buildpackage: `gbp buildpackage`
  - There are many arguments to fine-tune the build (see `gbp buildpackage --help` and `dpkg-buildpackage --help`)
  - Notable options: `-b` (binary-only, no source files), `-us` (unsigned source package), `-uc` (unsigned .buildinfo and .changes file), `--git-export-dir=<somedir>` (before building the package export the source there)

## TODOs

- Automatic upload to an apt provider
- Automatic notification on new upstream releases. Optimally with automatic PR with those updates
