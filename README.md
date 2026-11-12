<p align="center"><img src="assets/icon.svg" width="88" alt="JianShanAgent"></p>

<h1 align="center">catalog</h1>

<p align="center"><a href="https://github.com/JianShanAgent/agent-core">JianShanAgent（见山）</a>的站点目录：做好了的站点插件有哪些。</p>

<p align="center">
  <img src="https://img.shields.io/badge/站点目录-sites.yaml-2f6b5a?style=flat-square&labelColor=1f3b34" alt="站点目录">
  <img src="https://img.shields.io/github/license/JianShanAgent/catalog?label=License&color=2f6b5a&style=flat-square&labelColor=1f3b34" alt="License">
</p>

<sub>The site catalog of JianShanAgent: a list of ready-made site plugins. The admin console reads it, filters by wiki platform, and installs a plugin with one click.</sub>

管理后台的「Wiki」页读的是这个仓库 `main` 分支上的 [`sites.yaml`](sites.yaml)：按平台筛选，点「添加」就把那个 wiki 挂到机器人上——环境里没有它的站点插件时，从插件仓库最新的 Release 下载安装包、核对校验和后装到数据目录里。

## 目录里的一项

```yaml
format: 1
sites:
  - id: huiji_yys                       # 站点插件的 id
    platform: huiji                     # 它是哪个平台上的站（核心带着的平台：huiji、bwiki）；自己架的 MediaWiki 站不写
    name: 阴阳师 Wiki                    # 给人看的名字
    description: …                      # 一两句话：它带来什么
    repo: JianShanAgent/site-huiji-yys  # 站点插件的仓库，要和这个目录在同一个组织下
    wiki:                               # 挂上时写进实例配置的那一项
      id: huiji                         # 建议的名字（添加时可以改）；不写的话，平台上的站用平台的 id，别的用站点插件的 id
      label: 灰机 wiki                  # 回答里标出处时的叫法
      api_url: https://yys.huijiwiki.com/api.php
      site_base: …                      # 这两项不写就按 MediaWiki 的默认
      article_path: …
      auth_header: X-authkey            # 要带放行请求头的站：请求头的名字（密钥在实例的 secrets.yaml）
```

## 加一个站点插件

1. 站点插件的仓库在 JianShanAgent 组织下，从 [`template-site-wiki`](https://github.com/JianShanAgent/template-site-wiki) 起；
2. 它发过 Release：带着安装包 `jianshanagent_site_<id>-<版本>-py3-none-any.whl` 和 `SHA256SUMS`（模板里的发版流程会做）；
3. 在 `sites.yaml` 里加一项，合进 `main`。各个实例十分钟内就能看到，不用更新核心。

站点插件所在的平台要是核心已经带着的；核心还不认识的平台，这一项在后台里会显示成用不了。

## 开源许可

[MIT License](LICENSE)
