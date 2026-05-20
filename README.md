# StringFog Android 字符串加密库

基于 StringFog 框架的 Android 字符串加密/解密库，用于保护 Android 应用中的字符串常量，防止被轻易逆向分析。

## 项目信息

| 属性 | 值 |
|------|-----|
| Group ID | `github.super200893154` |
| Artifact ID | `stringfog-en-de` |
| 当前版本 | `1.0.9` |
| 包类型 | AAR (Android Archive) |
| 远程仓库 | https://github.com/super200893154/lib-stringfog-en-de |

## 项目结构

```
lib-stringfog-en-de/
├── jitpack.yml              # JitPack 构建配置
├── pom-default.xml          # Maven POM 配置文件
├── stringfog-en-de-1.0.9.aar # 预编译的 Android 库文件
└── README.md               # 项目文档
```

## 技术栈

- **Kotlin**: 2.2.10
- **AndroidX Core KTX**: 1.18.0
- **AndroidX AppCompat**: 1.7.1
- **Material Components**: 1.14.0
- **StringFog Interface**: 5.3.1

## 使用方式

### 添加 JitPack 仓库

在项目的 `build.gradle` (Groovy) 或 `build.gradle.kts` (Kotlin DSL) 中添加 JitPack 仓库：

**Gradle Groovy:**
```groovy
repositories {
    maven { url 'https://jitpack.io' }
}
```

**Gradle Kotlin DSL:**
```kotlin
repositories {
    maven("https://jitpack.io")
}
```

### 添加依赖

**Gradle Groovy:**
```groovy
dependencies {
    implementation 'github.super200893154:stringfog-en-de:1.0.9'
}
```

**Gradle Kotlin DSL:**
```kotlin
dependencies {
    implementation("github.super200893154:stringfog-en-de:1.0.9")
}
```

> **注意**：更新版本时，请将 `1.0.9` 替换为所需的版本号。

## 构建和发布

### JitPack 自动发布

本项目使用 JitPack 进行自动构建和发布。当代码推送到 GitHub 仓库后，JitPack 会根据 `jitpack.yml` 配置自动构建。

**JitPack 配置（jitpack.yml）：**
```yaml
jdk:
  - openjdk17
install:
  - FILE="-Dfile=stringfog-en-de-1.0.9.aar"
  - mvn install:install-file $FILE -DgroupId=github.super200893154 -DartifactId=stringfog-en-de -Dversion=1.0.9 -Dpackaging=aar -DpomFile=pom-default.xml
```

### 本地安装

如需在本地测试库安装，可使用以下 Maven 命令：

```bash
mvn install:install-file -Dfile=stringfog-en-de-1.0.9.aar -DgroupId=github.super200893154 -DartifactId=stringfog-en-de -Dversion=1.0.9 -Dpackaging=aar -DpomFile=pom-default.xml
```

### 发布流程

1. 更新版本号（在所有相关文件中同步修改）
2. 生成新的 AAR 文件
3. 提交并推送到 GitHub
4. JitPack 自动构建并发布

## 开发约定

### 版本命名规范

版本号遵循语义化版本规范（Major.Minor.Patch）：

- **Major**: 主版本号，不兼容的重大更新
- **Minor**: 次版本号，向后兼容的功能更新
- **Patch**: 补丁版本号，向后兼容的问题修复

### 版本更新同步

更新版本时，需同步修改以下位置：

| 文件 | 修改内容 |
|------|----------|
| `jitpack.yml` | `install` 命令中的 `-Dversion` 参数和 AAR 文件名 |
| `pom-default.xml` | `<version>` 标签 |
| AAR 文件名 | `stringfog-en-de-{version}.aar` |

## 依赖说明

| 依赖 | 版本 | 范围 | 说明 |
|------|------|------|------|
| kotlin-stdlib | 2.2.10 | compile | Kotlin 标准库 |
| androidx.core:core-ktx | 1.18.0 | runtime | AndroidX 核心 Kotlin 扩展 |
| androidx.appcompat:appcompat | 1.7.1 | runtime | AndroidX AppCompat 库 |
| com.google.android.material:material | 1.14.0 | runtime | Material Design 组件 |
| com.github.super200893154.StringFog:interface | 5.3.1 | runtime | StringFog 接口定义 |
