# README #

学壹门户BLOG

### 开发介绍 ###

* rails version 4.1.9
* ruby version 2.1.5
* apache + passenger
* mysql5

### 开发 ###

```ruby

```

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
