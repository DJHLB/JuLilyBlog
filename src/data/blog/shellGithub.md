---
auther: DJLHB
pubDatetime: 2024-01-22T17:55:44Z
modDatetime: 2024-01-22T17:55:44Z
title: 获取Github开源项目最新版本下载地址
slug: Github-releasefile-download
featured: false
draft: false
tags:
  - Git
description:
  获取Github开源项目最新版本下载地址
---
## 下载指定的打包文件

```bash
releases_url=https://api.github.com/repos/open-tdp/tdp-cloud/releases/latest
tag_name=`wget -qO- $releases_url | grep tag_name | cut -f4 -d "\""`

wget https://github.com/open-tdp/tdp-cloud/releases/download/${tag_name}/tdp-cloud-android-arm64.gz
```

## 批量下载所有打包文件

```bash
releases_url=https://api.github.com/repos/open-tdp/tdp-cloud/releases/latest
url_list=`wget -qO- $releases_url | grep releases/download | cut -f4 -d "\""`

for url in $url_list; do
    wget $url
done
```