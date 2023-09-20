---
title: "Should You Use Neovim?"
date: 2023-09-17T10:54:43+04:00
summary: "There are several categories of programmers. Those who like to customize their workspace from scratch, every detail, every little thing,
and there are those who like to use something already ready and probably modify it a little for themselves (for example, change the editor theme)
and thus, do not spend a lot of time on it. But there are those who do not want to spend a lot of time, but want to customize the editor for themselves."
---

{{< figure src="/images/programming/should-i-use-neovim/header.webp" >}}

## Introduction

There are several categories of programmers. Those who like to customize their workspace from scratch, every detail, every little thing,
and there are those who like to use something already ready and probably modify it a little for themselves (for example, change the editor theme)
and thus, do not spend a lot of time on it. But there are those who do not want to spend a lot of time, but want to customize the editor for themselves.

You've probably already tried vim/neovim (~~and couldn't exit~~), but you immediately realized that you would spend a lot of time understanding the intricacies and how to configure it.
Therefore, you probably preferred a different code editor or IDE.

It's funny that according to the results of the [Stack Overflow Developer Survey 2022](https://survey.stackoverflow.co/2022), Neovim is the most loved editor for the second year in a row, and according to the results
of [Developer Survey 2023](https://survey.stackoverflow.co/2023/) Neovim is the most "admired" editor.

{{< figure src="/images/programming/should-i-use-neovim/main.webp"  >}}

But despite the fact that Neovim is highly respected among developers, the question of whether you should use it still remains open.
Let's look at the advantages of Neovim:

1. **Efficiency in code typing.** Neovim is designed to minimize mouse usage.

2. **Performance**

3. **Extensibility.**
Neovim supports a wide range of plugins, which allows you to customize it to your needs.

4. **Community and documentation.**
Neovim has an active community of users and developers, which means that there is extensive documentation and guides.

You will probably be interested in the first two points, since a large range of plugins and community are not something new for modern IDEs.
As for performance, Neovim is really fast. It runs very fast, it is also a winner in terms of memory consumption.
And yes, due to the emphasis on using the keyboard, you can really speed up the code typing.

So, since the author belongs to the category of people who do not want to spend a lot of time, but nevertheless want to get some benefits by using Neovim, as well as to do it painlessly, let's try it!
And if you also want to try something new without spending a lot of time, then this article is for you.

## Installation

In this article we will use ready-made Neovim configurations, it is assumed that you have installed neovim and minimal knowledge of it (insert mode/command mode).

*But wait, I wanted to set it up myself.*

Yes, we use already existing configurations, but this way we find the golden mean (we don't waste time, at the same time we can configure and get performance)

So, there are different configurations, such as NvChad, LunarVim, but we use AstroNvim because it initially has extensive capabilities that will simplify our work in configuration.
The installation is really simple, you just need to clone the repository and run nvim.

{{< highlight bash >}}
 git clone --depth 1 https://github.com/AstroNvim/AstroNvim ~/.config/nvim
 nvim
{{< / highlight >}}

Next, we need to familiarize ourselves with the Mason package manager, this is the Neovim plugin that AstroNvim installed for us. With just one command **:Mason** and through a user-friendly interface, we can install linters, formatters, [LSP servers](https://en.wikipedia.org/wiki/Language_Server_Protocol) that we need

Use **g?** to open help for Mason.

{{< figure src="/images/programming/should-i-use-neovim/mason.webp" >}}

## What's next?

So, without editing any configuration files, we were able to install the tools we needed for comfortable work and now you can start using nvim.

Use the [AstroNvim documentation](https://astronvim.com/Basic%20Usage/walkthrough) to familiarize yourself with the basic commands and mappings, this greatly simplifies the work.
If you forgot one or another mapping in a particular situation, you can press your Leader Key (**Space** by default) and you will see a panel with subsequent combinations that you can use.

{{< figure src="/images/programming/should-i-use-neovim/leader.webp" >}}

## AstroCommunity repository

AstroNvim also has a repository with a collection of plugins.
For example, you want a selection of plugins for working with C++.

To do this, you need to create your own ["User configuration"](https://astronvim.com/configuration/manage_user_config).
If desired, you can create a remote repository, but we will do it locally.

{{< highlight bash >}}
git clone https://github.com/AstroNvim/user_example.git ~/.config/nvim/lua/user
{{< / highlight >}}

Next, in the *~/.config/nvim/lua/user/plugins* file, you can specify which collection of plugins from the AstroCommunity repository you want to use,
in our case it is [astrocommunity.pack.cpp](https://github.com/AstroNvim/astrocommunity/tree/main/lua/astrocommunity/pack/cpp).

{{< highlight lua "linenos=inline,hl_lines=6">}}
return {
  -- Add the community repository of plugin specifications
  "AstroNvim/astrocommunity",
  -- example of importing a plugin, comment out to use it or add your own
  -- available plugins can be found at https://github.com/AstroNvim/astrocommunity
    { import = "astrocommunity.pack.cpp" },
    { import = "astrocommunity.colorscheme.dracula-nvim" },
    { import = "astrocommunity.pack.tailwindcss" },
    { import = "astrocommunity.pack.html-css" },
    { import = "astrocommunity.pack.typescript" },
}
{{< / highlight >}}

The next time you start nvim, all the necessary plugins will be installed automatically.

## Other settings
Of course, there are a bunch of other settings, you can continue to customize the editor for yourself,
for example, change the theme or change the home screen.

In this article, I used the "Dracula" theme, which was installed through the AstroCommunity repository.
You can change the theme and other settings in the file *~/.config/nvim/lua/user/init.lua*

{{< highlight lua "linenos=inline,linenostart=21">}}
colorscheme = "dracula",
{{< / highlight >}}

Let's also change the default home screen.
You can do this in the file *~/.config/nvim/lua/user/plugins/core.lua*.

Find some big text generator and use it as a home screen.

{{< figure src="/images/programming/should-i-use-neovim/home.webp" >}}

## Conclusion

Using Neovim configurations is an excellent way to try out this text editor and assess its advantages without the need for deep customization and time investment. It's also an easy entry point for beginners.

This article omitted topics such as debugging and git (which are already included in the configuration) since the goal was to provide a brief introduction and overview of the main features of Neovim configurations.

Also, the author used the usual gnome-terminal, you can also use tmux and other terminals to add transparency or other features.

Don't forget that Neovim has an active community that is always ready to help and share advice if you have any questions.

### Useful links
[Neovim website](https://neovim.io/)

[AstroNvim website](https://astronvim.com/)

[AstroNvim default mappings](https://astronvim.com/Basic%20Usage/mappings)

[AstroNvim discord](https://discord.astronvim.com/)
