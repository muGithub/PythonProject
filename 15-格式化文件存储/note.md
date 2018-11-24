# 结构化文件存储
- xml，json，
- 为了解决不同设备之间的信息交换
- xml
- json
- XML文件
- 参考资料
    - https://docs.python.org/3/library/xml.etree.elementtree.html
    
- XML(extensibleMarkuplanguage), 可扩展标记语言
    - 标记语言：语言中使用尖括号括起来的文本字符串标记
    - 可扩展：用户可以自己定于需要的标记
    - 例如：
            
            <Teacher>
                自定义标记Teacher
                在两个标记之间任何内容都应该跟Teacher相关
            </Teacher>
    - 是问c组织制定的一个标准
    - XML描述的是数据本身，即数据的结构和语义
    - HTML侧重于如何显示web页面中的数据
- XML文件的构成
    - 处理指令（可以认为一个文件内只有一个处理指令）
        - 最多只有一行且必须在第一行
        - 一般用于声明XML的版本和采用目的
            - version属性是必须的
            - encoding属性用来指出XML解释器使用的编码
        - 内容是与xml本身处理器相关的一些声明或者指令
        - 以xml相关字开头
        - 在xml文件中
    - 根元素（文件内只有一个根元素）
        - 在整个xml文件中，可以把它看作一个树形结构
        - 根元素有且只有一个
    - 子元素
    - 属性
    - 注释
        - 起说明作用的信息
        - 注释不能嵌套在标签里面
        - 只有在注释的开头和结尾使用双短横线
        - 三短横线只能出现在注释的开头而不能用在结尾
    - 内容
        - 表明标签所存储的信息
        
- 保留字符的处理
    - XML中使用的富豪可能跟实际符号冲突，典型的就是左右尖括号
    - 使用实体引用（EntityReference）来表示保留字符
            <score> score>80 </score> # 有错误，xm中不能出现>
            <score> score&gt </score> # 使用实体引用
    - 把含有保留字符的部分放在CDATA块内容，CDATA块把内部信息视为不需要转义
        
        - <![CDATA[
            select name,age
            from Student
            where score>80
            ]]>
            
    - 常用的需要转义的保留字符和相对应实体引用
        - &：&amp;
        - <: &lt;
        - >: &gt;
        - ': &apos;
        - ": &quot;
        - 一共五个，每个实体饮用都以&开头并且以分号结尾
        
XML标签的命名规则
    - Pascla命名法
    - 用单词表示，第一个字母大写
    - 大小写严格区分，大写不等于小写
    - 配对的标签必须一致
    
- 命名空间
    - 为了防止命名冲突
            
            <name type="web">
                haha（内容）
            </name>
            <age approach="by himself">
                18
                <!---这里是注释-->
            </age>
            
    - 如果归并上述两个内容信息，会产生冲突
            
             <name type="web">
                haha（内容）
            </name>
            <age approach="by himself">
                18
                <!---这里是注释-->
            </age>
    - 为了避免冲突，需要给可能冲突元素添加命名空间
    - xmlns：xml， name， space的缩写
        <Schooler xmlns:student="http://my_student" xmlns:room="http://my_room">
            <name type="web">
                haha（内容）
            </name>
            <age:name approach="by himself">
                18
                <!---这里是注释-->
            </age>
        </Schooler>

# XML访问

## 读取
- XML读取分两个主要技术，SAX，DOM
- SAX（simple API for XML）：
    - 基于事件驱动
    - 利用SAX解析文档涉及到解析器和事件处理两部分
    - 特点：
        - 快
        - 流式读取
            
- DOM
    - 是W3C规定的XML编程接口
    - 一个XML文件在缓存中以树形结构保存
    - 