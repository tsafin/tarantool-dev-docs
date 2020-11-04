FROM artembo/python-texlive:latest

COPY .devcontainer/requirements.txt /tmp/requirements.txt
RUN pip --disable-pip-version-check --no-cache-dir install -r /tmp/requirements.txt

RUN apt update && apt install -y luarocks && \
    luarocks install penlight

# Install node
RUN curl -sL https://deb.nodesource.com/setup_11.x | bash -
RUN apt-get install -y nodejs
RUN npm install -g jshint

# COPY requirements.txt /tmp/pip-tmp/
# RUN pip3 --disable-pip-version-check --no-cache-dir install -r /tmp/pip-tmp/requirements.txt \
#    && rm -rf /tmp/pip-tmp

# install ldoc
ADD https://api.github.com/repos/tarantool/LDoc/git/refs/heads/tarantool version.json
RUN git clone https://github.com/tarantool/LDoc.git /usr/local/ldoc

#install tarantool
RUN curl -L https://tarantool.io/installer.sh | bash

RUN mkdir /doc
WORKDIR /doc
