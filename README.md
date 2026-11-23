# n900-sdk-mirror

Our copy of the Maemo 5 (Fremantle) SDK packages that the sysroot of [n900-devkit](https://github.com/n900-resurrection/n900-devkit) is built from
(`make sysroot`). The layout is the one of repository.maemo.org (`pool/`, `dists/fremantle/sdk/{free,non-free}/binary-armel/Packages`), so it serves as a
plain apt-style mirror (GitHub Pages). `MISSING` lists the names the SDK does not have (virtual packages, translations).

`scripts/fetch_sysroot.py` takes the packages from here first and goes to the old mirrors (maemo.plan9.de, maemo.viniciuspaes.com) only for what is
not here. When this repository is cloned as `sdk-mirror/` in the project, what it had to take from them is copied here: commit and push it.

Only the packages that are needed are mirrored, not the whole SDK.
