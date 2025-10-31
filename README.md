[合集 - 深度(6)](https://github.com)

1.深入浅出 ES Module10-31

[2.JavaScript 沙箱09-25](https://github.com/keepsmart/p/19111065)[3.传统软件部署的痛点09-12](https://github.com/keepsmart/p/19087510)[4.Docker 容器化09-12](https://github.com/keepsmart/p/19087473):[milou加速器](https://milou6.com)[5.浅谈前端水印2021-05-30](https://github.com/keepsmart/p/14829134.html)[6.前端缓存2020-02-21](https://github.com/keepsmart/p/12340805.html)

收起

# 概述

在 JavaScript 模块化发展历程中，为解决**全局变量污染，代码依赖管理**等问题，先后出现了 CommonJS（CJS）、AMD、CMD、UMD、ES6 Module（ESM）五大主流方案。不同方案因设计目标、运行环境（浏览器 / Node）的差异，形成了各自的语法特性与生态定位。

其中ES6 Module是 ES6 官方定义的**标准化模块化方案**，旨在统一浏览器与服务器端的模块化语法，解决传统模块化方案（如 CommonJS、AMD）的碎片化问题。

# 核心特性

* **静态化设计**：模块的导入（import）与导出（export）声明必须在模块顶层，且导入导出的模块标识符（如文件路径）需是静态字符串，不能动态拼接（如 ·import('./' + path)· 是不允许的）。这一特性让 JavaScript 引擎在编译阶段就能分析模块依赖关系，实现 Tree-Shaking（摇树优化，剔除未使用的代码）。
* **独立模块作用域**：每个 ESM 模块都是一个独立的作用域，模块内声明的变量、函数、类默认不对外暴露，需通过export显式导出后，其他模块才能通过import导入使用，这样可以避免全局变量污染。
* **值引用特性**：ESM 导入的模块成员是 “值的引用”（而非 CommonJS 的值的拷贝），若导出模块修改了导出的变量（如导出一个 let 声明的变量并后续修改），导入模块会同步感知到变化（需注意：基础类型值若用const声明，因不可修改，不会有此特性）。
* **异步加载**：在浏览器环境中，ESM 默认通过
