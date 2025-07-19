# sensitive-word-data

[sensitive-word-data](https://github.com/houbb/sensitive-word-data) 作为敏感词库和 [sensitive-word](https://github.com/houbb/sensitive-word) 配套使用。

[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.github.houbb/sensitive-word-data/badge.svg)](http://mvnrepository.com/artifact/com.github.houbb/sensitive-word-data)
[![Open Source Love](https://badges.frapsoft.com/os/v2/open-source.svg?v=103)](https://github.com/houbb/sensitive-word-data)
[![](https://img.shields.io/badge/license-Apache2-FF0080.svg)](https://github.com/houbb/sensitive-word-data/blob/master/LICENSE.txt)

如果有一些疑难杂症，可以加入：[技术交流群](https://mp.weixin.qq.com/s/rkSvXxiiLGjl3S-ZOZCr0Q)

## 创作目的

大家好，我是老马。

一直想实现一款简单好用敏感词工具，于是开源实现了这个工具。

欢迎 PR 改进， github 提需求，或者加入技术交流群沟通吹牛！

以前词库和算法核心库在一起，但是安卓的一些伙伴希望安全检测等原因，所以期望可以单独排除，所以将二者拆分开。

## 特性

- 6W+ 词库，且不断优化更新

- 基于 fluent-api 实现，使用优雅简洁

- [基于 DFA 算法，性能为 7W+ QPS，应用无感](https://github.com/houbb/sensitive-word-data#benchmark)

- [支持敏感词的判断、返回、脱敏等常见操作](https://github.com/houbb/sensitive-word-data#%E6%A0%B8%E5%BF%83%E6%96%B9%E6%B3%95)

- [支持常见的格式转换](https://github.com/houbb/sensitive-word-data#%E6%9B%B4%E5%A4%9A%E7%89%B9%E6%80%A7)

全角半角互换、英文大小写互换、数字常见形式的互换、中文繁简体互换、英文常见形式的互换、忽略重复词等

- [支持敏感词检测、邮箱检测、数字检测、网址检测、IPV4等](https://github.com/houbb/sensitive-word-data#%E6%9B%B4%E5%A4%9A%E6%A3%80%E6%B5%8B%E7%AD%96%E7%95%A5)

- [支持自定义替换策略](https://github.com/houbb/sensitive-word-data#%E8%87%AA%E5%AE%9A%E4%B9%89%E6%9B%BF%E6%8D%A2%E7%AD%96%E7%95%A5)

- [支持用户自定义敏感词和白名单](https://github.com/houbb/sensitive-word-data#%E9%85%8D%E7%BD%AE%E4%BD%BF%E7%94%A8)

- [支持数据的数据动态更新（用户自定义），实时生效](https://github.com/houbb/sensitive-word-data#%E5%8A%A8%E6%80%81%E5%8A%A0%E8%BD%BD%E7%94%A8%E6%88%B7%E8%87%AA%E5%AE%9A%E4%B9%89)

- [支持敏感词的标签接口+内置分类实现](https://github.com/houbb/sensitive-word-data#%E6%95%8F%E6%84%9F%E8%AF%8D%E6%A0%87%E7%AD%BE)

- [支持跳过一些特殊字符，让匹配更灵活](https://github.com/houbb/sensitive-word-data#%E5%BF%BD%E7%95%A5%E5%AD%97%E7%AC%A6)

- [支持黑白名单单个的新增/修改，无需全量初始化](https://github.com/houbb/sensitive-word-data?tab=readme-ov-file#%E9%92%88%E5%AF%B9%E5%8D%95%E4%B8%AA%E8%AF%8D%E7%9A%84%E6%96%B0%E5%A2%9E%E5%88%A0%E9%99%A4%E6%97%A0%E9%9C%80%E5%85%A8%E9%87%8F%E5%88%9D%E5%A7%8B%E5%8C%96)

- [支持词匹配模式的两种模式](https://github.com/houbb/sensitive-word-data?tab=readme-ov-file#wordfailfast-%E6%95%8F%E6%84%9F%E8%AF%8D%E5%8C%B9%E9%85%8D%E5%BF%AB%E9%80%9F%E5%A4%B1%E8%B4%A5%E6%A8%A1%E5%BC%8F)

# 快速开始

## 准备

- JDK1.8+

- Maven 3.x+

## Maven 引入

```xml
<dependency>
    <groupId>com.github.houbb</groupId>
    <artifactId>sensitive-word-data</artifactId>
    <version>1.0.0</version>
</dependency>
```

## 项目推荐

下面是一些日志、加解密、脱敏安全相关的库推荐：

| 项目                                                                    | 介绍                    |
|:----------------------------------------------------------------------|:----------------------|
| [sensitive-word](https://github.com/houbb/sensitive-word)             | 高性能敏感词核心库             |
| [sensitive-word-data](https://github.com/houbb/sensitive-word-data)             | 高性能敏感词核心库数据           |
| [sensitive-word-data-admin](https://github.com/houbb/sensitive-word-data-admin) | 敏感词控台，前后端分离           |
| [sensitive](https://github.com/houbb/sensitive)                       | 高性能日志脱敏组件             |
| [auto-log](https://github.com/houbb/auto-log)                         | 统一日志切面组件，支持全链路traceId |
| [encryption-local](https://github.com/houbb/encryption-local)         | 离线加密机组件               |
| [encryption](https://github.com/houbb/encryption)         | 加密机标准API+本地客户端        |
| [encryption-server](https://github.com/houbb/encryption-server)        | 加密机服务                 |

### 敏感词控台

有时候敏感词有一个控台，配置起来会更加灵活方便。

> [java 如何实现开箱即用的敏感词控台服务？](https://mp.weixin.qq.com/s/rQo75cfMU_OEbTJa0JGMGg)

### 敏感词标签文件

梳理了大量的敏感词标签文件，可以让我们的敏感词更加方便。

这两个资料阅读可在下方文章获取：

> [v0.11.0-敏感词新特性及对应标签文件](https://mp.weixin.qq.com/s/m40ZnR6YF6WgPrArUSZ_0g)

目前 v0.24.0 已内置实现单词标签，需要的建议升级到最新版本。

# 拓展阅读

[sensitive-word-data-admin 敏感词控台 v1.2.0 版本开源](https://mp.weixin.qq.com/s/7wSy0PuJLTudEo9gTY5s5w)

[sensitive-word-data-admin v1.3.0 发布 如何支持分布式部署？](https://mp.weixin.qq.com/s/4wia8SlQQbLV5_OHplaWvg)

[01-开源敏感词工具入门使用](https://houbb.github.io/2020/01/07/sensitive-word-data-00-overview)

[02-如何实现一个敏感词工具？违禁词实现思路梳理](https://houbb.github.io/2020/01/07/sensitive-word-data-01-intro)

[03-敏感词之 StopWord 停止词优化与特殊符号](https://houbb.github.io/2020/01/07/sensitive-word-data-02-stopword)

[04-敏感词之字典瘦身](https://houbb.github.io/2020/01/07/sensitive-word-data-03-slim)

[05-敏感词之 DFA 算法(Trie Tree 算法)详解](https://houbb.github.io/2020/01/07/sensitive-word-data-04-dfa)

[06-敏感词(脏词) 如何忽略无意义的字符？达到更好的过滤效果](https://houbb.github.io/2020/01/07/sensitive-word-data-05-ignore-char)

[v0.10.0-脏词分类标签初步支持](https://juejin.cn/post/7308782855941292058?searchId=20231209140414C082B3CCF1E7B2316EF9)

[v0.11.0-敏感词新特性：忽略无意义的字符，词标签字典](https://mp.weixin.qq.com/s/m40ZnR6YF6WgPrArUSZ_0g)

[v0.12.0-敏感词/脏词词标签能力进一步增强](https://mp.weixin.qq.com/s/-wa-if7uAy2jWsZC13C0cQ)

[v0.13.0-敏感词特性版本发布 支持英文单词全词匹配](https://mp.weixin.qq.com/s/DXv5OUyOs0y2dAq8nFWJ9A)

[v0.16.1-敏感词新特性之字典内存资源释放](https://mp.weixin.qq.com/s/zbeJR-OkWjxashtjiopnMA)

[v0.19.0-敏感词新特性之敏感词单个编辑，不必重复初始化](https://houbb.github.io/2020/01/07/sensitive-word-data-10-v0.19.0-deny-word-edit)

[v0.20.0 敏感词新特性之数字全部匹配，而不是部分匹配](https://houbb.github.io/2020/01/07/sensitive-word-data-11-v0.20.0-num-match)

[v0.21.0 敏感词新特性之白名单支持单个编辑，修正白名单包含黑名单时的问题](https://houbb.github.io/2020/01/07/sensitive-word-data-12-v0.21.0-allow-word-edit)

[v0.23.0 敏感词结果条件拓展，内置支持链式+单词标签](https://houbb.github.io/2020/01/07/sensitive-word-data-13-v0.23.0-result-condition-enhance)

[v0.24.0 新特性支持标签分类，内置实现多种策略](https://houbb.github.io/2020/01/07/sensitive-word-data-13-v0.24.0-word-tag-impl)

[v0.25.0 新特性之 wordCheck 策略支持用户自定义](https://houbb.github.io/2020/01/07/sensitive-word-data-14-v0.25.0-url-define)

[v0.25.1 新特性之返回匹配词，修正 tags 标签](https://houbb.github.io/2020/01/07/sensitive-word-data-14-v0.25.1-tags-match)

![wechat](https://img-blog.csdnimg.cn/63926529df364f09bcb203a8a9016854.png)

# NLP 开源矩阵

[pinyin 汉字转拼音](https://github.com/houbb/pinyin)

[pinyin2hanzi 拼音转汉字](https://github.com/houbb/pinyin2hanzi)

[segment 高性能中文分词](https://github.com/houbb/segment)

[opencc4j 中文繁简体转换](https://github.com/houbb/opencc4j)

[nlp-hanzi-similar 汉字相似度](https://github.com/houbb/nlp-hanzi-similar)

[word-checker 拼写检测](https://github.com/houbb/word-checker)

[sensitive-word-data 敏感词](https://github.com/houbb/sensitive-word-data)

# 支持开源

开源不易，如果本项目对你有帮助，你可以请老马喝一杯奶茶。

<img src="https://github.com/houbb/sensitive-word/raw/master/lmxxf_reword.png?raw=true" style="width: 300px; height: 200px;"/>
