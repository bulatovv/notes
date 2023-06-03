---
tags: linux, archlinux, pacman, shell
---
# Полезные скрипты для работы pacman


## Установить пакет со всеми опциональными зависимостями
```sh
pacman -S $PKG --asdeps --needed $(
	pacman -Si $PKG |
		grep -Pzo '(?s)(?<=Optional Deps\s{3}:).*(?=Conflicts With)' |
		tr -d '\0' | cut -d':' -f '1' |
		while read -r line; do
			pacman -Ss > /dev/null "^$line" && echo "$line"
		done
)
```

## Показать отсортированные по размеру пакеты
```sh
pacman -Qi | \
	grep -Po '(?<=Name\s{12}:\s|Installed Size\s{2}:\s).*' | \
	tr -d ' ' | \
	awk 'ORS=NR%2?FS:RS' | \
	sort -r -h -k2
```