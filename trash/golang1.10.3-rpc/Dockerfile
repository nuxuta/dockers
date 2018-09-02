FROM golang:1.10.3-alpine
ENV PROTOBUF_TAG=v3.5.1
ADD ./build-protobuf.sh /tmp/build-protobuf.sh
RUN chmod +x /tmp/build-protobuf.sh
RUN /tmp/build-protobuf.sh