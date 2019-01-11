HDFS的优点
- 高容错性（数据多副本，自动恢复）
- 适合批处理
    - 移动计算而非数据
    - 数据位置暴露给计算框架
- 适合大数据处理
    - GB，TB，PB级数据
    - 百万规模以上
    - 10K+ 节点
- 可构建在廉价机器上（容错机制）


HDFS的缺点
- 延迟高
- 小文件存储
    - 占用 NameNode 大量内存
    - 寻道时间超过读取时间
- 并发写入，文件随机修改
    - 一个文件只能有一个 writer
    - 仅支持 append（2.0 有这个功能，但生产环境一般不开放）


--------------------------------------------------


HDFS 数据存储单元（block）
- 每个 block 默认3个副本（例如，一个服务器断电，会自动复制一个，通电后会一直保持4个）
- block 默认64M
- 所占磁盘空间按照实际来