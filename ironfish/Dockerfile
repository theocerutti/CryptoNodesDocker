FROM ghcr.io/iron-fish/ironfish:latest

RUN ironfish status
RUN ironfish config:set blockGraffitti "TheoC Server"

CMD ["start", "--rpc.ipc", "--rpc.tcp"]
