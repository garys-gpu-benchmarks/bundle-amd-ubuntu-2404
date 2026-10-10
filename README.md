# AMD ROCm - Ubuntu 24.04 benchmark bundle

32 system and GPU benchmarks for AMD GPU machines running Ubuntu 24.04,
each pinned to its tested v1.0.9 release.

Use this bundle only on that platform. The others have their own bundle:
[AMD 24.04](https://github.com/garys-gpu-benchmarks/bundle-amd-ubuntu-2404) ·
[NVIDIA 24.04](https://github.com/garys-gpu-benchmarks/bundle-nvidia-ubuntu-2404) ·
[AMD 26.04](https://github.com/garys-gpu-benchmarks/bundle-amd-ubuntu-2604) ·
[NVIDIA 26.04](https://github.com/garys-gpu-benchmarks/bundle-nvidia-ubuntu-2604)

## Before you start

- A freshly installed **Ubuntu 24.04** machine with AMD GPUs, connected to the internet.
- **root** access: log in as root, or run `sudo -i` first.
- Plenty of free disk space. Each benchmark installs its own software the first
  time it runs, and checks for at least 20 GiB free before it does. The AI
  benchmarks also download models.
- For the AI model benchmarks (123 to 131): if a model's license on Hugging
  Face requires it, accept the license there and set a token first:
  `export HF_TOKEN=hf_...`

## Install

```bash
apt-get update && apt-get install -y git tmux
git clone --recurse-submodules https://github.com/garys-gpu-benchmarks/bundle-amd-ubuntu-2404 /opt/benchmarks
cd /opt/benchmarks
./run.sh list
```

`./run.sh list` should show all 32 benchmarks as `ready`.
Do not use GitHub's **Download ZIP**: it leaves the benchmark folders empty.

## Getting started: three quick benchmarks

```bash
cd /opt/benchmarks
./run_benchmark_suite.sh -w 101,102,115 -p smoke
```

This runs the short `smoke` profile of three benchmarks:

| Benchmark | What it checks |
|---|---|
| 101 | the GPU software stack is installed and working |
| 102 | GPU health |
| 115 | GPU memory (HBM) bandwidth |

The first run takes much longer than later ones: it installs ROCm and each
benchmark's software. The install may restart the machine once. If it does,
log in again after the restart, wait a few minutes for setup to finish on its
own, and run the same command again.

Each run prints a short block, and the suite ends with a pass/fail summary.
The full output is in `/opt/benchmarks/benchmark_suite_log/`.

To run a single benchmark with its output on screen:

```bash
./run.sh 105                # setup, then the smoke profile of benchmark 105
./run.sh 105 --baseline     # the standard profile
```

## Run everything

Run the full suite inside `tmux`, so it keeps running if your connection drops.
It takes many hours.

```bash
tmux new -s bench
cd /opt/benchmarks
./run_benchmark_suite.sh
```

This runs all 32 benchmarks with the `smoke` profile, then all with
`baseline`, then all with `extended`. Detach with **Ctrl+B** then **D**;
reattach later with `tmux attach -t bench`.

Run "Getting started" first on a new machine, so the one-time install (and any
restart) happens before the long run.

| Option | What it does |
|---|---|
| `-p smoke` | profiles to run, in order (`smoke`, `baseline`, `extended`; comma-separated) |
| `-w 101,107,121` | only these benchmarks; ranges work too: `-w 101-110` |
| `-r 20` | repeat the whole set 20 times (soak test) |
| `--fail-fast` | stop at the first failed run |
| `-n` | show what would run, without running it |
| `--help` | all options |

## Results

| What | Where |
|---|---|
| Summary of the suite | end of the screen output |
| Full output of every run | `/opt/benchmarks/benchmark_suite_log/` |
| Each benchmark's results | `/opt/benchmarks/<benchmark>/results/` (`raw/` and `parsed/`) |
| One line per run (time, exit code) | `/var/opt/benchmarks/runtime_ledger.csv` |

To copy everything to a Windows laptop, use `get_remote_info.sh` from
[gpu-bench-suite](https://github.com/garys-gpu-benchmarks/gpu-bench-suite).

## Update to a newer release

```bash
cd /opt/benchmarks
git pull && git submodule update --init --recursive
```

Copies made before v1.0.5 keep their benchmarks in a `benchmarks/` subfolder;
delete those and clone again as shown under Install.

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

