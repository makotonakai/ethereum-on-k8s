FROM ubuntu:22.04 

RUN apt update
RUN apt install -y curl build-essential sudo nano

RUN mkdir hornet
RUN curl -LJO https://github.com/iotaledger/hornet/releases/download/v1.2.0/HORNET-1.2.0_Linux_x86_64.tar.gz
RUN tar xvzf HORNET-1.2.0_Linux_x86_64.tar.gz -C hornet --strip-components 1

WORKDIR /hornet/private_tangle
RUN mkdir -p snapshots/private_tangle2/
COPY full_snapshot.bin /hornet/private_tangle/snapshots/private_tangle2/full_snapshot.bin
COPY run_node.sh /hornet/private_tangle/run_node.sh
RUN chmod 777 run_node.sh
RUN cp ../profiles.json ./
RUN cp ../peering.json ./

CMD ["/hornet/private_tangle/run_node.sh"]
