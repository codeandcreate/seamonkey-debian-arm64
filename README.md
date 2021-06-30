# SeaMonkey for Debian/Arm64
Patches and builds for [SeaMonkey](https://www.seamonkey-project.org) on Debian (bullseye/unstable) on Arm64.

The license in this repository only applies to my patches! The builds released under the same license(s) Seamonkey uses. Please look at the "LICENSE"-file bundled with the sources of Seamonkey.

## Status and versions

- **Release 2.53.8** is configured and compiled without webrtc, since the sources doesn't include the Arm64 stuff of modern Firefox (...) that is necessary for a successfull compilation.

## Preparations and compiling yourself

- To compile Seamonkey yourself with this patches you should carefully read the [SeaMonkey Building & Source Code Documentation](https://www.seamonkey-project.org/dev/code-development)!
- Always use the [lastest version of rust/cargo](https://doc.rust-lang.org/cargo/getting-started/installation.html), not the version of the official debian repositories!
- Create a directory like "~/Development/seamonkey"
- In this directory check out https://github.com/giampaolo/psutil or download and untar/unzip a release - i use release-5.8.0
- Download and untar the Seamonkey sources, for example [2.53.8](https://archive.mozilla.org/pub/seamonkey/releases/2.53.8/source/seamonkey-2.53.8.source.tar.xz)
- Your directory structure should look like this:
``` raw
.../seamonkey
.../seamonkey/psutil-release-5.8.0.zip
.../seamonkey/psutil-release-5.8.0/
.../seamonkey/seamonkey-2.53.8.source.tar.xz
.../seamonkey/seamonkey-2.53.8/
```
- Make a link inside the Seamonkey source directory to the psutil sources: ```ln -s psutil-release-5.8.0 seamonkey-2.53.8/psutil```
- Create a build directory somewhere inside your build directory like ```mkdir ~/Development/seamonkey/seamonkey-2.53.8/moz_objdir```
- [Apply the patches](https://www.pair.com/support/kb/paircloud-diff-and-patch/) from this repository and place the .mozconfig file in your seamonkey source directory targeting the matching Seamonkey release
- Edit .mozconfig based on your directory structure; ```mk_add_options MOZ_OBJDIR=``` need to be pointing to the build directory you created above; for me a relative path doesn't work.
- Compile the Source with ```./mach build```

