# build-docbook-catalog

This is the source for `app-text/build-docbook-catalog`, which is a
script to regenerate the xml docbook catalog.

You can find it here:
	http://sources.gentoo.org/gentoo-src/build-docbook-catalog/

To make a release of this script, do the following:

1. Commit your changes, create the tarball, and post it:
```
    make dist
    cp build-docbook-catalog-*.tar.xz /usr/portage/distfiles/
    scp build-docbook-catalog-*.tar.xz dev.gentoo.org:/space/distfiles-local/
```

2. Make a new version of the build-docbook-catalog ebuild:
```
    ego build-docbook-catalog
    cp $(ls -t1 *.ebuild | head -n 1) build-docbook-catalog-${rev}.ebuild
    ekeyword ~all build-docbook-catalog-${rev}.ebuild
```

3. Do the normal steps to generate a digest, mark the previous version
   stable, use echangelog to add a ChangeLog entry, etc.
```
    cvs add build-docbook-catalog-${rev}.ebuild
    ebuild build-docbook-catalog-${rev}.ebuild digest
    echangelog
    repoman commit -m "version bump to ${rev}"
```

vim:sw=4 expandtab
