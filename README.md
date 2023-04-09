# 云尚办公系统

## 一、项目介绍

### 1、介绍

云尚办公系统是一套自动办公系统，系统主要包含：管理端和员工端

管理端包含：权限管理、审批管理、公众号菜单管理

员工端采用微信公众号操作，包含：办公审批、微信授权登录、消息推送等功能



项目服务器端架构：SpringBoot + MyBatisPlus + SpringSecurity + Redis + Activiti+ MySQL

前端架构：vue-admin-template + Node.js + Npm + Vue + ElementUI + Axios



### 2、核心技术

| 基础框架：SpringBoot                                         |
| ------------------------------------------------------------ |
| 数据缓存：Redis                                              |
| 数据库：MySQL                                                |
| 权限控制：SpringSecurity                                     |
| 工作流引擎：Activiti                                         |
| 前端技术：vue-admin-template + Node.js + Npm + Vue + ElementUI + Axios |
| 微信公众号：公众号菜单 + 微信授权登录 + 消息推送             |



### 3、项目模块

最终服务器端架构模块

guigu-oa-parent：根目录，管理子模块：

​	common：公共类父模块

​		common-util：核心工具类

​		service-util：service模块工具类

​		spring-security：spring-security业务模块

​	model：实体类模块

​	service-oa：系统服务模块



### 4、数据库

数据库从资料文件中获取，导入数据库，Activiti表后续自动导入，数据库表如下：

![67177892343](README/1671778923438.png)

## 项目总结

## 1、项目功能模块和核心业务流程

### 1.1、管理端

#### 1.1.1、系统管理：

##### （1）用户管理、角色管理、菜单管理

##### （2）表之间关系

**角色表、用户表、菜单表**

**用户和角色是多对多关系**

**角色和菜单是多对多关系**

#### 1.1.2、审批模块

##### （1）审批类型管理

##### （2）审批模板管理

##### （3）审批列表

#### 1.1.3、公众号菜单管理



### 1.2、员工端

#### 1.2.1、微信授权登录

##### （1）通过手机号和微信openid进行用户关联

#### 1.2.2、显示所有审批类型和模板

#### 1.2.3、发起申请

#### 1.2.4、消息推送

#### 1.2.5、待处理和已处理

#### 1.2.6、查询审批详情和审批操作



## 2、项目技术

| 基础框架：SpringBoot                                         |
| ------------------------------------------------------------ |
| 数据缓存：Redis                                              |
| 数据库：MyBatisPlus + MySQL                                  |
| 权限控制：SpringSecurity                                     |
| 工作流引擎：Activiti7                                        |
| 前端技术：vue-admin-template + Node.js + Npm + Vue + ElementUI + Axios |
| 微信公众号：公众号菜单 + 微信授权登录 + 消息推送             |



## 3、项目问题和解决方式

### 3.1、跨域问题

**访问协议**： http   https

**端口号**：8800  9528

**多种解决方式：**

（1）在controller类上面添加注解

（2）在前端进行配置



### 3.2、mapper扫描问题

```java
//第一种方式 ：创建配置类，使用@MapperScan注解
@Configuration
@MapperScan(basePackages = {"com.XZY_SUNSHINE.auth.mapper","com.XZY_SUNSHIN.process.mapper","com.XZY_SUNSHIN.wechat.mapper"})
public class MybatisPlusConfig {

}

//第二种方式：在mapper的接口上面添加注解 @Mapper
@Mapper
public interface SysMenuMapper extends BaseMapper<SysMenu> {
    
}
```



### 3.3、xml文件加载问题

**Maven默认情况下，在src - main -java目录下面，只会加载java类型文件，其他类型文件不会加载的**

**第一种解决方式：把xml文件放到resources目录下**

**第二种解决方式：在pom.xml和项目配置文件进行配置**



### 3.4、流程定义部署zip文件

**zip文件规范（要求）**

**（1）zip文件名称和流程key保持一致**  

例如：<process id="qingjia" isExecutable="true"> 文件名称 qingjia.zip

**（2）在zip文件打包xml文件，xml文件命名 .bpmn20.xml**

例如：jiaban.bpmn20.xml
