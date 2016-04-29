Ansible role for EasyBuild (with Lmod)
======================================


Requirements
------------

- CentOS 6
- Ansible version 2.0.1


Variables
---------

### `easybuild_root`

Default: `/apps`

Directory in which to store all EasyBuild and Lmod files.


Todo
----

### Yum vs EasyBuild

For some base packages, figure out whether to install with yum or with
EasyBuild (e.g., Perl).

### Incorrect source downloads

How to work around EasyBuild packages where the source tarball downloads are
incorrect (e.g., `GCCcore/gmp-6.0.0a.tar.bz2` for which an HTML page is
dowloaded)?

Possible solutions:

1. Patch the recipe.
2. Download the tarball separately.
3. Include the tarball with the playbook.

### Package installation

How to proceed with actually installing EasyBuild packages, preferably driven
by other roles? Options:

1. Just use tasks like the following:
   `shell: . {{ easybuild_root }}/modules/modules.bashrc && module load EasyBuild && eb SOME_PACKAGE --robot`
2. Have a custom `easybuild` Ansible module which wraps this.
3. Have a `easybuild_packages` variable with a list of packages to be
   installed by this role.
4. Similar, but as a separate `easybuild-packages` role which is cheaper to
   repeatedly include from other roles.

I'm inclined to start with 1 and later choose between 2 and 4.
