# Awesome-GPU-Orchestration-Allocation-Schedulers

# Top GPU Orchestration & Allocation Schedulers Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on GPU Fractioning, Workload Scheduling & Cluster Utilization*  
**Last updated: October 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **GPU Orchestration & Allocation Schedulers**. These tools enable organizations to maximize GPU utilization, prevent compute idling during sporadic agent calls, and share expensive accelerators across teams—using fractional allocation, gang scheduling, and quota-based resource governance.

**Examples** include Run:ai, CoreWeave, Lambda Labs, Modal, RunPod, Prime Intellect, Shadeform, Together GPU Clusters, Nebius AI Studio, and Crusoe Cloud (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, Kubernetes-native GPU scheduling, and open workload orchestration—ideal for ML platform teams, AI infrastructure engineers, and developers seeking transparent, vendor-independent GPU management.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[CoreWeave](https://www.coreweave.com/)**  
  The AI Hyperscaler™ providing purpose-built cloud infrastructure for accelerated computing. First cloud provider to deploy **NVIDIA H200 Tensor Core GPUs** and bring up an **NVIDIA GB200 NVL72 cluster** . Features **Mission Control** for automated node lifecycle management, proactive health checking, and fleet reliability . Deployed in clusters of up to **42,000 GPUs** with 3200Gbps NVIDIA Quantum-2 InfiniBand networking . Also offers **NVIDIA GH200 Grace Hopper Superchips** with 96GB HBM3 and 480GB CPU memory, plus L40/L40S instances for inference workloads .

- **[Nebius AI Studio](https://nebius.com/)**  
  AI cloud with managed Kubernetes and **NVIDIA Run:ai** available as an application . Joint benchmarks with NVIDIA showed **fractional GPU allocation at 0.5 GPU delivers 77% of full-GPU throughput and 86% of concurrent-user capacity** . Co-locating chat, reasoning, and embedding models on shared GPUs served **roughly 3x more total users** than dedicated allocation, with combined throughput above **350k tokens per second** . Provides high-performance NVIDIA infrastructure with dynamic workload orchestration across teams.

- **[Lambda Labs](https://lambdalabs.com/)**  
  GPU cloud platform with on-demand and reserved instances for AI training and inference. Features one-click Jupyter notebooks, pre-configured ML environments, and multi-node cluster support.

- **[Modal](https://modal.com/)**  
  Serverless GPU platform with **gVisor container isolation** and native GPU support (A10G, A100, H100). Scales to **50,000+ concurrent containers**. Python-first API with sub-second cold starts. Sandbox workloads priced at ~$0.14/vCPU-hour.

- **[RunPod](https://www.runpod.io/)**  
  GPU cloud with serverless endpoints, pods, and secure cloud options. Features instant deployment, per-second billing, and community cloud pricing.

- **[Prime Intellect](https://www.primeintellect.ai/)**  
  Decentralized GPU cloud aggregating compute across providers. Features competitive pricing, global availability, and support for distributed training workloads.

- **[Shadeform](https://www.shadeform.ai/)**  
  Multi-cloud GPU platform aggregating instances across providers. Features price comparison, unified API, and workload portability across clouds.

- **[Together GPU Clusters](https://www.together.ai/)**  
  Full-stack generative AI platform with managed GPU clusters for training and inference. Features instant deployment, auto-scaling, and pay-per-token pricing for inference.

- **[Crusoe Cloud](https://crusoe.ai/)**  
  Carbon-reduced GPU cloud infrastructure. Features on-demand and reserved instances, managed Kubernetes, and sustainability-focused compute.

## Open-Source GitHub Projects

- **[KAI Scheduler (NVIDIA)](https://github.com/NVIDIA/KAI-Scheduler)**  
  **The most production-grade open-source GPU scheduler for Kubernetes** (Apache-2.0, CNCF Sandbox project) . Powers **NVIDIA Run:ai** and is the upstream engine for all Run:ai scheduling development . Features: **gang scheduling** (all pods in a group scheduled together or not at all), **bin-packing and spread scheduling**, **hierarchical queues** for organizational control, **Dominant Resource Fairness (DRF)**, **workload consolidation** for defragmentation, **elastic workloads**, **Dynamic Resource Allocation (DRA)** for vendor-specific hardware, and **GPU sharing** for fractional allocation . Deployed in clusters of thousands of nodes with high-throughput workloads. **The de facto standard for open-source GPU scheduling at scale** .

- **[NVIDIA Run:ai (Open Source)](https://github.com/NVIDIA/run-ai)**  
  **The full Run:ai platform is now open source** (October 2026) as part of NVIDIA DSX AI Factory Platform . Provides **production-grade AI workload and GPU orchestration** for Kubernetes . Four modular components: **KAI Scheduler** (scheduling engine), **GPU Fractioning Operator** (CUDA-native fractional GPU allocation with hard memory isolation), **KAI Resource Management** (projects, departments, quotas, node pools), and **Workload Map** (workload-management contract for PyTorchJobs, RayClusters, custom resources) . Available on NGC as a Community Product with Helm chart—**no paid subscription or NVIDIA support entitlement required** . **The most comprehensive open-source GPU orchestration platform available.**

- **[GPU Fractioning Operator (NVIDIA)](https://github.com/NVIDIA/k8s-gpu-fractioning-operator)**  
  **CUDA-native GPU fractioning for Kubernetes** (Apache-2.0) . Brings the fractional GPU capability that Run:ai pioneered to the open-source community. The CUDA driver enforces a **hard limit on GPU memory** for each workload—each workload sees only the GPU memory allocated to its fraction . Provides a metrics exporter for per-pod visibility into fractions in use. **Scheduler-agnostic**—works with KAI Scheduler or other schedulers . **Critical for preventing compute idling**—enables interactive notebooks and smaller inference models to share underutilized GPU capacity without reserving full devices .

- **[NVIDIA GPU Operator](https://github.com/NVIDIA/gpu-operator)**  
  **Automates the management of NVIDIA software components required to provision GPU nodes** in Kubernetes . Manages the full stack: **Node Feature Discovery (NFD)** for hardware detection, **NVIDIA Driver** via DaemonSet, **NVIDIA Container Toolkit** for runtime configuration, **NVIDIA Device Plugin** for schedulable resources (nvidia.com/gpu), **NVIDIA DRA Driver** for Dynamic Resource Allocation, **MIG Manager** for Multi-Instance GPU partitioning, and **DCGM Exporter** for telemetry . **The foundational GPU infrastructure layer** for any Kubernetes-based GPU cluster .

- **[NVIDIA Device Plugin](https://github.com/NVIDIA/k8s-device-plugin)**  
  Lightweight GPU scheduling for Kubernetes (Apache-2.0). Discovers GPUs on worker nodes and advertises them as extended resources (nvidia.com/gpu) . **Option A (Simple Path)**—ideal for standard workloads where containers consume whole, un-partitioned GPUs . **Choose this when you don't need MIG slicing or advanced features** . The GPU Operator already contains the device plugin internally—do not deploy both independently or they will conflict .

- **[KubeRay](https://github.com/ray-project/kuberay)**  
  Kubernetes operator for Ray (Apache-2.0, CNCF Sandbox project). Provides **RayCluster, RayJob, and RayService** custom resources for managing Ray workloads . Explicitly tailored for Ray's **stateful head/worker architecture, actor-based dynamic placement, fine-grained GPU/TPU resource allocation, and zero-downtime model serving** . Integrates with **Cluster Autoscaler and KEDA** for scaling, and standard Ingress controllers for exposing Ray Dashboard and Ray Serve endpoints . **Critical for multi-model serving on shared GPUs**—Ray Serve wraps vLLM for multi-replica autoscaling and multi-model routing . **Production rule**: Ray Head should NOT be co-located on GPU nodes—place head on CPU instance (m5.xlarge) to avoid wasting GPU memory on scheduler processes .

- **[Slurm](https://github.com/SchedMD/slurm)**  
  **The most widely deployed HPC workload manager** with mature GPU support (GPL-2.0). Features **GRES (Generic Resource Scheduling)** for GPU allocation, **preemptable queues** for opportunistic GPU access, and **constraint-based GPU type selection** . Supports **VRAM-per-GPU requests** via no_consume GRES for memory-aware scheduling . **Preemption with requeue** enables long-running jobs to be interrupted and restarted—critical for cluster utilization . **The standard for on-premise HPC clusters** and research environments.

- **[vLLM](https://github.com/vllm-project/vllm)**  
  **The most widely used open-source LLM inference engine** (Apache-2.0) . Features **PagedAttention** for efficient KV cache management, **continuous batching** for throughput, and **Sleep Mode** for releasing GPU memory without stopping the server . **Hierarchical paging** (MIT research) extends vLLM for **efficient multi-model serving on shared GPUs**—organizes block allocation in two-level hierarchy (large blocks per model layer, subdivided into small blocks per request) with **memory isolation** between models . **The foundation for multi-model GPU sharing**—pairs with KubeRay for autoscaling and multi-replica serving .

- **[Kueue](https://github.com/kubernetes-sigs/kueue)**  
  Kubernetes-native job queueing (Apache-2.0) for **quota-based scheduling and fair sharing** across teams . Manages workload queues with priorities, preemption, and borrowing policies. **Complements KAI Scheduler** for organizational quota management.

### Additional Strong Open-Source Options

- **[Volcano](https://github.com/volcano-sh/volcano)** — Cloud-native batch scheduling system (Apache-2.0) for high-performance workloads. CNCF Incubating project with gang scheduling, queue management, and GPU sharing.
- **[Kubeflow](https://github.com/kubeflow/kubeflow)** — ML toolkit for Kubernetes (Apache-2.0) with training operator and pipeline orchestration.
- **[Ray](https://github.com/ray-project/ray)** — Distributed computing framework (Apache-2.0) with Ray Serve for model serving and Ray Train for distributed training.
- **[KEDA](https://github.com/kedacore/keda)** — Kubernetes Event-driven Autoscaling (Apache-2.0) for scaling workloads based on custom metrics.
- **[NVIDIA DCGM](https://github.com/NVIDIA/DCGM)** — Data Center GPU Manager for telemetry collection (GPU usage, temperature, power) exposed to Prometheus and Grafana .
- **[vLLM Production Stack](https://github.com/vllm-project/production-stack)** — Reference architecture for deploying vLLM at scale with router, autoscaler, and observability.
- Community **n8n** workflows for GPU utilization alerting and workload scheduling automation.

**Frameworks for building custom systems**: Combine **KAI Scheduler** for GPU-aware scheduling with **GPU Fractioning Operator** for memory-isolated sharing, **KubeRay + Ray Serve** for multi-model serving, **vLLM** for inference engine, and **NVIDIA GPU Operator** for infrastructure automation—creating a fully self-hosted, enterprise-grade GPU orchestration platform that prevents compute idling during sporadic agent calls.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- GPU orchestration systems controlling expensive accelerators must implement appropriate resource governance, access controls, and cost monitoring.
- **Open-source GPU orchestration is mature and production-grade.** KAI Scheduler powers NVIDIA Run:ai and is a CNCF Sandbox project . The full Run:ai platform is now open source with no paid subscription required for the Community Product . **These are genuine alternatives to commercial platforms.**
- **Fractional GPU allocation prevents compute idling.** The utilization math is compelling: **0.5 GPU delivers 77% of throughput and 86% of concurrent users** . Co-locating chat, reasoning, and embedding models on shared GPUs served **3x more users** than dedicated allocation . **All-or-nothing GPU allocation leaves capacity idle on every GPU that isn't saturated.**
- **Gang scheduling is critical for distributed training.** An eight-node job should never start seven nodes and wait on the eighth . KAI Scheduler provides gang scheduling out of the box .
- **Sleep Mode is essential for sporadic workloads.** vLLM's Sleep Mode releases up to **95%+ of VRAM** without stopping the server—critical for RLHF, dynamic model switching, and cost savings during idle periods .
- **Ray Head placement matters.** Production deployments must place the Ray Head on a **CPU instance** (m5.xlarge or similar) to avoid wasting GPU memory on scheduler/GCS processes .
- Self-hosted open-source solutions require proper security hardening, network configuration, and ongoing maintenance. GPU clusters are high-value targets—access controls and audit trails are essential.

---

**Made for ML platform engineers, AI infrastructure teams, and developers building transparent GPU orchestration solutions.**  
Let's make GPU Orchestration & Allocation Scheduling more open, data-driven, and utilization-aware.
