---
tags: linux, archlinux, pacman, shell
---
# Полезные команды при работе с pacman


## Установить пакет со всеми опциональными зависимостями
```sh
pacman -S $PKG --asdeps --needed $(pacman -Si $PKG | grep -Pzo '(?s)(?<=Optional Deps\s{3}:).*(?=Conflicts With)' | tr -d '\0' | cut -d':' -f '1' | while read -r line; do pacman -Ss > /dev/null ^$line && echo $line; done)
```