---
title: 'LaTeX笔记/提纲模板'
description: '自用的 LaTeX 模板'
publishDate: '2026-01-07 20:57:05'
heroImage: { src: './latex.png', alt: 'LaTeX', color: '#B4C6DA' }
tags:
    - LaTeX
draft: false
language: '中文'
comment: true
---

该模板基于<a href="https://unicov.cn/scu/">四川大学智锐科创协会</a>提供的 LaTeX 模板修改，适用于课堂笔记与提纲整理（如有侵权请联系作者，作者将立刻删除）

`note.tex`文件内容如下，直接复制即可，在编译时使用 `XeLaTeX` 作为编译器

在`note.tex`同级的目录下，需要新建 figures 文件夹，并在文件夹中放上`logo.png`

```LaTeX
\documentclass{article} 

% 核心宏包
\usepackage{ctex}       
\usepackage{graphicx}   
\usepackage{float}      
\usepackage{amsmath}    
\usepackage{tabularx}   
\usepackage{booktabs}   
\usepackage{fancyhdr}   
\usepackage{geometry}   
\usepackage{hyperref}   

% 字体设置
% 使用标准Windows字体集
\ctexset{fontset = none}

% 自定义宋体，支持伪斜体和伪粗体
\setCJKfamilyfont{zhsong}[
  AutoFakeSlant = {0.3},    % 伪斜体，倾斜角度0.3
  AutoFakeBold = {2.3}      % 伪粗体，加粗程度2.3
]{SimSun}
\renewcommand*{\songti}{\CJKfamily{zhsong}}

% 定义楷体
\setCJKfamilyfont{zhkai}[AutoFakeBold = {2.3}]{KaiTi}
\newcommand{\mykaiti}{\CJKfamily{zhkai}}


% 设置全局字体
\setCJKmainfont{SimSun}
\setCJKsansfont{SimHei}
\setCJKmonofont{FangSong}

% 页面设置
\geometry{a4paper,left=2cm,right=2cm,top=2cm,bottom=2cm}
\graphicspath{{figures/}} 

% 超链接设置
\hypersetup{
  colorlinks=true,
  linkcolor=black,
  citecolor=blue
}

% 自定义命令
\newcommand{\covertitle}{\zihao{-0}\heiti\bfseries}  
\newcommand{\covertablename}{\heiti \zihao{-3}}      
\newcommand{\covertablecontent}{\mykaiti \zihao{-3}} 
\newcommand\covertable[2]{ 
  \begin{table}[H]
    \centering
    \begin{tabular}{p{12em}}
      {\covertablename #1 }\\
    \end{tabular}
    \begin{tabular}{p{14em}<{\centering}}
      {\covertablecontent #2 }\\
      \hline
    \end{tabular}
  \end{table}
}

% 正文字体命令
\newcommand\textFont{\songti \zihao{-4}}

% 修改目录名称
\renewcommand{\contentsname}{\centerline{目录}} 

% 页眉设置
\pagestyle{fancy} 
\fancypagestyle{页眉}{
  \fancyhead{}
  \fancyhead[C]{你的名字}   
  \renewcommand\headrulewidth{.5pt}
}

\begin{document}

% 封面区域
\quad \\ \\ 

% Logo
\begin{figure}[H]
  \centering
  \includegraphics[width=0.5\linewidth]{logo}
\end{figure}

\quad \\ 
\begin{center}
  \covertitle{\zihao{2}文章标题}
\end{center}

\quad \\ \\ \\

% 封面信息表格
\covertable{作\hskip 5em 者}{你的名字}
\covertable{提\quad 交\quad 日\quad 期}{\today}
\covertable{学\hskip 5em 院}{xx学院}
\covertable{专\hskip 5em 业}{xx专业}

% 空白页结束
\thispagestyle{empty}
\newpage

% 目录页
\thispagestyle{empty}  % 目录页不显示页眉页脚

% 生成目录
\tableofcontents
\newpage

% 正文开始
\setcounter{page}{1}
\pagestyle{页眉}

\section{正文基础示例}
\textFont

这是正文基础段落示例，LaTeX会自动完成排版对齐，无需手动调整格式。

\subsection{字体样式示例}
可轻松实现 \textbf{加粗文字}、\emph{斜体文字}，或调整字号 {\zihao{3} 大号文字}。

\textbf{伪粗体测试：这段文字应该显示为伪粗体效果。}

\emph{伪斜体测试：这段文字应该显示为伪斜体效果。}

\subsection{数学公式示例}
行内公式：$E = mc^2$

行间公式：
$$ \int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi} $$

\subsection{表格示例}
\begin{table}[h!]
  \centering
  \caption{基础三线表示例}
  \begin{tabularx}{0.9\textwidth}{l X X}
    \toprule
    \textbf{维度} & \textbf{示例1} & \textbf{示例2} \\
    \midrule
    内容1 & 基础文本内容 & 自动换行的长文本内容，无需手动调整宽度 \\
    内容2 & 公式嵌入 & $A = \begin{bmatrix}1 & 0 \\0 & 1\end{bmatrix}$ \\
    \bottomrule
  \end{tabularx}
\end{table}

\section{结语}
以上为LaTeX基础使用示例，可根据需求修改内容、样式及结构。

{\songti 宋体文本} {\mykaiti 楷体文本} {\heiti 黑体文本} 

\end{document}
```