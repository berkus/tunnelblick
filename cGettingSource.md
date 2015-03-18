## Getting the source code for Tunnelblick ##

All of the source code for Tunnelblick is in the development trunk of the svn repository. Because of the way that svn works, you can get the source code for any prior version by getting a particular revision of the trunk.

(As a convenience, stable releases are "copied" to separate branches, so you can get them there.)

### Most-recent version ###
To get a "read-only" copy of the most recent update of the repository, you would enter

> `svn checkout http://tunnelblick.googlecode.com/svn/trunk/   new-folder`

"`new-folder`" is the path for a folder which will be created to put the source into.

("read-only" means that you cannot commit any modifications you make back to the repository. It does NOT mean that the copy you get is "read only" as far as making changes to it.)

### Other versions ###
To get the source as of a particular revision, for example, [r123](https://code.google.com/p/tunnelblick/source/detail?r=123), use

> `svn checkout http://tunnelblick.googlecode.com/svn/trunk/   -r   123   new-folder`

The "`-r   123`" tells svn to get the source code as of the [r123](https://code.google.com/p/tunnelblick/source/detail?r=123) revision.

To get a particular version of the source code, you need to know the revision number for the specific version of the software that you want. You do that by looking at the "Changes" sub-tab of the Source page (http://code.google.com/p/tunnelblick/source/list). Look for a commit message that says something like "now the same as version XXXXX', where XXXXX is the particular version that you want.

For example, to get the source for 3.1beta10, you find the line in the "Changes" that looks like:

> `r970   Build 1970: update trunk so it is now the same as version 3.1beta10 build 1969, except that it is 3.1beta11 build 1970`

See the "`r970`"? That's the revision you want. So you would enter

> `svn checkout http://tunnelblick.googlecode.com/svn/trunk/   -r   970   new-folder`

Notes:
  1. I try to keep the build number exactly 1000 higher than the revision level. So if you are looking for "3.1beta04 (build 1745)", look for a commit after revision [r745](https://code.google.com/p/tunnelblick/source/detail?r=745). ([r746](https://code.google.com/p/tunnelblick/source/detail?r=746) - [r753](https://code.google.com/p/tunnelblick/source/detail?r=753) were wiki changes, so [r754](https://code.google.com/p/tunnelblick/source/detail?r=754) is the one you would want). This won't work for very old versions because the build numbers and revision numbers were not kept 1000 apart.
  1. I don't make it easy to get the exact source for a beta which identifies itself as being the same version and build as the beta so that people can tell if they are running a "released" version of the software or one that has been created from building the source. That gives people an indication that they are running a potentially modified version.