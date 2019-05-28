# tfidf
TF-IDF（Term Frequency-Inverse Document Frequency）是在信息检索和文本挖掘中常用的加权算法。IF-IDF用以评估一个词对一个文档在一个文档集（语料库）中的重要程度。词的重要程度与词在本文档中出现的频率成正比但随着词在文档集中出现的总频率增加而下降，TF-IDF算法常用于搜索引擎、文件索引、关键词提取。
TF（Term Frequency）词频，指的是一个词在文档中出现的频次。

IDF（Inverse Document Frequency）逆文档频率，指的是一个词在文档集中的重要性的度量。

文档D中词w在文档集U中的TF-IDF值表示为（2-11）：

TF‐IDF(w)=tf(w)*idf(w)
=tf(w)*log(N/df(w) )                  （2-11）

其中，tf(w)表示词w在文档D中出现的频率，df(w)表示文档集U中出现词w的文档数量，N表示文档集U的文档总数量。

在通常情况下进行TF‐IDF进行关键词提取需要首先排除无实际意义的停用词，如“的”、“地”、“很”等。

TF-IDF运用于文本特征值提取时，文档集的选取有重要的关系，如果文档集的选择不全面会影响关键词提取的准确性。本文利用百度搜索引擎收录的文档作为文档集D，百度搜索返回结果条数作为df(w)。通过搜索“的”、“地”等字发现百度搜索最大能返回100000000（一亿）条相关结果，故将N的值设定为100000000。

例如，本文截止2019年5月28日使用百度搜索“TF-IDF”，通过使用上文中提到的Web页面信息抽取技术可获取df(TF-IDF)=3,580,000。

基于搜索引擎的TF-IDF算法，充分利用百度等搜索引擎海量的数据存储、快速的文本索引的特点，将TF-IDF中的文本集使用百度所收录的Web网页集合表示，将文档频率用百度搜索返回数量表示，使TF-IDF算法更加适用于异源在线社会网络信息的关键词提取，基于搜索引擎的TF-IDF算法流程如图2-6所示，详细步骤如下：

Step1：输入文本的词集合，各个词的词频，提取关键词的数量n；

Step2：遍历词集合，从DF数据库查询每个词的文档频率；

Step3：如果没有找到词的文档频率，通过利用百度搜索返回的搜索条数为文档频率DF，并将结果写入DF数据库；

Step4：计算词集合中每个词的TF-IDF值；

Step5：返回词集合中TF-IDF值最大的n个词作为该文本的关键词集合。


