# 日报 20-11-12 | 缓存穿透、雪崩和击穿

[经常被提到的缓存穿透、雪崩和击穿到底是什么](https://segmentfault.com/a/1190000037782785)

这篇文章很通俗易懂地介绍了这三个概念：

* redis 缓存穿透

访问透过 redis 直接经过 mysql，通常是一个不存在的 key,在数据库查询为 null。每次请求落在数据库、并且高并发。数据库扛不住会挂掉。

* redis 缓存雪崩

雪崩，就是某东西蜂拥而至的意思，像雪崩一样。在这里，就是 redis 缓存集体大规模集体失效，在高并发情况下突然使得 key 大规模访问 mysql，使得数据库崩掉。可以想象下国家人口老年化。以后那天人集中在 70-80 岁，就没人干活了。国家劳动力就造成压力。

* redis 缓存击穿

缓存击穿，是指一个 key 非常热点，在不停的扛着大并发，大并发集中对这一个点进行访问，当这个 key 在失效的瞬间，持续的大并发就穿破缓存，直接请求数据库，好像蛮力击穿一样。