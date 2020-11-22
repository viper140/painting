# PlantUML

## 1 简介

开源的绘图工具

- 官网：<https://plantuml.com/>
- 还有个中文官网：<https://plantuml.com/zh/>

## 2 优势

### 2.1 语法简单

简单几句语法勾勒，就能渲染出图片。

### 2.2 支持的软件多

语雀，hackmd

## 3 如何调试

- 在线调试：<http://www.plantuml.com/>
- 本地调试：IDEA 插件 PlantUML integration

## 4 如何部署（渲染图片）

### 4.1 plantUML 代理

代理格式：http://www.plantuml.com/plantuml/proxy?cache=no&src=xxx

- 源地址：https://github.com/viper140/painting/xx.md
- 二进制地址：https://raw.githubusercontent.com/viper140/painting/xx.md（一定要在 github 上点一下 raw 按钮来生成，否则是没有的）
- 代理后的地址：http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/viper140/painting/xx.md

### 4.2 本地部署

- war 包：https://sourceforge.net/projects/plantuml/files/plantuml.war/download
- 本地启动：http://localost:8080/plantuml
