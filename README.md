# 第二次挑战 · 姜佳岩

本仓库保存 SGLang 前缀缓存实验与请求流程阅读的提交材料。

## 提交与查看

- [提交压缩包：HW2-姜佳岩.zip](HW2-%E5%A7%9C%E4%BD%B3%E5%B2%A9.zip)
- [实验报告：report.pdf](report.pdf)
- [AI 使用说明情况（第二次挑战）.pdf](AI%20%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E%E6%83%85%E5%86%B5%EF%BC%88%E7%AC%AC%E4%BA%8C%E6%AC%A1%E6%8C%91%E6%88%98%EF%BC%89.pdf)

提交时使用 ZIP。根目录的两份 PDF 与 ZIP 内版本一致，供直接查看。
ZIP 解压后仅包含 `HW2-姜佳岩/` 一个根目录，其中包括：

```text
HW2-姜佳岩/
├── README.md
├── report.pdf
├── AI 使用说明情况（第二次挑战）.pdf
├── src/
│   ├── target1/  # 实验客户端与固定负载
│   ├── target2/  # 源码定位与学习讲义
│   └── report/   # 本人回答的文字快照
└── results/target1/
    ├── shared_prefix/run-1/
    ├── dispersed_prefix/run-1/
    ├── probe.json
    ├── run-1-comparison.json
    └── verification.json
```

## 实验与核对

- 实验日期：2026-10-01；材料更新：2026-10-03。
- SGLang 0.5.14、Ray 2.56.0、Qwen/Qwen3-0.6B。
- WSL Ubuntu-24.04，RTX 4060 Laptop GPU（8 GB）；Python 3.12.3、PyTorch 2.11.0、CUDA runtime 13.0、nvcc 13.0.88。
- 两组各 32 条测量请求，最大并发 8，输入 2112 token、输出 16 token，64 条全部成功。
- 共享前缀缓存命中率 96.9697%，分散前缀 0%；Prefill token 总数分别为 2048 和 67584。
- 逐请求数据、原始 SSE 事件、汇总统计与报告数据已核对。
- 报告正文 6 页，任务二流程图与说明共 2 页。

以上数据来自一次固定配置实验。安装、启动与完整运行说明见 ZIP 内的 `README.md`。

## 重跑

启动模型服务后，在另一个 Ubuntu 终端进入解压目录：

```bash
source ~/venvs/sglang/bin/activate
cd ~/HW2-姜佳岩
python src/target1/experiment.py run --run-name run-2
```

`cd` 使用实际解压位置。重跑复用包内固定负载，结果另存到两组的 `run-2/` 目录，保留提交中的 `run-1`；若 `run-2` 已有结果，使用 `run-3` 等新编号。

压缩包 SHA256：

```text
9f068e40a1fe1a087e7a94adf31758cc338addec2d78f968178f4705f04b1c55
```
