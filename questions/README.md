为了在移动端可以动态加载KYC问卷，我们将问卷问题以JSON格式存放在本目录中。

每个版本的问卷，都需要有三个语言的版本，分别是：

- 中文简体，questions_zh_Hant.json
- 中文繁体，questions_zh_Hans.json
- 英文，questions_en.json

理论上讲，每个版本的以上三个文件内容都是一样的，只是把每个题目的**题干**和**选项**更换了语言。

本仓库内的所有问卷文件，由**产品团队**维护。

**当前版本**的问卷（1.0.1），有任何的改动，即需要生成新的版本(1.0.2)。

同时，将1.0.1版本的三份文件做重命名，并保存在当前目录中，重命名规则为：

- 中文简体，questions_zh_Hant_1.0.1.json
- 中文繁体，questions_zh_Hans_1.0.1.json
- 英文，questions_en_1.0.1.json

**当前版本**的文件不包括版本号，所有历史版本都需要包括版本号。

所有的历史版本的文件，原则上不应该被改动。只能在当前版本的基础上创建新的版本。

json文件的格式定义如下：

```json
{
    "version": "1.0.0",// json文件的版本号，由产品来管理
    "questions": [
        {
            "key":"xxxx",//为了兼容web现有实现，value由产品从web kyc字段的excel中获取
            "type": "single",//题型 单选single、多选multiple
            "title": "加密货币交易的经验",//问题
            "column": 1,//每行展示列数，产品根据选项文案的长度来确定，如BTC、ETH币种选项时为3
            "choices": [//选项列表
                "暂无经验",
                "1-3年",
                "5-10年"
            ],
            "required": true,//true 必填，false 选填
            "lastUserInput": false,//true 选中最后一项用户，可输入其他文本
            "hintText": "请输入其他加密货币名称"//lastUserInput 为true 时必传，为文本输入框的占位
        },
        {
            "key":"xxxx",
            "type": "multiple",
            "title": "与我们交易的原因",
            "column": 1,
            "choices": [
                "交易加密货币投资",
                "钱包和托管服务",
                "支持OTC业务交易"
            ],
            "required": false,
            "lastUserInput": false
        }
    ]
}
```