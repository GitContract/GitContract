<p align="center"><img width="240" src="https://github.com/GitContract/GitContract/blob/main/docs/logo.png?raw=true" alt="GitContract logo"></p>


本项目目的在于利用Git工具和公开仓库来存放、公示和追溯合约。

合约是以Github账号为主体的，因此不应该出现个人姓名或公司名称。

本仓库不接受任何回滚操作和创建分支操作，且将永久公开。



### 目录结构

```
|_ published
|  |_templates
|. |_contracts
|
|_ draft
   |_templates
   |_contracts
```

其中，`published`用于存放正式的合约模版和已签订合约，`draft`中用于存放合约模版草案以及待签订合约。`published`和`draft`下都包涵了`templates`和`contracts`目录，用于分别存放合约模版与合约。



### 发布流程

合约模版必须先提交草案。草案阶段的合约模版不接受任何签约操作。草案阶段中，模版提交方应不断审核该草案的合理性并在需要时进行调整。

#### 草案阶段

1. fork本仓库并clone下来
2. 在`draft->templates`中创建目录，目录名称为合约主体中雇佣方的Github用户名，若已存在则忽略本步骤
3. 在步骤2创建的目录中，放入合约模版草案文件，该文件命名方式为`合约模版名-版本号`
4. 提交代码并创建pull request
5. GitContract会审核合约模板，主要验证提交方用户名是否与草案中雇佣方同名，以及敏感词类审核

#### 发布阶段

当发布方确认当前草案模版可以正式发布时，执行如下流程：

1. 在`published->templates`中创建目录，目录名称为合约主体中雇佣方的Github用户名，若已存在则忽略本步骤
2. 将`draft->templates->GITNAME`下要发布的合约模板文件移动到步骤1创建的目录中
3. 提交代码并创建pull request
4. GitContract会审核合约模板，主要验证提交方用户名是否与草案中雇佣方同名，以及敏感词类审核



### 合约签署流程

合约的签署需要合约双方进行配合操作。流程如下：

1. 被雇佣方fork本仓库并clone下来
2. 在`draft->contracts`中创建目录，目录名称为合约主体中被雇佣方的Github用户名，若已存在则忽略本步骤
3. 将编辑好的合约文件放入步骤2创建的目录中，该文件命名方式为`合约模板雇佣方Github名称-合约模版名-版本号`
4. 提交代码并创建pull request
5. GitContract会审核合约草案，主要验证提交方用户名是否与合约草案中被雇佣方同名，以及敏感词类审核
6. 雇佣方fork本仓库并clone下来
7. 在`published->contracts`中创建目录，目录名称为合约主体中被雇佣方的Github用户名，若已存在则忽略本步骤
8. 将`draft->contracts->GITNAME`下要发布的合约文件移动到步骤7创建的目录中
9. 提交代码并创建pull request
10. GitContract会审核合约，主要验证提交方用户名是否与合约中雇佣方同名，以及敏感词类审核



### 文件格式要求

#### 合约模板

1. 不得在合约模板内部带有暴力、性交易、政治敏感、管制器械、管制药品、黑客入侵等反人道词汇
2. 合约模板仅限于雇佣与被雇佣两方，不应包含第三方参与签署
3. 合约中变量部分可以使用`{var}`进行标注，其中`var`为自定义变量名

示例

```
本人xxx@email.com，于2021年4月19日发起本合约。
...
受雇人员{employee}，每月可获的酬劳为{payment}元。
...
```



#### 合约

1. 合约文本为JSON格式对象结构，每一个key值应与合约模板中的变量一一对应
2. 不得在合约内部带有暴力、性交易、政治敏感、管制器械、管制药品、黑客入侵等反人道词汇

示例

```json
{
  "employee": "Github用户名",
  "payment": "1"
}
```
