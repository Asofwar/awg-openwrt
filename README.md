# Автоматическая настройка AmneziaWG для OpenWRT версии 24.10.0-rc5 и более новых

## Automatic configuration of AmneziaWG for OpenWRT version 24.10.0-rc5 and newer

Для автоматической настройки рекомендую использовать [скрипт](https://github.com/itdoginfo/domain-routing-openwrt) от пользователя itdog. Этот скрипт позволяет автоматически скачать нужные пакеты из собранных здесь и настроить [точечный обход блокировок по доменам](https://habr.com/ru/articles/767464/).

For automatic configuration, I recommend using the [script](https://github.com/itdoginfo/domain-routing-openwrt) by user itdog. This script allows you to automatically download the necessary packages from those collected here and configure [domain-based bypass of blocks](https://habr.com/ru/articles/767464/) (instructions in Russian).

Если же вам нужно только установить пакеты, я добавил скрипт amneziawg-install - он автоматически скачает пакеты из этого репозитория под ваше устройство (только для стабильной версии OpenWRT), а также предложит сразу настроить интерфейс с протоколом AmneziaWG.

If you only need to install the packages, I have added the amneziawg-install script - it will automatically download the packages from this repository for your device (only for the stable version of OpenWRT) and also offer to configure the interface with the AmneziaWG protocol.

Для запуска скрипта подключитесь к роутеру по SSH, введите команду и следуйте инструкциям на экране:

To run the script, connect to the router via SSH, enter the command, and follow the on-screen instructions:
```
sh <(wget -O - https://raw.githubusercontent.com/Asofwar/awg-openwrt/refs/heads/master/amneziawg-install.sh)
```

# Сборка пакетов для всех устройств, поддерживающих OpenWRT

## Building packages for all devices supporting OpenWRT

В репозиторий добавлен скрипт, который парсит данные о поддерживаемых платформах со страницы OpenWRT и автоматически запускает сборку пакетов AmneziaWG для всех устройств.

A script has been added to the repository that parses data on supported platforms from the OpenWRT page and automatically starts building AmneziaWG packages for all devices.

## Выбор пакетов для своего устройства

## Selecting packages for your device

Определить `target` и `subtarget` вашего устройства. Далее перейти на страницу релиза, соответствующего вашей версии OpenWRT, затем поиском по странице (Ctrl+F) найти 3 пакета, название которых оканчивается на `target_subtarget.ipk`, соответствующие вашему устройству.

Determine the `target` and `subtarget` of your device. Then go to the release page corresponding to your OpenWRT version, then search the page (Ctrl+F) to find 3 packages whose names end in `target_subtarget.ipk`, corresponding to your device.

## Как запустить сборку для всех поддерживаемых устройств

## How to run a build for all supported devices

1) Создать форк этого репозитория
2) Переключиться на вкладку Actions и включить Github actions (по умолчанию для форков они выключены)
3) Затем перейти на вкладку Code => Releases (в правой части экрана) => Draft a new release
4) Нажать Choose a tag и создать новый тег формата vX.X.X, где вместо X.X.X нужно подставить требуемую версию OpenWRT, например, v23.05.4
5) Выбрать в качестве target ветку `master`
6) Ввести Release title
7) Нажать внизу зеленую кнопку Publish release

1) Create a fork of this repository
2) Switch to the Actions tab and enable Github actions (they are disabled for forks by default)
3) Then go to the Code tab => Releases (on the right side of the screen) => Draft a new release
4) Click Choose a tag and create a new tag in the format vX.X.X, where you need to substitute the required OpenWRT version instead of X.X.X, for example, v23.05.4
5) Select the `master` branch as the target
6) Enter Release title
7) Click the green Publish release button at the bottom

## Сборка пакетов под определенную платформу

## Building packages for a specific platform

Как запустить сборку пакетов для определенной платформы можно посмотреть в [инструкции на вики](https://github.com/itdoginfo/domain-routing-openwrt/wiki/Amnezia-WG-Build). Сборка под одно устройство займет около 2 часов.

You can see how to start building packages for a specific platform in the [wiki instructions](https://github.com/itdoginfo/domain-routing-openwrt/wiki/Amnezia-WG-Build). Building for one device will take about 2 hours.

