# wazo-python-werkzeug-packaging

Debian packaging for [werkzeug](https://github.com/pallets/werkzeug) used in Wazo.

## Reason

* Include a patch to never send content-length for 204. This patch is backported from python-werkzeug 0.16.

## Upgrading

To upgrade werkzeug:

* Update the version number in the `VERSION` file
* Update the changelog using `dch -i` to the matching version
* Refresh patches
* Push the changes

## Building Locally

To build on a test environment before submitting a change to production the following procedure can be used.

```sh
make -f debian/rules get-orig-source
tar -xvf ../wazo-python-werkzeug-packaging_*.orig.tar.gz  --strip 1
dpkg-buildpackage -us -uc
```
The `.deb` will be located in the parent directory.

# Add patches

To add patches:

```sh
make -f debian/rules get-orig-source
tar -xvf ../wazo-python-werkzeug-packaging_*.orig.tar.gz  --strip 1
vim <filename.py>
dpkg-source --commit
dpkg-buildpackage -us -uc

