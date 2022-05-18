# Basilisk-Node-Setup

## Section 1

### I go to the github Repo of Basilisk
![Screenshot](https://i.ibb.co/RjpykQT/image.png)

### I read the README.md

### I make a new Folder. I call it **BugFinding** 🐒.

![Screenshot](https://i.ibb.co/2ZzYzC7/image.png)

### I switch to my bash Shell, because my fish Shell could make trouble and I run the curl command in my new Folder.

![Screenshot](https://i.ibb.co/hdnQMzm/image.png)

### It finished and I run source ~/.cargo/env

![Screenshot](https://i.ibb.co/hY84fxR/image.png)

### I git clone the repo
![Screenshot](https://i.ibb.co/7GGj141/image.png)

### I go into The Folder, look whats inside there and run `make build`
![Screenshot](https://i.ibb.co/v42D25j/image.png)

### After my PC almost burned my legs, i recieved this error
![Screenshot](https://i.ibb.co/SXBsQbh/image.png)
![Screenshot](https://i.ibb.co/kmWZbb6/image.png)
```sh
rustc 
      --crate-name polkadot_cli 
      --edition=2018 /home/frank/.cargo/git/checkouts/polkadot-9da13ac14bbabc7b/de0ecd4/cli/src/lib.rs 
      --error-format=json 
      --json=diagnostic-rendered-ansi 
      --crate-type cdylib 
      --crate-type rlib 
      --emit=dep-info,link 
      -C opt-level=3 
      -C embed-bitcode=no 
      --cfg 'feature="clap"' 
      --cfg 'feature="cli"' 
      --cfg 'feature="db"' 
      --cfg 'feature="default"' 
      --cfg 'feature="frame-benchmarking-cli"' 
      --cfg 'feature="full-node"' 
      --cfg 'feature="polkadot-native"' 
      --cfg 'feature="polkadot-node-core-pvf"' 
      --cfg 'feature="polkadot-performance-test"' 
      --cfg 'feature="sc-cli"' 
      --cfg 'feature="sc-service"' 
      --cfg 'feature="sc-tracing"' 
      --cfg 'feature="service"' 
      --cfg 'feature="trie-memory-tracker"' 
      --cfg 'feature="try-runtime-cli"' 
      --cfg 'feature="wasmtime"' 
      -C metadata=ae7d5279fccf5e70 
      -C extra-filename=-ae7d5279fccf5e70 
      --out-dir /home/frank/BugFinding/Basilisk-node/target/release/deps 
      -L dependency=/home/frank/BugFinding/Basilisk-node/target/release/deps 
      --extern clap=/home/frank/BugFinding/Basilisk-node/target/release/deps/libclap-c6b67b9c8aecc8f5.rlib 
      --extern frame_benchmarking_cli=/home/frank/BugFinding/Basilisk-node/target/release/deps/libframe_benchmarking_cli-125ea57626bd8b70.rlib 
      --extern futures=/home/frank/BugFinding/Basilisk-node/target/release/deps/libfutures-64ed2158dc78bdf0.rlib 
      --extern log=/home/frank/BugFinding/Basilisk-node/target/release/deps/liblog-11f05d7eb3547cf7.rlib 
      --extern polkadot_node_core_pvf=/home/frank/BugFinding/Basilisk-node/target/release/deps/libpolkadot_node_core_pvf-de79f73567f312df.rlib 
      --extern polkadot_node_metrics=/home/frank/BugFinding/Basilisk-node/target/release/deps/libpolkadot_node_metrics-1a7a3817a7978e3e.rlib 
      --extern polkadot_performance_test=/home/frank/BugFinding/Basilisk-node/target/release/deps/libpolkadot_performance_test-cc6f7b07b18648b1.rlib 
      --extern service=/home/frank/BugFinding/Basilisk-node/target/release/deps/libpolkadot_service-6db3fe261fe3490e.rlib 
      --extern sc_cli=/home/frank/BugFinding/Basilisk-node/target/release/deps/libsc_cli-e8f24649f4f24fd9.rlib 
      --extern sc_service=/home/frank/BugFinding/Basilisk-node/target/release/deps/libsc_service-a48e013ec4c47881.rlib 
      --extern sc_tracing=/home/frank/BugFinding/Basilisk-node/target/release/deps/libsc_tracing-41c34a443ad52c83.rlib 
      --extern sp_core=/home/frank/BugFinding/Basilisk-node/target/release/deps/libsp_core-8553f53bdbc56604.rlib 
      --extern sp_trie=/home/frank/BugFinding/Basilisk-node/target/release/deps/libsp_trie-b7b6f3b73869bf0d.rlib 
      --extern thiserror=/home/frank/BugFinding/Basilisk-node/target/release/deps/libthiserror-928204ac2b80db45.rlib 
      --extern try_runtime_cli=/home/frank/BugFinding/Basilisk-node/target/release/deps/libtry_runtime_cli-2cf8a8c6302c6e05.rlib 
      --cap-lints allow 
      --cfg 'build_type="release"' 
      -L native=/home/frank/BugFinding/Basilisk-node/target/release/build/psm-62353cf8b10f4a34/out 
      -L native=/home/frank/BugFinding/Basilisk-node/target/release/build/zstd-sys-576be253ae324b87/out 
      -L native=/home/frank/BugFinding/Basilisk-node/target/release/build/wasmtime-runtime-3ca44e4281fef373/out 
      -L native=/home/frank/BugFinding/Basilisk-node/target/release/build/ring-fc0fc177158d3994/out 
      -L native=/home/frank/BugFinding/Basilisk-node/target/release/build/blake3-4ad677cfb9497af7/out 
      -L native=/home/frank/BugFinding/Basilisk-node/target/release/build/blake3-4ad677cfb9497af7/out 
      -L native=/home/frank/BugFinding/Basilisk-node/target/release/build/librocksdb-sys-81b6f015c39db987/out 
      -L native=/home/frank/BugFinding/Basilisk-node/target/release/build/librocksdb-sys-81b6f015c39db987/out 
      -L native=/home/frank/BugFinding/Basilisk-node/target/release/build/lz4-sys-575a5089c0868c75/out
```
## Section 2 - `polkadot-cli` BugFinding


### Reinstall polkadot with `--tag v0.9.21`, No Tag is not possible
![Screenshot](https://i.ibb.co/KVwz6HG/image.png)

### Story continues ...
most likely it will fail again and then I try maybe a VM or go to Docker or change some files or  ... I dont know, but that could be a long road ... 🛺
