# AI安全
1、AI原生安全：人工智能系统自身的安全问题
2、AI衍生安全：人工智能技术应用出现的安全问题

# AI安全框架
1、安全目标
AI系统自身的安全
AI技术的应用安全
2、安全风险
2.1、原生风险：
1、基础风险
---机器学习框架安全
人工智能算法基于机器学习框架完成其模型的搭建、训练和运行
深度学习框架需要依靠于大量的基础库和第三方组件支持
组件的复杂度会严重影响深度学习框架的安全性
2、核心风险：
---数据安全风险
利用模型的输出信息可以开展
模型盗取攻击和训练数据盗取攻击
故在机器学习模型的训练和应用过程中
所使用的训练数据和模型参数有被泄露的风险
---算法模型安全风险
针对人工智能深度学习算法提取样本特征的特点
在不改变深度学习系统模型的前提下
通过构造相关输入样本，使系统输出错误的结果来对抗样本攻击
这种类型攻击分为
躲避攻击和假冒攻击

2.2、衍生风险
---系统应用安全
不当使用
外部攻击
业务设计安全错误
会引发人工智能系统的应用安全风险

3、安全评估
3.1、基础设施安全评估
3.2、算法安全评估
3.3、数据安全评估
3.4、系统应用安全评估
4、安全保障
4.1、技术保障
1、深度伪造保障
2、数据安全保障
3、对抗样本保障
4、算法安全保障
5、模型缺陷保障
4.2、管理保障
1、战略保障
2、企业保障
3、运营保障


# JBFuzz：使用模糊测试高效破解大型语言模型
初始种子-模糊测试使用的提示模板
评估JBFUZZ
1、攻击成功率
2、成功所需迭代次数
3、效率比率
4、运行时间
5、平均标记技数
6、模糊测试速率
越狱攻击
1、基于策略的越狱攻击  这类攻击依赖于明确设计的策略，通常基于人类的直觉，来破坏 LLMs
2、基于优化的越狱攻击  这类攻击利用自动化算法来生成能够引发模型不良行为的提示
LLM存在的风险：越狱、投毒、敏感信息泄露、注入攻击

#  机器学习管道下的序列化
漏洞存在于流行框架处理模型序列化和反序列化
当你在其他框架中调用torch.load()或类似函数时，你实际上是在执行序列化文件中包含的任意代码
def load_pretrained_model(model_path):
    model = torch.load(model_path)
    model.eval()
    return model

#  无人修补的内存映射攻击面


# llm 
1、LLM 可以访问哪些 API
2、LLM Debug SQL API 接受哪些参数
