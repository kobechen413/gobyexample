## Go by Example 中文版

[Go by Example](https://gobyexample-cn.github.io/) 是一个通过带注释的示例程序学习 Go 语言的网站。网站包含了一系列简单的示例程序，并附带了注释说明，非常适合 Go 语言初学者。

如果您想学习 Go 语言基础知识，不要犹豫，请直接前往 [Go by Example](https://gobyexample-cn.github.io/) 开始学习。

## 综述

如果你想了解 Go by Example `网站` 是如何构建的，或者想为该项目贡献代码，请查看下面的内容：

本项目包含了网站的内容和构建工具链，网站使用的是 `public` 目录下静态文件（html 等文件）的内容。它是这样被构建出来的：通过 `程序` 提取 `examples` 目录下的源码及注释，并使用 `templates` 目录下的静态文件模板将其渲染为静态文件，最终将生成的静态文件输出到 `public` 目录下。

实现此构建过程的 `程序` 位于 `tools` 目录下，其相关的依赖库被放在了 `vendor` 目录下。构建得到的 `public` 目录下的静态文件（html 等文件），可以部署到任何支持静态内容的系统。例如 S3、CloudFront 以及任何 Web 服务器。

### 构建

[![Build Status](https://travis-ci.com/mmcgrana/gobyexample.svg "Travis CI status")](https://travis-ci.com/mmcgrana/gobyexample)

若想自行构建该网站，你需要安装 Go 和 Python。然后运行下面的命令：

```console
$ go get github.com/russross/blackfriday
$ tools/build
$ open public/index.html
```

如果你使用了 `GO MOD`，直接执行下面的命令即可：

```console
$ tools/build
$ open public/index.html
```

若想实时渲染，请使用持续构建：

```console
$ tools/build-loop
```

### 发布

下面的例子展示了如何将网站上传至 AWS：

```console
$ gem install aws-sdk
$ export AWS_ACCESS_KEY_ID=...
$ export AWS_SECRET_ACCESS_KEY=...
$ tools/upload
```

## 许可协议

该项目的著作权归 Mark McGranaghan 所有，并遵循 [CC BY-SA 3.0](http://creativecommons.org/licenses/by/3.0/) 协议。

Go Gopher 的版权归 [Renée French](http://reneefrench.blogspot.com/) 所有，并遵循 [CC BY-SA 3.0](http://creativecommons.org/licenses/by/3.0/) 协议。

## 其他语言

本项目只是 [mmcgrana](https://github.com/mmcgrana) 的 [Go by Example](https://github.com/mmcgrana/gobyexample) 项目的中文翻译。

除中文版外，该项目还有以下语言：

* [English](https://gobyexample.com) by [mmcgrana/gobyexample](https://github.com/mmcgrana/gobyexample)（原版）
* [Czech](http://gobyexamples.sweb.cz/) by [martinkunc](https://github.com/martinkunc/gobyexample-cz)
* [French](http://le-go-par-l-exemple.keiruaprod.fr) by [keirua](https://github.com/keirua/gobyexample)
* [Italian](http://gobyexample.it) by the [Go Italian community](https://github.com/golangit/gobyexample-it)
* [Japanese](http://spinute.org/go-by-example) by [spinute](https://github.com/spinute)
* [Korean](https://mingrammer.com/gobyexample/) by [mingrammer](https://github.com/mingrammer)
* [Spanish](http://goconejemplos.com) by the [Go Mexico community](https://github.com/dabit/gobyexample)
* [Ukrainian](http://gobyexample.com.ua/) by [butuzov](https://github.com/butuzov/gobyexample)

## 致谢

感谢 [Jeremy Ashkenas](https://github.com/jashkenas) 的 [Docco](http://jashkenas.github.com/docco/)，启发了这个项目。

## 贡献说明

> 从这部分开始，后面的内容都是中文版的贡献者们给自己加的戏（好吧，其实前面的内容也没有完全根据英文版翻译）。

如果你发现中文版的例子没有及时与英文版同步，或者你觉得某个例子翻译得不够好，甚至只是一个错误的文字、单词或符号，我们都 `非常欢迎` 你能够提交 pull request 以帮助我们使项目更完善，贡献流程大致如下：

1. Fork 该仓库。
1. 在 `examples` 目录下找到想要修改的例子，完成修改，这通常是以 `例子`（也就是一个目录）为单位进行修改，当然，你可以一次性修改多个例子。需要注意的是：只修改 `.go` 和 `.sh` 文件。`.hash` 文件是 `tools/build` 自动更新的，主要用于判断文件内容是否有改动；
1. 使用 `tools/build` 命令重新生成静态文件。这一步会格式化代码，并判断内容是否有改动。对于内容有改动的例子，会自动将该例子的代码提交至 `http://play.golang.org/` 进行测试（可能需要克服网络障碍）。通过测试后，会自动更新静态文件；
1. `tools/serve` 本地预览效果；
1. 通过自测后即可提交 pull request :)

## 构建说明

原版的英文项目使用 vendor 解决依赖，中文版可以使用 `GO MOD` 解决依赖。

注意：依赖库 [blackfriday](https://github.com/russross/blackfriday) 的 2.x.x 版本目前与项目不兼容，只能使用 1.x.x 版本，项目的 `go.mod` 文件已正确配置，同学们不要随意修改。直接执行 `tools/build` 等命令即可。 

## 致谢

感谢本翻译项目的原作者 [everyx](https://github.com/everyx)，完成了所有文件最初的翻译，同时也感谢项目每一位 [贡献者](https://github.com/gobyexample-cn/gobyexample/graphs/contributors) 的辛勤付出。

项目现由 [gobyexample-cn](https://github.com/gobyexample-cn) 维护，欢迎各位同学 fork 并提交 pull request。
