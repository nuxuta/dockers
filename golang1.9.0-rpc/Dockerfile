FROM golang:1.9-alpine
ENV PROTOBUF_TAG=v3.1.0
ADD ./build-protobuf.sh /tmp/build-protobuf.sh
RUN chmod +x /tmp/build-protobuf.sh
RUN /tmp/build-protobuf.sh