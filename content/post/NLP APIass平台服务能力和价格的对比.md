---
title: "NLP APIass平台服务能力和价格的对比"
date: 2024-09-20T14:30:08+00:00
# weight: 1
# aliases: ["/first"]
tags: ["NLP"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "通过调用各家提供的API进行测试，而不是自己搭建服务或者编写对应的算法"
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/BlackChainLife/personal_blog/tree/master/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

# 对比方法
1. 从东方财富网的股吧选取一条评论
2. 调用腾讯、阿里、百度的 nlp 情感分析的接口和 openai
3. 调用 LLM 模型：openai、ollama 模型
4. 通过 API 调用、调试、文档、响应速度、准确率进行分析

# 情感分析
对比文本：一千五百倍的市盈率，这种不赚钱的公司也能上天吗
## 腾讯云
**腾讯云判定结果为中性词语**
```json
{ "Response": 
     { 
         "Negative": 0.07114116102457047, 
         "Neutral": 0.928027868270874, 
         "Positive": 0.0008309169206768274, 
         "RequestId": "d1235265-78e2-4cce-9d26-1497c0fc29c7", 
         "Sentiment": "neutral" 
    } 
}
```

## 阿里云

**腾讯云判定情绪为积极情绪**

```json
{"positive_prob":0.9893,"sentiment":"正面","neutral_prob":0.0007,"negative_prob":0.0099}
```

## 百度云

**调用总是报 qps 的错误**

## openai

**采用 gpt-turbo-3.5**

```plaintext
问：一千五百倍的市盈率，这种不赚钱的公司也能上天吗。 判断文本的情感
答：这句话表达了对公司市盈率1500倍的怀疑和质疑，认为这样的公司可能无法持续盈利，因此对其未来表现持谨慎态度。所以，该文本的情感倾向可以被判断为消极或中性。
```

## ollama

**采用的是 ollama: 13B 的模型**
和 openai 回答的结果类似