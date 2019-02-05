---
description: >-
  This task is to access real knowledge bases like DBpedia, YAGO, and Wikidata
  and also access their ontology from a Java program.
---

# Access KBs and their Ontology Graph

## Wikidata

According to Summary\_Ontology, 参考他们获取ontology的办法如下：

1. The **Wikidata Toolkit** helps to parse the dump file and to analyze each of the entities contained in the ontology.
2. A separate controller, called “ClassParser.java”, was built to help in collecting only the class entities which have **‘subclass of**’ and **‘instance of**’ properties.
3. Only store the values for: ID, the label and description in English, and the value for ‘subclass of’ and ‘instance of’ statements of each found item.
4. transform the ID of each class entity, which is stored as a string value, into an integer type, by removing the “Q”char from it

### Things to do

#### 1. Use Wikidata Toolkit to use example code, such as 

存在问题\_1：wikidata toolkit 因为maven和Git插件的问题一直没有解决，确切的说是我还不知道怎么用这个library

1. 再仔细读文档
2. 上网搜下别人是怎么得到wikidata ontology的

已解决：

1. Eclipse&gt; help&gt; install new Software&gt; Enter site: [http://download.eclipse.org/technology/m2e/releases](http://download.eclipse.org/technology/m2e/releases)   \(Found it at [https://www.eclipse.org/m2e/](https://www.eclipse.org/m2e/) \)
2. Eclipse&gt; Preferences &gt; Maven&gt; Discovery&gt; Open Catalog &gt; Download egit \(m2e team provider\) which is a SCM handler for Maven
3. Eclipse&gt; File&gt; Import&gt; Maven&gt; Check out Maven Projects from SCM &gt;Choose git &gt; Enter site of github repository: [https://github.com/Wikidata/Wikidata-Toolkit.git](https://github.com/Wikidata/Wikidata-Toolkit.git) &gt; Finish

存在问题——2：怎么把import的project run起来，按以下步骤run，报了几个错。

Prepare to run 

1. Build the project with Maven: 
   1. Right-click on module “parent” 
   2. Run as&gt; Maven install 
   3. This downloads and installs all dependencies

报错——1：  
SLF4J: Failed to load class "org.slf4j.impl.StaticLoggerBinder".

SLF4J: Defaulting to no-operation \(NOP\) logger implementation

SLF4J: See http://www.slf4j.org/codes.html\#StaticLoggerBinder for further details.

解决——1：

[https://www.slf4j.org/codes.html](https://www.slf4j.org/codes.html)    [https://developers.perfectomobile.com/display/TT/Error+messages+during+Quantum+execution%3A+Failed+to+load+class+org.slf4j.impl.StaticLoggerBinder](https://developers.perfectomobile.com/display/TT/Error+messages+during+Quantum+execution%3A+Failed+to+load+class+org.slf4j.impl.StaticLoggerBinder)

报错——2：Failed to execute goal org.apache.maven.plugins:maven-surefire-plugin:2.12.4:test \(default-test\) on project wdtk-datamodel: There are test failures.

解决——2：

[https://groups.google.com/forum/\#!topic/selion/3m5uI9YpPkQ](https://groups.google.com/forum/#!topic/selion/3m5uI9YpPkQ) [https://github.com/cbeust/testng/issues/1693](https://github.com/cbeust/testng/issues/1693)

[Run a custom maven command in Eclipse as follows:](https://stackoverflow.com/questions/19793895/run-mvn-clean-install-in-eclipse)

1. Right-click the maven project or pom.xml
2. Expand **Run As**
3. Select **Maven Build...**
4. Set _Goals_ to the command,  `install -DskipTests`

Note: Eclipse prefixes the command with `mvn` automatically.

存在问题——3：

![Error when reading JSON for entity: Unexpected end of ZLIB input stream \(through reference chain: org.wikidata.wdtk.datamodel.implementation.ItemDocumentImpl\[&quot;claims&quot;\]-&amp;gt;java.util.LinkedHashMap\[&quot;P2856&quot;\]-&amp;gt;java.util.ArrayList\[0\]\) E](../../../.gitbook/assets/screen-shot-2019-01-27-at-3.08.41-pm.png)

有用的链接

{% embed url="https://interviewbubble.com/slf4j-failed-to-load-class-org-slf4j-impl-staticloggerbinder-slf4j-defaulting-to-no-operation-nop-logger-implementation-slf4j-see-http-www-slf4j-org-codes-htmlstaticloggerbinder-for-furth/" %}



{% embed url="https://stackoverflow.com/questions/18200248/cloning-a-repo-from-someone-elses-github-and-pushing-it-to-a-repo-on-my-github" %}

{% embed url="https://jitpack.io/\#dabingcheerup/Wikidata-Toolkit/-SNAPSHOT" %}

{% embed url="https://stackoverflow.com/questions/19848440/hot-fixing-a-bug-in-a-third-party-library-dependency" %}

{% embed url="https://bbs.csdn.net/topics/390763463" %}

{% embed url="https://mvnrepository.com/artifact/com.fasterxml.jackson.core/jackson-databind/2.9.5" %}

{% embed url="https://stackoverflow.com/questions/25413842/the-type-com-fasterxml-jackson-core-jsongenerator-cannot-be-resolved-it-is-indi" %}

{% embed url="https://stackoverflow.com/questions/9341644/the-project-was-not-built-since-its-build-path-is-incomplete" %}

{% embed url="https://stackoverflow.com/questions/14609722/the-import-org-apache-commons-cannot-be-resolved-in-eclipse-juno" %}

### 2. decompress dumps to generate graph and ontology graph by adjacent list

之前尝试使用wikidata toolkit, 在运行Example Code: DataExtractionProcessors.java 出现error：没法儿解决。

并且之前没弄清楚要做的，真正要做的是把数据转成有向图，通常的做法是用adjacent matrix或者adjacent list

因此，接下来目标是在下次开会的时候能够把wikidata的图给老师，并且开始做DBpedia 的！！！

要做的是：

1. [ ] decompress dumps
   1. [x] [https://topicseed.com/blog/importing-wikidata-dumps](https://topicseed.com/blog/importing-wikidata-dumps)
   2. [ ] 先试下simple dump，在思考要不要在local decompres 还是用API？ API怎么用？
2. [ ] data format
   1. [ ] Google
   2. [x] 打开dump来看\(sample\)
   3. [ ] [https://www.mediawiki.org/wiki/Wikibase/DataModel](https://www.mediawiki.org/wiki/Wikibase/DataModel)
3. [ ] How is the graph for random walk
   1. [ ] what is random walk?
   2. [ ] how is the graph?
4. [ ] how to generate directed graph for random walk?
   1. [ ] Google
      1. [x] [https://www.quora.com/How-do-you-create-a-directed-graph-in-Java](https://www.quora.com/How-do-you-create-a-directed-graph-in-Java) \(用adjacent list\)
   2. [ ] How is graph for random walk?
   3. [ ] Does wikidata provide any tools for graph generation?
   4. [ ] GitHub
   5. [ ] 总结思路
   6. [ ] 确定要的方程list
   7. [ ] 开始Code
   8. [ ] Preprocess\(discard entities without en label, en desc, instance of, subclass of
   9. [ ] 
5. [ ] how to generate directed ontology graph for random walk?
6. [ ] download DBpedia dumps
7. [ ] decompress dumps
8. [ ] data format
9. [ ] how to generate directed graph

尽量找别人做过的参考

## DBpedia

因为DBpedia的ontology包括YAGO，wikidata和其他数据库的，所以access完wikidata的，看DBpedia



