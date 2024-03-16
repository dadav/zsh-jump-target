# zsh-jump-target

zsh-jump-target is a ZLE widget for quickly jumping to a spot in a command
line, inspired by Vim's [EasyMotion][easy-motion] and Emacs' [avy][avy] and
[ace-jump-mode][ace-jump-mode].

[easy-motion]: https://github.com/easymotion/vim-easymotion
[avy]: https://github.com/abo-abo/avy
[ace-jump-mode]: https://github.com/winterTTr/ace-jump-mode

## Installation

Add this to your `.zshrc`

```zsh
plugins_dir="$HOME/.zsh/plugins"
[[ -d "$plugins_dir" ]] || mkdir -p "$plugins_dir"

additional_plugins=(
  'https://github.com/dadav/zsh-jump-target'
)

for plugin in $additional_plugins; do
  plugin_path="$plugins_dir/${plugin##*/}"
  [[ -d "$plugin_path" ]] || git clone "$plugin" "$plugin_path"
  for p in "$plugin_path"/*.plugin.zsh; do
    source "$p"
  done
done
```

## Usage

Bind some key to `jump-target`, default is `\ej` (alt+j):

```zsh
bindkey "^J" jump-target
```

When you want to jump to a particular spot in a command line, press the bound
key and it will prompt you for a character. For example, if you wanted to
jump to the beginning of this sentence, you would press capital `F`. All the
captial `F`'s in the command line will be overlaid with target letters. Press
the target letter you want and your cursor will jump to that spot.

## Options

`ZSH_JUMP_TARGET_CHOICES` is a string of characters that will be used to mark
targets. By default it is `a` through `z` and `A` through `Z`.

`ZSH_JUMP_TARGET_STYLE` is the style used to highlight targets. By default
they will be red, bold, and underlined.
