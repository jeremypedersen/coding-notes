---
id: 5bixl6kw3cmj3ec9zuvxi1e
title: 'Hardware'
desc: 'Hardware'
updated: 1713239852304
created: 1710410265296
---

This section talks about the different hardware configurations which can be used to run ML models. 

To avoid having this section explode to cover every recent version of every piece of hardware from every major vendor, we will try to focus on newer hardware, and on very large models like [SDXL](https://huggingface.co/docs/diffusers/en/using-diffusers/sdxl) or [Llama 2](https://huggingface.co/meta-llama), which are large enough that compute and memory constraints come into play even on new hardware.

For each piece of hardware we will try to address the following questions:

- What is its general type? 
    - CPU
    - GPU
    - FPGA
    - Something else
- What is its architecture? 
    - ARM
    - x86
    - Something else
- Where is it available? 
    - Cloud
        - Which provider?
        - Which regions?
    - Local
- What data types are supported? 
    - FLOAT32
    - FLOAT16
    - BFLOAT16
    - INT8
    - Others
- AI Acceleration features? 
    - OpenVINO toolkit (Intel)
    - Advanced Matrix Extensions (AMX - Intel)
    - Neuron (AWS Inferentia SDK)
- What does it cost?
    - Hourly
    - Yearly (for providers with up-front pricing options)
    - Fixed cost (for local hardware)
- How well does it perform? 
    - Inference and fine-tuning speeds
    - Inferences-per-second
    - Cost-per-inference

To try to keep things organized, we will sort hardware into two general categories:

1. Cloud: hardware available from major cloud providers.
2. Edge: hardware you run yourself locally.

This scheme results in some overlap as most of the hardware available through the major cloud providers will overlap, but it means we get to see differences in pricing and regional availability by provider. It also separates out consumer hardware intended to be used and purchased by individuals from server hardware (which is what the cloud companies buy and/or build). 




### Edge

Nothing here yet!

