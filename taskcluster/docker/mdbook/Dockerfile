# This Source Code Form is subject to the terms of the Mozilla Public
# License, v. 2.0. If a copy of the MPL was not distributed with this
# file, You can obtain one at http://mozilla.org/MPL/2.0/.

FROM python:3.7
MAINTAINER Axel Hecht <axel@pike.org>

# Add worker user
RUN mkdir /builds && \
    useradd -d /builds/worker -s /bin/bash -m worker && \
    mkdir /builds/worker/artifacts && \
    chown worker:worker /builds/worker/artifacts

# %include-run-task

RUN apt-get update && apt-get install -y --force-yes --no-install-recommends \
    ca-certificates \
    curl \
    git
RUN curl -L https://github.com/rust-lang/mdBook/releases/download/v0.3.5/mdbook-v0.3.5-x86_64-unknown-linux-gnu.tar.gz|tar -C /usr/local/bin/ -zx
ENV SHELL=/bin/bash \
    HOME=/builds/worker \
    PATH=/builds/worker/.local/bin:$PATH

VOLUME /builds/worker/checkouts
VOLUME /builds/worker/.cache

# Set a default command useful for debugging
CMD ["/bin/bash", "--login"]
