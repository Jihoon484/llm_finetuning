# llm_finetuning

- 환경
  - runpod/pytorch:2.4.0-py3.11-cuda12.4.1-devel-ubuntu22.04

### 1.
```
pip install -r requirements.txt
```

### 2.
```
ACCELERATE_USE_FSDP=1 FSDP_CPU_RAM_EFFICIENT_LOADING=1 torchrun --nproc_per_node=2 ./lora_multi_gemma.py --config ./config.yaml
```

### Error
- load_in_8bit=True 인자를 주니, 밑에와 같은 error 발생
```
raise ValueError("Cannot flatten integer dtype tensors")
```
