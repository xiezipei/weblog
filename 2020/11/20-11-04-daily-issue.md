# 日报 20-11-04

## eslint error 1

有时候 vscode 如果没有全局开启 ESLint，会报以下错误：

![esLint is disabled](https://user-images.githubusercontent.com/5949351/98124454-2cf16780-1eee-11eb-9b3d-51b0938f0c1c.png)

解决方法：悬停错误的地方，vscode 会提示：

> 提示：也可以使用 Mac 快捷键：`command + .`

![vscode 提示](https://user-images.githubusercontent.com/5949351/98124708-85286980-1eee-11eb-9c5e-6e593cd2998c.png)

选择 `ESLint: Manage Library Exceution` 会有一个弹窗（如下所示），选择 `Allow Everywhere` 即可：

![allow everywhere](https://user-images.githubusercontent.com/5949351/98124480-34187580-1eee-11eb-8531-c2ab530660d5.png)


## eslint error 2

ESLint 提示 switch 代码块中有报错，悬停波浪线地方（也就是 `case` 语句部分），会看到错误如下：

```sh
error: Unexpected lexical declaration in case block no-case-declarations
```

解决：将 `case` 里面的代码用 `{}` 括起来：

![fix-no-case-declarations](https://user-images.githubusercontent.com/5949351/98125985-046a6d00-1ef0-11eb-839f-176fb9ab48f6.jpg)

参考：[reactjs \- eslint: no\-case\-declaration \- unexpected lexical declaration in case block](https://stackoverflow.com/questions/50752987/eslint-no-case-declaration-unexpected-lexical-declaration-in-case-block)