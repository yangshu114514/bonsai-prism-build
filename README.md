# bonsai-prism-build

PrismML/llama.cpp `prism` 分支（支持 PQ2_0）的 Linux CUDA 自编译产物，供 Kaggle T4 部署直接下载。

- 源码：https://github.com/PrismML-Eng/llama.cpp （prism 分支 HEAD c96baf4，2026-10-25）
- 编译参数：`GGML_CUDA=ON` `CMAKE_CUDA_ARCHITECTURES=75`（T4 原生 Turing）
  `GGML_CUDA_FA_ALL_QUANTS=ON` `GGML_NATIVE=ON`，CUDA 12.8.1 工具链
- 相比官方 release 二进制的差异：仅含 sm_75 原生内核、开启 FA 全量化组合、
  含 release 之后未发版的提交（视觉编码器 2.2x @2048²）
- 解压后与官方包同构：`llama-server` 薄壳 + `libggml-*.so` / `libllama-*.so`，运行时依赖
  系统 `libcuda.so.1`（驱动）与 cu12 运行库

下载：`https://github.com/yangshu114514/bonsai-prism-build/releases/download/v1/bonsai-sm75.tar.gz`
