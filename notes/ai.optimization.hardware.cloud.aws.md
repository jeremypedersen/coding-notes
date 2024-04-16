---
id: yqa165ncnezvi0iuv6xi193
title: 'Amazon AWS'
desc: 'AWS hardware options for AI apps'
updated: 1713239877744
created: 1710410343454
---

Amazon AWS offers a wide range of hardware, including

- Intel and AMD CPUs (x86)
- FPGAs (Intel and Xilinx)
- GPUs (NVIDIA and AMD)
- Trainium (self-built hardware for training models)
- Inferentia (self-built hardware for running model inference)
- Graviton (self-built ARM processors)

Here we catalog some of it and provide pricing, benchmarks, and optimization strategies. 

# Intel CPUs (x86)

Large ML models can be run on the CPU using Intel's [OpenVINO toolkit](https://docs.openvino.ai/latest/index.html). 

Below are CPU-only benchmarks on several different EC2 instance types for several different models.

For each type of hardware listed in the notes, we try to provide tests for at least one popular LLM (such as Llama-7B) and at least one popular text-to-image model (such as SDXL). 

Time permitting, benchmarks will also be shown for other models. 

