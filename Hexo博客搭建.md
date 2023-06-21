## Hexo博客搭建

#### Hexo安装

```
npm install hexo -g
```

#### 初始化博客

```
hexo init [博客名字]
```

#### 安装依赖

```
npm install
```

#### 预览

```
hexo server
```

#### 安装主题

```
npm install hexo-butterfly-cli -g
```

#### 在博客根目录执行

```
git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
```

为了可用需要安装两个插件
```
npm install hexo-renderer-pug hexo-renderer-stylus --save

npm install hexo-wordcount --save

```

在博客根目录新建一个_config.butterfly.yml将主题的文件复制进去

#### 上传GitHub相关

配置git的config文件

```
git config --global user.name "GitHub用户名"
git config --global user.email "绑定的用户名"
```



#### 把网站跑起来

新建标签页

```
hexo new page tags
```

```
hexo clean 清除缓存
hexo g 生成文件
hexo d 上传文件
```

**小插曲 上传不了可以用hexo d --debug**

当hexo s 或者hexo cl 用不了的时候需要用到命令下载一个插件 npm install hexo-server --save

####  添加标签页

```
hexo new page tags
记得添加type:"tags"
```

#### 添加分类页

```
hexo new page categories
记得添加type:"categories"
```

#### 添加友情链接

```
hexo new page link
记得添加 type:"link"
```

创建link.yml

```
- class_name: 友情链接
  class_desc: 那些人，那些事
  link_list:
    - name: Hexo
      link: https://hexo.io/zh-tw/
      avatar: https://d33wubrfki0l68.cloudfront.net/6657ba50e702d84afb32fe846bed54fba1a77add/827ae/logo.svg
      descr: 快速、简单且强大的网志框架

- class_name: 网站
  class_desc: 值得推荐的网站
  link_list:
    - name: Youtube
      link: https://www.youtube.com/
      avatar: https://i.loli.net/2020/05/14/9ZkGg8v3azHJfM1.png
      descr: 视频网站
    - name: Weibo
      link: https://www.weibo.com/
      avatar: https://i.loli.net/2020/05/14/TLJBum386vcnI1P.png
      descr: 中国最大社交分享平台
    - name: Twitter
      link: https://twitter.com/
      avatar: https://i.loli.net/2020/05/14/5VyHPQqR6LWF39a.png
      descr: 社交分享平台
```

