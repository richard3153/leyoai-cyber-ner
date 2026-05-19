---
base_model: Qwen/Qwen2.5-1.5B-Instruct
library_name: peft
pipeline_tag: text-generation
tags:
  - leyoai
  - qwen2.5
  - lora
  - sft
  - cyber-security
  - video-analysis
  - workflow-automation
  - data-analytics
license: apache-2.0
language:
  - zh
  - en
datasets:
  - leyoai-custom-dataset
---

# leyoai-cyber-ner

## 中文介绍

LeyoAI Cyber NER 模型用于从网络安全文本中提取命名实体（如漏洞、攻击类型、CVE 编号等），基于 Qwen2.5-1.5B-Instruct 微调。

### 使用方法

```python
from modelscope import AutoModelForCausalLM, AutoTokenizer

# Load model
model = AutoModelForCausalLM.from_pretrained(
    "FFZwai/leyoai-cyber-ner",
    device_map="auto"
)
tokenizer = AutoTokenizer.from_pretrained("FFZwai/leyoai-cyber-ner")

# Inference
prompt = "从以下安全公告中提取所有 CVE 编号和漏洞类型：..."
inputs = tokenizer(prompt, return_tensors="pt").to(model.device)
outputs = model.generate(**inputs, max_length=100)
response = tokenizer.decode(outputs[0], skip_special_tokens=True)
print(response)
```

### 训练详情

- **基座模型**: Qwen2.5-1.5B-Instruct
- **微调方式**: LoRA (Low-Rank Adaptation)
- **LoRA Rank**: 16
- **LoRA Alpha**: 32
- **训练设备**: Mac Studio MPS (fp32)
- **部署平台**: HuggingFace Spaces / ModelScope

### 性能指标

- **Eval Loss**: 0.0046
- **Accuracy**: 95.3%

### 许可证

Apache License 2.0

---

## English Introduction

LeyoAI Cyber NER model extracts named entities (e.g., vulnerabilities, attack types, CVE numbers) from cybersecurity texts, fine-tuned from Qwen2.5-1.5B-Instruct.

### Usage

```python
from modelscope import AutoModelForCausalLM, AutoTokenizer

# Load model
model = AutoModelForCausalLM.from_pretrained(
    "FFZwai/leyoai-cyber-ner",
    device_map="auto"
)
tokenizer = AutoTokenizer.from_pretrained("FFZwai/leyoai-cyber-ner")

# Inference
prompt = "Extract all CVE numbers and vulnerability types from the following security advisory: ..."
inputs = tokenizer(prompt, return_tensors="pt").to(model.device)
outputs = model.generate(**inputs, max_length=100)
response = tokenizer.decode(outputs[0], skip_special_tokens=True)
print(response)
```

### Training Details

- **Base Model**: Qwen2.5-1.5B-Instruct
- **Fine-tuning Method**: LoRA (Low-Rank Adaptation)
- **LoRA Rank**: 16
- **LoRA Alpha**: 32
- **Training Device**: Mac Studio MPS (fp32)
- **Deployment**: HuggingFace Spaces / ModelScope

### Performance Metrics

- **Eval Loss**: 0.0046
- **Accuracy**: 95.3%

### License

Apache License 2.0

---

## 关于 LeyoAI (About LeyoAI)

**LeyoAI** 是杭州市上城区乐友信息服务工作室旗下的垂直领域 AI MaaS 平台，提供四大 AI 助手：

- **Cyber Model**: AI 安全助手
- **Video Model**: 视频安全助手
- **Flow Model**: 流程自动化助手
- **Analytics Model**: 数据分析助手

**LeyoAI** is a vertical AI MaaS platform by Hangzhou Shangcheng Leyou Information Service Studio, providing four AI assistants:

- **Cyber Model**: AI Security Assistant
- **Video Model**: Video Safety Assistant
- **Flow Model**: Workflow Automation Assistant
- **Analytics Model**: Data Analytics Assistant

### 链接 (Links)

- 官网 (Website): https://leyoai.vercel.app
- GitHub: https://github.com/richard3153/leyoai-landing
- HuggingFace: https://huggingface.co/FFZwai

---

## Framework Versions

- PEFT 0.18.1
- Transformers 4.51.3
- PyTorch 2.7.0
- Datasets 3.6.0
