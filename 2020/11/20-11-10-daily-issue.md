# 日报 20-11-10

## GitHub

今天发现 GitHub 没记录我这几天的 Contributions（有提交，但小方块没变绿），排查后知道原因了：本地 git 配置的 `name` 和 `email` 跟 GitHub 上的不一致。修改为信息为一致就可以解决了。

查看用户名和邮箱：

```sh
git config user.name
git config user.email
```

修改用户名和邮箱：

```sh
git config --global user.name <your name>
git config --global user.email <your email>
```

但是本地存在多个git账号（GitLab、GitHub等），每次这样改就麻烦了。像我用的 SoureTree 可以这样改：

> 注：切换本地 key，我用了 `skm`（npm 包）。

全局默认改为公司 GitLab 的：

![st-global](https://user-images.githubusercontent.com/5949351/98758103-ed081400-2408-11eb-92f9-701c2091ae34.png)

GitHub 项目仓库取消默认全局的：

![st-cancel](https://user-images.githubusercontent.com/5949351/98758100-e8dbf680-2408-11eb-910d-3d30254cc1df.png)

## Excel

> 注：Mac，Microsoft Excel

学到了两种快速输入：

第一种，输入时间：

* `command + ;` 插入当前时间，如 `10:43 AM`
* `control + ;` 插入当前日期，如 `2020/11/11`

第二种，快速复制粘贴一行信息：

悬停单元格右下角边框线，光标会变成黑色实心十字架，然后往下拖动即可，分几种情况：

* 如果是日期，会递增复制粘贴
* 如果是其它，直接复制粘贴

当然最重要的是，还可以选中整行来操作！
