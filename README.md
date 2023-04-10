# CRM-demo

## 项目技术框架选型与分析：
##### 视图层(view)：
展示数据，跟用户交互。
```
html,css,js,jquery,bootstrap
```
##### 控制层(Controller | Handler | MiddleWare)：
控制业务处理流程
```
  --接收请求,接收参数,封装参数;
  --根据不同的请求调用业务层Service处理业务;
  --根据处理结果，返回响应信息
    (servlet)SpringMVC
```
##### 业务层(Service)：
处理业务逻辑(处理业务的步骤以及操作的原子性)
```
JAVASE(工作流:处理复杂业务activity|JBPM)
-- 进行系统操作，service
-- 记录操作日志，log
```
##### 持久层(Dao/Mapper)：
操作SQL数据库,和可能的NOSQL
```
(jdbc)MyBatis(hibernate)
```
##### 整合层：
维护类资源,维护数据库资源

全局的model，作为上下文context，运用于service等各个层级
```
Spring(IOC,AOP)
(ejb,corba)
```

## 项目结构

```
├─java
│  └─com
│      └─bjpowernode
│          └─crm
│              ├─commons
│              │  ├─contants
│              │  ├─domain
│              │  └─utils
│              ├─settings
│              │  ├─domain
│              │  ├─mapper
│              │  ├─service
│              │  │  └─impl
│              │  └─web
│              │      ├─controller
│              │      └─interceptor
│              ├─web
│              │  └─controller
│              └─workbench
│                  ├─domain
│                  ├─mapper
│                  ├─service
│                  │  └─impl
│                  └─web
│                      └─controller
├─resources
└─webapp
    ├─image
    ├─jquery
    │  ├─bootstrap-datetimepicker-master
    │  │  ├─css
    │  │  ├─js
    │  │  └─locale
    │  ├─bootstrap-datetimepicker-master_bak
    │  │  ├─css
    │  │  ├─js
    │  │  └─locale
    │  ├─bootstrap_3.3.0
    │  │  ├─css
    │  │  ├─fonts
    │  │  └─js
    │  ├─bootstrap_3.3.0_bak
    │  │  ├─css
    │  │  ├─fonts
    │  │  └─js
    │  ├─bs_pagination-master
    │  │  ├─css
    │  │  ├─js
    │  │  └─localization
    │  ├─bs_typeahead
    │  ├─echarts
    │  └─zTree_v3-master
    │      ├─css
    │      │  └─zTreeStyle
    │      │      └─img
    │      │          └─diy
    │      └─js
    └─WEB-INF
        └─pages
            ├─settings
            │  ├─dictionary
            │  │  ├─type
            │  │  └─value
            │  └─qx
            │      ├─permission
            │      ├─role
            │      └─user
            └─workbench
                ├─activity
                ├─chart
                │  ├─activity
                │  ├─clue
                │  ├─customerAndContacts
                │  └─transaction
                ├─clue
                ├─contacts
                ├─customer
                ├─main
                └─transaction
```

