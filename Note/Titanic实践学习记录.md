# Titanic实践学习记录

**计算生存几率模块**

- value_counts()是一个Series类方法，计算Series对象中每个唯一值的出现次数。

- 绘制圆饼图
  - plt.pie()
  - autopct用于控制圆饼图中显示百分比标签的参数，里边设置与C语言大致相同，如：%1.1f%%表示为宽度为1，保留小数点一位，为浮点数，末尾百分号表示在末尾添加百分号。
  - labels = ['...','...']表示给不同块进行字符串标注。
  - pctdistance用于控制圆饼图中百分比标签的位置的参数。表示百分比标签与圆心的距离，其取值范围为0到1，0表示在圆心，1表示在圆边。默认值为0.6，表示百分比标签距离圆心的距离为半径的0.6倍。
  - labeldistance用于控制圆饼图标签位置。默认值为1.1，表示标签位于圆边之外的 1.1 倍半径处。
  - shadow = True表示设置阴影。
  - explode用于控制饼图扇区分离程度的参数之一，可以通过设置 `explode` 参数来突出显示某些扇区，使其与其他扇区分离开来。例如：explode = [0, 0.1, 0, 0]，可以突出显示B扇区。
  - textprops通常用于设置标签文本的样式，包括字体大小、颜色、加粗、斜体等。
  
- 设置中文

  - ```python
    # 设置字体为宋体
    plt.rcParams['font.sans-serif'] = 'SimSun'
    # 设置字体大小
    plt.rcParams['font.size'] = 12
    ```

![](https://pic.imgdb.cn/item/65b9a944871b83018a14d177.jpg)

--------



**不同性别乘客的生还几率**

- train.groupby(by = 'Sex')表示以性别为依据对数据进行分类。

- `subplot()` 函数用于创建多个子图，它接受三个参数：`subplot(nrows, ncols, index)`。这里的 `nrows` 表示子图的行数，`ncols` 表示子图的列数，`index` 表示当前子图的位置。

- ```python
  sex_count.loc['female'][::-1]
  ```

  通过 loc['female'] 选择了其中的女性数据，然后通过 [::-1] 进行逆序排列。这样做是为了使得图表中“死亡”和“存活”的顺序与传入的数据一致。

![](https://pic.imgdb.cn/item/65b9b6f6871b83018a358a7f.jpg)





****



**不同年龄段乘客生还几率**

- `np.histogram(age_range, range=[0, 80], bins=16)`：这部分调用了 `np.histogram()` 函数来计算年龄数据的直方图。`age_range` 是一个包含年龄数据的一维数组，`range=[0, 80]` 表示年龄范围从 0 到 80，`bins=16` 表示将年龄范围划分为 16 个等宽的区间。函数返回两个值，第一个值是每个区间内的计数，第二个值是区间的边界。

- `append()` 是 Python 列表（List）对象的一个方法。它用于在列表的末尾添加一个元素。
- `plt.grid(True,linestyle=':',alpha=0.6)`：打开网格线，线型为虚线，透明度为 0.6。

![](https://pic.imgdb.cn/item/65b9f20c871b83018ae69e87.jpg)

------



**不同入口的存活率**

![](https://pic.imgdb.cn/item/65ba55ee871b83018a624639.jpg)



------



**不同等级乘客生还率**

![](https://pic.imgdb.cn/item/65ba5a5a871b83018a78aa19.jpg)



-----



**不同票价乘客的生还率**

- fare_count.reset_index(inplace=True)作用是重置DataFrame的索引，使之变为普通的数据列，以至于可以方便的对该列进行数据分析操作。
- 