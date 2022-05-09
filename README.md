# excel23

excel 转 java、c#、lua 三种数据表形式

有问题可以加QQ群：589160967

1.第一次运行前，需要修改根目录 config 文件，文件说明<br>
  FileName=excel导出文件路径、文件名<br>
  JavaPath=Java反序列化文件路径、文件名<br>
  CsharpPath=C#反序列化文件路径、文件名<br>
  LuaPath=Lua反序列化文件路径、文件名<br>
  TablePath=excel文件夹路径，需要将excel后缀改为xml<br>
  
2.设置好后，运行工具<br>

3.表格部分说明<br>
    文档第几页：excel的页签下标，从0开始<br>
    开始行数：excel表格行数下标，从0开始<br>
    开始列数：excel表格列数下标，从0开始<br>
    数据列数：一共要读取的列数<br>
    表名："config" 配置文件中 "TablePath" 路径下的文件名（不包含 .xml 后缀）<br>
    程序中的名称：反序列化文件生成后的类名<br>
    
4.编码类型<br>
    UTF-8：通用格式，支持Lua<br>
    UTF-16：中文增强模式，不支持Lua<br>
    
5.根据需求操作最下排功能按钮：<br>
    添加列：在表格部分新增一列<br>
    删除选中列：删除表格中当前选中的列<br>
    备份当前列表：保存当前表格部分的列表数据，方便下次打开使用<br>
    还原表格列表：在有保存过表格列表的情况下，可进行还原操作<br>
    导出：按照表格部分形式数据导出excel数据，输出路径为 "config" 中的每个路径类型<br>
    清空：清除当前表格部分<br>
    
6.数据表格式<br>
    6.1.第一列必须为Id<br>
    6.2.支持 int、float、String、boolean、Array 五种数组类型<br>
    6.3.不能使用 int、float、array、string、list、map 作为列名<br>
    
7.使用(以测试数据表 tables/test.xml 为例)<br>
<p>
  C#:<br>
  byte[] bytes = ...;//读取表数据文件<br>
  org.jiira.protobuf.SAProtoDecode.getInstance().parsing(bytes);//反序列化表数据结构<br>
  List<ExTest> testList = ExTest.getList();<br>
  print(testList[0].Id);<br>
  Dictionary<int, ExTest> testMap = ExTest.getMap();<br>
  print(testMap[100].Id);<br>
</p>
  
<p>
  Java:<br>
  LittleEndianDataInputStream dos = new LittleEndianDataInputStream(new FileInputStream("数据表文件路径"));<br>
  SAProtoDecodeTemp.getInstance().parsing(dos);//反序列化表数据结构<br>
  ArrayList<ExTest> testList = ExTest.getList();<br>
  System.out.println(testList.get(0).getId());<br>
  Map<Integer, ExTest> testMap = ExTest.getMap();<br>
  System.out.println(testMap.get(100).getId());<br>
</p>
<p>
Lua:<br>  
  SAProtoDecode:parsing("数据表文件路径")<br>
  print(SAProtoDecode.STCharacter.list[0].Id)<br>
  print(SAProtoDecode.STCharacter.map[100].Id)<br>
</p>
<br>
8.有问题请加QQ群 589160967
    
