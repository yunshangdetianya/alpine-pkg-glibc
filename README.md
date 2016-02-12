# alpine-pkg-glibc

[![CircleCI](https://img.shields.io/circleci/project/andyshinn/alpine-pkg-glibc/master.svg)](https://circleci.com/gh/andyshinn/alpine-pkg-glibc)

This is the GNU C library as a Alpine Linux package to run binaries linked against `glibc`. This package utilizes a custom built glibc binary based on the vanilla glibc source. Built binary artifacts come from https://github.com/andyshinn/docker-glibc-builder.

## Releases

See the [releases page](https://github.com/andyshinn/alpine-pkg-glibc/releases) for the latest download links. If you are using tools like `localdef` you will need the `glibc-bin` and `glibc-i18n` packages in addition to the `glibc` package.

## Installing

The current installation method for these packages is to pull them in using `wget` or `curl` and install the local file with the `--allow-untrusted` option to `apk`:

```
apk --no-cache add ca-certificates
wget https://github.com/andyshinn/alpine-pkg-glibc/releases/download/2.22-r5/glibc-2.22-r5.apk
apk --allow-untrusted add glibc-2.22-r5.apk
```

## Locales

You will need to generate your locale if you would like to use a specific one for your glibc application. You can do this by installing the `glibc-i18n` package and generating a locale using the `localedef` binary. An example for en_US.UTF-8 would be:

```
apk --allow-untrusted add glibc-bin-2.22-r5.apk glibc-i18n-2.22-r5.apk
/usr/glibc-compat/bin/localedef -i en_US -f UTF-8 en_US.UTF-8
```
