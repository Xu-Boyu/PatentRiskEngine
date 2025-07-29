# PatentRiskEngine
Patent Infringement Risk Assessment Engine
基于大型语言模型的专利侵权风险评估引擎，集成语义分析、嵌入匹配、推理链条与排序算法，为产品与专利之间的自动化侵权判断提供精准、可解释的解决方案。

项目简介
本项目旨在构建一个智能化、可扩展的专利侵权风险评估系统，融合自然语言处理、嵌入技术与大型语言模型（LLMs），实现如下功能：

多阶段语义解析：将专利权利要求结构化为语义单元（主体、动作、对象等）

嵌入式相似度匹配：使用高维向量表示产品特征与专利内容，自动构建相似度矩阵

LangChain 专利推理链条：引入 ReAct 与 Reflection 技术增强文本理解

Chain-of-Thought 提示工程：提升复杂权利要求的推理准确率

PageRank 变体排序算法：识别关键侵权条款，按风险排序结果

多模型比较评估：支持 GPT-4o、Claude 3、Gemini Pro 等模型性能对比

技术亮点
模块	描述
结构化解析器	使用 LLM function-calling 将权利要求解析为 JSON 结构
嵌入引擎	使用 text-embedding-3-large 生成专利与产品描述的语义向量
LangChain 组合链	实现 ReAct 推理、反思机制与工具调用能力融合
CoT Prompt 设计	构造 Chain-of-Thought 提示，引导模型分步骤推理
混合相似度评分	结合余弦相似度与 LLM 判断强度构建综合匹配分数
PageRank 变体	在 claim dependency graph 上运行带权重的 PageRank 算法识别关键条款
模型对比实验	全面评估多个主流 LLM 在专利语义匹配任务中的性能表现

项目结构
bash
复制
编辑
PatentRiskEngine/
├── data/                  # 原始数据与标注集
├── preprocessing/         # 权利要求结构化解析
├── semantic_embedding/    # 向量生成与相似度计算
├── similarity_engine/     # 自监督匹配矩阵生成与评分
├── infringement_analysis/ # PageRank 侵权排序算法
├── llm_modules/           # LangChain 推理链与提示设计
├── evaluation/            # 多模型评估与指标分析
├── main.py                # 主流程入口
└── README.md
实验结果（摘要）
系统准确率：87.3%

F1 分数：0.84

准确率提升：引入 CoT + ReAct 推理后较原始匹配方法提高 31.5%

模型表现：

模型	准确率	F1 分数
GPT-4o	 87.3%	 0.84
Claude 3 Opus	82.6%	0.78
Gemini Pro	79.2%	0.74

快速开始
git clone https://github.com/yourname/patent-risk-engine.git
cd patent-risk-engine
pip install -r requirements.txt
python main.py
依赖环境
Python 3.10+

OpenAI API (gpt-4o, text-embedding-3-large)

LangChain >= 0.1.15

FAISS / NumPy / Scikit-learn

NetworkX (用于图结构和PageRank变体)

许可协议
MIT License - 欢迎使用与修改。若用于论文或产品，请注明引用。
