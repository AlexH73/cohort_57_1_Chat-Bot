# Чат-Бот группы cohort 57.1 AIT-TR

Групповая работа над проектом Чат-Бот.

Работаем над проектом вместе, обновляем скрипт по мере прохождения новых тем.

## Описание скрипта

Этот скрипт представляет собой простой текстовый интерфейс для оформления заказов в заведении общепита. Он позволяет пользователю выбрать блюдо из нескольких категорий, добавить к нему добавки и просмотреть итоговый заказ с общей суммой.

## Возможности

*   Поддержка нескольких языков (русский, английский, немецкий).
*   Выбор блюд из различных категорий.
*   Выбор добавок к блюдам.
*   Просмотр итогового заказа с ценами.
*   Возможность изменения/удаления блюд из заказа перед его подтверждением.
*   Интуитивно понятный текстовый интерфейс.

## Особенность

Главной особенностью скрипта является его мультиязычность и структурированная система хранения данных о блюдах и добавках, что позволяет легко добавлять новые позиции в меню и поддерживать несколько языковых версий приложения без значительных изменений кода. Данные о языках и блюдах хранятся в отдельных JSON файлах, что упрощает редактирование и управление ими.

## Потенциал

Скрипт имеет большой потенциал для дальнейшего развития:

*   **Интеграция с платежными системами:** Добавление возможности оплаты заказа онлайн.
*   **Расширение функционала:** Добавление новых категорий блюд, опций (например, уровень остроты, размер порции), дополнительных функций (например, история заказов, бонусная система).
*   **Разработка графического интерфейса:** Перенос функционала скрипта на более удобный графический интерфейс.
*   **Интеграция с базой данных:** Хранение данных о меню и заказах в базе данных для более эффективного управления.
*   **Использование в реальных условиях:** Развертывание скрипта на сервере или использование в качестве основы для полноценного приложения для приема заказов.

## Заключение

В целом, данный скрипт представляет собой хорошее начало для разработки более сложной системы управления заказами в сфере общепита. Его простота и расширяемость делают его удобным инструментом для экспериментов и дальнейшего развития.

## Файловая структура
Chat-Bot/ 
├── data/ 
│   ├── languages.json
│   └── menu.json 
├── docs/ 
│   └── README.md 
├── tests/ 
├── main.py 
├── ui.py 
├── order_logic.py 
└── utils.py

*   **`data/`:** Содержит файлы с данными (языковые строки и меню) в формате JSON.
*   **`docs/`:** Содержит документацию проекта.
*   **`tests/`:** Папка для хранения юнит-тестов.
*   **`main.py`:** Основной файл запуска приложения.
*   **`ui.py`:** Файл с функциями для работы с пользовательским интерфейсом.
*   **`order_logic.py`:** Файл с функцией `start_order`, управляющей логикой заказа.
*   **`utils.py`:** Файл с вспомогательными функциями.