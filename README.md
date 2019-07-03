# zypperdiff

This small utility is inspired by apt-listchanges for listing changes when updating packages with zypper.

It first downloads with zypper all packages to be installed.
Then it shows in a pager (less, most, etc) the changelog difference (thus what's new) for each package.
Finally, when the user has reviewed the changes, it asks if the packages must be installed.

# Install

```
wget https://raw.githubusercontent.com/bubbleguuum/zypperdiff/master/zypperdiff && chmod +x zypperdiff
```

Then move file somewhere in your PATH.

# Usage

Use the same zypper arguments that results in installing packages. Examples:

- `zypperdiff up`
- `zypperdiff dup`
- `zypperdiff in bash zsh`
- `zypperdiff inr`


No need to invoke with `sudo` as the script already uses it to invoke zypper.

IMPORTANT: running this script always clears the package cache in /var/cache/zypp !

# Example diff output:

```
========================================================================

libbluetooth3: Bluetooth Libraries

========================================================================

* Tue Jun 25 2019 Frederic Crozat <fcrozat@suse.com>
- Add avinfo to bluez-test, useful for debugging.
- Only BuildRequires pkgconfig(ell) on Tumbleweed.
- Add bluez-5.50-a2dp-backports.patch: A2DP fixes for newer codecs
  (upstream backport).
    
  
    
========================================================================

libbz2-1: The bzip2 runtime library

========================================================================

* Fri Jun 28 2019 Martin Pluskal <mpluskal@suse.com>
- Update bug reference
- Fix downloaded patches

* Thu Jun 27 2019 Bjørn Lie <bjorn.lie@gmail.com>
- Update to version 1.0.7:
  * Fix undefined behavior in the macros SET_BH, CLEAR_BH, &
    ISSET_BH.
  * bzip2: Fix return value when combining --test,-t and -q.
  * bzip2recover: Fix buffer overflow for large argv[0].
  * bzip2recover: Fix use after free issue with outFile
    (CVE-2016-3189).
  * Make sure nSelectors is not out of range (CVE-2019-12900
    bsc#1139083)
- Drop patches fixed upstream:
  * bzip2-unsafe_strcpy.patch.
  * bzip2-1.0.6-CVE-2016-3189.patch.
- Refresh patches with quilt.
```
