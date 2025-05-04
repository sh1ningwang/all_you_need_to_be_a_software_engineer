# What is Homebrew?
Homebrew is a powerful software package manager for macOS. Similar to tools on other platforms such as apt-get on a Ubuntu machine, homebrew helps you install and manage software packages from online resources.

To use homebrew, you need to understand the following terminologies a bit.
| Terminology | Description |
| ----------- | ----------- |
| tap | A tap is nothing but a git repository of packages. Typically, you will fined homebrew has a tap called `homebrew/core` tapped on your machine upon installation. This means that you can install packages from this source. |
| cellar | A cellar defines the location of the local packages installed by homebrew. Therefore, cellar exists only on your own local machine. |
| formula | A formula is simply a software package. When we want to install some softwares to our local machine, we install a formula. Homebrew keeps multiple version of formula in the cellar, so that you can downgrade a software if its latest version breaks something you already have. |

# Homebrew Installation
Installing homebrew is simply. Open a terminal and run the following.
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

# How to use Homebrew
## To find a package (formula) to install
`brew search <formula>`

## Install a package (formula)
`brew install <formula>`

This searches all the taps configured with Homebrew and finds a matching formula with the provided package name.

To install a specific version of the formula, you may append the version number like this `brew install <formula>@<version>`. For example, `brew install python@3.9`.

## View taps
`brew tap`

This lists down all the taps that are currently configured. By default, homebrew assumes you are looking for repository on Github. The convention for tap names is `<user>/<repo>`. Typically, the default tap `homebrew/core` represents there's a Github user account - homebrew with a repository - core.

## Add a tap
`brew tap <user>/<repo>`

This assumes that the adding tap is hosted on Github. If you want to tap repositories hosted else where, you can add the repo URL at the end like this. `brew tap <user>/<repo> <url>`

## Keep your packages up to date
`brew update && brew upgrade`

This firstly refresh the taps and get the latest package versions. (brew update)
It then upgrade your installed formulas to the latest version. (brew upgrade)

## Uninstall a package (formula)
`brew uninstall <formula>`

If you want to uninstall all versions of the formula, use `brew uninstall -f <formula>` instead.

## Remove old version of formulas
`brew cleanup`

This cleans up old versions, lock files and outdated files for the formulas installed on your machine. It helps free up some disk space.