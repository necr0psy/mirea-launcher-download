# Лаунчер на Linux

Сборки лежат в [выпуске 1.0.20](https://github.com/necr0psy/mirea-launcher-download/releases/tag/club-1.0.20). Все для **x86_64**, ARM пока нет.

## Kali, Debian и Ubuntu

Скачай `MireaLauncher-1.0.20-linux.deb`. В папке с файлом:

```sh
sudo apt install ./MireaLauncher-1.0.20-linux.deb
```

Потом открой MireaLauncher из меню приложений. Сам лаунчер запускай обычным пользователем, без sudo. Java и игру он скачает сам.

Нужна свежая система: glibc 2.39 или новее, GTK 3 и WebKitGTK 4.1. Сборка сделана на Ubuntu 24.04; старые Debian 12 и Ubuntu 22.04 для этого файла не подходят. Для Kali нужен актуальный Kali Rolling. Зависимости ставятся из репозиториев своей системы, чужие репозитории добавлять не надо.

## Arch и системы на его основе

Скачай `mirea-launcher-1.0.20-1-x86_64.pkg.tar.zst`:

```sh
sudo pacman -U ./mirea-launcher-1.0.20-1-x86_64.pkg.tar.zst
```

Pacman предложит зависимости. После установки лаунчер будет в меню приложений. Это готовый локальный пакет, в AUR его нет. На Manjaro нужны те же актуальные библиотеки.

## AppImage без установки

Скачай `MireaLauncher-1.0.20-x86_64.AppImage`:

```sh
chmod +x ./MireaLauncher-1.0.20-x86_64.AppImage
./MireaLauncher-1.0.20-x86_64.AppImage
```

Если система пишет про отсутствие FUSE, можно запустить с распаковкой:

```sh
./MireaLauncher-1.0.20-x86_64.AppImage --appimage-extract-and-run
```

Здесь тоже нужна glibc 2.39 или новее. AppImage не превращает сборку в совместимую со всеми старыми Linux. Автообновление Linux пока не подключено: новый пакет скачиваем и ставим поверх, AppImage заменяем новым файлом.

## Что проверено

Собрал `.deb`, пакет pacman через makepkg и AppImage. Pacman читает метаданные, AppImage распаковывается, библиотеки ELF находятся в среде сборки. На живых Arch/Kali с графическим окружением вход и запуск Minecraft ещё не проверял — сначала пробуем на одном ПК.

Форматы: [пакеты Arch](https://man.archlinux.org/man/alpm-package.7.en), [ограничения AppImage у Tauri](https://tauri.app/distribute/appimage/).
