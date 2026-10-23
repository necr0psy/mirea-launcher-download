# Лаунчер МИРЭА

Здесь готовый лаунчер 1.0.21 для Windows, macOS и Linux. Код лежит отдельно.

Добавили каталог Modrinth: в «Моды и оформление» → «Каталог» можно найти и поставить моды, ресурс-паки и шейдеры. Лаунчер подберёт версию и обязательные зависимости. Свои файлы тоже остались; включать и удалять дополнения можно во вкладке «Установлено».

## Скачать 1.0.21

- [Windows x86_64 — EXE](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.21/MireaLauncher-1.0.21.exe)
- [macOS, Intel и Apple Silicon — ZIP](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.21/MireaLauncher-1.0.21-macOS.zip)
- [Kali Rolling / Debian 13 / Ubuntu 24.04+ — DEB](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.21/MireaLauncher-1.0.21-linux.deb)
- [Arch / свежий Manjaro — пакет pacman](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.21/mirea-launcher-1.0.21-1-x86_64.pkg.tar.zst)
- [Linux — AppImage без установки](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.21/MireaLauncher-1.0.21-x86_64.AppImage)
- [Fedora / openSUSE — RPM](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.21/MireaLauncher-1.0.21-x86_64.rpm)
- [Подпись обновления Windows — EXE.sig](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.21/MireaLauncher-1.0.21.exe.sig)

[SHA256 всех файлов](https://github.com/necr0psy/mirea-launcher-download/releases/download/club-1.0.21/SHA256SUMS.txt) · [Описание выпуска](https://github.com/necr0psy/mirea-launcher-download/releases/tag/club-1.0.21)

Все Linux-сборки для x86_64, нужна glibc 2.39 или новее. [Как поставить на Linux](LINUX.md). Обновление Linux пока вручную. Не каждая версия Fedora или openSUSE подходит — сначала проверяем зависимости.

На Mac распакуй ZIP и перенеси MireaLauncher.app в «Программы». Нотариализации Apple пока нет.

## Как поставить в клубе и настроить Gizmo

Сначала ставим на один ПК в киберзоне. Главное — проверить, что после выхода из сеанса следующий человек не попадёт в чужой аккаунт. Если всё работает, ставим на остальные.

1. Скачай `MireaLauncher-1.0.21.exe` в любую папку и один раз запусти из cmd: `"C:\путь\MireaLauncher-1.0.21.exe" --shared-computer`. Он сам скопирует себя в `%LOCALAPPDATA%\MireaLauncher\MireaLauncher.exe` и откроется уже оттуда. Скачанный файл после этого не нужен.
2. При установке он сам кладёт ярлык на рабочий стол и в меню Пуск. Эти ярлыки без клубного режима, их надо удалить. Иначе кто-то откроет лаунчер как дома и его вход останется на ПК.
3. В Gizmo приложение настроить так: файл `C:\Users\ИМЯ\AppData\Local\MireaLauncher\MireaLauncher.exe`, аргументы `--shared-computer`. ИМЯ — пользователь Windows, под которым идёт сеанс. Просто двойной клик по EXE клубный режим не включает.
4. На выход из сеанса: Client Tasks, Logout, задание Process. Файл тот же, аргументы `--end-shared-session`, рабочая папка `C:\Users\ИМЯ\AppData\Local\MireaLauncher`. Запускать под тем же пользователем Windows, что и лаунчер, иначе команда ничего не найдёт и скажет, что всё хорошо.
5. Команда на выход может думать до 40 секунд. Если в задании есть ожидание завершения, включить. Сначала дождаться её, потом уже закрывать остальные процессы и чистить профиль.

Первый запуск скачивает Java и игру, это около 750 МБ. Вход студент подтверждает в Telegram со своего телефона. На клубном ПК личные дополнения остаются до конца сеанса.

## Как проверить клубный сеанс

1. Запустить через Gizmo. На экране входа должна быть плашка «Клубный компьютер: вход до конца сеанса». Если вместо неё внизу ссылка «Чужой компьютер?», значит запустили без `--shared-computer`: поправить аргументы в Gizmo.
2. Зайти первым аккаунтом через Telegram, запустить игру.
3. Закончить сеанс через Gizmo. Игра должна закрыться сама.
4. Открыть лаунчер снова. Он должен просить вход заново, старого аккаунта быть не должно.
5. Зайти вторым аккаунтом и посмотреть, что ник второй, а не первый.

Руками команду выхода можно проверить в cmd:

```bat
start /wait "" "%LOCALAPPDATA%\MireaLauncher\MireaLauncher.exe" --end-shared-session
echo %ERRORLEVEL%
```

`0` — вход убран и сервер это подтвердил, либо клубный лаунчер вообще не был запущен. `3` — на ПК всё убрано, но сервер не ответил; вход сам протухнет через пару минут. `2` — ошибка, следующего человека пока не пускать.

## Что спросить у админа клуба

- Под каким пользователем Windows идут сеансы и один ли он на всех.
- Стирается ли диск или профиль после перезагрузки. Если да, лаунчер и игра пропадут вместе с ним — напишите мне, поставим по-другому.
- Если окно лаунчера вообще не открылось на Windows 10, возможно, нет WebView2. Его можно поставить с сайта Microsoft, называется WebView2 Runtime.

## Если что-то не так

Если после установки дополнения игра не запускается, жми «Запустить без моих дополнений». Твой набор сохранится.

Подписи Authenticode для Windows пока нет. Файл `.exe.sig` — отдельная подпись для обновления лаунчера, она не убирает предупреждения Windows. Если антивирус ругается, скиньте скрин с сообщением; отключать его не надо.

Хеш EXE сверяй с `SHA256SUMS.txt` из этого же выпуска. В cmd:

```bat
certutil -hashfile MireaLauncher-1.0.21.exe SHA256
```

На настоящем Windows с Gizmo и Linux с графическим окружением эту версию ещё не проверял. Проверка формата пакетов и библиотек не подтверждает вход и запуск Minecraft — сначала пробуем на одном ПК.
