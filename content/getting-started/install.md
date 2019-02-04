---
title: Get jx
linktitle: Get jx
description: How to install the jx binary on your machine
date: 2017-02-01
publishdate: 2017-02-01
lastmod: 2017-02-01
categories: [getting started]
keywords: [install]
menu:
  docs:
    parent: "getting-started"
    weight: 10
weight: 10
sections_weight: 10
draft: false
aliases: [/overview/usage/,/extras/livereload/,/doc/usage/,/usage/]
toc: true
---

Pick the most suitable instructions for your operating system:

### macOS

On a Mac you can use brew:

```shell
brew tap jenkins-x/jx
brew install jx 
```

Or if you have not installed [brew](https://brew.sh/) and prefer to install by hand:

```shell
curl -L https://github.com/jenkins-x/jx/releases/download/v{{< version >}}/jx-darwin-amd64.tar.gz | tar xzv 
sudo mv jx /usr/local/bin
```

### Linux

```shell
mkdir -p ~/.jx/bin
curl -L https://github.com/jenkins-x/jx/releases/download/v{{< version >}}/jx-linux-amd64.tar.gz | tar xzv -C ~/.jx/bin
export PATH=$PATH:~/.jx/bin
echo 'export PATH=$PATH:~/.jx/bin' >> ~/.bashrc
```

### Windows

- If you use [Chocolatey](https://chocolatey.org/), then there is a [package available](https://chocolatey.org/packages/jenkins-x).

  To install the `jx` binary run:

  ```cmd
  choco install jenkins-x
  ```

  To upgrade the `jx` binary run:

  ```cmd
  choco upgrade jenkins-x
  ```

  - If you use [scoop](https://scoop.sh), then there is a [manifest available](https://github.com/lukesampson/scoop/blob/master/bucket/jx.json).

  To install the `jx` binary run:

  ```cmd
  scoop install jx
  ```

  To upgrade the `jx` binary run:

  ```cmd
  scoop update jx
  ```

### Other platforms
    
[download the binary](https://github.com/jenkins-x/jx/releases) for `jx` and add it to your `$PATH`

Or you can try [build it yourself](https://github.com/jenkins-x/jx/blob/master/docs/contributing/hacking.md). Though if build it yourself please be careful to remove any older `jx` binary so your local build is found first on the `$PATH` :)

## Getting Help

To find out the available commands type:

    jx

Or to get help on a specific command, say, `create` then type:

    jx help create

You can also browse the [jx command reference documentation](/commands/jx)
