# lib-stringfog-en-de 项目上下文

## 项目概述

这是一个 Android 字符串加密/解密库项目，基于 StringFog 框架开发。该项目提供预编译的 AAR（Android Archive）库，用于 Android 应用的字符串加密保护。

**项目信息：**
- **Group ID**: `github.super200893154`
- **Artifact ID**: `stringfog-en-de`
- **当前版本**: `1.0.8`
- **包类型**: `aar`
- **远程仓库**: https://github.com/super200893154/lib-stringfog-en-de

**主要技术栈：**
- Kotlin 2.0.10
- AndroidX Core KTX 1.13.1
- AndroidX AppCompat 1.7.0
- Material Components 1.12.0
- StringFog Interface 5.0.0

## 项目结构

本项目是一个精简的发布目录，包含以下关键文件：

```
lib-stringfog-en-de/
├── jitpack.yml              # JitPack 构建配置
├── pom-default.xml          # Maven POM 配置文件
├── stringfog-en-de-1.0.8.aar # 预编译的 Android 库文件
└── AGENTS.md               # 本文件（项目上下文文档）
```

**注意**：此目录不包含源代码，仅包含用于通过 JitPack 发布预编译库的必要文件。

## 构建和发布

### JitPack 自动发布

项目使用 JitPack 进行自动构建和发布。当推送到 GitHub 仓库时，JitPack 会根据 `jitpack.yml` 配置自动构建。

**JitPack 配置（jitpack.yml）：**
```yaml
jdk:
  - openjdk17
install:
  - FILE="-Dfile=stringfog-en-de-1.0.8.aar"
  - mvn install:install-file $FILE -DgroupId=github.super200893154 -DartifactId=stringfog-en-de -Dversion=1.0.8 -Dpackaging=aar -DpomFile=pom-default.xml
```

**构建要求：**
- OpenJDK 17
- Maven

### 本地测试安装

如果需要在本地测试库的安装，可以使用以下 Maven 命令：

```bash
mvn install:install-file -Dfile=stringfog-en-de-1.0.8.aar -DgroupId=github.super200893154 -DartifactId=stringfog-en-de -Dversion=1.0.8 -Dpackaging=aar -DpomFile=pom-default.xml
```

## 使用方式

### 在 Android 项目中引入

在 Android 项目的 `build.gradle` 或 `build.gradle.kts` 中添加依赖：

**Gradle (Groovy):**
```groovy
dependencies {
    implementation 'github.super200893154:stringfog-en-de:1.0.8'
}
```

**Gradle (Kotlin DSL):**
```kotlin
dependencies {
    implementation("github.super200893154:stringfog-en-de:1.0.8")
}
```

**注意**：需要添加 JitPack 仓库：
```groovy
repositories {
    maven { url 'https://jitpack.io' }
}
```

## 开发约定

### 版本管理

- 版本号遵循语义化版本规范（Major.Minor.Patch）
- 当前版本：1.0.8
- 更新版本时，需要同步更新：
  - `jitpack.yml` 中的版本号
  - `pom-default.xml` 中的 `<version>` 标签
  - AAR 文件名中的版本号

### 发布流程

1. 更新版本号（在所有相关文件中）
2. 生成新的 AAR 文件
3. 提交并推送到 GitHub
4. JitPack 自动构建并发布

### StringFog 集成

本库基于 StringFog 框架（版本 5.0.0），使用 `com.github.megatronking.stringfog:interface` 作为接口依赖。StringFog 是一个用于 Android 字符串加密的框架，通过编译时字节码插桩实现字符串加密。

## 依赖说明

**核心依赖：**
- `kotlin-stdlib` (2.0.10): Kotlin 标准库
- `androidx.core:core-ktx` (1.13.1): AndroidX 核心 Kotlin 扩展
- `androidx.appcompat:appcompat` (1.7.0): AndroidX AppCompat 库
- `com.google.android.material:material` (1.12.0): Material Design 组件
- `com.github.megatronking.stringfog:interface` (5.0.0): StringFog 接口定义

**依赖范围：**
- `compile`: 编译时依赖
- `runtime`: 运行时依赖

## 项目状态

- **项目类型**: Android 库发布目录
- **源代码**: 不在此目录中（可能在其他分支或单独的源代码仓库）
- **构建方式**: 预编译 AAR，通过 JitPack 发布
- **维护状态**: 活跃（最新版本 1.0.8）

## 注意事项

1. 本目录不包含源代码，仅用于发布预编译的 AAR 库
2. 如需修改库功能，需要在源代码仓库中进行修改，然后重新编译 AAR
3. 更新版本时务必同步更新所有相关配置文件
4. 使用 OpenJDK 17 确保 JitPack 构建兼容性