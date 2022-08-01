# MyBatis笔记

官方文档：https://mybatis.org/mybatis-3/zh/index.html  
GitHub地址：https://github.com/mybatis/mybatis-3

# MyBatis简介
    基于ORM的半主动轻量级持久层框架
    
# ORM（Objective Relational Mapping，对象关系映射）
    O：对象模型：实体对象
    R：关系型数据库的结构模型：数据库表
    M：映射：将实体对象与数据库表建立映射关系
    
    
# XML配置

* MyBatis 的配置文件包含了会深深影响 MyBatis 行为的设置和属性信息。 配置文档的顶层结构如下：
    
    * configuration（配置）
    * properties（属性）
    * settings（设置）
    * typeAliases（类型别名）
    * typeHandlers（类型处理器）
    * objectFactory（对象工厂）
    * plugins（插件）
    * environments（环境配置）
        * environment（环境变量）
        * transactionManager（事务管理器）
        * dataSource（数据源）
    * databaseIdProvider（数据库厂商标识）
    * mappers（映射器）

```xml

```

# XML映射文件

# MyBatis高级查询

## 1.1 ResultMap属性
    建立对象关系映射
    * resultType
        实体类的属性名与表中字段名一致，将查询结果自动封装到实体类中
    * resultMap
        实体类的属性名与表中字段名不一致，使用resultMap手动封装

## 1.2 多条件查询

## 1.3 模糊查询
    #{}和${}区别：
        #{}表示一个占位符
            * 通过#{}实现preparedStatement向占位符设置值，自动进行Java类型和jdbc类型转换，#{}可以有效防止sql注入
            * #{}可以接收简单类型值或pojo属性值
            * 如果parameterType是传输单个简单值，#{}中名称随便写
         
         ${}表示拼接字符串
            * ${}可以将parameterType传入的内容拼接在sql中不进行jdbc类型转换，会出现sql注入问题
            * ${}可以接收简单类型值或pojo属性值
            * 如果parameterType传输单个简单类型值，#{}括号中只能是value
                * TextSqlNode.java

    
## 1.4 返回主键

## 1.5 动态sql

### 1.5.1 if
### 1.5.2 set
### 1.5.3 foreach
### 1.5.4 动态sql
    提取重复的sql语句
    
    
    
# PageHelper

旧版本3.7.5配置

```xml

    <plugins>
        <plugin interceptor="com.github.pagehelper.PageHelper">
            <!--            指定方言：limit-->
            <property name="dialect" value="mysql"/>
        </plugin>
    </plugins>

```

## 数据库表的关系
    一对一
    一对多
    多对多
    * mybatis把多对多看成一对一
