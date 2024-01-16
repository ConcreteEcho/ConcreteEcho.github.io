---
title: Headless. Производительность.
description: Ускоряемся
slug: tekla-headless-p2
date: 2024-03-01 00:00:00+0000
math: false

categories:
    - tekla

tags:
    - headless

image: cover.png

draft: true
---

## BimPublisher vs Headless Tekla

Приведу данные по запуску и открытию Tekla модели из командной строки с использованием bypass (аналог BimPublisher, в таблице указан как BimPublisher) и с помощью Headless Tekla, данные усреднены по показателям 5 прогонов. Через слэш указаны время запуска и использование оперативной памяти.

| Вес .db1 | Комментарий                | BimPublisher   | Headless Tekla |
| -------- | -------------------------- | -------------- | -------------- |
| 10 kB    | Пустая модель              | 180s \| 1.2 GB | 30s \| 100 MB  |
| 60 MB    | КМ на 123 т                | 240s \|        | 40s \|         |
| 100 MB   | КЖ на 1234 м<sup>3<sup/>   | 240s \|        | 50s \|         |
| 250 MB   | КЖ на 100500 м<sup>3<sup/> | 300s \|        | 60s \| 300 MB  |

Видно, что скорость запуска Tekla и открытия модели минимум в 5 раз быстрее, чем та же операция, выполненная BimPublisher.

## Проблемы Headless Tekla

1. режим разработчика
2. процесс не может быть дочерним процессом
3. нельзя сразу запустить в режиме дебага, нужно подцепляться к процессу