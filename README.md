## Samsung Galaxy Note 4 and Tab S2 (Exynos) Lineage 18.1-Based ROMs

# Build guide
**1) Sync Source (LineageOS / RR OS Etc) as follows**

- `repo init -u https://github.com/LineageOS/android.git -b lineage-18.1 --depth=1`
- `repo sync --force-sync --no-clone-bundle --current-branch --no-tags -j128`

**2) Download our manifest**
- `git clone https://github.com/universal5433/local_manifests -b lineage-18.1 .repo/local_manifests`
- Remove XMLs that do not corrospond to your device (eg keep treltexx.xml in .repo/local_manifests)
- Alternativly `mkdir -p .repo/local_manifests && curl https://raw.githubusercontent.com/universal5433/local_manifests/lineage-18.1/treltexx.xml > .repo/local_manifests/treltexx.xml`

**3) ReSync Source with new manifest**
- `repo sync --force-sync --no-clone-bundle --current-branch --no-tags -j128`

**4) Setup Build enviroment**
- `. build/env*`

**5) Additionally apply patches**
- Head over to [Universal5433_Patches](https://github.com/universal5433/universal5433_patches)
- Clone into root directory of your ROM
- Apply via `git am /path/to/patch/*.patch` or use `repopick` if aplicable

**6) Start Compiling**
- `lunch lineage_treltexx-userdebug`
- `mka bacon`
- Alternativly, `brunch treltexx`

# Exta Misc Commands
* Enable CCACHE (Faster reoccuring compiles)

`export USE_CCACHE=1`

`export CCACHE_EXEC=/usr/bin/ccache`

* Fix git issues when syncing

`git config --global url."https://".insteadOf git://`

* repo sync alias

`alias rsf='repo sync --force-sync --no-clone-bundle --current-branch --no-tags -j128'`

* Build Clean (Clean out directory)

`cmka bacon`

* Common Build Dependencies (Ubuntu 22.04)

* `sudo apt install openssh-server screen python-dev-is-python3 git openjdk-8-jdk android-tools-adb bc bison \
build-essential curl flex g++-multilib gcc-multilib gnupg gperf imagemagick lib32ncurses-dev \
lib32readline-dev lib32z1-dev  liblz4-tool libncurses5-dev libsdl1.2-dev libssl-dev \
libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc yasm zip zlib1g-dev \
libtinfo5 libncurses5 repo ccache`

* Patchelf V0.9
`wget -o http://archive.ubuntu.com/ubuntu/pool/universe/p/patchelf/patchelf_0.9-1_amd64.deb &&
sudo dpkg -i patchelf*.deb`

## Copyright

* Copyright (C) 2022 ananjaser1211 (AnanJaser)
* Copyright (C) 2022 retiredtab
* Copyright (C) 2021 Lunarixus (Nathan)
* Copyright (C) 2021 stricted (Jan Altensen)
* Copyright (C) 2021 ripee
* Copyright (C) 2021 bonuzzz

## License
Apache License 2.0 (Apache-2.0) (Located at LICENSE, read more at [tldrlegal.com/license/apache-license-2.0](https://tldrlegal.com/license/apache-license-2.0-%28apache-2.0%29))

Short (no legal advice) summary of the used license:


**Can**

 * Commercial Use
 * Modify
 * Distribute
 * Sublicense
 * Private Use
 * Use Patent Claims
 * Place Warranty


**Cannot**

 * Hold Liable
 * Use Trademark


**Must**

 * **Include Copyright**
 * **Include License**
 * **State Changes**
 * **Include Notice**
