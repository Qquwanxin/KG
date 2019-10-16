# 知识图谱
- 知识图谱是由一些相互连接的实体和它们的属性构成的。
- 知识图表示一组相互链接的实体描述-现实世界的对象，事件，情况或抽象概念。[3]与本体不同，知识图谱（例如Google的知识图谱）通常包含大量具有较少形式语义的事实信息。在某些情况下，术语知识图用于表示任何以图形表示的知识库。
    - S -P-> O
- 文本文件----知识抽取、知识融合、知识众包等技术---数据---知识表示和知识推理、知识链接--->知识图谱数据->可视化表示
- 构建知识图谱->可视化
  

# 构建知识图谱
## 数据结构
- RDF(Resource Description Framework) W3C制定。用于描述实体/资源的**标准数据模型**。
    - 三元关系。(Subject, predicate, object)
- RDFS在RDF的基础上定义了一些固定的关键词如：Class，subClassOf，type， Property， subPropertyOf， Domain， Range以及多了Schema层。
    - 支持推理
- OWL(Web Ontology Language)
    - 子语言: OWL Lite、OWL DL、OWL Full
    - 支持推理等操作。
    - 比RDFS多了更多属性描述 eg.描述类别、属性之间关系的定义或约束, -> 比如两个类是否不相交
- ……

## 知识抽取
- NLP(Natural Language Processing), KR(Knowledge Represention)
- 抽取kr所需的三元组、多元关系...
- **爬虫获取非结构化的文本数据**->文本预处理->**文本数据**->机器学习等进行分词、词性标注、词法解析……->NER和实体链接工作->关系抽取和时间抽取->**三元组、多元关系、模态知识(知识图谱)**
- 结构化/半结构化数据
    - 表格
    - 通过direct mapping
        - 本质: 通过编写启发式规则将数据库中的表转换为RDF三元组。
            - table to class
            - cloumn to property
            - row to resource
            - cell to literal value
            - in addition cell to URI
                - if there is a forgin key constraint
        - 建立规则进行映射即可

    <!-- - 通过R2RML语言 //更灵活，定制性强。
        - 工具: eg.d2rq工具(基于R2RML-KIT)
        - D2RQ平台: 将关系数据库作为虚拟的只读RDF图进行访问的系统。
            - 提供对关系数据库内容的基于RDF的访问，而不必将其复制到RDF存储中。
            - eg. 你通过SPARQL端口查询，输入是SPARQL查询语言，D2RQ通过mapping文件将其转换为SQL语句在关系数据库上查询，因此实际上访问的是关系型数据库。(?) -->
- 非结构化文本
    - 实体抽取->关系抽取
    - 实体抽取
        - 人工编写规则
        - 机器学习->抽取出与之具有相似上下文特征的实体再筛选
        - 基于实体的语义特征->识别出命名实体, 聚类算法对识别出的实体对象进行聚类
    - 关系抽取
        - 基于模板
            人工构造语法和语义规则->模式匹配
            - 基于触发词/字符串
            - 基于依存句法
                - 分词 词性标注 命名实体识别 依存分析 -> 匹配得三元组 -> 扩展 -> 抽取三元组
                    - 依存分析: 依存关系->就是主谓宾定语    依存关系路径: 将分析结果视作Graph，Graph中对应这两个实体的结点间最短路径(?)[计算](https://patents.google.com/patent/CN104008092B/zh)
        - 机器学习
            少量人工标记数据（训练集）-> 实体关系分类模型 -> 分类 -> 抽取原型
    - *属性抽取
        - 百科
        - 文本
    - 一些库
        - deepdive  [支持中文的deepdive：斯坦福大学的开源知识抽取工具（三元组抽取）](http://www.openkg.cn/dataset/cn-deepdive)

## 知识融合
- 实体链接、知识合并...
- 消除歧义、冗余、错误
- 实体链接
    - 自然语言中的文本--知识库中的条目, 将知识库中没有的知识补全到库中
    - 引用表构建: 引用表存储一个名字所有可能指向的实体
        - eg: 名字-目标实体-次数
    - 实体知识构建
        - 根据实体知名度、实体上下文、实体语义关联度、文章主题等
    - 链接推理算法
- 知识合并
    - 合并外部数据库等


## 知识储存
- 图数据库: 基于图论实现的一种新型NoSQL数据库
    - 数据数据存储结构和数据的查询方式都以图论为基础, 节点和边->节点和关系。
    - eg. Neo4j, Oracle NoSQL，OrientDB，HypherGraphDB，GraphBase，InfiniteGraph，AllegroGraph...
- Neo4j[https://neo4j.com/](https://neo4j.com/)
    - 顶点（Vertex） + 边（Edge） + 属性（Property），顶点和边都可以设置属性（一个或多个）, 有向图
    - tutorial
        - [官](https://neo4j.com/docs/getting-started/current/get-started-with-neo4j/)
        - [w3c](https://www.w3cschool.cn/neo4j/)
        - [1](https://zhuanlan.zhihu.com/p/48708750)
        - [2](https://segmentfault.com/a/1190000014488430)

## 知识推理 知识检索...

------

## 存
1. [一个数据集](http://zhishi.me/) <!-- 支持百度百科，沪东百科和中文维基百科。 -->
0. [KG t](https://zhuanlan.zhihu.com/c_211846834)
0. [KG t](http://pelhans.com/2018/03/19/xiaoxiangkg-note3/)
0. [论文集合](https://zhuanlan.zhihu.com/p/44904796)
0. [一个简单KG](https://github.com/lemonhu/stock-knowledge-graph)
0. [基于百度百科KG构建过程](https://zhuanlan.zhihu.com/p/54051921)
    - [github](https://github.com/Pelhans/Z_knowledge_graph)
0. [一些示例](https://zhuanlan.zhihu.com/p/77339370)
0. [zjl_KG](https://zhuanlan.zhihu.com/p/58248608)
    - [github](https://github.com/zhangtao-seu/Jay_KG)
0. [Game of thrones](https://github.com/jeffreylancaster/game-of-thrones)
0. [star war](https://github.com/YZHANG1270/starwar_visualization)