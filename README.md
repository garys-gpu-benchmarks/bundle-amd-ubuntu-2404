# AMD ROCm - Ubuntu 24.04 benchmark bundle

All 32 benchmarks for this platform, each pinned to its tested v1.0.6 commit as a git submodule.
Project home: https://github.com/garymichaelbass

## Install

On a fresh Ubuntu machine, this downloads all 32 benchmarks into /opt/benchmarks:

```bash
git clone --recurse-submodules https://github.com/garys-gpu-benchmarks/bundle-amd-ubuntu-2404 /opt/benchmarks
```

As a normal user (not root), first install git and create the folder:

```bash
sudo apt-get update && sudo apt-get install -y git
sudo mkdir -p /opt/benchmarks && sudo chown "$USER":"$USER" /opt/benchmarks
git clone --recurse-submodules https://github.com/garys-gpu-benchmarks/bundle-amd-ubuntu-2404 /opt/benchmarks
```

Each benchmark is then in its own folder, for example /opt/benchmarks/101-…, next to run.sh and run_benchmark_suite.sh. Check with:

```bash
cd /opt/benchmarks && ./run.sh list
```

`./run.sh list` should show all 32 benchmarks as `ready`. To download only the benchmarks you run, leave out `--recurse-submodules`: `./run.sh` then fetches each benchmark the first time it is used.

Do not use Download ZIP: GitHub's ZIP files leave the benchmark folders empty.

## Run

```bash
cd /opt/benchmarks
./run.sh 105                 # setup, then a smoke run of benchmark 105
./run.sh 105 --baseline      # standard run
./run.sh all                 # all 32, logs in results/
```

The first benchmark's setup may install the GPU software stack, ask for your sudo password, and need a reboot. Read each benchmark's README.md before running it.

## Run the whole suite

`run_benchmark_suite.sh` runs every installed benchmark with each profile (smoke, then baseline, then extended), prints one short block per run, keeps the full output in a log file, and ends with a pass/fail summary.

```bash
cd /opt/benchmarks
./run_benchmark_suite.sh                         # all 32 benchmarks, smoke + baseline + extended
./run_benchmark_suite.sh -p smoke                # quick check of everything
./run_benchmark_suite.sh -w 101,107,121 -p baseline  # chosen benchmarks only
./run_benchmark_suite.sh -r 20                   # repeat the whole set 20 times
./run_benchmark_suite.sh --help                  # all options
```

## Update

```bash
cd /opt/benchmarks
git pull && git submodule update --init --recursive
```

If your copy keeps its benchmarks in a benchmarks/ subfolder (bundles published before v1.0.5), delete it and clone again instead, as shown under Install.

## Benchmarks

- **101** - [101-sys-bench-amd-rocm-stack-validation-ubu2404](https://github.com/garys-gpu-benchmarks/101-sys-bench-amd-rocm-stack-validation-ubu2404)
- **102** - [102-sys-bench-amd-rocm-health-validation-ubu2404](https://github.com/garys-gpu-benchmarks/102-sys-bench-amd-rocm-health-validation-ubu2404)
- **103** - [103-sys-bench-amd-system-stress-stability-ubu2404](https://github.com/garys-gpu-benchmarks/103-sys-bench-amd-system-stress-stability-ubu2404)
- **104** - [104-gpu-bench-amd-sdc-ecc-integrity-ubu2404](https://github.com/garys-gpu-benchmarks/104-gpu-bench-amd-sdc-ecc-integrity-ubu2404)
- **105** - [105-gpu-bench-amd-pytorch-tensor-correctness-ubu2404](https://github.com/garys-gpu-benchmarks/105-gpu-bench-amd-pytorch-tensor-correctness-ubu2404)
- **106** - [106-sys-bench-amd-fio-nvme-sweep-ubu2404](https://github.com/garys-gpu-benchmarks/106-sys-bench-amd-fio-nvme-sweep-ubu2404)
- **107** - [107-sys-bench-amd-stream-ddr5-bandwidth-ubu2404](https://github.com/garys-gpu-benchmarks/107-sys-bench-amd-stream-ddr5-bandwidth-ubu2404)
- **108** - [108-sys-bench-amd-iperf3-network-performance-ubu2404](https://github.com/garys-gpu-benchmarks/108-sys-bench-amd-iperf3-network-performance-ubu2404)
- **109** - [109-sys-bench-amd-multichase-numa-latency-ubu2404](https://github.com/garys-gpu-benchmarks/109-sys-bench-amd-multichase-numa-latency-ubu2404)
- **110** - [110-sys-bench-amd-numa-cache-performance-ubu2404](https://github.com/garys-gpu-benchmarks/110-sys-bench-amd-numa-cache-performance-ubu2404)
- **111** - [111-sys-bench-amd-linux-perf-pmu-ubu2404](https://github.com/garys-gpu-benchmarks/111-sys-bench-amd-linux-perf-pmu-ubu2404)
- **112** - [112-sys-bench-amd-lmbench-microbench-suite-ubu2404](https://github.com/garys-gpu-benchmarks/112-sys-bench-amd-lmbench-microbench-suite-ubu2404)
- **113** - [113-sys-bench-amd-gups-random-memory-ubu2404](https://github.com/garys-gpu-benchmarks/113-sys-bench-amd-gups-random-memory-ubu2404)
- **114** - [114-gpu-bench-amd-hipmemcpy-transfer-bandwidth-ubu2404](https://github.com/garys-gpu-benchmarks/114-gpu-bench-amd-hipmemcpy-transfer-bandwidth-ubu2404)
- **115** - [115-gpu-bench-amd-babelstream-hbm-bandwidth-ubu2404](https://github.com/garys-gpu-benchmarks/115-gpu-bench-amd-babelstream-hbm-bandwidth-ubu2404)
- **116** - [116-gpu-bench-amd-rccl-bandwidth-test-ubu2404](https://github.com/garys-gpu-benchmarks/116-gpu-bench-amd-rccl-bandwidth-test-ubu2404)
- **117** - [117-gpu-bench-amd-gemm-rocblas-micro-ubu2404](https://github.com/garys-gpu-benchmarks/117-gpu-bench-amd-gemm-rocblas-micro-ubu2404)
- **118** - [118-gpu-bench-amd-miopen-convolution-micro-ubu2404](https://github.com/garys-gpu-benchmarks/118-gpu-bench-amd-miopen-convolution-micro-ubu2404)
- **119** - [119-gpu-bench-amd-torch-micro-suite-ubu2404](https://github.com/garys-gpu-benchmarks/119-gpu-bench-amd-torch-micro-suite-ubu2404)
- **120** - [120-gpu-bench-amd-linpack-rochpl-fp64-ubu2404](https://github.com/garys-gpu-benchmarks/120-gpu-bench-amd-linpack-rochpl-fp64-ubu2404)
- **121** - [121-gpu-bench-amd-resnet50-pytorch-training-ubu2404](https://github.com/garys-gpu-benchmarks/121-gpu-bench-amd-resnet50-pytorch-training-ubu2404)
- **122** - [122-gpu-bench-amd-resnet50-pytorch-inference-ubu2404](https://github.com/garys-gpu-benchmarks/122-gpu-bench-amd-resnet50-pytorch-inference-ubu2404)
- **123** - [123-gpu-bench-amd-bert-base-inference-ubu2404](https://github.com/garys-gpu-benchmarks/123-gpu-bench-amd-bert-base-inference-ubu2404)
- **124** - [124-gpu-bench-amd-sdxl-diffusers-latency-ubu2404](https://github.com/garys-gpu-benchmarks/124-gpu-bench-amd-sdxl-diffusers-latency-ubu2404)
- **125** - [125-gpu-bench-amd-distilbert-hf-classification-ubu2404](https://github.com/garys-gpu-benchmarks/125-gpu-bench-amd-distilbert-hf-classification-ubu2404)
- **126** - [126-gpu-bench-amd-jax-xla-forwardpass-ubu2404](https://github.com/garys-gpu-benchmarks/126-gpu-bench-amd-jax-xla-forwardpass-ubu2404)
- **127** - [127-gpu-bench-amd-vllm-kvcache-stress-ubu2404](https://github.com/garys-gpu-benchmarks/127-gpu-bench-amd-vllm-kvcache-stress-ubu2404)
- **128** - [128-gpu-bench-amd-vllm-throughput-latency-ubu2404](https://github.com/garys-gpu-benchmarks/128-gpu-bench-amd-vllm-throughput-latency-ubu2404)
- **129** - [129-gpu-bench-amd-vllm-mistral-rocm-ubu2404](https://github.com/garys-gpu-benchmarks/129-gpu-bench-amd-vllm-mistral-rocm-ubu2404)
- **130** - [130-gpu-bench-amd-sglang-prompt-response-ubu2404](https://github.com/garys-gpu-benchmarks/130-gpu-bench-amd-sglang-prompt-response-ubu2404)
- **131** - [131-gpu-bench-amd-sglang-serving-latency-ubu2404](https://github.com/garys-gpu-benchmarks/131-gpu-bench-amd-sglang-serving-latency-ubu2404)
- **132** - [132-gpu-bench-amd-rag-faiss-end2end-ubu2404](https://github.com/garys-gpu-benchmarks/132-gpu-bench-amd-rag-faiss-end2end-ubu2404)

