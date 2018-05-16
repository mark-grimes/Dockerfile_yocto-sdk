FROM debian:stretch

RUN apt-get update \
    && apt-get install -y curl git build-essential python \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN curl -fsSL get.docker.com -o get-docker.sh \
    && chmod u+x get-docker.sh \
    && CHANNEL="stable" ./get-docker.sh \
    && rm ./get-docker.sh

RUN curl -L http://downloads.yoctoproject.org/releases/yocto/yocto-2.5/toolchain/x86_64/poky-glibc-x86_64-core-image-sato-aarch64-toolchain-2.5.sh -o install.sh \
    && chmod u+x /install.sh \
    && /install.sh \
    && rm /install.sh

# Get the cross-toolchain compatible version of ldd to figure out which libraries
# need to be in a docker image.
RUN curl -fsSL https://gist.github.com/jerome-pouiller/c403786c1394f53f44a3b61214489e6f/raw/eb44581caf7dd60b149a6691abef46264c46e866/cross-compile-ldd \
    | sed s:"\${prefix}-gcc":"arm-poky-linux-gnueabi-gcc": \
    | sed s:"\${prefix}-readelf":"readelf": > /bin/xldd \
    && chmod ugo+x /bin/xldd
