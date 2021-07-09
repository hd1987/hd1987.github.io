---
title: CommandLineTools reinstall
date: 2021-08-11 17:49:58
tags: terminal
---

```
xcode-select --print-path
# in my case /Library/Developer/CommandLineTools

# the next line deletes the path returned by the command above
sudo rm -rf $(xcode-select --print-path)

# install them (again) if you don't get a default installation prompt
xcode-select --install
```
