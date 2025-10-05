# myopen-projects

具有技术典型性的开源示例项目集合

## 项目简介

myopen-projects 是一个包含多个 Java Web 示例项目的代码仓库，主要用于展示不同技术框架的整合应用。项目包含两个主要的示例应用：sitemesh-easyui-demo 和 authority-demo。

## 技术栈

- **Java**: 1.6+
- **构建工具**: Maven
- **Web框架**: Spring MVC 3.1.0
- **持久层**: MyBatis 3.0.6
- **前端框架**: jQuery EasyUI
- **模板引擎**: SiteMesh, JSP
- **安全框架**: Apache Shiro 1.1.0
- **数据库**: MySQL / Oracle (支持多数据库)
- **连接池**: BoneCP, C3P0, Proxool, DBCP
- **日志**: SLF4J + Logback
- **其他**: Jackson (JSON处理), Kaptcha (验证码)

## 子项目说明

### 1. sitemesh-easyui-demo

SiteMesh 与 jQuery EasyUI 的结合应用示例项目。

**功能特性**:
- SiteMesh 页面装饰器模式应用
- jQuery EasyUI 前端组件集成
- 书籍管理的 CRUD 操作示例
- DataGrid 数据表格展示
- 后台管理界面示例

**技术要点**:
- 使用 SiteMeshFilter 进行页面布局统一
- Servlet 处理业务逻辑
- EasyUI 组件的使用示例

**截图**:
![后台管理](https://raw.github.com/luowei/myopen-projects/master/sitemesh-easyui-demo/doc/img/background.png)

### 2. authority-demo

用户、角色、权限管理的后台框架项目，展示了企业级权限管理系统的基本架构。

**功能特性**:
- 用户管理（CRUD）
- 角色管理（CRUD）
- 权限（模块）管理
- 用户-角色关联
- 角色-权限关联
- 字段级权限控制
- 登录验证码
- 文件上传
- 动态菜单加载

**技术架构**:
- **表现层**: Spring MVC + Jackson (JSON)
- **业务层**: Spring Service
- **持久层**: MyBatis + 多数据库方言支持
- **安全**: 登录拦截器
- **分页**: MyBatis 拦截器实现的物理分页

**核心模块**:
- `com.rootls.authority.web.controller`: 控制器层
  - LoginController: 登录控制
  - UserController: 用户管理
  - RoleController: 角色管理
  - ModuleController: 权限模块管理
  - FieldController: 字段管理
- `com.rootls.authority.service`: 业务逻辑层
- `com.rootls.authority.dao`: 数据访问层 (MyBatis Mapper)
- `com.rootls.authority.pojo`: 实体类和工具类

**截图**:
![管理后台](https://raw.github.com/luowei/myopen-projects/master/authority-demo/doc/img/background.png)

## 项目结构

```
myopen-projects/
├── pom.xml                    # Maven 父项目配置
├── README.md                  # 项目说明文档
├── sitemesh-easyui-demo/     # SiteMesh + EasyUI 示例
│   ├── src/                   # 源代码
│   ├── WebRoot/              # Web 根目录
│   │   ├── WEB-INF/          # Web 配置
│   │   ├── easyui/           # EasyUI 资源
│   │   ├── js/               # JavaScript 文件
│   │   └── *.jsp             # JSP 页面
│   └── doc/                  # 文档和截图
└── authority-demo/           # 权限管理示例
    ├── pom.xml               # Maven 配置
    ├── src/
    │   ├── main/
    │   │   ├── java/         # Java 源代码
    │   │   │   └── com/rootls/authority/
    │   │   │       ├── common/        # 公共工具类
    │   │   │       ├── dao/           # 数据访问层
    │   │   │       ├── pojo/          # 实体类
    │   │   │       ├── service/       # 业务逻辑层
    │   │   │       └── web/           # Web层
    │   │   └── resources/    # 配置文件
    │   │       ├── config/spring/     # Spring 配置
    │   │       └── config/ibatis/     # MyBatis 配置
    │   └── test/             # 测试代码
    └── doc/                  # 文档和截图
```

## 依赖要求

- **JDK**: 1.6 或更高版本
- **Maven**: 3.x
- **数据库**: MySQL 5+ 或 Oracle 10g+
- **应用服务器**: Tomcat 6+ 或其他 Servlet 2.5+ 容器

## 安装和运行

### 1. 环境准备

确保已安装 JDK 和 Maven，并配置好环境变量。

### 2. 数据库配置

根据项目需要配置数据库连接信息（在 Spring 配置文件中）。

### 3. 编译打包

```bash
# 进入项目根目录
cd myopen-projects

# Maven 编译打包（跳过测试）
mvn clean package -Dmaven.test.skip=true
```

### 4. 运行项目

**方式一：使用 Maven Tomcat 插件**

```bash
# 进入子项目目录
cd authority-demo

# 启动 Tomcat（默认端口 8080）
mvn tomcat:run
```

**方式二：部署到 Tomcat**

将生成的 war 包部署到 Tomcat 的 webapps 目录下，启动 Tomcat 即可。

### 5. 访问应用

- SiteMesh-EasyUI Demo: `http://localhost:8080/sitemesh-easyui-demo/`
- Authority Demo: `http://localhost:8080/authority-demo/`

## 开发说明

### authority-demo 配置要点

1. **数据库方言配置**: 支持 MySQL, Oracle, PostgreSQL, SQL Server 等多种数据库
2. **连接池配置**: 可选择 BoneCP, C3P0, Proxool, DBCP
3. **分页拦截器**: 使用 MyBatis 拦截器实现物理分页
4. **日期序列化**: 自定义 Jackson 序列化器处理日期格式

### sitemesh-easyui-demo 使用说明

1. **页面装饰**: 通过 SiteMesh 的 decorator 统一页面布局
2. **EasyUI 组件**: 使用 DataGrid, Dialog, Form 等组件
3. **数据交互**: Servlet 处理请求，返回 JSON 数据

## 主要特性

- **模块化设计**: 清晰的分层架构
- **多数据库支持**: 通过方言模式支持多种数据库
- **权限控制**: 完整的 RBAC 权限模型实现
- **前后端分离**: JSON 数据交互
- **响应式布局**: 使用 EasyUI 的响应式组件

## 技术亮点

1. **MyBatis 分页拦截器**: 实现了物理分页，支持多种数据库
2. **自定义日期序列化**: Jackson 处理多种日期格式
3. **统一异常处理**: 规范的异常返回格式
4. **Spring 配置模块化**: 分离不同关注点的配置文件
5. **SiteMesh 装饰器模式**: 优雅的页面布局方案

## 许可证

本项目仅供学习和参考使用。
