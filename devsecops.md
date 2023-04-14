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
常见的工具Coverity、Checkmarx、FindBugs等，比较新的CodeQL和ShiftLeft inspect
dast(dynamic application security test)动态应用程序安全测试，


