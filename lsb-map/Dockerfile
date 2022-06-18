#
# Copyright (c) 2022 Chris Manigan
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
#

FROM        ubuntu:20.04

LABEL       author="Chris Manigan" maintainer="ganiman@madetoraid.com"

LABEL       org.opencontainers.source="https://github.com/GanimanSwift/lsb-docker"
LABEL       org.opencontainers.image.licenses=MIT

ENV         DEBIAN_FRONTEND=noninteractive

RUN         apt update \
                && apt upgrade -y \
                && apt install -y net-tools nano software-properties-common git clang-11 cmake make libluajit-5.1-dev libzmq3-dev libssl-dev zlib1g-dev mariadb-client libmariadb-dev luarocks \
                && adduser -m -d /home/container container

USER        container
ENV         USER=container HOME=/home/container

ENV         CC=/usr/bin/clang-11
ENV         CXX=/usr/bin/clang++-11

WORKDIR     /home/container

COPY        ./entrypoing.sh /entrypoint.sh

CMD         ["/bin/bash", "/entrypoint.sh"]
