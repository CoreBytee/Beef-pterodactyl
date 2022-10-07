FROM        ghcr.io/parkervcp/yolks:debian

RUN apk add --no-cache --update curl ca-certificates openssl git tar bash sqlite fontconfig 
RUN adduser --disabled-password --home /home/container container

RUN curl -sSL https://get.rvm.io | bash -s -- --autolibs=install-packages
RUN sudo .rvm/bin/rvm requirements
RUN curl -sSL https://get.rvm.io | bash -s stable --ruby
RUN rvm install "ruby-2.5.3"
RUN git clone https://github.com/beefproject/beef && cd ./beef && ./install

USER container
ENV  USER=container HOME=/home/container

WORKDIR /home/container
COPY ./entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]