---
title: w3m
author: Kung (goukun07@gmail.com)
date: Mar 31, 2020
---

# w3m

Short introduction.

[TOC]

## Basic Concept/Overview

Content.

## Use cases

Content.

## Usage

Content.

## Tips and tricks

### display image in terminal

```sh
W3MIMGDISPLAY="/usr/lib/w3m/w3mimgdisplay"

declare -i x=500
y=0

width=40
height=40

w3m_command="0;1;$x;$y;$width;$height;;;;;$1\n4;\n3;"

echo -e "$w3m_command" | $W3MIMGDISPLAY
```

## Topic

Content.

## See also

*   [vifm wiki - how to preview images](https://wiki.vifm.info/index.php/How_to_preview_images)
