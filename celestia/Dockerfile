FROM ghcr.io/celestiaorg/celestia-node:0.6.2

WORKDIR /

RUN apt-get -y update && apt-get -y install git curl tar wget clang pkg-config libssl-dev jq build-essential git make ncdu

RUN wget "https://golang.org/dl/go1.19.1.linux-amd64.tar.gz"
RUN rm -rf /usr/local/go
RUN tar -C /usr/local -xzf "go1.19.1.linux-amd64.tar.gz"
RUN rm "go1.19.1.linux-amd64.tar.gz"
RUN echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile
RUN source $HOME/.bash_profile

RUN git clone https://github.com/celestiaorg/celestia-node.git

WORKDIR /celestia-node

RUN git checkout v0.6.2
RUN make install
RUN make cel-key

COPY keyring-test ~/.celestia-light-mocha/keys/

CMD ["/celestia", "light", "start", "--core.ip", "https://rpc-mocha.pops.one", "--keyring.accname", "theo-key", "--gateway", "--gateway.addr", "127.0.0.1", "--gateway.port", "26659", "--p2p.network", "mocha" ]
