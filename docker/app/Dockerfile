FROM rust:1.79.0-bookworm

RUN rustup component add rustfmt \
  && rustup component add clippy \
  && cargo install cargo-watch

RUN git clone https://github.com/rui314/mold.git\
  && mkdir mold/build \
  && cd mold/build \
  && git checkout v2.4.0 \
  && ../install-build-deps.sh \
  && cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_CXX_COMPILER=c++ .. \
  && cmake --build . -j $(nproc) \
  && cmake --build . --target install

ENV CARGO_BUILD_TARGET_DIR=/tmp/target
WORKDIR /app
