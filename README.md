# llm_finetuning

- 환경
  - runpod/pytorch:2.4.0-py3.11-cuda12.4.1-devel-ubuntu22.04
- Task
  - 8bit 양자화 모델을 fsdp로 lora 학습 시키기
  - 양자화 하지 않았을 때는 밑의 코드를 실행시키니 학습이 문제없이 진행됨.
  - 하지만 모델 load 시, load_in_8bit =True 인자를 주면, 밑과 같은 error발생 

### 1.
- train_dataset.zip 압축풀기 
### 2.
```
pip install -r requirements.txt
```

### 3.
```
ACCELERATE_USE_FSDP=1 FSDP_CPU_RAM_EFFICIENT_LOADING=1 torchrun --nproc_per_node=2 ./lora_multi_gemma.py --config ./config.yaml
```

### Error
- load_in_8bit=True 인자를 주니, 밑에와 같은 error 발생
```
raise ValueError("Cannot flatten integer dtype tensors")
```

- BitsAndBytesConfig 사용해서 양자화 해도 같은 문제 발생. 
