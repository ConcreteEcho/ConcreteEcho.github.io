---
title: Bluetooth - no default controller available
description: Первый сюрприз от linux с bluetooth
slug: bluetooth-no-default-controller
date: 2024-06-08 07:00:00+0000
math: false

categories:
    - til

tags:
    - Linux

draft: false
---

## Bluetooth - no default controller

Суть проблемы - после сна компьютер не видит bluetooth адаптер.
В моем случае это Intel AX210.

Как это выглядит в живую:

Команда

```shell
bluetoothctl info
```

Дает такой ответ:

```text
Missing device address argument
No default controller available
```

Соответственно, ни одно bluetooth устройство не может быть обнаружено.

## Решение

Не элегантное решение - перезагрузка компьюетра.
После перезагрузки модуль bluetooth работает как и должен.

Решение простое и элегантное - выгрузить и загрузить модуль ядра `btusb`:

```shell
sudo modprobe -r btusb
sudo modprobe btusb
bluetoothctl power on
```

Результат - `Changing power on succeeded`, и теперь bluetooth устройства
обнаруживаются и могут быть подключены.
