# DEVSECOPS
需求设计-----研发------测试-------预发布-------运维---------事件---------优化+分析
# 安全设计  威胁建模
开源的威胁建模工具，有微软提供的威胁建模工具threat modeling tool，OWASP 的桌面和web版本的威胁建模工具Threat Dragon


owasp threat dragon。 该工具的主要工作流程是：绘制数据流图、进行威胁分析，制定消减措施。

通过访谈架构师及开发人员可以了解应用架构，并快速分解应用程序，进而绘制出详尽的数据流图。

绘制数据流图，是分解应用程序的一种技术，以可视方式展示数据如何在应用程序或系统中移动，以及各个组件在何处更改或存储数据。其中信任边界特指数据流中的卡点，在该点上需要对数据进行验证。信任边界是用数据流图进行威胁建模的关键。



数据流图主要由外部实体、处理过程、数据存储、数据流及信任边界组成。


威胁分析


Threat dragon采用STRIDE威胁分析方法。STRIDE从攻击者角度，把威胁分成仿冒、篡改、抵赖、信息泄漏、拒绝服务及权限提升。针对数据流图中的每个元素，分析其面临的威胁，并针对威胁制定消减措施。绘制完数据流图以后，就是对数据流中的每个元素可能面临的威胁逐个进行分析，但不是每个元素的STRIDE六类威胁都要去分析，图中表格列出每类元素可能面临的威胁，比如数据流只面临“篡改”、“信息泄露”、“拒绝服务”三种威胁。


自动化的威胁建模工具，比如ThreatModeler


# 源代码安全扫描


本地源代码安全检测--对于java项目来说，可以采用安全扫描插件FindSecurityBugs


# SAST源代码安全扫描


源代码安全扫描，可以使用sonarqube + findsecuritybugs插件


# DAST黑盒安全测试


# SCA开源组件安全扫描--Dependency Check是OWASP出品的开源组件安全扫描工具


# 容器安全扫描--Clair是CoreOS发布的开源容器漏洞静态分析工具，首先对镜像layer进行特征的提取，匹配CVE漏洞库，检测是否含有安全漏洞，侧重于扫描容器中的OS和应用的CVE漏洞



# MAST移动应用安全测试--MobSF是一款自动化移动APP安全测试工具，适用于iOS和Android，支持静态和动态分析。



# 安全加固--安全配置基线可以参考CIS Benchmark


# 漏洞管理--OWSAP DefectDojo是一款漏洞管理的开源工具，支持导入多种开源或商业安全工具的扫描结果，如Clair、Dependency Check、Harobr、MobSF、Sonarqbue、Zap等，实现在一个平台上对项目所有漏洞的集中化管理


# RASP运行时应用安全保护技术--OpenRASP是百度安全推出的一款开源的应用运行时自我保护产品



# 应用资产安全风险感知--kibana实现资产的可视化展示


# 威胁监控


可以基于ELK等开源技术，实现初级的SOC平台。网络流量监控采用suricata和zeek，规则采用ET开源规则库。各种日志、告警数据通过logstash采集入ES库，再通过kibana进行可视化展示

可以使用flink实现规则引擎，实现关联分析等。通过该平台安全日志的快速检索、网络流量监控、告警监控等功能，提高安全运营的效率。



# DevSecOps理念及思考
https://mp.weixin.qq.com/s/_jBmFdtyXY5D_YrrTUP1iQ

从目前业界的最佳实践来看，这其中主要包括几个关键的东西：持续集成（Continuous Integration，俗称“CI”）、持续交付（Continuous Delivery，俗称“CD”）、微服务（Microservices）、自动化测试、基础设施即代码（Infrastructureas Code，俗称“IaC”，又隐含包括了虚拟化、容器、自动编排、配置即代码等技术和理念）、监控和日志记录（Monitoring and Logging）等。业界围绕DevOps已经形成了一系列的工具集合和解决方案


SDL(security  development lifecycle) 安全开发生命周期

![image](https://user-images.githubusercontent.com/7948479/231744048-e0ed8cb9-5553-4095-84de-12b43c1d3ebe.png)

完全遵循DevOps的思想，将安全无缝集成到其中，使之升级成为DevSecOps
![image](https://user-images.githubusercontent.com/7948479/231745561-bba22ea9-3c69-4326-8e31-85fd46cfa8bd.png)

devsecops原则
1          安全左移
关注研发流程的“左”边，在更早的环节中（设计、编码、自动测试）也要进行安全介入和管控
需求和架构设计中的快速安全评估机制以及简易威胁建模方法论和工具集
2          默认安全
3          运行时安全
运行时应用自我保护（RASP，Runtime Application Self-Protection）技术
4          【安全服务自动化/自助化（Security as Code/Pipeline）】
5           【利用基础设施即代码（IaC）】
6            【利用持续集成和交付】
7           【需要组织和文化建设】

devsecops实践
![image](https://user-images.githubusercontent.com/7948479/231747563-dde74113-f2db-4209-99dc-bfc26b563fe5.png)


【Plan（需求和设计）】
威胁建模方法论\checklist\安全知识库
开源的威胁建模工具，有微软提供的威胁建模工具threat modeling tool，OWASP 的桌面和web版本的威胁建模工具Threat Dragon


【Create（编码/编译）】
ide安全扫描插件
FindSecurityBugs/snyk/codeql

【Verify（测试/验证）】
自动化测试
sast(static application security test)静态应用安全测试，针对源代码   ----白盒测试
常见的工具Coverity、Checkmarx、FindBugs等，比较新的CodeQL和ShiftLeft inspect、sonarqube + findsecuritybugs
dast(dynamic application security test)动态应用程序安全测试  ----黑盒测试
常见的工具Web应用商业和开源的AcunetixWVS，长亭科技X-Ray、w3af等
iast(interactive application security testing)交互式应用程序安全测试
常见的工具ShiftLeft protect、百度的openrasp-iast
sca(software composition analysis)软件成分分析，中间件扫描
常见的工具Dependency Check是OWASP出品的开源组件安全扫描工具


【Preprod（预发布）】
Fuzzing/集成测试

【Release（发布）】
软件签名

【Prevent（预防）】
签名验证
完整性检查
纵深防御措施----采用分层的方式，使用独立的一个个措施来层层的进行防御。是安全建设领域广泛采用的一种思路

【Detect（检测）】
rasp（runtime application self-protetection）运行时应用自我保护，自动化的实时监控、检测或阻断实际产生的安全攻击，使应用程序具备自我保护能力
常用的工具百度的OpenRASP
ueba/网络监控（user and entity behavior analytics）用户和实体行为分析，通过对用户以及系统实体在数据层面的异常行为利用机器学习的方法来发现网络安全、IT办公安全、内外部的业务安全等风险，如数据泄露、入侵、内部滥用等的安全问题。在安全领域，异常分析是一个最重要的能力
渗透测试
攻防演练和不断的渗透


Respond（响应）
安全编排自动化和响应（soar,security orchestration,automation and response）
安全编排与自动化soa/安全事件响应平台sirp/威胁情报平台tip

【Predict（预测）】
漏洞相关性分析，软件漏洞管理Application VulnerabilityCorrelation（AVC）
威胁情报
高级持续性威胁（Advanced Persistent Threat，APT）


【Adapt（适应）】


DevSecOps工具链
【Plan（需求和设计）】
•         公司安全规范/安全评估/威胁建模

•         安全培训

•         编码安全规范



【Create（编码/编译）】
•         安全开发库

•         安全相关的基础设施&框架机制

•         IDE中的代码质量工具

•         代码review

•         安全加固的统一编译构建环境

•         安全加固的腾讯软件源



【Verify（测试/验证）】


【Preprod（预发布）】
•         SAST 静态代码扫描“啄木鸟”

•         内部开源代码自动安全检查

•         DAST “洞犀”/“金刚”

•         IAST “洞犀”

–        结合流量代理技术

–        结合RASP和DAST技术

•         APP加固

•         Fuzzing

–        团队持续关注适时启动，reisk在《Fuzzing平台建设的研究与设计》与《持续Fuzzing在DevSecOps中的应用》中思考了很多，不再赘述。

•         混沌工程



【Release（发布）】
•         后台服务发布，安全加固的统一服务发布平台

•         APP发布，证书和软件签名/发布

•         镜像安全扫描

•         安全加固的腾讯tlinux内核



【Prevent（预防）】
•         安全可追溯的运维访问

•         零信任安全网关



【Detect（检测）】
•         网络流量安全分析

–        相关内容《流量分析在安全攻防上的探索实践》一文对部分工作做了很好的说明

•         洞犀-上线后安全扫描

–        高危服务：针对内外网上的高危服务（如可被直接入侵、数据泄露等）进行全端口的持续监测，对于其中可蠕虫可入侵类的风险提供30秒内的发现能力。部分机房的外网开放风险可“一键防护”（基于宙斯盾的阻断能力），帮助运维同学快速的临时止损。参见《拥抱DevOps-“洞犀”高危服务扫描方案》

–        Web漏洞：会有大量的Web业务并不进行上线前的安全扫描，因此洞犀系统会对外网所有的Web请求进行采集、去脏、去重等处理，识别出有效的CGI及参数（从万亿提取出百万量级CGI）。通过替换内置账号登录态（包括QQ、微信等）来发起安全扫描。

•         金刚-上线后安全扫描

–        也会有公司App不在上线之前做安全扫描，因此金刚系统与应用宝合作，会自动拉取公司的App进行安全扫描并跟进漏洞处理完成。有个外部可用的金刚服务可供测试。

•         洋葱（入侵检测系统）

–        利用公司服务器母盘中洋葱Agent采集到的进程、连接、可疑文件等信息，外加网络流量中的信息，采用专家规则和UEBA方式来发现入侵行为，是公司反入侵领域最强大的基石系统。部分内容参考《披荆斩棘：论百万级服务器反入侵场景的混沌工程实践》

•         RASP方案TRASP

–        通过分析应用的运行行为以及上下文来发现Web应用安全威胁，并精准定位到漏洞源，由于与应用融为一体，可实时监测、阻断攻击，使应用自身拥有自保护的能力。可以实时检测发现针对web系统的各类入侵行为，包括SQL注入、命令注入、任意文件上传、任意文件读取、代码执行等。

•         腾讯安全应急响应中心（TSRC）漏洞奖励计划

–        提供资金激励吸引外部安全研究人员帮助腾讯发现更多潜在安全风险和漏洞

–        提供其他公司快速搭建SRC平台的 开源版本以及 SaaS版本，目前已经有10+知名公司使用

•         腾讯蓝军渗透测试

–        内容敏感不列出，持续进行。

–        获pony点赞《【原创】腾讯有个技术军团，“疯起来”连自己都打》，更多公开信息见lake的《网络空间安全时代的红蓝对抗建设》，蓝军领队wqzhong的《以攻促防：企业蓝军建设思考》



【Respond（响应）】
•         安全事件应急响应小组

–        7*24小时安全事件应急响应，第一时间响应，降低或消除事件影响

•         宙斯盾（DDoS防护）

–        见文章《军备竞赛：DDoS攻击防护体系构建》《浅谈DDoS攻防对抗中的AI实践》

•         门神（WAF）

–        见文章《WAF建设运营及AI应用实践》



【Predict（预测）】
•         安全服务中心

•         安全事件工单系统

•         威胁情报：TSRC安全情报平台，主动及时感知外部安全情报

–        提供100+知名软件的官方更新情报，5分钟内发现，30+外部公司使用



Adapt（适应）
•         待实践


