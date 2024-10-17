# VSHE-Hack-PSB
Блокнот решения с хакатона по ML "ВШЭ ПСБ.Хак", проходившего 22.09.2024

## О хакатоне
Хакатон проходил с 20 по 22 сентября 2024 года от лица ВШЭ при поддержке ПСБ. Был дан набор данных с информацией о клиентах некоторой сети гостиниц (4 гостиницы в 2 регионах). Задачей было прогнозирование отмены бронирования номера - бинарная классификация.
Решение, представленное в ноутбуке, набрало значение 0.7658 по ROC AUC, что выше проходного.

## Постановка задачи
Красивое введение от организаторов:

> Правда ли, что если проанализировать данные по оплатам, бронированиям и отменам для крупной сети гостиниц и попытаться найти скрытые зависимости с датами заезда, формой оплаты и другими признаками, то можно создать новый банковский продукт, который поможет с организацией отдыха для студентов? <br> Посмотрим, смогут ли алгоритмы машинного обучения и искусственного интеллекта ответить на этот вопрос.

На практике:

Данные представляют собой информацию о бронировании номеров различных категорий в разных гостиницах. Гостиницы с номерами 1 и 2 - один регион РФ, с номерами 3 и 4 - другой регион РФ.
<br>
Задача: предсказать отмену бронирования (бинарная классификация).
<br>
Структура данных следующая:
<br>
* № брони - идентификатор брони <br>
* Номеров - количество номеров в бронировании <br>
* Стоимость - стоимость номеров в рублях <br>
* Внесена предоплата - сумма внесенной предоплаты <br>
* Способ оплаты - один из 12 способов оплаты <br>
* Дата бронирования - дата бронирования с точностью до минуты <br>
* Дата отмены - дата отмены бронирования с точностью до минуты, если было <br>
* Заезд - дата заезда с точностью до дня <br>
* Ночей - количество ночей <br>
* Выезд - дата выезда с точностью до дня <br>
* Источник - онлайн-канал продаж <br>
* Статус брони - один из 5 статусов <br>
* Категория номера - описание категории номера. Если бронировалось несколько номеров, то идет сплошное описание с нумерацией. <br>
* Гостей - число гостей <br>
* Гостиница - номер гостиницы <br>

Целевое поле - Дата отмены: если поле заполнено, то это
соответствует целевому значению 1, иначе - О. Статусы в поле Статус брони уточняют состояние и носят справочный характер (но могут помочь при построении модели).
<br>
Метрика качества - ROC AUC.
<br>
