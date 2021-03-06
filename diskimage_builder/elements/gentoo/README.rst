========
Gentoo
========
Use a Gentoo cloud image as the baseline for built disk images. The images are
located in profile specific sub directories:

    http://distfiles.gentoo.org/releases/amd64/autobuilds/

As of this writing, only amd64 and arm64 images are available.

Notes:

* There are very frequently new automated builds that include changes that
  happen during the product maintenance. The download directories contain an
  unversioned name and a versioned name. The unversioned name will always
  point to the latest image, but will frequently change its content. The
  versioned one will never change content, but will frequently be deleted and
  replaced by a newer build with a higher version-release number.

* In order to run the package-installs element you will need to make sure
  `dev-python/pyyaml` is installed on the host.

* In order to run the vm element you will need to make sure `sys-block/parted`
  is installed on the host.

* Other profiles can be used by exporting GENTOO_PROFILE with a valid profile.
  A list of valid profiles follows:

    default/linux/amd64/17.1
    default/linux/amd64/17.1/no-multilib
    default/linux/amd64/17.1/hardened
    default/linux/amd64/17.1/no-multilib/hardened
    default/linux/amd64/17.1/systemd
    default/linux/arm64/17.0
    default/linux/arm64/17.0/systemd

* You can set the `GENTOO_PORTAGE_CLEANUP` environment variable to False to
  disable the clean up of portage repositories (including overlays).  This
  will make the image bigger if caching is also disabled.

* Gentoo supports many different versions of python, in order to select one
  you may use the `GENTOO_PYTHON_TARGETS` environment variable to select
  the versions of python you want on your image.  The format of this variable
  is a string as follows `"python2_7 python3_6"`.

* You can enable overlays using the `GENTOO_OVERLAYS` variable.  In it you
  should put a space separated list of overlays.  The overlays must be in the
  official overlay list and must be git based.

* `GENTOO_EMERGE_ENV` is a bash array containing default environment
  variables for package install, you can override it with another bash array.

* `GENTOO_EMERGE_DEFAULT_OPTS` can be set to control the default options
  passed to emerge for all package actions, this includes operations like
  depclean and preserved-rebuild.
