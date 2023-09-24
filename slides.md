---
theme: default
class: text-center
lineNumbers: false
drawings:
  persist: false
transition: slide-left
title: GitHub CLI を使ってみた
mdc: true
---

# GitHub CLI を使ってみた
@Mizuki901

<div class="abs-br m-6 flex gap-2">
  <a href="https://github.com/Mizuki901/github-cli-study" target="_blank" alt="GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

---

# 目次

<Toc maxDepth="1"></Toc>

---

# GitHub CLI とは

- ブラウザ上でGitHubを操作するのではなく、GitHubをCLIで操作するためのツール
- pull request、issues、GitHub Actions、などのGitHubの機能をCLIから行える
- 参考：[GitHub CLI について](https://docs.github.com/ja/github-cli/github-cli/about-github-cli)

---

# インストール

- 参考：[インストール方法](https://github.com/cli/cli#installation)
- macOSの場合はHomebrewでインストール可能
- インストール後、GitHubへのログインが必要

```sh {all|1-2|3}
brew install gh
gh -v
gh auth login
```

---

# 基本的な使い方

1. GitHubからclone済みのローカルリポジトリのディレクトリに移動
1. `gh` コマンドを使って操作する

```sh {all|1|2}
cd <ローカルリポジトリ>
gh <command> <subcommand> [flags]
```
