# [cmake](https://github.com/cmake/cmake) 中文手册

[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/Freed-Wu/cmake-zh/main.svg)](https://results.pre-commit.ci/latest/github/Freed-Wu/cmake-zh/main)
[![github/workflow](https://github.com/Freed-Wu/cmake-zh/actions/workflows/main.yml/badge.svg)](https://github.com/Freed-Wu/cmake-zh/actions)

[![github/downloads](https://shields.io/github/downloads/Freed-Wu/cmake-zh/total)](https://github.com/Freed-Wu/cmake-zh/releases)
[![github/downloads/latest](https://shields.io/github/downloads/Freed-Wu/cmake-zh/latest/total)](https://github.com/Freed-Wu/cmake-zh/releases/latest)
[![github/issues](https://shields.io/github/issues/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh/issues)
[![github/issues-closed](https://shields.io/github/issues-closed/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh/issues?q=is%3Aissue+is%3Aclosed)
[![github/issues-pr](https://shields.io/github/issues-pr/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh/pulls)
[![github/issues-pr-closed](https://shields.io/github/issues-pr-closed/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh/pulls?q=is%3Apr+is%3Aclosed)
[![github/discussions](https://shields.io/github/discussions/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh/discussions)
[![github/milestones](https://shields.io/github/milestones/all/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh/milestones)
[![github/forks](https://shields.io/github/forks/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh/network/members)
[![github/stars](https://shields.io/github/stars/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh/stargazers)
[![github/watchers](https://shields.io/github/watchers/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh/watchers)
[![github/contributors](https://shields.io/github/contributors/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh/graphs/contributors)
[![github/commit-activity](https://shields.io/github/commit-activity/w/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh/graphs/commit-activity)
[![github/last-commit](https://shields.io/github/last-commit/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh/commits)
[![github/release-date](https://shields.io/github/release-date/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh/releases/latest)

[![github/license](https://shields.io/github/license/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh/blob/main/LICENSE)
[![github/languages](https://shields.io/github/languages/count/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh)
[![github/languages/top](https://shields.io/github/languages/top/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh)
[![github/directory-file-count](https://shields.io/github/directory-file-count/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh)
[![github/code-size](https://shields.io/github/languages/code-size/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh)
[![github/repo-size](https://shields.io/github/repo-size/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh)
[![github/v](https://shields.io/github/v/release/Freed-Wu/cmake-zh)](https://github.com/Freed-Wu/cmake-zh)

## 安装

您可以先试一下在线预览。

- [![简体中文](https://img.shields.io/readthedocs/cmake?label=%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)](https://cmake.readthedocs.io/zh_CN/latest)
- [![繁體中文](https://img.shields.io/readthedocs/cmake?label=%E7%B9%81%E4%BD%93%E4%B8%AD%E6%96%87)](https://cmake.readthedocs.io/zh_TW/latest)

### Debian

[下载 deb](https://github.com/Freed-Wu/cmake-zh/releases)

```bash
dpkg -i cmake-zh_cn-*-Linux.deb
dpkg -i cmake-zh_tw-*-Linux.deb
```

### Redhat

[下载 rpm](https://github.com/Freed-Wu/cmake-zh/releases)

```bash
rpm -i cmake-zh_cn-*-Linux.rpm
rpm -i cmake-zh_tw-*-Linux.rpm
```

### [AUR](https://aur.archlinux.org/packages/cmake-zh_cn)

```bash
yay -S cmake-zh_cn
yay -S cmake-zh_tw
```

### nix

```bash
nix-shell -p github:Freed-Wu/cmake-zh
```

## 构建时依赖

### 必选

- [cmake](https://github.com/Kitware/CMake)
- [sphinx](https://www.sphinx-doc.org)
- [sphinx-intl](https://sphinx-intl.readthedocs.io)

### 可选

- [opencc](https://github.com/BYVoid/OpenCC): 繁体中文支持

## 构建

```bash
cmake -Bbuild -DZH_CN=ON -DZH_TW=ON -DHTML=ON -DMAN=ON
cmake --build build
```

## 运行时依赖

- [man](http://man-db.nongnu.org)

## 用法

```bash
export -Lzh_CN:zh_CHS:zh
man cmake
```

## TODO

Google 翻译很多地方不够好，后面会考虑换 GPT （如果买得起？）
