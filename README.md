# 从零构建 LLM：学习笔记与实现

这是一个围绕 **GPT/大语言模型从零实现** 的学习仓库，记录了从文本预处理、注意力机制到 GPT 模型搭建、训练与加载 GPT-2 权重的实践过程。

项目主要参考 Sebastian Raschka 的《Build a Large Language Model (From Scratch)》。仓库中的 Notebook 以学习推导和实验为主，Python 脚本则汇集了可复用的模型与训练代码。

> 这是学习项目，旨在帮助理解 LLM 的核心组件与训练流程，并非生产级训练框架。

## 学习内容

- 文本分词、滑动窗口采样与 `DataLoader` 构建
- Self-Attention、Causal Attention 与 Multi-Head Attention
- Layer Normalization、GELU、前馈网络与残差连接
- Decoder-only Transformer / GPT 模型结构
- 训练、验证损失评估与文本生成
- 下载并加载预训练 GPT-2 权重

## 项目结构

```text
.
├── 我的/                         # 学习笔记、Notebook 与个人实现
│   ├── 2 Data preparation & sampling.ipynb
│   ├── 3 Attention mechanism.ipynb
│   ├── 4 LLM architecture .ipynb
│   ├── 5 LLM training function.ipynb
│   ├── gpt_model.py              # 数据集、注意力层与 GPT 模型实现
│   ├── gpt_download.py           # GPT-2 权重下载与加载工具
│   └── 5 load GPT-2.py           # 加载预训练 GPT-2 的示例
└── 官方的/                        # 与原书配套的参考代码
    ├── gpt.py
    └── gpt_train.py
```

## 快速开始

建议使用 Python 3.10 或更高版本，并在虚拟环境中安装依赖：

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\\Scripts\\activate
pip install torch tiktoken numpy matplotlib requests jupyter
```

随后可启动 Jupyter，按章节顺序阅读和运行 Notebook：

```bash
jupyter notebook
```

推荐学习顺序：

1. `2 Data preparation & sampling.ipynb`
2. `3 Attention mechanism.ipynb`
3. `4 Layer Normalization.ipynb`、`4 Feed forward network.ipynb` 与 `4 LLM architecture .ipynb`
4. `4 gpt model.ipynb`
5. `5 LLM training function.ipynb` 与 `5 training and validation losses.ipynb`
6. `5 load GPT-2.py`

## 注意事项

- 运行 GPT-2 加载示例时会下载模型文件；这些文件会保存到 `gpt2/`，并已被 `.gitignore` 排除。
- 部分示例使用 `the-verdict.txt` 或 `small-text-sample.txt` 作为训练/测试文本，请从对应目录运行，或相应调整文件路径。
- GPU 可显著加快训练；没有 GPU 时也可以使用 CPU 完成小规模实验。

## 参考资料与致谢

- Sebastian Raschka, [*Build a Large Language Model (From Scratch)*](https://www.manning.com/books/build-a-large-language-model-from-scratch)
- 原书配套代码：[rasbt/LLMs-from-scratch](https://github.com/rasbt/LLMs-from-scratch)

`官方的/` 目录中的代码基于原书配套代码整理；相关版权与许可证信息请以其源项目为准。
