# rawtherapee-flatpak

**RawTherapee** is a powerful, cross-platform raw photo processing program.

![rawtherapee-flatpak screenshot](rawtherapee-flatpak.png)

[Homepage](https://rawtherapee.com)

This repo is about the flatpak package.

## Instructions

### Requirements

* [flatpak](https://github.com/flatpak/flatpak)
* [flatpak-builder](https://github.com/flatpak/flatpak-builder)

For EL7:

```
# yum install 'flatpak' 'flatpak-builder'
```

You may also wish to install the `xdg-desktop-portal*` packages:

```
# yum install 'xdg-desktop-portal*'
```

See also:

* [flatpak setup](https://flatpak.org/setup)

### Adding repository

```
$ flatpak remote-add --if-not-exists "flathub" "https://dl.flathub.org/repo/flathub.flatpakrepo"
```

See also:

* [flathub setup](http://docs.flatpak.org/en/latest/using-flatpak.html#add-a-remote)

### Prepare

```
$ flatpak install "flathub" "org.gnome.Sdk//3.34"
```

```
$ flatpak install "flathub" "org.gnome.Platform//3.34"
```

Clone this repository, then checkout the right branch.

### Build

```
$ flatpak-builder "build" "com.rawtherapee.RawTherapee.yaml" --force-clean --install-deps-from="flathub"
```

### Test

```
$ flatpak-builder --run "build" "com.rawtherapee.RawTherapee.yaml" "sh"
```

### Test run

```
$ flatpak-builder --run "build" "com.rawtherapee.RawTherapee.yaml" "rawtherapee"
```

### Create repo

```
$ flatpak-builder --repo="repo" --force-clean "build" "com.rawtherapee.RawTherapee.yaml"
```

### Install

```
$ flatpak --user remote-add --no-gpg-verify "rawtherapee" "repo"
```

```
$ flatpak --user install "rawtherapee" "com.rawtherapee.RawTherapee"
```

### Run

```
$ flatpak run "com.rawtherapee.RawTherapee"
```

### Uninstall

```
$ flatpak --user uninstall "com.rawtherapee.RawTherapee"
```

```
$ flatpak --user remote-delete "rawtherapee"
```

### Build single-file bundle

```
$ flatpak build-bundle "repo" "rawtherapee.flatpak" "com.rawtherapee.RawTherapee" --runtime-repo="https://flathub.org/repo/flathub.flatpakrepo"
```

### Install single-file bundle

If you have already [installed](#install) the package, you have to [uninstall](#uninstall) it before continuing.

```
$ flatpak --user install "rawtherapee.flatpak"
```

See also:
* [Building your first Flatpak](http://docs.flatpak.org/en/latest/first-build.html)
* [Single-file bundles](http://docs.flatpak.org/en/latest/single-file-bundles.html#single-file-bundles)

## FAQ

### Why not a RPM package?

I already provided [COPR repo](https://copr.fedorainfracloud.org/coprs/scx/rawtherapee) with (S)RPM packages for EL.

### Are you the author of RawTherapee?

No, I only created the flatpak package for it.

See also:

* [GitHub repo](https://github.com/Beep6581/RawTherapee)

