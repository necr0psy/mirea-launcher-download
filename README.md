# Лаунчер МИРЭА

тут готовый лаунчер для Windows и Linux, чтобы скачать сразу на пк без флешки. код лежит отдельно

**[скачать exe, версия 1.0.20](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.20/MireaLauncher-1.0.20.exe)**

[как поставить и настроить Gizmo](https://github.com/necr0psy/mirea-launcher-download/releases/tag/club-1.0.20)

## Linux

Все сборки для x86_64. Нужна glibc 2.39 или новее.

- [Kali Rolling / Debian 13 / Ubuntu 24.04+ — .deb](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.20/MireaLauncher-1.0.20-linux.deb)
- [Arch / свежий Manjaro — пакет pacman](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.20/mirea-launcher-1.0.20-1-x86_64.pkg.tar.zst)
- [AppImage без установки](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.20/MireaLauncher-1.0.20-x86_64.AppImage)

[Как поставить на Linux](LINUX.md). На настоящих Arch и Kali пока не проверял — сначала пробуем на одном пк.

## что сейчас

пока ставим на один пк в киберзоне и проверяем что все работает. самое главное чтобы после выхода из сеанса следующий человек не зашел в чужой аккаунт. если все норм тогда уже на остальные

## коротко про клуб

- запускать с `--shared-computer`. просто открыть exe недостаточно чтобы включить клубный режим. если все правильно, на экране входа сверху плашка «Клубный компьютер». если вместо нее внизу ссылка «Чужой компьютер?», значит аргумент не передался
- на выход из сеанса в Gizmo поставить `--end-shared-session`
- после первого запуска лаунчер сам кладет ярлык на рабочий стол и в Пуск. в клубе их надо удалить, они открывают обычный домашний режим

все по шагам написано в инструкции по ссылке выше

## если что-то не так

подписи Windows пока нет. если антивирус ругается скиньте скрин что именно пишет, отключать его не надо

хеш файла, SHA256: `3106c5dc747c001c8df986ef78153512838d53e2776aaf98900d6d5aa9cbbef5`
