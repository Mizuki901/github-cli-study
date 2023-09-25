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
gh help
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

---
layout: iframe-right
url: https://cli.github.com/manual/
---

# Core Commands

- https://cli.github.com/manual/gh
- GitHubの一通りの機能はCLIで操作できそう
- GitHub Actions用のコマンドもある
- Additional commandsにある、 `gh alias` や `gh extension` が、使ってみたら結構面白かった（後述）

---

# Core Commandsを使ってみる
  
例: `gh issue` を使って、Issueを一括操作する

準備

```sh
git clone https://github.com/Mizuki901/github-cli-study.git
cd github-cli-study
```

Issueの一覧を表示

```sh
gh issue list
gh issue list --limit 10 --state all
gh issue list --assignee Mizuki901
```

複数のIssueにラベルを一括付与

```sh
gh issue edit 1 2 3 --add-label bug
```

---
layout: iframe-right
url: https://cli.github.com/manual/gh_extension
---

# `gh extension` とは

- https://cli.github.com/manual/gh_extension
- GitHub CLIの拡張機能のこと
- Core Commandsだけではやりたいことが実現できないような場合に、ユーザーが自由に拡張機能を自作したり、世の中に公開することができる
- GitHubらしさを感じる機能
- aliasコマンド: `gh ext`

---

# `gh extension` の使い方

```sh
gh <extension|ext> help
```

拡張機能の検索

```sh
gh ext search --sort stars --limit 50
gh ext search hogefuga
```

拡張機能のインストール

```sh
gh ext install <インストールしたい拡張機能名>
```

インストール済みの一覧表示

```sh
gh ext list
```

拡張機能の使用

```sh
gh <拡張機能>
```

---
layout: image-right
image: ./img/gh_ext_search.png
---

# 人気の拡張機能

- 右の画像は、下記コマンドを実行してみた例
  ```sh
  gh ext search --sort stars --limit 50
  ```
- 便利そうなもの、面白そうなもの、色々ある
- 個人的には、 `k1LoW/gh-grep` と `github/gh-actions-importer` は使えそうだなと思った
- 手始めには、 `dlvhdr/gh-dash` と `vilmibm/gh-screensaver` は入れておきたい

---

# `gh alias` とは

- 自分でaliasコマンドを作れる機能
- よく使うコマンドをaliasとして登録できる
- より早くGitHubを操作したい場合に使える

---

# `gh alias` の使用例
例: 人気の拡張機能をすぐに探せるように、コマンドをaliasに登録する

`es` というaliasコマンドを登録

```sh
gh alias set es 'extension search --sort stars --limit 50'
```

aliasコマンドを使って実行

```sh
# `gh extension search --sort stars --limit 50` を実行するのと同じ
gh es
```

登録済みのaliasコマンドの一覧表示

```sh
gh alias list
```

`es` というaliasコマンドを削除

```sh
gh alias delete es
```

---

# 所感

- 普段からわざわざ使うほどではないと感じた
  - 普段はブラウザ操作で十分事足りる
- 個人として、ブラウザ / GitHub API / GitHub CLI の操作の選択肢を持っておくことは良いことだと思う
  - 複数のIssue、リポジトリ、などを横断的に操作したい場合などには、CLIは便利かも
- GitHub APIよりも、GitHub CLIを使いたいシーンはありそう
  - プログラムを書いてAPIを呼び出すよりも、CLIですぐに操作できるほうが便利な場合もある
- `gh alias` や `gh extension` は結構好みな機能だった

---
layout: center
---

# Fin.
