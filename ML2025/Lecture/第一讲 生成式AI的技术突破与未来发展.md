# Generative AI
## 1. 有什么样的行为
 - 不只是生成，还能够操控物件
 - 按照指令，完成多个步骤
 - 找到特定的函数***f***（的参数），使得对于任意输入***x***有合适的输出***y***
## 2. 运作机制
- 复杂物件由有限的基本单位(token)组成
- Autoregressive Generation：根据已有的所有x和y生成下一个y(输出一个**概率分布**) ![](assets/第一讲%20生成式AI的技术突破与未来发展.png)
- Neutral Network：类神经网络
- 深度学习(Deep Learning): 把一個問題拆解成 𝐿 (layer 數目) 個步驟 ——将无穷的排列组合变为若干的有限的（将***f***变为若干个***fi***串联） ![](assets/第一讲%20生成式AI的技术突破与未来发展-1.png)
- 让机器“思考”：深度不够，长度来凑——Testing Time Scaling
![](assets/第一讲%20生成式AI的技术突破与未来发展-2.png)
- Self-attention Layer: 看过所有输入之后决定下一个输出
	含有self-attention layer 的 neutral network: Transformer
## 3. 如何产生
类神经网络：架构 vs 参数
函数***f***包含两部分：
1. 架构(architecture):由开发者决定
2. 参数(parameter):由训练资料决定

**分类**：有限可能（选择题）
通用机器学习模型

第一形态：编码器(encoder)+特化模型
![](assets/第一讲%20生成式AI的技术突破与未来发展-3.png)

第二形态：有完整的文字生成功能 + 参数微调(fine-tune) ——架构相同，参数不同
![](assets/第一讲%20生成式AI的技术突破与未来发展-4.png)

第三形态：能够遵照输入的指令(prompt)——架构相同，参数相同
![](assets/第一讲%20生成式AI的技术突破与未来发展-5.png)
## 4. 如何赋予新的能力
机器的终生学习（life-long learning)时代
输入指令：参数固定，不会永久改变某种行为
永久具有新技能：
1. 改变参数——微调：注意一定要让AI**保持原来的能力**
	微调具有相当大的风险，应该先确定不微调就无法具备目标能力，才选择微调
2. 模型编辑(Model Editing)——手动修改相关参数
3. 模型结合(Model Merging)——结合多个具有不同功能的模型的参数


# HW1
## What is RAG?
![](assets/第一讲%20生成式AI的技术突破与未来发展-6.png)
Retrieval augmeted generation (RAG) is a method that allows LLMs to answer the query with external knowledge. In a naive RAG approach, the query will be fed to a knowledge base to gather relevant information first.

Then, both the query and the retrieved information will be passed to the LLM simultaneously, allowing the LLM to answer the query with external knowledge.

## Why RAG?
### Knowledge cutoff
An LLM must be trained on data that "exist" at the time it was trained. For example, an LLM trained in 2024 will not know about anything in 2025. RAG can let the LLM have the access to the latest information.

### Reducing the cost of training
When dealing with private data that an LLM unlikely have seen, one can choose to fine-tune the LLM. However, it is costly to fine-tune an LLM. RAG is another approach to allow LLMs to access the private data without the need of training.

### Improving the reliabilities of generated answers
By the nature of LLMs, it is a common issue that LLMs will produce hallucinations. With RAG, one can examine the source of the generated texts, hence improve the reliabilities of the answers.

## What is Agentic System

An agentic system is a framework where LLMs act as individuals and cooperate to complete complex tasks.
![](assets/第一讲%20生成式AI的技术突破与未来发展-7.png)
