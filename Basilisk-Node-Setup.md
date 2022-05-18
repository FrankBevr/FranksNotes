
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

### Got the same error but 2021 edition 😐
![Screenshot](https://i.ibb.co/B62fGJ6/image.png)
https://i.ibb.co/B62fGJ6/image.png
```sh
rustc 
  --crate-name polkadot_cli 
  --edition=2021 cli/src/lib.rs 
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
  --cfg 'feature="kusama-native"' 
  --cfg 'feature="polkadot-client"' 
  --cfg 'feature="polkadot-native"' 
  --cfg 'feature="polkadot-node-core-pvf"' 
  --cfg 'feature="polkadot-performance-test"' 
  --cfg 'feature="rococo-native"' 
  --cfg 'feature="sc-cli"' 
  --cfg 'feature="sc-service"' 
  --cfg 'feature="sc-tracing"' 
  --cfg 'feature="service"' 
  --cfg 'feature="trie-memory-tracker"' 
  --cfg 'feature="try-runtime-cli"' 
  --cfg 'feature="wasmtime"' 
  --cfg 'feature="westend-native"' 
  -C metadata=7f1e4e10e83efa4d 
  --out-dir /tmp/cargo-installRRDXGO/release/deps 
  -L dependency=/tmp/cargo-installRRDXGO/release/deps 
  --extern clap=/tmp/cargo-installRRDXGO/release/deps/libclap-67180049c03c1774.rlib 
  --extern frame_benchmarking_cli=/tmp/cargo-installRRDXGO/release/deps/libframe_benchmarking_cli-889a275a14595224.rlib 
  --extern futures=/tmp/cargo-installRRDXGO/release/deps/libfutures-faba47a47099c091.rlib 
  --extern log=/tmp/cargo-installRRDXGO/release/deps/liblog-9bdf5b6277bfbc51.rlib 
  --extern polkadot_client=/tmp/cargo-installRRDXGO/release/deps/libpolkadot_client-6629dbde29368f11.rlib 
  --extern polkadot_node_core_pvf=/tmp/cargo-installRRDXGO/release/deps/libpolkadot_node_core_pvf-ac6132bd9194becb.rlib 
  --extern polkadot_node_metrics=/tmp/cargo-installRRDXGO/release/deps/libpolkadot_node_metrics-bbf0e8c0ef8974a0.rlib 
  --extern polkadot_performance_test=/tmp/cargo-installRRDXGO/release/deps/libpolkadot_performance_test-3a9019484fbc0e90.rlib 
  --extern service=/tmp/cargo-installRRDXGO/release/deps/libpolkadot_service-07416f81ed098893.rlib 
  --extern sc_cli=/tmp/cargo-installRRDXGO/release/deps/libsc_cli-b0e2f6b529d57517.rlib 
  --extern sc_service=/tmp/cargo-installRRDXGO/release/deps/libsc_service-40c60fbb3f253596.rlib 
  --extern sc_tracing=/tmp/cargo-installRRDXGO/release/deps/libsc_tracing-b789ec3d40adef14.rlib 
  --extern sp_core=/tmp/cargo-installRRDXGO/release/deps/libsp_core-648641ae987f2663.rlib 
  --extern sp_trie=/tmp/cargo-installRRDXGO/release/deps/libsp_trie-55a883554852bbdb.rlib 
  --extern thiserror=/tmp/cargo-installRRDXGO/release/deps/libthiserror-092adf41dd3afe3e.rlib 
  --extern try_runtime_cli=/tmp/cargo-installRRDXGO/release/deps/libtry_runtime_cli-5287f1ba00d747f7.rlib 
  --cfg 'build_type="release"' 
  -L native=/tmp/cargo-installRRDXGO/release/build/tikv-jemalloc-sys-a141bf6f954b632a/out/build/lib 
  -L native=/tmp/cargo-installRRDXGO/release/build/secp256k1-sys-4ed5f554ed721c19/out 
  -L native=/tmp/cargo-installRRDXGO/release/build/psm-23a29a2de79ff90f/out 
  -L src/imp/linux_raw/arch/outline/release -L native=/tmp/cargo-installRRDXGO/release/build/zstd-sys-bfc1d02e200f82fb/out 
  -L native=/tmp/cargo-installRRDXGO/release/build/wasmtime-runtime-f91edc9bfb69a2a1/out 
  -L native=/tmp/cargo-installRRDXGO/release/build/ring-d1bb17fce8d8df4b/out 
  -L native=/tmp/cargo-installRRDXGO/release/build/libz-sys-0ba56d5eb34bf760/out/lib 
  -L native=/tmp/cargo-installRRDXGO/release/build/libz-sys-0ba56d5eb34bf760/out/lib 
  -L native=/tmp/cargo-installRRDXGO/release/build/blake3-f0a6be6e5f25ab28/out 
  -L native=/tmp/cargo-installRRDXGO/release/build/blake3-f0a6be6e5f25ab28/out 
  -L native=/tmp/cargo-installRRDXGO/release/build/librocksdb-sys-f39d5b2ee0acbe7f/out 
  -L native=/tmp/cargo-installRRDXGO/release/build/librocksdb-sys-f39d5b2ee0acbe7f/out 
  -L native=/tmp/cargo-installRRDXGO/release/build/bzip2-sys-56a72a1f81dd5259/out/lib 
  -L native=/tmp/cargo-installRRDXGO/release/build/lz4-sys-607aff43723f5693/out
```

### Docker Trial

`docker compose up` didn't work and `docker image` didn't work

I restarted my docker with `service start docker`

`docker compose up` throw and wsl error, i read the [docs](https://docs.docker.com/desktop/windows/wsl/)

I recognized that my Docker on my wsl was working but the latest version of docker allowed wsl to communicate with my Docker Windows.

I updated my docker

Restarted my PC

`docker compose up` is now running

![screenshot](https://i.ibb.co/YZ9c2dp/image.png)

Aaand it failed. At least now I know that its unlikely that the problem is own my side. Its the same Error and its running in Docker, which means it is own isoleted System. 

![screenshot](https://i.ibb.co/DYXwKHd/image.png)

### Story continues ...

I guess the next test would be to run it own a remote server. ufff looong roaaad 🛺

