# Lacmia

Lacmia 是一个针对中国多民族语言文本摘要的开源 Python 库。它旨在为研究人员和开发人员提供一个简单、高效、易于使用的工具，用以处理多元化的中国语言资源，并生成准确的摘要。Lacmia 支持包括汉语、藏语、维吾尔语等在内的多种民族语言。

## 特点

- 支持多种中国民族语言。
- 利用先进的自然语言处理技术生成摘要。
- 灵活的接口，易于集成到现有的 Python 项目中。
- 高效的处理速度，能够快速处理大量文本。

## 安装

你可以使用 pip 命令轻松安装 Lacmia：

```bash
pip install Lacmia
```

## 快速上手
下面是如何使用 Lacmia 生成一个简单的文本摘要的例子：

```python
from Lacmia.models.Lacmia import Lacmia

text = ["这里是需要生成摘要的文本内容列表。"]
model = Lacmia()

#use in chinese 
Abstractive = model.Abstractive(text,batch_size=1) # or Abstractive = model.Abstractive(text, language='zh', batch_size=1)

#use in Tibetan
#Abstractive = model.Abstractive(text, language='bo', batch_size=1)
#use in Uyghur
#Abstractive = model.Abstractive(text, language='ug', batch_size=1)
```
## 模型下载地址
|     type     	|   link   	| 提取码 	|
|:------------:	|:--------:	|----------	|
| Lacmia+LE+FT 	| [百度网盘](https://pan.baidu.com/s/1ieMSXL-_yf7TcgTD0JI5Xw?pwd=muc8) 	|     muc8     	|
| Lacmia-all1  	| [百度网盘](https://pan.baidu.com/s/1WgnV9fAUPiPK7SeiYhxrTA?pwd=muc6) 	|      muc6    	|
| Lacmia-all2  	| [百度网盘](https://pan.baidu.com/s/14zf5He5LwheEvOGQhY9nqA?pwd=muc0) 	|     muc0     	|

之后您可以这样使用模型
```python
from Lacmia.models.Lacmia import Lacmia
device = 'cpu' # or gpu(cuda)
model = Lacmia(model_path=your_model_path, device=device)
``` 

## 模型关于维吾尔语的说明
维吾尔语的书写可以分为“分词形式”和“连续书写形式”。

- **分词形式（Tokenized Form）**：
  - 单词之间用空格分隔，便于语言处理和分析。

- **连续书写形式（Continuous Script Form）**：
  - 单词连贯书写，无空格，传统书写方式。

### 示例

- **分词形式**：
  - *مەكتەپكە باردىم.*

- **连续书写形式**：
  - *مەكتەپكەباردىم.*

两者表达的意思相同，即“我去学校了”。

- **分词形式**：
  - *مەن بۈگۈن كەچتە دوستلىرىم بىلەن باغچاغا بارىدىغان بولدۇم.*

- **连续书写形式**：
  - *مەنبۈگۈنكەچتەدوستلىرىمبىلەنباغچاگابارىدىغانبولدۇم.*

这两句话的意思都是“我今晚要和朋友们去公园。”

针对两种形式的维吾尔语，我们都训练了对应的模型,其中`Lacmia-all-1`支持分词形式，`Lacmia-all-2`支持连续书写模型。
## 支持的语言
目前，Lacmia 支持以下民族语言的摘要生成：

- 汉语（zh）
- 藏语（bo）
- 维吾尔语（ug）

- ...更多语言支持即将到来！

--- 
## MESUM数据集

多民族语言的数据集MESUM(Multi-Ethnic Summarization)。该数据集将下面中、藏、维三种语言的训练集进行随机顺序的混合组成，其构成如下：

1. 中文LCSTS数据集：在清洗数据集之后，本文使用原本数据集的训练集，测试集，验证集进行融合，再按照8:1:1的比例划分训练集，验证集，测试集，清洗过后的训练集有162111条摘要文本对。
2. 藏文数据集：藏文数据集是我们从多个藏文网站上爬取的新闻和文本对，本文将藏文数据集按照8:1:1的比例划分为训练集，验证集和测试集，得到训练集37985条数据，测试集3800条数据。
3. 维吾尔语数据集：本文的维吾尔语数据集都是从维文网站上爬取的新闻文本对，同样经过清洗之后，获得了1824条训练数据对和200条测试数据对。


## 数据集获取说明

### 获取流程

1. **申请邮件**：
   - 请将申请邮件发送至 `liuzheng@muc.edu.cn`。
   - 邮件主题请注明“少数民族摘要数据集申请”。

2. **邮件内容**：
   - **姓名**：研究者的全名。
   - **机构**：所属研究机构或大学。
   - **研究目的**：简要描述研究项目和数据集的使用目的。
   - **数据使用计划**：详细说明如何使用数据集，包括预期成果和可能的发表途径。

3. **审批流程**：
   - 我们将在收到申请后尽快进行审核。
   - 审核通过后，将通过邮件发送数据集下载链接和使用协议。

### 使用限制

- **学术用途**：数据集仅限于非商业的学术研究使用。
- **引用要求**：任何发表的研究需在文中注明数据集的来源。
- **隐私保护**：禁止尝试还原或识别数据中的个人信息。
- **二次分发**：未经许可，禁止将数据集分享给第三方。

### 特殊说明
因为MESUM数据集中有部分**敏感数据**，所以我们分享的数据集中对应三种语言的数量并不一定与论文中相同。


我们期待与您合作，共同推进少数民族语言研究的发展。

--- 



## 贡献
我们欢迎任何形式的贡献，无论是新语言的支持、bug 修复、功能增强或是文档改进。\
\
请遵循以下步骤：

- Fork 项目到你的 GitHub 账户下。
- 创建你自己的分支（git checkout -b feature-fooBar）。
- 提交你的改变（git commit -am 'Add some fooBar'）。
- 推送到分支（git push origin feature-fooBar）。
- 创建一个新的 Pull Request。

## 许可证
本项目采用 MIT 许可证 - 详见 LICENSE 文件。

## 支持
如果在使用 Lacmia 时遇到任何问题，或者有任何建议，欢迎通过 GitHub 的 issues 来提交。