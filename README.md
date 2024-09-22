---
base_model:
- jpacifico/Chocolatine-3B-Instruct-DPO-Revised
- microsoft/Phi-3-mini-4k-instruct
library_name: transformers
tags:
- mergekit
- merge

---
# 3PRYMMAL-PHI3-3B-SLERP

This is a merge of pre-trained language models created using [mergekit](https://github.com/cg123/mergekit).

## Merge Details
### Merge Method

This model was merged using the SLERP merge method.

### Models Merged

The following models were included in the merge:
* [jpacifico/Chocolatine-3B-Instruct-DPO-Revised](https://huggingface.co/jpacifico/Chocolatine-3B-Instruct-DPO-Revised)
* [microsoft/Phi-3-mini-4k-instruct](https://huggingface.co/microsoft/Phi-3-mini-4k-instruct)

### Configuration

The following YAML configuration was used to produce this model:

```yaml

slices:
  - sources:
      - model: jpacifico/Chocolatine-3B-Instruct-DPO-Revised
        layer_range: [0, 32]
      - model: microsoft/Phi-3-mini-4k-instruct
        layer_range: [0, 32]    
merge_method: slerp
base_model: jpacifico/Chocolatine-3B-Instruct-DPO-Revised
parameters:
  t:
    - filter: self_attn
      value: [0, 0.25, 0.5, 0.75, 1]
    - filter: mlp
      value: [1, 0.75, 0.5, 0.25, 0]
    - value: 0.5
dtype: bfloat16

```
