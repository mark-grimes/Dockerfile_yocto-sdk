# yocto-sdk

Image to cross compile code for ARM using the yocto sdk. Includes docker so that container images can
be created from build result.

Includes a cross compile compatible version of ldd from
https://gist.github.com/jerome-pouiller/c403786c1394f53f44a3b61214489e6f to figure out what libraries
should be in an image. This version is at `/bin/xldd` and should be executed with the sysroot as an
argument, i.e. `xldd --root /opt/poky/2.4.2/sysroots/cortexa8hf-neon-poky-linux-gnueabi`.

Also useful (but not included) is the
[extractDynamicLibs.sh](https://github.com/mark-grimes/Dockerfiles/blob/master/extractDynamicLibs.sh)
script which can pull out those libraries into a single directory for addition to the docker image.
