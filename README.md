# 校园二手书交易平台

本项目是基于 Spring Boot 的校园二手书交易平台，包含前台用户端、后台管理端和 MySQL 数据库脚本。系统围绕校园二手书流转场景，提供图书浏览、发布、购物车、订单、留言、求购、用户管理和后台数据维护等功能。

## 技术栈

- 后端：Spring Boot、MyBatis-Plus、MySQL
- 前台：HTML、CSS、JavaScript
- 后台管理端：Vue、Element UI
- 构建工具：Maven

## 主要功能

- 用户注册、登录和个人信息维护
- 二手书信息浏览、查询、详情展示
- 图书发布、留言、求购信息管理
- 购物车和订单流程
- 收货地址管理
- 后台用户、图书、订单、留言、资讯和基础字典管理

## 本地运行

1. 创建 MySQL 数据库并导入脚本：

   ```sql
   CREATE DATABASE ershoushujiaoyipingtai DEFAULT CHARACTER SET utf8mb4;
   ```

   然后导入项目根目录下的 `db.sql`。

2. 检查数据库连接配置：

   ```yaml
   spring:
     datasource:
       url: ${DB_URL:jdbc:mysql://127.0.0.1:3306/ershoushujiaoyipingtai?...}
       username: ${DB_USERNAME:root}
       password: ${DB_PASSWORD:123456}
   ```

   如果本机 MySQL 账号密码不同，可以通过环境变量 `DB_URL`、`DB_USERNAME`、`DB_PASSWORD` 覆盖。

3. 启动后端服务：

   ```bash
   mvn spring-boot:run
   ```

4. 浏览器访问：

   - 前台用户端：`http://localhost:8080/ershoushujiaoyipingtai/front/index.html`
   - 后台管理端：`http://localhost:8080/ershoushujiaoyipingtai/admin/dist/index.html`

## 测试账号

- 后台管理员：`admin / admin`
- 普通用户：`a1 / 123456`
- 普通用户：`a2 / 123456`
- 普通用户：`a3 / 123456`

## 展示材料

- 中期展示脚本：`docs/midterm-demo-script.html`

## 目录说明

- `src/main/java`：后端控制器、服务、实体、DAO 和工具类
- `src/main/resources/mapper`：MyBatis XML 映射文件
- `src/main/resources/front`：前台页面资源
- `src/main/resources/admin`：后台管理端源码和构建结果
- `src/main/resources/static/upload`：演示用上传资源
- `db.sql`：数据库建表和演示数据脚本
