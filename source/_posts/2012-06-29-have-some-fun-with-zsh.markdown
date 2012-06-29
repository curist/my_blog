---
layout: post
title: "Have Some Fun With Zsh"
date: 2012-06-29 14:56
comments: true
categories: zsh, shell, linux, git
---

bash is fine, but I want to try something different and see if I like it.
zsh seems to be a pretty popular alternative among some groups,
so.. why not? lets have some fun with it.

1. follow [oh-my-zsh repository](https://github.com/robbyrussell/oh-my-zsh)
to get some really fancy settings.
1. choose your favorite themes from [oh-my-zsh themes](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes), or you can customize your own for sure.

What I need from a shell prompt are basically

* current working dir
* git info

the git_prompt_info comes with oh-my-zsh won't display a thing when you are not
on any branch, that's not acceptable for me.. I want to know I'm currently in
some git repository even not on any branch.

so I end up using something between the bira and candy themes,
but with bash's git-completion.

{% gist 3016468 ~/.zshrc %}

{% gist 3016473 %}


