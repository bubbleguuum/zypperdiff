# zypperdiff

This small utility is inspired by apt-listchanges.

It first downloads with zypper all packages to be installed.
Then it shows in a pager (less, most, etc) the changelog difference (thus what's new) for each package.
Finally, when the user has reviewed the changes, it asks if the packages must be installed.

# Usage

Use the same zypper argument that results in installing packages. Examples:

- `zypperdiff up`
- `zypperdiff dup`
- `zypperdiff in bash zsh`
- `zypperdiff inr`


No need to invoke with `sudo` as the script already uses it to invoke zypper.

IMPORTANT: running this script always clears the package cache in /var/cache/zypp !

