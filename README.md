# Flower Spring Cloud Dependencies

Flower Spring Cloud 的依赖管理模块（BOM），统一管理所有子模块和第三方依赖的版本。

## 项目简介

本项目是一个 Maven BOM（Bill of Materials）项目，用于集中管理 Flower Spring Cloud 框架及其相关第三方依赖的版本。通过引入此 BOM，业务项目可以：

- 统一管理依赖版本，避免版本冲突
- 简化依赖声明，无需指定版本号
- 确保各组件之间的兼容性

## 技术栈版本

| 技术 | 版本 |
|------|------|
| Spring Boot | 3.5.12 |
| Spring Cloud | 2025.0.1 |
| Spring Cloud Alibaba | 2025.0.0.0 |
| MyBatis Plus | 3.5.15 |
| MySQL Connector | 9.3.0 |
| Seata | 2.5.0 |
| RocketMQ | 5.3.2 |
| Knife4j | 4.5.0 |
| SpringDoc | 2.3.0 |
| JWT | 0.12.6 |
| Fastjson2 | 2.0.49 |
| Hutool | 5.8.40 |
| MinIO | 8.6.0 |
| Spring State Machine | 4.0.0 |
| Transmittable ThreadLocal | 2.8.1 |
| Apache Commons Lang3 | 3.20.0 |
| WeChat Pay | 0.2.17 |

## 快速开始

### 1. 引入 BOM

在业务项目的 `pom.xml` 中添加：

```xml
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>top.flowerstardream.base</groupId>
            <artifactId>flower-spring-cloud-dependencies</artifactId>
            <version>release-1.0.0</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```

### 2. 添加依赖（无需版本号）

引入 BOM 后，可以直接添加 Flower Spring Cloud 相关依赖，无需指定版本：

```xml
<dependencies>
    <!-- Flower Spring Cloud Starter -->
    <dependency>
        <groupId>top.flowerstardream.base</groupId>
        <artifactId>flower-spring-cloud-starter</artifactId>
    </dependency>

    <!-- 或单独引入 Core 模块 -->
    <dependency>
        <groupId>top.flowerstardream.base</groupId>
        <artifactId>flower-core</artifactId>
    </dependency>
</dependencies>
```

## 管理的依赖清单

### Spring 生态

| 依赖 | Artifact ID |
|------|-------------|
| Spring Boot | `spring-boot-dependencies` |
| Spring Cloud | `spring-cloud-dependencies` |
| Spring Cloud Alibaba | `spring-cloud-alibaba-dependencies` |
| Spring State Machine | `spring-statemachine-starter` |

### 数据访问

| 依赖 | Artifact ID |
|------|-------------|
| MyBatis Plus | `mybatis-plus-bom` |
| MySQL Connector | `mysql-connector-j` |

### 消息队列

| 依赖 | Artifact ID |
|------|-------------|
| RocketMQ Client | `rocketmq-client` |
| RocketMQ ACL | `rocketmq-acl` |

### 分布式事务

| 依赖 | Artifact ID |
|------|-------------|
| Seata | `seata-spring-boot-starter` |

### API 文档

| 依赖 | Artifact ID |
|------|-------------|
| Knife4j | `knife4j-openapi3-jakarta-spring-boot-starter` |
| Knife4j UI | `knife4j-openapi3-ui` |
| Knife4j Gateway | `knife4j-gateway-spring-boot-starter` |
| SpringDoc WebFlux | `springdoc-openapi-starter-webflux-ui` |

### 安全认证

| 依赖 | Artifact ID |
|------|-------------|
| JWT API | `jjwt-api` |
| JWT Impl | `jjwt-impl` |
| JWT Jackson | `jjwt-jackson` |
| Nimbus JOSE JWT | `nimbus-jose-jwt` |

### 工具类库

| 依赖 | Artifact ID |
|------|-------------|
| Hutool | `hutool-all` |
| Fastjson2 | `fastjson2` |
| Apache Commons Lang3 | `commons-lang3` |
| Transmittable ThreadLocal | `transmittable-thread-local` |
| ASCII Table | `asciitable` |

### 文件存储

| 依赖 | Artifact ID |
|------|-------------|
| MinIO | `minio` |

### 支付

| 依赖 | Artifact ID |
|------|-------------|
| WeChat Pay | `wechatpay-java` |

### 响应式 Feign

| 依赖 | Artifact ID |
|------|-------------|
| Feign Reactor BOM | `feign-reactor-bom` |

### 安全补丁

以下依赖版本被显式指定以修复已知安全漏洞：

| 依赖 | 版本 | 说明 |
|------|------|------|
| protobuf-java | 4.28.2 | 协议缓冲区 |
| commons-beanutils | 1.11.0 | Bean 工具 |
| grpc-netty-shaded | 1.75.0 | gRPC |
| lz4-java | 1.8.1 | LZ4 压缩 |
| spring-cloud-gateway-server | 4.3.2 | 网关服务 |
| commons-fileupload | 1.6.0 | 文件上传 |
| bcprov-jdk18on | 1.78.1 | Bouncy Castle |
| guava | 32.0.1-android | Google 工具库 |

## 版本升级指南

### 升级 BOM 版本

修改 `dependencyManagement` 中的版本号：

```xml
<dependency>
    <groupId>top.flowerstardream.base</groupId>
    <artifactId>flower-spring-cloud-dependencies</artifactId>
    <version>release-1.1.0</version>  <!-- 升级到新版本 -->
    <type>pom</type>
    <scope>import</scope>
</dependency>
```

### 覆盖特定依赖版本

如需覆盖 BOM 中的某个依赖版本，可以在 `dependencyManagement` 中显式声明：

```xml
<dependencyManagement>
    <dependencies>
        <!-- 先引入 BOM -->
        <dependency>
            <groupId>top.flowerstardream.base</groupId>
            <artifactId>flower-spring-cloud-dependencies</artifactId>
            <version>release-1.0.0</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>

        <!-- 覆盖特定版本 -->
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-bom</artifactId>
            <version>3.5.16</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```

## 相关项目

| 项目 | 说明 |
|------|------|
| [flower-spring-cloud](https://github.com/your-org/flower-spring-cloud) | 基础框架主体项目 |
| flower-spring-cloud-starter | 起步依赖模块 |
| flower-core | 核心功能模块 |

## 许可证

[Apache License 2.0](LICENSE)
