# 对招聘数据进行爬取和分析

## 问题背景
笔者对统计专业适用的岗位不甚了解，因此希望通过对拉勾网的招聘数据进行爬取与分析，以了解统计专业所适用的职业。笔者根据多个与统计相关的关键词爬取招聘数据，并使用IF-IDF方法选取关键词并组合，根据组合关键词对拉勾网二次搜索，并使用统计方法筛选匹配的招聘职位，最后对招聘数据进行可视化。
## 方法步骤
- 查阅中国人民大学本硕统计学院培养方案和学院介绍、统计与大数据研究院招生简章和学院介绍，提取第一次搜索关键词
- 使用selenium、urllib3、BeautifulSoup根据第一次搜索关键词爬取第一次招聘数据，并清洗和处理数据，生成csv文件
- 根据第一次招聘数据职位描述对数据标注是否适用统计专业学生
- 使用jieba对职位描述进行分词，并使用IF-IDF方法选取词汇，并手动地对词汇进行组合，生成有效第二次搜索关键词
- 根据第二次搜索关键词爬取第二次招聘数据，约25000条数据，并清洗和处理数据，生成csv文件
- 根据第一次招聘数据的标注，使用对数似然概率的优势比对第二次招聘数据是否使用统计专业学生进行分类，其中使用十折交叉验证选择合适的模型参数
- 获得约20000条适用的招聘数据
- 根据城市、经验、学历、行业等维度，使用直方图、箱线图、条形图、棒棒图、词云图对招聘数据进行可视化
## 文件结构
__数据爬取.ipynb__：
负责根据关键词对拉勾网进行数据爬取

__数据清洗和建模.ipynb__：
对爬取的数据进行清洗、转换，生成pandas.DataFrame,并根据第一次招聘数据的标注，使用对数似然概率的优势比对第二次招聘数据是否使用统计专业学生进行分类

__数据分析.ipynb__：
根据城市、经验、学历、行业等维度，使用直方图、箱线图、条形图、棒棒图、词云图对招聘数据进行可视化

__test_data__：
文件夹，存储清洗过的第一次招聘数据的csv文件

__key_id.json__：
存储第二次爬取获取的position_id

__data.json__：
存储第二次爬取结果的json格式数据


__work_data.csv__：
存储清洗过的第二次招聘数据的csv文件

__培养方案关键词.txt__：
存储第一次搜索关键词

__拓展关键词组合.txt__：
存储第二次搜索关键词

__stealth.min.js__：
对selinium注入js，进行伪装

__stopwords.txt__：
jieba分词时使用的停用词

__数据集存储地址__：  链接：https://pan.baidu.com/s/1TzI1be8T6giEdxrA12kNrw  提取码：a7q1（存储 __test_data__ 、__key_id.json__、__data.json__、__work_data.csv__）

## 数据可视化
![Boxplot of Month Salary](https://github.com/dengniewei/crawer-and-analysis-for-cecruiting-data/blob/main/Screenshots/Boxplot%20of%20Month%20Salary.png)

