# OmegaConf

> 专门用来管理配置文件。

## Usage

```python
from omegaconf import OmegaConf
cfg = OmegaConf.load("config.yaml")
```

## 加载预训练模型

### 1. 从官网下载相应文件

```bash
wget https://huggingface.co/facebook/esm2_t33_650M_UR50D/resolve/main/config.json
wget https://huggingface.co/facebook/esm2_t33_650M_UR50D/resolve/main/pytorch_model.bin
wget https://huggingface.co/facebook/esm2_t33_650M_UR50D/resolve/main/special_tokens_map.json
wget https://huggingface.co/facebook/esm2_t33_650M_UR50D/resolve/main/tokenizer_config.json
wget https://huggingface.co/facebook/esm2_t33_650M_UR50D/resolve/main/vocab.txt
```

### 2. 加载相应模型

```python
ems2_model_path = 'models/protein/esm2_model'
tokenizer = AutoTokenizer.from_pretrained(ems2_model_path)
model = EsmModel.from_pretrained(ems2_model_path).to(device)
model.eval()  # disables dropout for deterministic results
```

### 3. 使用预训练模型提取特征

```python
# 示例氨基酸序列
protein_seq = "MAKELVLVVGGGLALALVVPAA"
inputs = tokenizer(
    protein_seq,
    truncation=True,
    max_length=1024,
    return_tensors="pt"
).to(device)
with torch.no_grad():
    outputs = model(**inputs)

# 获取对应的全局特征
feature = outputs.last_hidden_state[:, 0, :].squeeze()  # (1280)

# 获取特征矩阵
feature_matrix = outputs.last_hidden_state.squeeze()  # (pro_length, 1280)
```
