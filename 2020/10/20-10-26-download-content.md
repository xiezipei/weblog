# 记一次 Content Download 调优

## 问题

一天，测试发现某接口请求特别慢，检查发现接口的 Content Download 时间特别长（16s+）：

![下载时间太长](https://user-images.githubusercontent.com/5949351/97248738-6286b880-183d-11eb-8e45-23570ba37a9d.png)

## 解决

进一步检查，发现 Content 的 Size 也特别大：

![size特别大](https://user-images.githubusercontent.com/5949351/97251754-72090000-1843-11eb-96a7-6ef55dae1bee.png)

开始排查：

* 前端渲染组件没问题，跟其它页面用的是同一个组件，其它页面没问题
* 后端接口响应也没问题，响应速度正常，其它页面接口响应和 Content Download 也很快

觉察到该接口返回的数据在 Chrome Network 面板的 Preview 和 Response 也无法加载出来，于是换了 Swagger 来试下调接口：

速度很慢，加载动画一直在转圈，但是过了一会儿返回结果显示出来的时候，心中就答案了——元凶就是 `headImage` ：

![找到元凶](https://user-images.githubusercontent.com/5949351/97251762-76351d80-1843-11eb-9420-bfd93652aaa6.png)

`headImage` 用于保存用户的头像，页面中只需要用户名字，但后端直接吧用户的详细信息全返回了，就包括了这个 `headImage`。

这个字段用 `base64` 形式保存，也就是说这个 Content Size 之所以这么大，是因为包含了一页的用户头像（测试阶段并没有限制上传头像的图片大小）。

最后，跟后端沟通，修改接口不返回用户的 `headImage` 字段，问题解决了。