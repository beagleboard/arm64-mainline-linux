# Issue Tracker:

https://github.com/beagleboard/arm64-mainline-linux/issues

# CI:

https://git.beagleboard.org/beagleboard/arm64-mainline-linux/-/jobs

# Weekly Build image for BBAI64 and PLAY (CRON job Wednesday Morning)

https://rcn-ee.net/rootfs/debian-arm64-12-bookworm-minimal-mainline/

# CI: Linux-stable (daily 9am):

https://git.beagleboard.org/beagleboard/arm64-linux
https://git.beagleboard.org/beagleboard/arm64-linux/-/jobs

Add repo via:

```
sudo sh -c "echo 'deb [trusted=yes] https://beagleboard.beagleboard.io/arm64-linux stable main' > /etc/apt/sources.list.d/arm64-linux.list"
```

# CI: Linux-next (daily 9am):

https://git.beagleboard.org/beagleboard/arm64-linux-next
https://git.beagleboard.org/beagleboard/arm64-linux-next/-/jobs

Add repo via:

```
sudo sh -c "echo 'deb [trusted=yes] https://beagleboard.beagleboard.io/arm64-linux-next stable main' > /etc/apt/sources.list.d/arm64-linux-next.list"
```

# Info

This is just a set of scripts to rebuild a known working kernel for ARM devices.

Script Bugs: "robertcnelson+bugs@gmail.com"

Note, for older git tag's please use: https://github.com/RobertCNelson/yakbuild

Dependencies: GCC Cross ToolChain

https://mirrors.edge.kernel.org/pub/tools/crosstool/

Dependencies: Linux Kernel Source

This git repo contains just scripts/patches to build a specific kernel for some
ARM devices. The kernel source will be downloaded when you run any of the build
scripts.

By default this script will clone the linux-stable tree:
https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git
to: ${DIR}/ignore/linux-src:

If you've already cloned torvalds tree and would like to save some hard drive
space, just modify the LINUX_GIT variable in system.sh to point to your current
git clone directory.

Build Kernel Image:

```
./build_kernel.sh
```

Optional: Build Debian Package:

```
./build_deb.sh
```

Development/Hacking:

first run (to setup baseline tree):

```
./build_kernel.sh
```

then modify files under KERNEL directory
then run (to rebuild with your changes):

```
./tools/rebuild.sh
```

