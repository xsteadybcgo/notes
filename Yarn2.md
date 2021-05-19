- Zero-Installs的概念，在yarn2中推荐使用`Zero-Installs`，墨菲定律告诉我们只要一件事情有出错概率，无论概率多小发生的次数多了，最终都会导致错误。yarn 1.x的设计或多或少都有导致项目安装出现错误的可能。
该特性减少了依赖安装包的大小，并且在执行效率上有很大的提升，具体看[文档](https://yarnpkg.com/features/zero-installs#is-it-different-from-just-checking-in-the-node_modules-folder)
- Yarn的不同不在于性能，yarn将workspace作为一等公民。
