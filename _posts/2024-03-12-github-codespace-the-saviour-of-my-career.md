---
title: "Github Codespace: The Saviour of my Career"
author: windu
date: 2024-03-12 16:39:00 +0700
categories: [Engineering, Tutorial]
tags: [github, codespace, cloud]
pin: true
img_path: 'assets/img/posts/20240312'
image:
  path: git-mascot.jpg
---

## Disastrous Encounter

So, picture this: September 2023, I was on a mission to kickstart my career after taking two months break. As a software engineer, armed with my old trusty MacBook Pro, I was all set to dive back into the job hunt and re-sharpen my LeetCode skills.

Long story short, I had my resume updated and applied to a bunch of companies I was interested in. While waiting for a reply, one fine evening, I was playing around with some leetcode, then suddenly Murphy's Law kicks in.

> ***“Anything that can go wrong will go wrong, and at the worst possible time.”***

Yep, my MacBook suddenly decided it's time to bid farewell (rest in peace my dearest friend). Some companies had even already gotten back to me about the interviews, and here I was, left high and dry without my main tool. Talk about bad timing!

The only alternative I had left was my wife’s aging Windows laptop. Despite its best efforts, it struggled to perform even some basic tasks, let alone handle coding environments. I found myself in quite the predicament. The horrors of being blacklisted by those companies for not following up haunted me.

So, I quickly started to look for an alternative, maybe there’s a good cloud development environment that I could use. At the end of the day, I found some, but they are all mostly paid services from the get go. Well, except for one: **GitHub Codespace**.

## Introduction

> **Disclaimer**: This is NOT a paid advertisement post.
{: .prompt-info }

Github Codespace is a cloud-based tool for software development. It eliminates setup worries, providing a full development environment for writing, running, and debugging code. It’s really ideal for quick prototyping and code showcasing, and the best part is that it's *free!* (to a certain point, but quite generous already)

![Desktop View](github-codespace-payment-tier.png)
_Github CodeSpace Payment Tier_

## How To Use

### Using a ready-to-use template

GitHub is quite thoughtful, we can simply head out to [github.com/codespaces/template](https://github.com/codespaces/template) and there are already ready-to-use templates a single click away.

![Desktop View](github-codespace-template.png)
_GitHub Codespace Template_

By clicking the <kbd>Use this template</kbd> on chosen template, it will startup the containers shortly. In this example, I chose the `Ruby on Rails` template as example.

![Desktop View](rails-codespace.jpeg)
_GitHub Codespace - Ruby on Rails_

*Voila!* Ruby on Rails app is ready to develop and run in your browser!

### Using a customized template

If you are like me, you probably don’t have the need to use a full-fledged app and tools running, or maybe just have the itches to mess around with the configuration. Then, we can also build our own codespace template. Check my template here: [github.com/windurisky/ruby-codespace-template](https://github.com/windurisky/ruby-codespace-template), you can run it

#### Devcontainer

Simply initiate a new github repo, and then create a `.devcontainer` folder, this folder will be the primary place to setup all the codespace container-related configs.

For example in my ruby codespace template, I added two files to that folder:

- `Dockerfile`

    ```docker
    ## available variants list is on https://mcr.microsoft.com/en-us/product/devcontainers/ruby/tags
    ARG VARIANT="3.3"
    FROM mcr.microsoft.com/vscode/devcontainers/ruby:${VARIANT}
    ```

- `devcontainer.json`

    ```json
    {
      "build": {
        "dockerfile": "Dockerfile",
        "args": { "VARIANT": "3.3" }
      },
      "customizations": {
        "vscode": {
          "extensions": [
            "iliazeus.vscode-ansi",
            "ms-azuretools.vscode-docker",
            "manuelpuyol.erb-linter",
            "waderyan.gitblame",
            "GitHub.github-vscode-theme",
            "eamodio.gitlens",
            "IBM.output-colorizer",
            "castwide.solargraph",
            "rebornix.Ruby",
            "wingrunr21.vscode-ruby",
            "bung87.vscode-gemfile",
            "vscode-icons-team.vscode-icons"
          ],
          "settings": {
            "files.trimTrailingWhitespace": true
          }
        }
      },
      "onCreateCommand": "gem install solargraph"
    }
    ```


They are pretty much self-explanatory at this point, you can check out more advanced details about devcontainer settings in [containers.dev](https://containers.dev/) site and [VS Code devcontainer docs](https://code.visualstudio.com/docs/devcontainers/create-dev-container)

## Conclusion

Thanks to GitHub Codespace enabling me to continue my coding exercises, I received three job offers and accepted the one that best suited me, effectively saving my career. I've also come to realize that with the advancement of cloud technology, the type and capacity of our devices are becoming less relevant, especially for coding. I can now code on my mobile phone, or literally any device with an internet connection and a browser!