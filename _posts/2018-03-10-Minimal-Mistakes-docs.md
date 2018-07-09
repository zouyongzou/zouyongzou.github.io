---
title: "Minimal Mistakes Jekyll Theme 文档"
excerpt: "Minimal Mistakes Jekyll Theme 文档"
comments: true
search: true
tags:
  - Jekyll
last_modified_at: 2018-06-21
toc: true
toc_sticky: true
---

## 文件结构
```bash
minimal-mistakes
├── _data                      # data files for customizing the theme
|  ├── navigation.yml          # main navigation links
|  └── ui-text.yml             # text used throughout the theme's UI
├── _includes
|  ├── analytics-providers     # snippets for analytics (Google and custom)
|  ├── comments-providers      # snippets for comments (Disqus, Facebook, Google+, and custom)
|  ├── footer                  # custom snippets to add to site footer
|  ├── head                    # custom snippets to add to site head
|  ├── base_path               # site.url + site.baseurl shortcut
|  ├── feature_row             # feature row helper
|  ├── gallery                 # image gallery helper
|  ├── group-by-array          # group by array helper for archives
|  ├── nav_list                # navigation list helper
|  ├── toc                     # table of contents helper
|  └── ...
├── _layouts
|  ├── archive-taxonomy.html   # tag/category archive for Jekyll Archives plugin
|  ├── archive.html            # archive base
|  ├── categories.html         # archive listing posts grouped by category
|  ├── category.html           # archive listing posts grouped by specific category
|  ├── collection.html         # archive listing documents in a specific collection
|  ├── compress.html           # compresses HTML in pure Liquid
|  ├── default.html            # base for all other layouts
|  ├── home.html               # home page
|  ├── posts.html              # archive listing posts grouped by year
|  ├── search.html             # search page
|  ├── single.html             # single document (post/page/etc)
|  ├── tag.html                # archive listing posts grouped by specific tag
|  ├── tags.html               # archive listing posts grouped by tags
|  └── splash.html             # splash page
├── _sass                      # SCSS partials
├── assets
|  ├── css
|  |  └── main.scss            # main stylesheet, loads SCSS partials from _sass
|  ├── images                  # image assets for posts/pages/collections/etc.
|  ├── js
|  |  ├── plugins              # jQuery plugins
|  |  ├── vendor               # vendor scripts
|  |  ├── _main.js             # plugin settings and other scripts to load after jQuery
|  |  └── main.min.js          # optimized and concatenated script file loaded before </body>
├── _config.yml                # site configuration
├── Gemfile                    # gem file dependencies
├── index.html                 # paginated home page showing recent posts
└── package.json               # NPM build scripts
```

## Post
### YAML
```yaml
---
title: "文章标题" # 标题
excerpt: "文章摘要" # 摘要
excerpt_separator: "<!--more-->" # 摘要分隔符
comments: true
search: false #
categories:   # 分类
  - document
tags:         # 标签
  - Post Formats
  - notice
last_modified_at: 2018-06-21 # 最后修改时间
toc: true # toc(table of contents) 目录
toc_sticky: true  # 固定
toc_label: "Unique Title" # 自定义title
toc_icon: "heart"  # 对应 Font Awesome icon 名 (没有 fa 前缀)
link: https://github.com # 当前 post 链接到
header:
  image: /assets/images/page-header-image.png
  og_image: /assets/images/page-header-og-image.png
read_time: true # 阅读时间
related: true # 相关推荐
share: true # 分享
author_profile: false # 作者信息栏
---
```

### Notice
Basic usage

```markdown
**Default Notice:** 默认 Notice 样式
{: .notice}

**Primary Notice:**
{: .notice--primary}

**Info Notice:**
{: .notice--info}

**Warning Notice:**
{: .notice--warning}

**Danger Notice:**
{: .notice--danger}

**Success Notice:**
{: .notice--success}
```

**Default Notice:** `Default Notice`
{: .notice}

**Primary Notice:** `Primary Notice`
{: .notice--primary}

**Info Notice:** `Info Notice`
{: .notice--info}

**Warning Notice:** `Warning Notice`
{: .notice--warning}

**Danger Notice:** `Danger Notice`
{: .notice--danger}

**Success Notice:** `Success Notice`
{: .notice--success}

Want to wrap several paragraphs or other elements in a notice? Using Liquid to capture the content and then filter it with `markdownify` is a good way to go.

```html
{% raw %}{% capture notice-2 %}
#### New Site Features

* You can now have cover images on blog pages
* Drafts will now auto-save while writing
{% endcapture %}{% endraw %}

<div class="notice">{% raw %}{{ notice-2 | markdownify }}{% endraw %}</div>
```

{% capture notice-2 %}
#### New Site Features

* You can now have cover images on blog pages
* Drafts will now auto-save while writing
{% endcapture %}

<div class="notice">
  {{ notice-2 | markdownify }}
</div>

Or you could skip the capture and stick with straight HTML.

```html
<div class="notice">
  <h4>Message</h4>
  <p>A basic message.</p>
</div>
```

<div class="notice">
  <h4>Message</h4>
  <p>A basic message.</p>
</div>

### Quote
> Only one thing is impossible for God: To find any sense in any copyright law on the planet.
  
> <cite><a href="http://www.brainyquote.com/quotes/quotes/m/marktwain163473.html">Mark Twain</a></cite>

### Video
YouTube video embed below.

<iframe width="640" height="360" src="" frameborder="0" allowfullscreen></iframe>

### Header image
This post has a header image with an OpenGraph override.

```yaml
header:
  image: /assets/images/page-header-image.png
  og_image: /assets/images/page-header-og-image.png
```
This post has a header image with an OpenGraph override.

```yaml
header:
  overlay_image: /assets/images/unsplash-image-1.jpg
  og_image: /assets/images/page-header-og-image.png
  caption: "Photo credit: [**Unsplash**](https://unsplash.com)"
  cta_url: "https://unsplash.com"
```

### Image
[![foo](https://farm5.staticflickr.com/4073/4939853213_33ffc0290b_b.jpg)](https://flic.kr/p/8ww3fZ)

Standard image with no width modifier classes applied.

**HTML:**

```html
{% raw %}<img src="{{ site.url }}{{ site.baseurl }}/assets/images/filename.jpg" alt="">{% endraw %}
```

**or Kramdown:**

```markdown
{% raw %}![alt]({{ site.url }}{{ site.baseurl }}/assets/images/filename.jpg){% endraw %}
```

Image that fills page content container by adding the `.full` class with:

**HTML:**

```html
{% raw %}<img src="{{ site.url }}{{ site.baseurl }}/assets/images/filename.jpg" alt="" class="full">{% endraw %}
```

**or Kramdown:**

```markdown
{% raw %}![alt]({{ site.url }}{{ site.baseurl }}/assets/images/filename.jpg)
{: .full}{% endraw %}
```


This post has a teaser image with an OpenGraph override.

```yaml
header:
  teaser: /assets/images/page-header-teaser.png
  og_image: /assets/images/page-header-og-image.png
```

{% capture fig_img %}
[![Foo](https://farm5.staticflickr.com/4134/4940462712_7c28420b27_b.jpg)](https://flic.kr/p/8wzarA)
{% endcapture %}

{% capture fig_caption %}
Stairs? Were we're going we don't need no stairs.
{% endcapture %}

<figure>
  {{ fig_img | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>{{ fig_caption | markdownify | remove: "<p>" | remove: "</p>" }}</figcaption>
</figure>

<figure>
  {{ fig_img | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>Photo from Unsplash.</figcaption>
</figure>

### Gallery
```yaml
gallery:
  - url: /assets/images/unsplash-gallery-image-1.jpg
    image_path: /assets/images/unsplash-gallery-image-1-th.jpg
    alt: "placeholder image 1"
    title: "Image 1 title caption"
```

And then drop-in the gallery include --- gallery `caption` is optional.

```liquid
{% raw %}{% include gallery caption="This is a sample gallery with **Markdown support**." %}{% endraw %}
```
And for giggles one more gallery just to make sure this works. To fill page content container add `class="full"`.

## Layout

## Markup
