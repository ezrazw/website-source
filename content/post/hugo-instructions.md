---
title: "Hugo Instructions"
author: Yuchen Jin
tags: ["Hugo"]
date: 2019-04-14T15:51:46-05:00
slug: "hugo-instructions"
draft: true
---

Here we discuss about how to maintain a hugo website that is equipped with a renewable theme. In particular, this site is exactly suitable for the case discussed in this article.

<!--more-->

# Download (for a new user)

A new user for this website need to ensure that you have installed `git` and `hugo (extended)`.

* For installing `git`, check [here][inst-git] to see some instructions.
* For installing `hugo`, check [here][inst-hugo] to download the newest release. Especially, to make use of this theme, we need to download the **extended version** which should have a larger size than the standard release.

After that, run such command to pull down the newest branch of this website.

```
git clone -b hugo-nuo https://github.com/cainmagi/hugo-templates.git my-website-nuo
cd my-website-nuo
git pull --recurse-submodules
```

Then you could enter the folder `my-website-nuo` to check the pulled website source.

# Debug (for writting draft)

Make sure the current path of your command window is inside your website folder (take `my-website-nuo` as an example). Then use such a command to start a new drafting session:

```
hugo server --buildDrafts --watch
```

Then you will see the command window shows that a new session should be opened at `localhost:1313`. You could open a new web browser and get access to the real-time updated local website. This website could be only examined by your local device.

When the drafting session is opened, you could modify any website file and see the update in real time. A hugo session would block your command window and would not get stopped until you interrupt it manually (by <kbd>Ctrl</kbd>+<kbd>C</kbd>).

## Change a port number

The above command would use the default port number `1313`. If you want to change a port number, you could use a command like this:

```
hugo server --buildDrafts --watch --port 1000
```

Then the local website could be viewed by `localhost:1000`. This option is useful when your default port for `Hugo` (`1313`) is being used, which may occur when you are drafting with more than one hugo site.

## Share your local site in local network

This technique is useful for users who need to work with more than one device which are in the same local area network (LAN). In this case, you need to find your IP address for LAN first. Linux users and Mac users use 

```
ifconfig
```

while windows users use

```
ipconfig
```

After examining the IP address, for example, if my IP address is `192.168.10.10`, then we could use this command to start a new drafting session,

```
hugo server --buildDrafts --watch --bind="192.168.10.10" --baseURL="http://192.168.10.10/"
```

These settings enable you to get access to your local website by `192.168.10.10:1313`. Different from `localhost:1313` which could be only viewed from your local device, this address could be viewed by any device that shares the same LAN with your `Hugo` host. In some OSes (like windows), this feature could be only enabled when you give the authority to `Hugo`.

# Add a new page

To add a new page, you need to use such a command:

```
hugo new content/post/new-page.md
```

This command enables you to create a new markdown file with a name `new-page` in `content/post`. Note that when you are opening a drafting session, you may not be able to call `hugo new ...` in the same command window. In this case we suggest you to interrupt the current drafting session, create a new file and re-open the session again to make sure the session to be aware of new files.

# Update the theme (template) to newest version

Make sure your current path of your command window is inside the folder of the website, then you only need to run this command to update the theme:

```
git submodule update --recursive --remote
```

This command would update your theme folder from the original author's work directly. Note that you should not pull `hugo-templates.git` again, because the website source and theme source are separated. The website source is defined in `hugo-templates.git`, however the theme source is not. You need to modify your website source to add your own articles, so you should not let the website source override your customized works. But you could update your theme source in any time once the original author update the theme.

# Produce the release

Inside your website folder, run this command directly to get the release

```
hugo
```

After that, you could find your website inside your `./public/` folder. Move all contents in this folder to your website host or git-page repository, then you could post (or renew) your site.

[inst-git]:https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
[inst-hugo]:https://github.com/gohugoio/hugo/releases