# n900-sdk-mirror

Our copy of the Maemo 5 (Fremantle) SDK packages that the sysroot of [n900-devkit](https://github.com/n900-resurrection/n900-devkit) is built from
(`make sysroot`). The layout is the one of repository.maemo.org (`pool/`, `dists/fremantle/sdk/{free,non-free}/binary-armel/Packages`), so it serves as a
plain apt-style mirror (GitHub Pages). `MISSING` lists the names the SDK does not have (virtual packages, translations).

`scripts/fetch_sysroot.py` takes the packages from here first and goes to the old mirrors (maemo.plan9.de, maemo.viniciuspaes.com) only for what is
not here. When this repository is cloned as `sdk-mirror/` in the project, what it had to take from them is copied here: commit and push it.

Only the packages that are needed are mirrored, not the whole SDK.

## First-boot tools (`dists/fremantle/extras/free/`)
Not SDK packages: the device packages with which a stock N900 is brought back to life, kept here because the old Extras repositories are gone
(32 packages, 11 MB, copied from the Extras copy of maemo.plan9.de, every file checked against its MD5sum). Pool path: `pool/fremantle/free/`.

The ones that matter most when reviving an old phone (they make everything else easier):
- **U-Boot:** `u-boot-flasher`, `u-boot-bootimg`, `u-boot-tools` (both versions), `fiasco-image-update-ask`
- **SSH:** `openssh` (client, server, common), with `rootsh` and `sudser`
- **Shell:** `bash3`, `busybox-power`

Also: `tmux` (+ `libevent-2.0-5`), `tinysmb`/`tinysmbgui` and FFmpeg 0.5 with its `-dev` packages (+ `libfaad2-0`). Git is not here: `n900-repository`
has a newer one. Filled by `scripts/mirror_extras.py` of the project n900-resurrection/nokia-n900-apps. The sysroot does not use these packages
(`fetch_sysroot.py` reads only `dists/fremantle/sdk`).
