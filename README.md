# Fedora Minimal Project

[![RPM lint](https://github.com/adelton/fedora-minimal/actions/workflows/rpmlint.yml/badge.svg)](https://github.com/adelton/fedora-minimal/actions/workflows/rpmlint.yml)
[![RPM install test](https://github.com/adelton/fedora-minimal/actions/workflows/e2e.yml/badge.svg)](https://github.com/adelton/fedora-minimal/actions/workflows/e2e.yml)
[![RPM build in copr repo](https://copr.fedorainfracloud.org/coprs/adelton/fedora-minimal/package/fedora-minimal/status_image/last_build.png)](https://copr.fedorainfracloud.org/coprs/adelton/fedora-minimal/package/fedora-minimal/)

A set of `fedora-minimal-conflicts-*` packages that conflict with various
areas that might not be desired on a given machine. By installing these
conflicting subpackages, you minimize the chance that a huge list of
dependencies will get installed during `dnf upgrade` for example via weak
dependencies, making the system consume more disk space, less manageable,
and ultimately less secure.

## Enable repository

Packages are automatically built in the
https://copr.fedorainfracloud.org/coprs/adelton/fedora-minimal/ repository.
Enable access to them with

```
dnf copr enable -y adelton/fedora-minimal
```

## Review available options

Check output of
```
dnf search fedora-minimal-conflicts-
```
to see what is available.

## Iterative process of minimizing the setup

Try to enable all of them
```
sudo dnf install --skip-broken 'fedora-minimal-conflicts-*'
```
At the
```
Is this ok [y/N]:
```
prompt decide if you want to install at least the packages without
conflicts, giving you protection in those areas.

You will likely have some packages reported with conflicts because you
installation has some useful parts that would be prevented by complete
set. But maybe it will force you to think if you really use or need
all those packages on your setup. Clean up what you don't need and try
to add more `fedora-minimal-conflicts-*` packages.

