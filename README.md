# 校园二手书交易平台（中期检查版）

> **本仓库为课程设计中期检查交付版本。** 按任务书工作计划：第 1 周完成需求分析、数据库设计、前后端框架搭建，以及用户与权限、图书信息管理等核心模块；第 2 周完成购物车下单、订单发货收货等**交易闭环**的开发与联调。因此本版本中交易闭环相关接口（结算下单、直接下单、发货、收货、退款）暂以"功能开发中"占位返回提示，将在第二阶段联调完成。

本项目是基于 Spring Boot 的校园二手书交易平台，包含前台用户端、后台管理端和 MySQL 数据库脚本。系统围绕校园二手书流转场景，覆盖图书浏览、发布、留言、求购、购物车、订单、用户管理和后台数据维护等业务。

## 技术栈

- 后端：Spring Boot、MyBatis-Plus、MySQL
- 前台：HTML、CSS、JavaScript
- 后台管理端：Vue、Element UI
- 构建工具：Maven

## 中期完成情况

### 已完成（第 1 周）

- 需求分析：游客 / 注册用户 / 管理员三类角色与核心业务流程拆分
- 数据库设计：13 张业务表，含主键、外键、非空、唯一等完整性约束（见 `db.sql`）
- 前后端分层框架搭建：Controller / Service / DAO / Entity 分层，前台 + 后台 Vue 管理端
- 用户与权限模块：登录、注册、Token 鉴权拦截、个人信息维护
- 图书信息管理模块：图书分页查询、详情、发布、编辑、逻辑删除、批量导入
- 配套模块：图书留言、图书求购、公告资讯、收货地址、数据字典与系统配置

### 开发中（第 2 周，交易闭环联调）

- 购物车结算下单（`/tushuOrder/order`）、直接下单（`/tushuOrder/add`）
- 管理员发货（`/tushuOrder/deliver`）、用户确认收货（`/tushuOrder/receiving`）、退款（`/tushuOrder/refund`）
- 上述接口当前返回"功能开发中"占位提示，下一阶段完成库存扣减、余额支付、订单状态流转与异常校验，并补充测试用例与运行截图

> 说明：购物车浏览、订单列表与详情查询等读接口已可用；待联调的是"下单 → 发货 → 收货"的写入闭环。

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
- 本地开发与交付证据说明：`docs/local-development-evidence.md`

## 目录说明

- `src/main/java`：后端控制器、服务、实体、DAO 和工具类
- `src/main/resources/mapper`：MyBatis XML 映射文件
- `src/main/resources/front`：前台页面资源
- `src/main/resources/admin`：后台管理端源码和构建结果
- `src/main/resources/static/upload`：演示用上传资源
- `db.sql`：数据库建表和演示数据脚本
