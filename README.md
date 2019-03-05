[![LPPL](https://img.shields.io/badge/license-LPPL-green.svg)](https://github.com/Daniel612/gdutthesis/blob/develop/LICENSE)

# gdutthesis - 广东工业大学毕业论文模板
gdutthesis 是根据[《广东工业大学本科毕业设计(论文)手册》](http://jwc.gdut.edu.cn/info/1082/2164.htm)编写的 [LaTeX](https://zh.wikipedia.org/wiki/LaTeX) 模板，旨在帮助广东工业大学的本科毕业生高效地完成毕业论文的写作。模板提供各种方便的命令，自动化地排版论文的各个部分，使毕业论文轻易地满足学校的格式要求。
## 使用方法
### 环境配置
使用模板之前需要在操作系统上安装 [TeX](https://zh.wikipedia.org/wiki/TeX) 系统（例如 [TexLive](https://www.tug.org/texlive/)、[MacTex](http://www.tug.org/mactex/) 和 [MiKTeX](https://miktex.org/)）。如果你想下载体积较小的 [BasicTeX](http://www.tug.org/mactex/morepackages.html)，则还需要安装一些该模板中需要宏包（已在样板 [`main.pdf`](main.pdf) 中列出）。推荐使用自带的 TeX Live 包管理器 [`tlmgr`](https://tug.org/texlive/tlmgr.html) 对宏包进行管理以及 Visual Studio Code 的 [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) 插件来编写文档。

由于文档使用了中文排版，因此需要安装中文字体。出于版权和跨平台的考虑，该模板采用了 Adobe 与 Google 合作开发的[思源黑体](https://github.com/adobe-fonts/source-han-sans/blob/release/OTF/SimplifiedChinese/SourceHanSansSC-Regular.otf)和[思源宋体](https://github.com/adobe-fonts/source-han-serif/blob/release/OTF/SimplifiedChinese/SourceHanSerifSC-Light.otf)。如果想了解更多有关字体的用法，请参考[《在 LaTeX 中使用 OpenType 字体》](https://stone-zeng.github.io/2018-08-08-use-opentype-fonts/)。
### 文档编译
编译文档请使用 XeLaTeX 引擎。在终端执行
``` shell
xelatex main.tex
```
若文档内部有交叉引用或录入参考文献则需要编译两次。因为该模板使用 BibTeX 录入参考文献，所以需要先运行一次 xelatex，一次 bibtex，再运行两次 xelatex。
``` shell
xelatex main.tex
bibtex main.aux
xelatex main.tex
xelatex main.tex
```
再次推荐使用 LaTeX Workshop 插件自定义编译方案。具体方案请参考[《使用VSCode编写LaTeX》](https://zhuanlan.zhihu.com/p/38178015)。
## 写作指南
### 封面
论文封面在 data 文件夹的件 [cover.tex](data/cover.tex) 文件中，通过 `\input{data/cover}` 放入主源文件 [main.tex](data/main.tex) 中。你可以根据注释提示替换自己的信息。
### 摘要
中英文摘要包含在 `cabstract` 和 `eabstract` 环境命令中，对应的关键字使用 `\ckeywords` 和 `\ekeywords` 命令添加。请在 [abstract.tex](data/abstract.tex) 文件中编辑。
### 目录
论文目录由命令 `\tableofcontents` 添加，并且自动处理标题，页眉以及缩进等问题。
### 论文主体
论文主体按章划分，例如第一章放在 [chapter1.tex](data/chapter1.tex)，通过 `\input{data/chapter1}` 放入主源文件中。论文主体的写作参考一般的 LaTeX 教程。
### 参考文献
使用 BibTeX 工具实现自动生成参考文献列表。参考文献数据库是 ref 文件夹中 [refs.bib](data/refs.bib) 文件。每条文献保存着文献的类型、标签名、作者、年代等信息。你需要将引用的参考文献条目放入到该文件中。[Google Scholar](https://scholar.google.com/) 免费提供 BibTeX 条目信息的导出。

在论文主体中需要上标引用时，使用 `\upcite` 命令，参数为参考文献条目的简称（第一个尖括号后的内容）。
### 致谢
致谢包含在 `ack` 环境中，详情见 [ack.tex](data/ack.tex)。
### 附录
附录包含在 `appxchp` 环境中，详情见 [appendix01.tex](data/appxchp.tex)。
## License
gdutthesis is released under the [LPPL Version 1.3c](https://www.latex-project.org/lppl/lppl-1-3c.txt)

