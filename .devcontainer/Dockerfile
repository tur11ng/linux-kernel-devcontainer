FROM ubuntu:latest

RUN apt update

# Generic prerequisites
RUN apt install --yes build-essential git

# Virtme-ng prerequisites
RUN apt install --yes software-properties-common
RUN add-apt-repository ppa:arighi/virtme-ng
RUN apt install --yes virtme-ng

# Linux kernel prerequisites
RUN apt install --yes libncurses-dev gawk flex bison openssl libssl-dev \
    dkms libelf-dev libudev-dev libpci-dev libiberty-dev autoconf llvm \
    clang libclang-dev lld gdb clangd

# Rust prerequisites
RUN curl https://sh.rustup.rs -sSf | \
    sh -s -- --default-toolchain stable -y
ENV PATH=/root/.cargo/bin:$PATH

# Rust for linux prerequisites
RUN rustup override set stable
RUN rustup component add rust-src
RUN rustup component add rustfmt
RUN rustup component add clippy
RUN cargo install --locked bindgen-cli

WORKDIR /workspaces