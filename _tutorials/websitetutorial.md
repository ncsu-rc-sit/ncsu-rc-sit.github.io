---
layout: post
title: Jekyll static site generator
feature-img: "assets/img/background-color.png"
date: 26 November 2024
---
Jekyll is really useful for building static websites. You can use a Jekyll theme to write posts using markdown with less amount of HTML, CSS, and have a responsive good looking website. If you are a developer who loves to create websites while having control of every single aspect of HTML and CSS, Jekyll allows for all of that. You can create your own themes, layouts, control, and configure the entire site.

We will present enough information to get you started with your first Jekyll website, from creating content to serving them on Github pages.


1. [Installation](#install)
2. [Creating a site](#create)
3. [Front matter](#front)
4. [Config.yaml](#config)
5. [Installing themes](#themes)
6. [Layouts](#layouts)
7. [Includes](#includes)
8. [Hosting on Github pages](#hosting)
9. [Wiki](#wiki)



<a name="install"></a>
## Installation
The Jekyll website provides [installation](https://jekyllrb.com/docs/installation/) instructions that cover Windows, Mac, and Linux operating systems.

<a name="create"></a>
## Creating a site
For this tutorial, we will name our website "test_blog". Issue the command below at the terminal to create your new site.
```yml
jekyll new test_blog
```

<img src="/assets/img/tutorialsimages/jekyll/1.png" >

Jekyll creates some default content for the new site.

<img src="/assets/img/tutorialsimages/jekyll/2.png" >
Change directory into the `test_blog` directory
```yml
cd test_blog
```
Run the command below at the terminal and Jekyll will take all the pieces of our website and serve them in our browser. Browse the displayed server address `http://127.0.0.1:400/` to see the content of the website. You can also stop the display with the command `ctrl-c`

```yml
bundle exec jekyll serve
```
<img src="/assets/img/tutorialsimages/jekyll/3.png" >

The local host server now displays the new website from the browser.

<img src="/assets/img/tutorialsimages/jekyll/4.png" >
                                       
`test_blog`: the root directory
`_posts`: folder with all the blog posts.
`_site`:  folder with the final output of the website.
`_config.yaml`: file with the settings and basic attributes of the site.
`Gemfile`: holds all the dependencies for the website.
`pages`: Folder for adding new pages to website.
The rest of the files just default basic parts of our website.

<a name="front"></a>
## Front matter
[Front matter](https://jekyllrb.com/docs/front-matter/) is the site attribute
such as `Title` and `author's name` and many others, depending on our preference.
Jekyll reads the front matter first when a file is being executed to check the
layout specifications. See the example below.

```
---
layout: post
title: Jekyll static site generator
date: 14 August 2020
author: Joe Doe
---
```
We see some special information at the top of our post which is different from the content, That is called front matter.

config.yaml file has the settings and basic attributes of the site. 
<a name="config"></a>
## Config.yaml
It is the very important file in creating the website as this file has the settings and the attributes related to the site.
The format of the config.yaml file looks like this:

```yml
title: Your awesome title
author:
  name: GitHub User
  email: your-email@domain.com
description: > # this means to ignore newlines until "show_excerpts:"
  Write an awesome description for your new site here. You can edit this
  line in _config.yml. It will appear in your document head meta (for
  Google search results) and in your feed.xml site description.
show_excerpts: false # set to true to show excerpts on the homepage

# Minima date format
# refer to https://shopify.github.io/liquid/filters/date/ if you want to customize this
minima:
  date_format: "%b %-d, %Y"

  # generate social links in the footer
  social_links:
    twitter: jekyllrb
    github:  jekyll
    # devto: jekyll
    # dribbble: jekyll
    # facebook: jekyll
    # flickr:   jekyll
    # instagram: jekyll
    # linkedin: jekyll
    # pinterest: jekyll
    # youtube: jekyll
    # youtube_channel: UC8CXR0-3I70i1tfPg1PAE1g
    # youtube_channel_name: CloudCannon
    # telegram: jekyll
    # googleplus: +jekyll
    # microdotblog: jekyll
    # keybase: jekyll

    # Mastodon instances
    # mastodon:
    # - username: jekyll
    #   instance: example.com
    # - username: jekyll2
    #   instance: example.com

    # GitLab instances
    # gitlab:
    # - username: jekyll
    #   instance: example.com
    # - username: jekyll2
    #   instance: example.com

# If you want to link only specific pages in your header, uncomment
# this and add the path to the pages in order as they should show up
#header_pages:
# - about.md

# Build settings
theme: minima

plugins:
 - jekyll-feed
 - jekyll-seo-tag
```
Above is an example config.yaml file of `jekyll-minimal` theme. As said earlier this has all the basic configurations and settings of the website.

The detailed information of each attribute is as follows:

**Title**: The title of the page. <br>
**Author**: <br>
  **name**: THe name of the website author. <br>
  **email**: The email of the author <br>
**description**: This contains the information about website. <br>
**Minima date format**: This contains the date format to be used in the website. <br>
**social_links**: You may add the links to your social accounts here. This generates a hyperlink directly to your mentioned social account. <br>
**Build settings**: This section have the information related to the theme. <br>

For a detailed information on how to setup the config file, click [here](https://jekyllrb.com/docs/step-by-step/09-collections/)

<a name="themes"></a>
## Installing themes
By default, we will be having a minima theme for our Jekyll website. If we want a different theme for our website, there are lots of freely available themes on the internet.

Website for free themes:
 * [Jekyll themes](http://jekyllthemes.org/)
 * [Free jekyll themes](https://jekyll-themes.com/free/)

You can find many other good websites on the internet.

We will be showing an example of the theme change.
Every theme has a link to the Github repository which shows exactly how to use the theme in the `readme.md` section.
For the example, we selected a "Jekyll-hacker theme" from the internet. We will read the instructions on how to use it and install it. We will show the difference between the Jekyll minima theme and the new theme.

<img src="/assets/img/tutorialsimages/jekyll/5.png" >

We can see the theme change.

So basic steps to follow once you select a theme are,
 In the gem file add your selected theme, then install the theme by the command below.
```yml
bundle install
```
Change the theme attribute in the `_config.yaml` file and restart the server with the command below.
```yml
bundle exec jekyll serve
```
 
 <mark> Do not forget to change the layout names in your posts according to the theme you selected. If you don't change the layout you will not see the changes once you restart the server. </mark>

<a name="layouts"></a>
## Layouts
Layouts are skeletons of HTML code used to define the looks and feels of different pages or your entire site. By default, Jekyll will provide layouts for our pages. If you want to create your own layout.
1. Go to the root directory and create the `_layouts` folder.
2. Create an html file of your own and start making your own layout.

In the `_layouts` folder creating your own layout looks like this.
The code snippet below is an example of a layout called "`Home.html`" which uses the default layout.
```
---
layout: default
---

<div class="home">

    <div id="main" class="call-out"
         style="background-image: url('{{ site.header_feature_image | relative_url }}')">
        <h1> {{ site.header_text | default: "Change <code>header_text</code> in <code>_config.yml</code>"}} </h1>
    </div>
</div>

```

After you create your own layout, you can switch your site layout to it, which will then show up.

<a name="includes"></a>
## Includes
Includes allow us to take certain components of our site such as the header, the footer, or a navigation list and abstract them into their own html files. That means we can have an html file that describes the header or footer for the entire site. We can have a navigation list designed and include that on any page we want on the site. Follow the steps below to create your own layout.
1. Go to the root directory and create the `includes` folder.
2. Create a html file of your own and start to make components of your website.

In the `_includes` folder creating your own layout looks like this.
The code snippet below is an example of an include html file which creates a navigation list and can be further used anywhere on the site.

```
<div class="navigation-list">
   
<li>
<p><a href="{{ item.url | relative_url }}">{{ item.title }}</a></p>
</li>
   
</div>

```

The include file can be included in any part of your website.

<a name="Posts"></a>
## Creating blog posts
The _posts folder is where your blog posts live. Posts can be written in both Markdown and HTML. 
1. In the root directory, open the _posts folder.
2. Add all the similar blog posts to that particular folder. 

* BLog posts should start with a front matter.

You may include pictures/ images in the blog posts. To do that, use

```
![My helpful screenshot](/assets/screenshot.jpg)
```

This helps in icluding images in the post.

<a name="Assets"></a>
## Assets and how to use them

Using CSS, JS, images and other assets is straightforward with Jekyll. Place them in your site folder and they’ll copy across to the built site.
Jekyll sites often use this structure to keep assets organized:

```
├── assets
│   ├── css
│   ├── images
│   └── js
```

So, from your assets folder, create folders called css, images and js. Additionally, directly under the root create another folder called ‘_sass’. You could use a standard CSS file for styling, we’re going to take it a step further by using Sass. 

**CSS file**
In CSS folder, save the styling files and the bootstrap files.

**JS file**
In this folder, we have all other UI related files.

**Assets folder**
Assets folder can also be used to store images and call these images in the posts. Simply add images in the assets folder and use the image path in the blog posts. 
here are two ways to call the images in the blog posts.

**Use HTML tags**

```
<img src="/assets/images/img.jpg" >
```
_**img**_ is a HTML tag to display image. src is the path for the image where the image is located. This path is counted from the root directory. In the above example, assests is the root folder, in assets there is another folder as images and inside images folder the image, img.jpg is stored. However, we can create many folders inside image folder and sort the images respectively. The image path should be used in order to display the images on the webpage.

**Use simple syntax**

```
![](/assets/screenshot.jpg)
```
Instead of using html tags, we can use image path to display images on the webpage. Instead of giving html tag, simple use the image path in the parentheses. 

For example, Let us see how we have displayed the below image in this page.

![](/assets/img/tutorialsimages/jekyll/image(1).png)

Steps involved:
1. Save the image in the Assets folder.
2. Copy the path of the image. The path looks like this: "/assets/img.jpg"
3. Use the path in the file where the image needs to be displayed by using one of paths above.

**Note:** When displaying images, always use the correct extension of the image. If the image used is JPEG, use imagename.JPEG. follow same for png and jpg.

OK! But can we display a pdf on the webpage?

The answer is YES! we can display pdf, create a link to open pdf as a new webpage using Jekyll. This can be acheived by using HTML tags.

1. Display the pdf in the same webpage.

```
<embed src="/assets/pdf/1.pdf" width="100%" height="1200px" />
```
**embed:** It the HTML tag that allows to display the pdf on the webpage.

**src:** The path where the pdf is saved. We have saved the pdf in the pdf folder that is in the assets folder. You may save the pdf whereever you want. Simply copy the path and use it in the above code snippet to display the pdf on the webpage.

**width:** Defining the width of the pdf to be displayed on the webpage. 

**height:** Defining the height of the pdf to be displayed on the webpage.

2. Create a link to display the pdf in a seperate webpage.
```
<a href = "https://gcrnet.github.io/assets/pdf/1.pdf">
```
This is basically creating a hyperlink to display the pdf an a new webpage. In href, use the path as, "page url/pdf path". In the above code snippet, we want to display the pdf for the same website. Hence we are using **"https://gcrnet.github.io"** as the page url and **"/assets/pdf/1.pdf"** as page path.

After all the formating is done and when the website is ready to publish, we use git hub to host the website.

<a name="hosting"></a>
## Hosting on Github pages
Github pages (gh-pages) is a service that Github offers and allows you to build and host a static website completely for free. Jekyll integrates with gh-pages very well.

Setting up and hosting a static site in gh-pages:
1. Create a Github account.
2. Install git on your computer.
3. Create a new repository and name that, `test_blog`. Do not initialize a readme file.
<img src="/assets/img/tutorialsimages/jekyll/6.png" >
4. After creating the repository, we need to edit a variable in the config.yaml file.
   * Edit `baseurl` attribute.
   * Add the website name into the base URL, in this case, it is `test_blog`.
   * If you are planning on using a custom domain name you need to put that in the base URL.
<img src="/assets/img/tutorialsimages/jekyll/7.png" >
5. Set up a Github repository inside of the Jekyll project and upload it into Github.

Git commands for creating a repository and uploading all files to Github :
1. `git init` <br>
This will initialize an empty repository.
2. `git chechout -b gh-pages` <br>
We need to store our files on the gh-pages branch of our repository. The above command will checkout the gh-pages branch.
3. `git add .` <br>
This will add all our files to staging.
4. `git commit -m "initial commit"`<br>
This is an initial commit.
5. `git remote add origin "add your repository address here"`<br>
6. `git push origin gh-pages` <br>
This will upload all the files to the gh-pages.

<img src="/assets/img/tutorialsimages/jekyll/8.png" >

After you upload you will see all the files in Github

<img src="/assets/img/tutorialsimages/jekyll/9.png" >

You can go to the settings tab and scroll down you will see "your site is published."

<img src="/assets/img/tutorialsimages/jekyll/10.png" >

You can use that link to visit your static website.

<a name="wiki"></a>
## Wiki

[This link](https://jekyllrb.com/docs/step-by-step/01-setup/) will give a more detailed step by step guidance to build the website.

[Here](https://www.youtube.com/watch?v=T1itpPvFWHI&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB) is a link to a video tutorial by Giraffe academy.
This tutorial is very helpful for more detailed information.

