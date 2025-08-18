---
{"dg-publish":true,"permalink":"/Encoder vs Decoder/","created":"2025-06-12T17:33:10.605-07:00"}
---

- 通俗理解 encoder 是把 文字 转换成 embedding
- decoder 把 embedding 转换回 文字

- Transformer 中
    - Encoder: 输入 文字，encoder 做 self-attention 把 文字 之间的关系提取出来，并且做成 文字 的 embedding
    - Decoder: 输入 需要生成的序列的前一部分，目标是生成后一个单词
        - 训练：
            - 生成下一个词 需要 **前边的所有词** + **输入的句子**
            - 先做 masked self-attention 获得 **前边的所有词** 的信息
            - 再把这个作为 Q，与 encoder 得到的 embedding 做 cross-attention，获得 **输入的句子** 的信息
            - 每个位置的 embedding 做 softmax 得到 生成单词 的预测
        - inference：
            - 循环生成下一个单词
