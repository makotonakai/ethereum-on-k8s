FROM ubuntu:22.04 

RUN apt update
RUN apt install -y curl build-essential sudo nano

RUN mkdir hornet
RUN curl -LJO https://github.com/iotaledger/hornet/releases/download/v1.2.0/HORNET-1.2.0_Linux_x86_64.tar.gz
RUN tar xvzf HORNET-1.2.0_Linux_x86_64.tar.gz -C hornet --strip-components 1

WORKDIR /hornet/private_tangle
RUN mkdir -p snapshots/private_tangle1/
RUN ../hornet tools snap-gen --networkID private_tangle1 --mintAddress 60200bad8137a704216e84f8f9acfe65b972d9f4155becb4815282b03cef99fe --outputPath snapshots/private_tangle1/full_snapshot.bin
COPY run_coo.sh /hornet/private_tangle/run_coo.sh
RUN chmod 777 run_coo.sh
RUN cp ../profiles.json ./
RUN cp ../peering.json ./

CMD ["/hornet/private_tangle/run_coo.sh"]



