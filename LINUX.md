# Лаунчер на Linux

Файлы для [выпуска 1.0.22](https://github.com/necr0psy/mirea-launcher-download/releases/tag/club-1.0.22). Все для **x86_64 с glibc**, ARM и musl/Alpine пока нет.

## Kali, Debian и Ubuntu

Скачай [MireaLauncher-1.0.22-linux.deb](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.22/MireaLauncher-1.0.22-linux.deb). В папке с файлом:

```sh
sudo apt install ./MireaLauncher-1.0.22-linux.deb
```

Потом открой MireaLauncher из меню приложений. Сам лаунчер запускай обычным пользователем, без sudo. Java и игру он скачает сам.

Нужна свежая система: glibc 2.39 или новее, GTK 3 и WebKitGTK 4.1. Сборка сделана на Ubuntu 24.04; старые Debian 12 и Ubuntu 22.04 для этого файла не подходят. Для Kali нужен актуальный Kali Rolling. Зависимости ставятся из репозиториев своей системы, чужие репозитории добавлять не надо.

## Arch и системы на его основе

Скачай [mirea-launcher-1.0.22-1-x86_64.pkg.tar.zst](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.22/mirea-launcher-1.0.22-1-x86_64.pkg.tar.zst):

```sh
sudo pacman -U ./mirea-launcher-1.0.22-1-x86_64.pkg.tar.zst
```

Pacman предложит зависимости. После установки лаунчер будет в меню приложений. Это готовый локальный пакет, в AUR его нет. На Manjaro нужны те же актуальные библиотеки.

Пакет Arch сделан из того же DEB, повторной компиляции нет. Для установки готового файла инструменты сборки не нужны.

## Fedora и openSUSE

Скачай [MireaLauncher-1.0.22-x86_64.rpm](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.22/MireaLauncher-1.0.22-x86_64.rpm). На Fedora:

```sh
sudo dnf install ./MireaLauncher-1.0.22-x86_64.rpm
```

На openSUSE:

```sh
sudo zypper install ./MireaLauncher-1.0.22-x86_64.rpm
```

RPM пока без подписи: менеджер пакетов предупредит об этом. Сначала сверяй SHA256 с файлом [SHA256SUMS.txt](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.22/SHA256SUMS.txt) из выпуска.

Нужны glibc 2.39 или новее, GTK 3, WebKitGTK 4.1 и Ayatana AppIndicator. В RPM зависимости записаны по библиотекам, потому что в Fedora и openSUSE пакеты называются по-разному. Не любая версия Fedora или Leap подходит: если система не находит зависимости, этот выпуск лаунчера на неё не ставим с `--nodeps` и не подключаем чужие репозитории. На Fedora и openSUSE с графическим окружением пока не проверял.

RPM сделан из того же DEB. Зависимости включают нужные версии glibc и библиотеку значка в трее.

## AppImage без установки

Скачай [MireaLauncher-1.0.22-x86_64.AppImage](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.22/MireaLauncher-1.0.22-x86_64.AppImage):

```sh
chmod +x ./MireaLauncher-1.0.22-x86_64.AppImage
./MireaLauncher-1.0.22-x86_64.AppImage
```

Если система пишет про отсутствие FUSE, можно запустить с распаковкой:

```sh
./MireaLauncher-1.0.22-x86_64.AppImage --appimage-extract-and-run
```

Здесь тоже нужна glibc 2.39 или новее. AppImage не превращает сборку в совместимую со всеми старыми Linux. Автообновление Linux пока не подключено: новый пакет скачиваем и ставим поверх, AppImage заменяем новым файлом.

## Что проверено

Собрал DEB, пакет Arch, RPM и AppImage. Проверил метаданные, внутренние хеши RPM, распаковку AppImage и зависимости ELF в сборочном Ubuntu-контейнере. Бинарники DEB/Arch/RPM совпадают; в AppImage тот же код с добавленным путём к своим библиотекам. Минимальная glibc по ELF — 2.39. Эти проверки не подтверждают вход и запуск Minecraft. На живых Ubuntu/Debian/Kali, Arch, Fedora и openSUSE с графическим окружением эту версию ещё не проверял — сначала пробуем на одном ПК.

Форматы: [пакеты Arch](https://man.archlinux.org/man/alpm-package.7.en), [ограничения AppImage у Tauri](https://tauri.app/distribute/appimage/).
