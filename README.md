# AMD ROCm - Ubuntu 24.04 benchmark bundle

All 32 benchmarks for this platform, each pinned to its tested v1.0.3 commit as a git submodule.
Project home: https://github.com/garymichaelbass

```bash
git clone --recurse-submodules https://github.com/garys-gpu-benchmarks/bundle-amd-ubuntu-2404.git
cd bundle-amd-ubuntu-2404
./run.sh list                # the 32 benchmarks
./run.sh 105                 # smoke run of benchmark 105
./run.sh 105 --baseline      # standard run
./run.sh all                 # all 32, logs in results/
```

Clone without --recurse-submodules to download only what you run: ./run.sh fetches each benchmark on first use.

Do not use Download ZIP: GitHub's ZIP files leave the benchmarks/ folders empty.

## Benchmarks

- **101** - `benchmarks/amd-u24-101` - [101-sys-bench-amd-rocm-stack-validation-ubu2404](https://github.com/garys-gpu-benchmarks/101-sys-bench-amd-rocm-stack-validation-ubu2404)
- **102** - `benchmarks/amd-u24-102` - [102-sys-bench-amd-rocm-health-validation-ubu2404](https://github.com/garys-gpu-benchmarks/102-sys-bench-amd-rocm-health-validation-ubu2404)
- **103** - `benchmarks/amd-u24-103` - [103-sys-bench-amd-system-stress-stability-ubu2404](https://github.com/garys-gpu-benchmarks/103-sys-bench-amd-system-stress-stability-ubu2404)
- **104** - `benchmarks/amd-u24-104` - [104-gpu-bench-amd-sdc-ecc-integrity-ubu2404](https://github.com/garys-gpu-benchmarks/104-gpu-bench-amd-sdc-ecc-integrity-ubu2404)
- **105** - `benchmarks/amd-u24-105` - [105-gpu-bench-amd-pytorch-tensor-correctness-ubu2404](https://github.com/garys-gpu-benchmarks/105-gpu-bench-amd-pytorch-tensor-correctness-ubu2404)
- **106** - `benchmarks/amd-u24-106` - [106-sys-bench-amd-fio-nvme-sweep-ubu2404](https://github.com/garys-gpu-benchmarks/106-sys-bench-amd-fio-nvme-sweep-ubu2404)
- **107** - `benchmarks/amd-u24-107` - [107-sys-bench-amd-stream-ddr5-bandwidth-ubu2404](https://github.com/garys-gpu-benchmarks/107-sys-bench-amd-stream-ddr5-bandwidth-ubu2404)
- **108** - `benchmarks/amd-u24-108` - [108-sys-bench-amd-iperf3-network-performance-ubu2404](https://github.com/garys-gpu-benchmarks/108-sys-bench-amd-iperf3-network-performance-ubu2404)
- **109** - `benchmarks/amd-u24-109` - [109-sys-bench-amd-multichase-numa-latency-ubu2404](https://github.com/garys-gpu-benchmarks/109-sys-bench-amd-multichase-numa-latency-ubu2404)
- **110** - `benchmarks/amd-u24-110` - [110-sys-bench-amd-numa-cache-performance-ubu2404](https://github.com/garys-gpu-benchmarks/110-sys-bench-amd-numa-cache-performance-ubu2404)
- **111** - `benchmarks/amd-u24-111` - [111-sys-bench-amd-linux-perf-pmu-ubu2404](https://github.com/garys-gpu-benchmarks/111-sys-bench-amd-linux-perf-pmu-ubu2404)
- **112** - `benchmarks/amd-u24-112` - [112-sys-bench-amd-lmbench-microbench-suite-ubu2404](https://github.com/garys-gpu-benchmarks/112-sys-bench-amd-lmbench-microbench-suite-ubu2404)
- **113** - `benchmarks/amd-u24-113` - [113-sys-bench-amd-gups-random-memory-ubu2404](https://github.com/garys-gpu-benchmarks/113-sys-bench-amd-gups-random-memory-ubu2404)
- **114** - `benchmarks/amd-u24-114` - [114-gpu-bench-amd-hipmemcpy-transfer-bandwidth-ubu2404](https://github.com/garys-gpu-benchmarks/114-gpu-bench-amd-hipmemcpy-transfer-bandwidth-ubu2404)
- **115** - `benchmarks/amd-u24-115` - [115-gpu-bench-amd-babelstream-hbm-bandwidth-ubu2404](https://github.com/garys-gpu-benchmarks/115-gpu-bench-amd-babelstream-hbm-bandwidth-ubu2404)
- **116** - `benchmarks/amd-u24-116` - [116-gpu-bench-amd-rccl-bandwidth-test-ubu2404](https://github.com/garys-gpu-benchmarks/116-gpu-bench-amd-rccl-bandwidth-test-ubu2404)
- **117** - `benchmarks/amd-u24-117` - [117-gpu-bench-amd-gemm-rocblas-micro-ubu2404](https://github.com/garys-gpu-benchmarks/117-gpu-bench-amd-gemm-rocblas-micro-ubu2404)
- **118** - `benchmarks/amd-u24-118` - [118-gpu-bench-amd-miopen-convolution-micro-ubu2404](https://github.com/garys-gpu-benchmarks/118-gpu-bench-amd-miopen-convolution-micro-ubu2404)
- **119** - `benchmarks/amd-u24-119` - [119-gpu-bench-amd-torch-micro-suite-ubu2404](https://github.com/garys-gpu-benchmarks/119-gpu-bench-amd-torch-micro-suite-ubu2404)
- **120** - `benchmarks/amd-u24-120` - [120-gpu-bench-amd-linpack-rochpl-fp64-ubu2404](https://github.com/garys-gpu-benchmarks/120-gpu-bench-amd-linpack-rochpl-fp64-ubu2404)
- **121** - `benchmarks/amd-u24-121` - [121-gpu-bench-amd-resnet50-pytorch-training-ubu2404](https://github.com/garys-gpu-benchmarks/121-gpu-bench-amd-resnet50-pytorch-training-ubu2404)
- **122** - `benchmarks/amd-u24-122` - [122-gpu-bench-amd-resnet50-pytorch-inference-ubu2404](https://github.com/garys-gpu-benchmarks/122-gpu-bench-amd-resnet50-pytorch-inference-ubu2404)
- **123** - `benchmarks/amd-u24-123` - [123-gpu-bench-amd-bert-base-inference-ubu2404](https://github.com/garys-gpu-benchmarks/123-gpu-bench-amd-bert-base-inference-ubu2404)
- **124** - `benchmarks/amd-u24-124` - [124-gpu-bench-amd-sdxl-diffusers-latency-ubu2404](https://github.com/garys-gpu-benchmarks/124-gpu-bench-amd-sdxl-diffusers-latency-ubu2404)
- **125** - `benchmarks/amd-u24-125` - [125-gpu-bench-amd-distilbert-hf-classification-ubu2404](https://github.com/garys-gpu-benchmarks/125-gpu-bench-amd-distilbert-hf-classification-ubu2404)
- **126** - `benchmarks/amd-u24-126` - [126-gpu-bench-amd-jax-xla-forwardpass-ubu2404](https://github.com/garys-gpu-benchmarks/126-gpu-bench-amd-jax-xla-forwardpass-ubu2404)
- **127** - `benchmarks/amd-u24-127` - [127-gpu-bench-amd-vllm-kvcache-stress-ubu2404](https://github.com/garys-gpu-benchmarks/127-gpu-bench-amd-vllm-kvcache-stress-ubu2404)
- **128** - `benchmarks/amd-u24-128` - [128-gpu-bench-amd-vllm-throughput-latency-ubu2404](https://github.com/garys-gpu-benchmarks/128-gpu-bench-amd-vllm-throughput-latency-ubu2404)
- **129** - `benchmarks/amd-u24-129` - [129-gpu-bench-amd-vllm-mistral-rocm-ubu2404](https://github.com/garys-gpu-benchmarks/129-gpu-bench-amd-vllm-mistral-rocm-ubu2404)
- **130** - `benchmarks/amd-u24-130` - [130-gpu-bench-amd-sglang-prompt-response-ubu2404](https://github.com/garys-gpu-benchmarks/130-gpu-bench-amd-sglang-prompt-response-ubu2404)
- **131** - `benchmarks/amd-u24-131` - [131-gpu-bench-amd-sglang-serving-latency-ubu2404](https://github.com/garys-gpu-benchmarks/131-gpu-bench-amd-sglang-serving-latency-ubu2404)
- **132** - `benchmarks/amd-u24-132` - [132-gpu-bench-amd-rag-faiss-end2end-ubu2404](https://github.com/garys-gpu-benchmarks/132-gpu-bench-amd-rag-faiss-end2end-ubu2404)
