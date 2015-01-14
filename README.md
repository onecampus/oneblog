# README #

学壹门户BLOG

### 开发介绍 ###

* rails version 4.1.9
* ruby version 2.1.5
* apache + passenger
* mysql5

### 部署 ###

```ruby
git clone git@github.com:onecampus/oneblog.git
cd wine
cp ./config/database.yml.mysql ./config/database.yml
# 编辑 database.yml, 修改为你的 mysql 数据库密码, 其他最好别动
bundle install
rake db:create # 创建数据库
rake db:migrate # 导入数据库表
rake db:seed # 导入测试数据
rails s # 启动开发服务器
# 访问 http://127.0.0.1:3000
# 访问 http://127.0.0.1:3000/refinery

# 如果需要重置数据库
rake db:reset
```

### github workflow

```bash
git clone git@github.com:onecampus/oneblog.git
git branch -r
git checkout -b dev origin/dev # 检出 dev 分支, 并对应到本地的dev分支
git checkout -b your_name dev # 创建自己的私有分支, start_point 为dev
# 做修改, 提交, 注意不要推送到远程
git checkout dev # 切换到 dev 分支
git pull # 拉取远程更新
# 如果拉取遇到问题, 可能需要 git branch --set-upstream-to=origin/dev dev
git merge --no-ff your_name # 合并 your_name 到当前分支, 这里是 dev, 必须使用 --no-ff
git branch -d your_name # 删除 your_name 本地分支
git push origin dev # 推送 dev 分支到远程
```

### 注意

1. 在每次合并前, 都要先 `git pull` 来拉取远程更新, 然后再合并
2. 除了我外, 其他人不要操作 `master` 分支
3. 多用 `git status`, `git branch`, `git log`
4. 把不用的文件加入到 `.gitignore`, 例如 `.idea`
5. 不要直接在 `dev` 分支上开发, 按步骤来, 先建立自己的私有分支, 开发后再合并
6. 保证每一次提交都是必要的, 而不是为了保存代码就做一次提交
7. 当合并功能分支的时候，加上 `-no-ff` 选项强制进行一次全新的commit

### CMD

```ruby
rails new oneblog -m http://refinerycms.com/t/edge

# add gem gem 'refinerycms-blog', git: 'https://github.com/refinery/refinerycms-blog', branch: 'master'
rails generate refinery:blog
rake db:migrate
rake db:seed

# config the language and company name

# override views
rake refinery:override view=refinery/_footer
rake refinery:override view=refinery/pages/show
rake refinery:override view=refinery/pages/home
rake refinery:override view=refinery/_content_page
rake refinery:override view=refinery/_javascripts
rake refinery:override view=refinery/_header
rake refinery:override view=refinery/_head

# https://github.com/refinery/refinerycms-blog/tree/master/app/views/refinery/blog
rake refinery:override view=refinery/blog/categories/show
rake refinery:override view=refinery/blog/comment_mailer/notification

rake refinery:override view=refinery/blog/posts/_comment
rake refinery:override view=refinery/blog/posts/_comments
rake refinery:override view=refinery/blog/posts/_nav
rake refinery:override view=refinery/blog/posts/_post
rake refinery:override view=refinery/blog/posts/archive
rake refinery:override view=refinery/blog/posts/index.rss
rake refinery:override view=refinery/blog/posts/show
rake refinery:override view=refinery/blog/posts/tagged

rake refinery:override view=refinery/blog/shared/_body_content_right
rake refinery:override view=refinery/blog/shared/_categories
rake refinery:override view=refinery/blog/shared/_post
rake refinery:override view=refinery/blog/shared/_posts
rake refinery:override view=refinery/blog/shared/_rss_feed
rake refinery:override view=refinery/blog/shared/_tags

rake refinery:override view=refinery/blog/widgets/_blog_archive

rake refinery:override view=layouts/application
```
