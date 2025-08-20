# 🌐 Distributed Training: Key Concepts

## How DataParallel (DP) Works

- **Single process** (one Python program)  
- This process manages **all GPUs at once**  

**Algorithm:**  
1. Data is loaded on CPU.  
2. The process **copies the model to each GPU**.  
3. The batch is split into N sub-batches (one per GPU).  
4. Each GPU computes forward and backward passes.  
5. Gradients are gathered on GPU0 (main), weights are updated, then copied back to all other GPUs.  

**Cons:**  
- Main process and GPU0 can become a **bottleneck**  
- Many extra memory copies between GPUs  

---

## How DistributedDataParallel (DDP) Works

- **Multiple processes** — one per GPU  
- Each process:  
  - Loads its **own copy of the model**  
  - Gets its **chunk of data** (via `DistributedSampler`)  

**Algorithm:**  
1. Processes compute forward and backward passes independently.  
2. After `.backward()`, an **all-reduce** is performed — gradients are averaged across GPUs **directly via NCCL** (no CPU involved).  
3. Weights are updated locally in each process, but remain identical because gradients are synchronized.  

**Pros:**  
- No bottleneck on GPU0  
- Less communication overhead  
- Better scalability

## Other
Also, there are **Model Parallelism**, **Tensor Parallelism**, **Pipeline Parallelism**, but it's less used usually.