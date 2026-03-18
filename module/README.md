## BUPT 国际学校 TA 招聘系统（Servlet/JSP 版）

### 技术约束符合说明
- **架构**：轻量级 Java Servlet/JSP Web 应用（无 Spring Boot）。
- **存储**：仅使用纯文本文件（`CSV` + 简历文件），无数据库。
- **依赖**：仅依赖 Servlet 容器（如 Tomcat）提供的 Servlet/JSP API。

### 核心角色与功能
- **TA**：创建/维护申请档案（基础信息）、上传简历、浏览岗位、投递申请、查询申请状态
- **MO（模块组织者）**：发布招聘岗位、查看/筛选申请者（更改申请状态：入围/拒绝）
- **管理员**：查看 TA 整体工作量（按 TA 统计：申请数、入围数）

### 账号体系
- **TA/MO**：通过注册页创建账号（注册时选择 TA 或 MO）
- **管理员**：系统预置 `admin / admin`（不可注册）
- **口令存储**：以哈希形式保存到纯文本 `users.csv`（不落明文）

### 运行方式（推荐：IntelliJ + Smart Tomcat + Tomcat 10.1）
1. 安装并配置 Tomcat 10.1（本项目使用 `jakarta.servlet.*`）。
2. IntelliJ 安装 Smart Tomcat 插件。
3. Smart Tomcat 配置建议：
   - Deployment directory：`module/webapp`
   - Context path：`/ta-recruit`
   - 端口默认 8080（冲突则改 8081）
4. 访问：`http://localhost:8080/ta-recruit/`

入口页面：
- `/home`（导航）
- `/login`（登录）
- `/register`（TA/MO 注册）

### 数据文件位置
运行后会在部署目录的 `WEB-INF/data/` 生成（仍为纯文本文件）：
- `users.csv` 用户
- `profiles.csv` TA 档案
- `jobs.csv` 岗位
- `applications.csv` 申请记录
- `resumes/` 简历文件夹（上传文件会落盘）

