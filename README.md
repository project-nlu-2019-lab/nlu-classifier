# nlu-classifier

NLU 意图识别 三级分类任务

## 项目目录结构
```
nlu-classifier
│
├── data：存放训练/测试数据，进行数据预处理
│
├── bert-master：训练/测试分类器目录
│   └── chinese_L-12_H-768_A-12：存放BERT预训练模型（中文，Tensorflow格式）
│
├── classifier：最终要交付的程序，实现多级分类的一系列逻辑
│   ├── resources：存储各类资源文件（如分类器模型参数、匹配规则、各类配置、关键词表、停用词表等）
│   ├── modules：存放
│   └── main.py: 分类主程序，给定一句话，输出类别
│
└── README.md：项目说明文件
```

## 类别层级
```
/客户
/客户/我有钱
/客户/过段时间再说
/客户/已经投保
/客户/是家庭主妇
/客户/缴费时长
/客户/负担不了保费
/客户/号码来源
/客户/是否是保险公司员工
/客户/保险不如存银行方便
/客户/过段时间再说
/客户/没结婚
/客户/诱导销售伪造信息
/客户/诱导销售态度恶劣
/客户/诱导销售许可客户代签字
/客户/诱导销售提供个人联系方式
/客户/诱导销售混淆其他金融产品
/客户/诱导销售承诺上门理赔直接取现金
/客户/诱导销售用赠送保险的名义
/客户/诱导销售提保障不需要消费
/客户/诱导销售说出与保监会不实的规定
/客户/诱导销售虚假宣传保险相关法律法规
/客户/诱导销售诋毁同业
/客户/诱导销售说打折减免优惠
/客户/诱导销售说收益
/客户/诱导销售对减额缴清年限举例不当
/客户/诱导销售保单贷款说法有误
/客户/诱导销售不正确说明理赔的医院限制
/客户/诱导销售出现保单不符合受理或承保要求
/客户/没钱以后再说
/客户/存银行
/客户/宁可存银行
/客户/花钱给别人享受
/客户/人不在了要钱没用
/客户/不想买保险给太太当嫁妆
/客户/对救治不报希望
/客户/没兴趣
/客户/忌讳谈保险
/客户/宁愿炒股票
/客户/买理财
/客户/希望资金灵活
/客户/有钱及时行乐
/客户/存钱买房
/客户/身体很健康
/客户/年纪大了没子女
/客户/靠子女
/客户/光棍
/客户/有亲朋好友在保险公司
/客户/有社保和医保
/客户/公务员
/客户/公司买了各种保险
/客户/收入不稳定
/客户/和家里人商量
/客户/我太太不同意
/客户/是否保意外
/客户/找代理
/客户/肯定答复
/客户/答复工作
/客户/答复买过什么保险
/客户/询问投保时间
/客户/答复投保时间
/客户/答复血压
/客户/答复脂肪肝
/客户/否定答复
/客户/没空
/客户/违禁语
/客户/结束语
/客户/问候语
/客服
/客服/联络
/客服/联络/问候
/客服/联络/说明来意
/客服/联络/挽回
/客服/联络/再见
/客服/联络/再约
/客服/促成
/客服/促成/在线下单
/客服/促成/保险与银行
/客服/促成/保险与银行/保险和银行存款可以兼得
/客服/促成/保险与银行/保险比银行保障更及时
/客服/促成/健康保险刻不容缓
/客服/促成/健康保险刻不容缓/此血压需及时购买
/客服/促成/健康保险刻不容缓/轻度脂肪肝需及早购买
/客服/促成/健康保险刻不容缓/健康比意外更需要保障
/客服/促成/健康保险刻不容缓/保费会逐年增长
/客服/促成/健康保险刻不容缓/有钱更需要健康保障
/客服/促成/我更专业
/客服/促成/我更专业/电销监管比代理更严格
/客服/促成/公司有竞争力
/客服/促成/家庭责任
/客服/促成/家庭责任/自己的人生自己把握
/客服/告知
/客服/告知/险种介绍
/客服/告知/险种介绍/险种涵盖
/客服/告知/险种介绍/轻症的确认和赔付
/客服/告知/险种介绍/身故或重疾的赔付
/客服/告知/险种介绍/健康平安的获利
/客服/告知/险种介绍/投保人意外
/客服/告知/险种介绍/等待期免责
/客服/告知/险种介绍/缴费方式
/客服/告知/信息安全
/客服/告知/信息安全/通话录音
/客服/告知/信息安全/身份告知
/客服/告知/信息安全/号码来源
/客服/告知/信息安全/不允许代签
/客服/告知/信息安全/骗保
/客服/告知/信息安全/虚假信息
/客服/告知/贷款利息
/客服/告知/私人医院不赔付
/客服/询问
/客服/询问/询问工作
/客服/询问/购买过何种保险
/客服/询问/何时购买的保险
/客服/询问/不良记录
/客服/询问/疾病历史
/客服/询问/询问姓名
/客服/询问/询问身份证
/客服/询问/询问血压
/客服/询问/询问脂肪肝
/客服/确认
/客服/确认/确认地址
/客服/确认/下单确认
/客服/拒绝
/客服/拒绝/高血压无法购买
/客服/拒绝/脂肪肝无法购买
/客服/拒绝/一般
/客服/违禁语
```

## TODO

- 数字归一化
- 特长句如何解决
- 在设计时需要考虑异常处理（系统可用性）