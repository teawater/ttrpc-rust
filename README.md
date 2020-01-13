# ttrpc-rust

`ttrpc-rust` is a Rust version of [ttrpc](https://github.com/containerd/ttrpc). [ttrpc](https://github.com/containerd/ttrpc) is GRPC for low-memory environments.

The ttrpc compiler of `ttrpc-rust` `ttrpc_rust_plugin` is modified from gRPC compiler of [gRPC-rs](https://github.com/pingcap/grpc-rs) [grpcio-compiler](https://github.com/pingcap/grpc-rs/tree/master/compiler).

# Usage

To generate the sources from proto files:

1. Install protoc from github.com/protocolbuffers/protobuf

2. Install protobuf-codegen from github.com/pingcap/grpc-rs

3. Install ttrpc_rust_plugin from ttrpc-rust/compiler

4. Generate the sources:

```
$ protoc --rust_out=. --ttrpc_out=. --plugin=protoc-gen-ttrpc=`which ttrpc_rust_plugin` example.proto
```

# Run Examples
1. Go to the directory

    `$ cd ttrpc-rust/example`

2. Start the server

    `$ cargo run --example server unix:///tmp/1`

3. Start a client

    `$ cargo run --example client /tmp/1`

# Notes

The version of protobuf-codegen which you are using to generate codes should be exactly same with the version of protobuf library.

The reason is that [files generated by protobuf-codegen are compatible only with the same version of runtime](https://github.com/stepancheg/rust-protobuf/commit/2ab4d50c27c4dd7803b64ce1a43e2c134532c7a6)