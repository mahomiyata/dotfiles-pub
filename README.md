# Dotfiles Setup Guide

このリポジトリは、Mac のシェル設定をシンプル且つ再現可能にするための dotfiles 管理用です。

## Directory Structure

```
~/
  ├─ .zshrc               # 薄いラッパ。dotfiles を読み込むのみ
  ├─ .zshenv              # 必要なら環境変数のみ
  └─ .dotfiles/
      ├─ zsh/
      │   ├─ zshrc        # 実体
      │   ├─ zshenv       # 実体
      │   ├─ prompt.zsh   # PS1設定（🦭）
      │   └─ aliases.zsh  # alias
      └─ README.md
```

## Setup (New Mac)

### 1. Clone this repository

```sh
git clone git@github.com:mahomiyata/dotfiles-pub.git ~/.dotfiles
```

### 2. Create minimal ~/.zshrc and ~/.zshenv

```sh
cat > ~/.zshrc << 'EOF'
DOTFILES="$HOME/.dotfiles"
if [ -f "$DOTFILES/zsh/zshrc" ]; then
  source "$DOTFILES/zsh/zshrc"
fi
EOF
```

```sh
cat > ~/.zshenv << 'EOF'
DOTFILES="$HOME/.dotfiles"
if [ -f "$DOTFILES/zsh/zshenv" ]; then
  source "$DOTFILES/zsh/zshenv"
fi
EOF
```


### 3. Apply settings

```sh
source ~/.zshrc
```

## Customizing

| 目的               | ファイル                          |
| ---------------- | ----------------------------- |
| alias            | `~/.dotfiles/zsh/aliases.zsh` |
| PS1（プロンプト）       | `~/.dotfiles/zsh/prompt.zsh`  |
| Zsh 設定           | `~/.dotfiles/zsh/zshrc`       |
| PATHなど必要最低限の環境変数 | `~/.dotfiles/zsh/zshenv`      |


## Rules

* ホーム直下の `.zshrc` / `.zshenv` は編集しない
* 実体ファイルはすべて `~/.dotfiles` に集約
* pyenv / rbenv / SDKMAN / volta / flutter などは必要になったときに入れる
* 設定追加時は dotfiles 内で明示的に記述

---

## Future Options (optional)

* brew bundle for package list
* VSCode settings sync
* iTerm2 config
* starship / p10k prompt configs
