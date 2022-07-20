<p align="center">
<img src="https://pic.rmb.bdstatic.com/bjh/e2fe27dbed5b8c43bbd59374360c5763.png" width="100px">
</p>


<h1 align="center">wflow 工作流</h1>

[![star](https://gitee.com/willianfu/jw-workflow-engine/badge/star.svg?theme=dark)](https://gitee.com/willianfu/jw-workflow-engine/stargazers) [![fork](https://gitee.com/willianfu/jw-workflow-engine/badge/fork.svg?theme=dark)](https://gitee.com/willianfu/jw-workflow-engine/members) <img src="https://img.shields.io/badge/release-v0.0.1-brightgreen.svg"> <img src="https://shields.io/badge/license-APACHE2.0-blue">


## 简介

`wflow-web` 是 `wflow工作流` 项目的前端设计器，免费且开源，本设计器包含表单设计，审批流程设计。

> 区别于传统Bpmn自带流程设计器，传统设计器晦涩难懂，对于普通企业用户使用门槛偏高，没有经过专业培训根本无从下手，需要相关专业人员辅助来创建流程。而本设计器界面简单，符合普通大众的思维逻辑，易于理解和上手使用。



**感兴趣的小伙伴可以加我微信 `willianfu_`进群交流**

<p style="color: red">请务必备注： wflow </p>


  👉 在线体验地址： [戳我打开演示页面](http://47.100.202.245:83) 👈

  📃 详细文档请访问 ： [wflow文档](https://willianfu.github.io/wflow/)



## 界面一览

###  **工作区面板** 

<img src="https://images.gitee.com/uploads/images/2020/1005/140253_39e3f2d5_4928216.png" alt="输入图片说明" title="屏幕截图.png" style="zoom: 50%;" />

<img src="https://images.gitee.com/uploads/images/2020/1005/140329_89cd5aac_4928216.png" alt="输入图片说明" title="屏幕截图.png" style="zoom:50%;" />

**设计器表单回显**

![image-20220711112958351](https://pic.rmb.bdstatic.com/bjh/a8266ac95ccc577c565d6abae7b05588.png)



### 表单管理

 **工作流表单管理，支持分组和单组表单拖拽排序** 

<img src="https://images.gitee.com/uploads/images/2020/1005/140358_17fc6838_4928216.png" alt="输入图片说明" title="屏幕截图.png" style="zoom:50%;" />

<img src="https://images.gitee.com/uploads/images/2020/1005/140502_bdc2ea04_4928216.png" alt="输入图片说明" title="屏幕截图.png" style="zoom:50%;" />


---------

####  **表单基本设置** 

<img src="https://images.gitee.com/uploads/images/2020/1005/140559_5c51a89b_4928216.png" alt="输入图片说明" title="屏幕截图.png" style="zoom: 50%;" />




--------

####  **表单布局设计器**

![image-20220711111255178](https://pic.rmb.bdstatic.com/bjh/abc8f22612e35a4ecc74adf024af3025.png)


---------

 #### 流程设计器

> 任意条件层级审批流程设计， 审批节点支持多种业务类型设置，支持流程校验

![image-20220711111351476](https://pic.rmb.bdstatic.com/bjh/3300dbc60218a8376b45ed6ed46e8162.png)

**支持无限层级嵌套**

![image-20220711111911427](https://pic.rmb.bdstatic.com/bjh/02cd8936e081bdd053bfa695826817ba.png)




---------

**自定义复杂流转条件**

> 可视化流程逻辑分支条件

<img src="https://images.gitee.com/uploads/images/2021/0416/195844_51ece085_4928216.png" alt="输入图片说明" title="屏幕截图.png" style="zoom:50%;" />

---------



 **支持多种类型业务节点，支持配置校验，灵活配置，赋予无限可能** 

![输入图片说明](https://pic.rmb.bdstatic.com/bjh/5393cbdcb4d01fe35a994b87b5488dcc.png)
---------

**条件节点优先级动态拖拽，实时刷新**

<img src="https://images.gitee.com/uploads/images/2021/0416/200127_a59216a1_4928216.png" alt="输入图片说明" title="屏幕截图.png" style="zoom:50%;" />



## 开发



📃 详细文档请访问 ： [wflow文档](https://willianfu.github.io/wflow/)



### 项目结构

```
├─api 接口
├─assets
│  └─image
├─components 通用组件
│  └─common
├─router 路由
├─store vuex，设计器数据存储
├─utils
└─views 主要页面及视图
    ├─admin
    │  └─layout
    │      ├─form 表单设计
    │      └─process 流程设计
    ├─common
    │  ├─form 表单
    │  │  ├─components 表单组件
    │  │  ├─config 表单组件配置
    │  │  ├─expand 扩展组件
    │  │  └─settings 设置
    │  └─process 流程
    │      ├─config 流程节点设置
    │      └─nodes 流程节点
    └─workspace 工作区
```



### 设计器数据

> 设计器的数据都存在Vuex中，需要传递到后端时，直接取出提交到接口

```json
{
    "formId":"37289743892", //表单ID，由后端生成
    "formName":"补卡申请", //表单名称
    "logo":{ //图标
        "icon":"图标/图片base64",
        "background":"#FEFEFE" //如果是图片则不生效
    },
    //表单权限及其他属性设置
    "settings":{
        "commiter": [], //哪些人可以提交发起表单
    	"admin":[], //表单管理员，可以编辑及导出数据
        "singn": false, //全局设置审批时是否需要签字
        "notify":{
            "type": "APP", //通知类型 APP QQ WX DING EMAIL
            "title": "消息通知标题"
        }
    },
    "group":20, //所在分组
    "formItems":[],//表单设计数据
    "process":{}, //流程数据
    "remark":"备注说明"
}
```





**开源不易，需要鼓励，如果觉得这个项目有帮助到了你请我喝杯咖啡吧😋** 
<img src="https://pic.rmb.bdstatic.com/bjh/a4a29377ac6ae1f8d4ea4a513a5c5129.png" alt="支持作者" style="zoom:60%;" />
