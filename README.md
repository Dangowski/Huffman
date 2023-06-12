一、处理原始数据

1.待编码的数据在word文件，因此导入python针对word处理的包docx。Docx读入每一段落的数据并存储在列表中。简单分析，提取需要编码的段落索引。

![img](file:///C:/Users/zkw/AppData/Local/Temp/msohtmlclip1/01/clip_image002.jpg)

2.统计字符类型和数量，并建立字符频率字典。

![img](file:///C:/Users/zkw/AppData/Local/Temp/msohtmlclip1/01/clip_image004.jpg)

![img](file:///C:/Users/zkw/AppData/Local/Temp/msohtmlclip1/01/clip_image006.jpg)

二、Huffman树构造

1.定义结点类，类定义huffman树类。

![img](file:///C:/Users/zkw/AppData/Local/Temp/msohtmlclip1/01/clip_image008.jpg)

![img](file:///C:/Users/zkw/AppData/Local/Temp/msohtmlclip1/01/clip_image010.jpg)

2.Huffman树构建步骤:

1).符号按概率大到小排序，权重为概率；

 2).取概率最小的字符作为左结点，其次小的符号为右结点；

 3).将2中两个(最小)元素合并作为新的结点，权重为概率和；

 4).新结点和剩余结点重新排序；

 5).重复步骤(2),直到待排列的结点只剩一个（即为根结点）;

 6).最后产生的树状图就是Huffman树；

 7).左节点为0，右节点为1，从根节点到子节点的一条路径即是符号的码字；

3.编码：从叶子结点到根结点

4.解码：从根结点到叶子结点

5.一个简单例子测试上述编码解码的正确性

 

![img](file:///C:/Users/zkw/AppData/Local/Temp/msohtmlclip1/01/clip_image012.jpg)

![img](file:///C:/Users/zkw/AppData/Local/Temp/msohtmlclip1/01/clip_image014.jpg)

![img](file:///C:/Users/zkw/AppData/Local/Temp/msohtmlclip1/01/clip_image016.jpg)

![img](file:///C:/Users/zkw/AppData/Local/Temp/msohtmlclip1/01/clip_image018.jpg)

![img](file:///C:/Users/zkw/AppData/Local/Temp/msohtmlclip1/01/clip_image020.jpg)

三、数据编码

编码过程就是从叶子结点到根结点逆读取

1.利用第一步统计的数据，建立huffman编码表，在第一部基础上把列表改为字典，并去掉频率字典中为0的元素。

![img](file:///C:/Users/zkw/AppData/Local/Temp/msohtmlclip1/01/clip_image022.jpg)

![img](file:///C:/Users/zkw/AppData/Local/Temp/msohtmlclip1/01/clip_image024.jpg)

2.再一次遍历统计数据列表，进行huffman编码

![img](file:///C:/Users/zkw/AppData/Local/Temp/msohtmlclip1/01/clip_image026.jpg)

四、数据解码

解码只需要将经过编码的比特串不断从huffman树的根结点遍历。每到一次叶子结点，即解码出一个字符。

![img](file:///C:/Users/zkw/AppData/Local/Temp/msohtmlclip1/01/clip_image028.jpg)

五、计算压缩比

不同的编程语言对于字符的存储内存分配机制不同。这里假设，一个字符分配1个字节(Byte)，即8比特(bit)。huffman编码将每个字符编码为一个长度不一的二进制bit串，故能压缩编码长度。最终计算出压缩比为44.9086%.

![img](file:///C:/Users/zkw/AppData/Local/Temp/msohtmlclip1/01/clip_image030.jpg)