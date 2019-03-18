# DataCenter

Todo:
1. CDH, hbase,zk 部署和配置。代码发布。
2. presto , redis集群，cachecloud 部署。
3. Hive 开发的流程。 azkaban安装部署。
4. Doubble 服务安装部署。 
5. MySQL的在模块里的配置。


计划：
1. 3月底代码整体提交，做一次部署测试发现问题。 3月底验证可部署性。
2. 4月份提供可以使用的一个版本。              4月底验证可使用性。
3. 5，6月份主要是做一些二次开发，使得像一个真正的产品。   6月底验证产品完整性。

### 项目说明
项目整体架构  
数据服务中心管理了所有业务服务的数据访问，业务层对外提供的是dubbo接口或Rest风格接口，路由网关负责对外接口的管理，是的web应用或其他三方应用的访问具有可控性

![avatar](架构图.png)
#### big-cbr(报表系统)
数据报表系统，报表元数据存储在数据库，可以通过前端进行动态配置报表的样式和数据查询功能
#### big-dbms(数据库管理系统)
可以理解它为’一个超级大的数据访问层’，在整个项目中承担了所有数据访问的工作，
#### big-dbms-server（数据查询服务系统）
提供数据的查询功能，可集成数据源有：mysql，hive，presto
#### big-gateway（服务网关）
所有对外服务接口api（dubbo，http）管理中心，可配置api的超时，权限，重试次数
#### big-msg（消息推送 提醒）
公司内部模块（考虑删除）
#### big-whtc（数仓配置服务）
提供数仓的基本任务配置功能，提供datax的配置
#### bigdata-interface（模块的对外服务接口）
所有模块间的调用接口信息
#### bigdata-parent（父工程）
包含了所有基础框架 [详情](bigdata-parent/README.md)
### 部署顺序
#### 1、部署安装前置依赖服务
#### 2、部署bigdata-parent
因为此项目是其他项目的依赖，所以需要最先部署
```bash
cd path/to/bigdata-parent
mvn clean install
```
#### 3、部署数据服务中心项目


