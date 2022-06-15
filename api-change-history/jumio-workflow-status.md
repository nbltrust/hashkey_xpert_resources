API变更申请状态（初始/讨论/通过/拒绝/搁置）

***


接口：GET /api/v1/kyc/application


变动：
```javascript
response body 添加字段 jumioWorkflowStatus:
{
    jumioWorkflowStatus: "INITIATED"   // INITIATED/ACQUIRED/PROCESSED/SESSION_EXPIRED/TOKEN_EXPIRED，具体值说明见 apipost
}
```

***

对web端的影响分析：
web端 jumio 是同步获取结果的，不需要知道 jumio workflow 的状态

对App端的影响分析：
app 可以根据此状态判断是否已经进行了 jumio 认证

***

***

接口：GET /api/v1/kyc/application/jumio


变动：
```javascript
response error code 添加
20047 -- Jumio Acquired，jumio认证已提交
20048 -- Jumio Processed，jumio认证已结束
```

***

对web端的影响分析：
web端 jumio 是同步获取结果的，不需要知道 jumio workflow 的状态

对App端的影响分析：
app 可以根据此返回码判断是否已经进行了 jumio 认证

***

变动发起人：zhang yang
