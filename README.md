# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнил:
- Лепинских Максим Игоревич
- РИ220943

Отметка о выполнении заданий:

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Реализация выполнения задания. Визуализация результатов выполнения.
- Задание 2.
- Реализация выполнения задания. Визуализация результатов выполнения.
- Задание 3.
- Реализация выполнения задания. Визуализация результатов выполнения.
- Выводы.
- ✨Magic ✨

## Цель работы
Научиться передавать в Unity данные из Google Sheets с помощью Python.

## Задание 1
### Выберите одну из компьютерных игр, приведите скриншот её геймплея и краткое описание концепта игры. Выберите одну из игровых переменных в игре (ресурсы, внутри игровая валюта, здоровье персонажей и т.д.), опишите её роль в игре, условия изменения / появления и диапазон допустимых значений. Постройте схему экономической модели в игре и укажите место выбранного ресурса в ней.
![image](https://github.com/MAXBAF1/DA-in-GameDev-lab2/assets/63009846/e3b498e4-5da1-4238-937d-728d795659d1)
#### Counter Strike
Многопользовательская компьютерная игра в жанре шутера от первого лица, разработанная и выпущенная для Windows американской компанией Valve.
#### Игровая переменная
Игровая валюта используется для покупки оружия, брони и гранат. Игроки зарабатывают деньги путем убийств врагов, выполнения задач и завершения раундов. Сумма денег зависит от успеха в предыдущих раундах, и они варьируются от 0 до нескольких тысяч долларов. Командное планирование и управление деньгами играют важную роль в достижении успеха в игре.
#### Схема модели игровой валюты.
![image](https://github.com/MAXBAF1/DA-in-GameDev-lab2/assets/63009846/5c14132c-d650-45b8-b0db-15811e794de1)

## Задание 2
### С помощью скрипта на языке Python заполните google-таблицу данными, описывающими выбранную игровую переменную в выбранной игре (в качестве таких переменных может выступать игровая валюта, ресурсы, здоровье и т.д.). Средствами google-sheets визуализируйте данные в google-таблице (постройте график, диаграмму и пр.) для наглядного представления выбранной игровой величины.
#### Python скрипт
Этот скрипт создает и отслеживает количество денег в игре. Он проводит 12 игр и в каждой игре случайным образом изменяет количество денег в соответствии с правилами:
- За убийство игрок получает 100 долларов.
- За успешное размещение бомбы игрок получает 200 долларов.
- За смерть игрок теряет 500 долларов.

Результаты каждой игры записываются в Google Sheets.

```py
import gspread
import random
gc = gspread.service_account(filename='ad-gamedev-f8188b326391.json')
sh = gc.open("AD GameDev")
money = 1000
money_for_kill = 100
money_for_bomb = 200
die_price = -500
prices = [money_for_kill, money_for_bomb, die_price]
games = list(range(1,13))
i = 0
while i <= len(games):
    action = prices[random.randint(0, 2)]
    new_money = money + action
    if (new_money >= 0):
        i += 1
        money = new_money
        sh.sheet1.update(('A' + str(i)), i)
        sh.sheet1.update(('B' + str(i)), new_money)
        sh.sheet1.update(('C' + str(i)), action)
        print(money)
```
#### Визуализация
![image](https://github.com/MAXBAF1/DA-in-GameDev-lab2/assets/63009846/26e31034-5a02-4766-b4ba-a8fbbc2e3921)

## Задание 3
### Настройте на сцене Unity воспроизведение звуковых файлов, описывающих динамику изменения выбранной переменной. Например, если выбрано здоровье главного персонажа вы можете выводить сообщения, связанные с его состоянием.
Вы можете загрузить файл сцены и ресурсами из этого репозитория, либо перейти по следующей ссылке для его скачивания: https://github.com/MAXBAF1/DA-in-GameDev-lab2/blob/main/ad-lab2.unitypackage

## Выводы

Получил навык создания начальных настроек игры и автоматической записи их в Google Sheets с использованием Python-скрипта. Кроме того, освоил метод, который позволяет Unity читать данные из этих таблиц и, основываясь на этой информации, воспроизводить звуковые эффекты или выполнять другие действия в игре.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
