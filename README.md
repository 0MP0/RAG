# RAG根据项目文件分析,这是一个 RAG法律助手 项目,主要使用说明如下:

## 📋 项目概述
这是一个基于RAG(Retrieval Augmented Generation)技术的法律助手系统,使用本地模型实现刑法知识检索问答。

## 🛠️ 技术栈
- 向量数据库 : Chroma
- Embedding模型 : BAAI/bge-base-zh-v1(本地路径: D:\AIProjects\modelscope\BAAI\bge-base-zh-v1___5 )
- LLM模型 : Ollama的qwen2.5:1.5b模型
- 框架 : LangChain
## 📖 使用步骤
### 1️⃣ 环境准备
- 安装依赖包: langchain, chroma, langchain-huggingface, ollama等
- 确保已下载Embedding模型到指定路径
- 确保Ollama已安装并加载了qwen2.5:1.5b模型
### 2️⃣ 运行流程
打开 TCM_AI_ASSISTANT.ipynb Notebook,按顺序执行:

步骤1 : 加载并分割文档

- 从 ./documents/中华人民共和国刑法.txt 加载法律文本
- 使用RecursiveCharacterTextSplitter切片(chunk_size=200, overlap=30)
步骤2 : 向量化存储

- 使用HuggingFaceEmbeddings进行向量化
- 存储到 ./chrome_db 目录
步骤3 : 构建问答链

- 通过Ollama连接本地LLM
- 构建RetrievalQA链
步骤4 : 提问测试

```
result = qa_chain.invoke("张三抢劫银行获得十万元,将受到什么判
罚？")
```
### 3️⃣ 高级功能
- 评估 : 使用ragas进行回答质量评估
- 优化 : 使用MultiQueryRetriever和ContextualCompressionRetriever提升准确度
## 🔧 配置文件
.env 文件包含各类API密钥(阿里云、智谱、腾讯、HuggingFace等)
