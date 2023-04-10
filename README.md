# CRM-demo

CRM(Customer Relationship Management)客户关系管理是管理**企业与客户之间关系**的新型管理机制。

目标：吸引新客户、保留老客户、转变为忠诚客户。
#### 业务
```
系统管理功能：不是直接处理业务数据，为了保证业务管理的功能正常安全运行而设计的功能。
          用户登录,安全退出,登录验证等
          给超级管理员，开发和运维人员使用。

业务管理功能：处理业务数据
          市场活动：市场部，设计市场活动营销活动
          线索(潜在用户)：销售部,增加线索
          客户和联系人：销售部,有效地区分和跟踪客户和联系人.
          交易：销售部,更好地区分和统计交易的各个阶段。
          售后回访：客服部,妥善安排售后回访。主动提醒。
          统计图表：管理层,统计交易表中各个阶段数据量。
```

## 项目技术框架选型与分析：
视图层-->控制层-->业务层-->持久层-->数据库
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
    可能用SpringBoot
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
可能会用Redis为cache，可以单独一个缓存层(Cache)
```
##### 整合层()：
维护类资源,维护数据库资源

全局的model，作为上下文context，运用于service等各个层级
```
Spring(IOC,AOP)
(ejb,corba)
```
## 数据库设计
```
/*
一般不设置外键，不过字段会当做外键用；
牺牲了数据库中数据的一致性，但是却能够减少数据库的负载
*/
/*
主键自增效率低，可能出现多线程同时自增，数据库会加锁；
一般手动生成主键值，比如UUID，128位；Snowflake 雪花算法64位，正好是一个8字节的long

密码一般采用hash值，HASH现在MD5，SHA1的彩虹表比较多，可考虑SHA2；
实在需要找回的，可以采用椭圆算法计算来存
*/
/*
关于日期和时间的字段，都按照字符串处理：
     char(10)   yyyy-MM-dd
     char(19)   yyyy-MM-dd HH:mm:ss
比如MySQL和Java的日期类型是要相互转换的，会有性能问题，不如直接String
*/
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
