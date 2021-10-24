# PlantUML

## 引言

作图可以说是程序员的必备技能，最近发现身边同学们主要还是在用 OmniGraffle、ProcessOn、draw.io 这类软件作图，用的过程中可以思考一下下面这些问题是否困扰了你：

- 二次编辑很困难：假如老文档中的设计图需要修改，找源文件得费点功夫，如果这图当时不是你画的，那更是完蛋，准备好重画吧；
- 版本管理、团队协同困难；
- 作图效率不够高：如果希望作图质量保持一定的水准，又想画得快，多数人都做不到；
- 强迫症患者经常把时间浪费在了对齐矩形、对齐间距上。

鉴于上述困扰，忍不住要向大家安利一下 PlantUML，上述问题迎刃而解。

## 1 PlantUML 简介

PlantUML 是一款开源的绘图工具，不，是**绘图语言**！所以它和 OmniGraffle 们并不是一个维度的东西。
PlantUML 优点多多：
- 上手快：学习成本超低，部分场景甚至几乎没有学习成本；
- 作图心智舒适：绝大多数情形不用关心布局、样式等问题，告别对齐矩形、调间距这种繁琐无意义的事情，我们只用把心里所想表达出来即可，心智自然；
- 超强的可维护性：永远不用担心图的源文件丢了，它自己本身就是源文件，避免了文档维护的割裂；
- 容易实现版本管理、团队协同；

具体语法没必要展开讲，官网讲得非常清楚：<https://plantuml.com>

## 2 语雀 + PlantUML

语雀对 PlantUML 有非常好的支持，两者搭配食用更佳，编辑模式插入“文本绘图”即可开始作图：
![](https://ata2-img.oss-cn-zhangjiakou.aliyuncs.com/neweditor/8b6cb6ef-6c4a-4be0-9d72-cea94195023c.png)

一直强调学习成本超低，因为语雀提供了大量现成模板，照葫芦画瓢即可：
![](https://ata2-img.oss-cn-zhangjiakou.aliyuncs.com/neweditor/07eb87d0-79cc-4581-8350-02401b88d6e6.png)

至此，你就已经能在语雀上画 UML 图了，上手真的很快，而且再也不用担心下次要修改图片找不到源文件了，换个人一样能修改，而且语雀的加持还有修改记录。

但如果你对脱离语雀如何单独使用 PlantUML 感兴趣，请接着往下看。

## 3 PlantUML 本地创作 + 远程渲染图片

如果有些站点没有支持 PlantUML 的渲染，那么需要先进行本地创作，再借助服务进行渲染，渲染后的图片链接可以随处使用，而创作的文本用 gitlab 之类的版本控制软件进行管理，便于团队成员共同维护图片的编辑。

### 3.1 本地编辑、预览

- 编辑：推荐使用 vscode 作编辑器，创建文本，进行作图，保存文件格式为`.puml`
- 实时预览：安装 vscode 插件`PlantUML`: <https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml>。开启预览的效果：
![](https://ata2-img.oss-cn-zhangjiakou.aliyuncs.com/neweditor/9465123a-b7b1-4be7-ae4a-7c85a061fea7.png)

### 3.2 渲染图片

- 源文件管理：假设你团队用 gitlab 管理团队文档，将创作好的 `.puml` 文件推送到远端，便于大家共同维护源文件
- 生成图片：
  - 方式一（借助官网服务渲染）：点击 gitlab 页面上的`RAW`按钮以生成 raw 的链接，将 raw 链接借助 PlantUML proxy 渲染服务生成最终的图片地址，这个 url 就可以自由引用了。代理服务地址的填写样式: <http://www.plantuml.com/plantuml/proxy?cache=no&src=xxx>

 ```text
  方式一（借助官网服务渲染）示例：
  - 源地址：<https://github.com/viper140/painting/blob/main/plantuml/usecase/bank-domain.puml>
  - RAW地址：<https://raw.githubusercontent.com/viper140/painting/main/plantuml/usecase/bank-domain.puml>
  - 代理后的地址：<http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/viper140/painting/main/plantuml/usecase/bank-domain.puml>
```
  - 方式二（自搭建服务渲染）：下载渲染服务 jar 包 <https://plantuml.com/zh/download>，本地启动，在 GUI 中选择要渲染的路径，这个设定比较奇怪，它会自动扫描路径下的所有可渲染文件自动生成目标图片，比如会把`test.puml`自动生成图片`test.png`
![](https://ata2-img.oss-cn-zhangjiakou.aliyuncs.com/neweditor/14c71c90-70c4-4bb4-8cfb-191f39f635e7.png)

## 4 注意事项

- PlantUML 官方不断有新特性迭代更新，比如图的主题样式，但语雀的 PlantUML 渲染能力并没有及时更新，为了兼容性，尽量还是别用些花里胡哨的特性，毕竟内容本身才是最重要的，好看的皮囊只能算锦上添花。

## 写在最后

当我跳出 PlantUML 的诸多优点，思考我追求的东西的本质是什么，其实就是**用文本替代二进制文件**，因为文本的可维护性强、版本管理容易。

这里希望用 PlantUML 来描述设计图；再往早些看，尤其是研发人员喜欢用 markdown 来替代 word 甚至 excel 的最基础功能；再有，我个人会用 vscode 插件`Markdown Preview Enhanced`来做 ppt <https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced>。这些精神是一脉相承的。
