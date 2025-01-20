# Чат-Бот группы cohort 57.1 AIT-TR
Групповая работа над проектом Чат-Бот.

Работаем над проектом вместе, обновляем скрипт по мере прохождения новых тем.

Думаю имеет смысл разбить скрипт на три файла - языковой, список блюд и сам скрипт. 

## Функции

1.  **`choose_language()`**
    *   **Сущность:** Выводит меню выбора языка и возвращает выбранный язык в виде строки.
    *   **Аргументы:** Нет.
    *   **Возвращает:**
        *   `"en"`: Если выбран английский язык.
        *   `"ru"`: Если выбран русский язык.
        *   `"de"`: Если выбран немецкий язык.

2.  **`choose_item(items, category_name, lang, selected_language, show_back=True)`**
    *   **Сущность:** Выводит меню элементов (блюд/товаров) и обрабатывает выбор пользователя.
    *   **Аргументы:**
        *   `items` (list): Список словарей, содержащий элементы меню.
        *   `category_name` (str): Название категории (используется для отображения заголовка).
        *   `lang` (dict): Словарь с текстовыми строками для выбранного языка.
        *   `selected_language` (str): Выбранный язык.
        *   `show_back` (bool, *optional*): Показывать ли опцию "9. Назад". По умолчанию `True`.
    *   **Возвращает:**
        *   `dict`: Словарь с информацией о выбранном элементе (`name`, `price`, `extras`), если пользователь выбрал элемент.
        *   `None`: Если пользователь выбрал "0" (пропустить) и `show_back` равен `False`.
        *   `"back"`: Если пользователь выбрал "9" (назад) и `show_back` равен `True`.

3.  **`choose_extras(extras, lang, selected_language, max_extras=0)`**
    *   **Сущность:** Выводит меню добавок и обрабатывает выбор пользователя.
    *   **Аргументы:**
        *   `extras` (list): Список словарей, представляющий доступные добавки.
        *   `lang` (dict): Словарь с текстовыми строками для выбранного языка.
        *   `selected_language` (str): Выбранный язык.
        *    `max_extras` (int, *optional*): Максимальное количество добавок, которое можно выбрать. По умолчанию `0` (без ограничений).
    *   **Возвращает:**
        *   `list`: Список словарей выбранных добавок.

4.  **`confirm_order(order, lang, selected_language)`**
    *   **Сущность:** Выводит сводку заказа и общую стоимость.
    *   **Аргументы:**
        *   `order` (list): Список словарей, представляющий заказ (каждый словарь содержит информацию о выбранном элементе).
        *   `lang` (dict): Словарь с текстовыми строками для выбранного языка.
        *   `selected_language` (str): Выбранный язык.
    *   **Возвращает:** Нет.

5.  **`change_order(order, lang, selected_language)`**
    *   **Сущность:** Позволяет пользователю изменить заказ (удалить блюдо или перейти к добавлению блюда).
    *   **Аргументы:**
        *   `order` (list): Список словарей, представляющий заказ.
        *   `lang` (dict): Словарь с текстовыми строками для выбранного языка.
        *   `selected_language` (str): Выбранный язык.
    *  **Возвращает:**
        *   `list`: Измененный список словарей, представляющий заказ.

6.  **`start_order(selected_language, order=None)`**
    *   **Сущность:** Управляет основным циклом заказа, предлагая пользователю категории блюд и обрабатывая их выбор.
    *   **Аргументы:**
        *   `selected_language` (str): Выбранный язык.
        *    `order` (list, *optional*): Список словарей, представляющий текущий заказ. По умолчанию `None`.
    *   **Возвращает:** Нет.

## Переменные

**Глобальные переменные:**

1.  **`LANGUAGES`**
    *   **Сущность:** Словарь, содержащий текстовые строки для разных языков.
    *   **Тип:** `dict`
    *   **Структура:**
        *   Ключи: Строки, представляющие языковые коды (например, `"ru"`, `"en"`, `"de"`).
        *   Значения: Словари, где:
            *   Ключи: Строки, представляющие ключи для доступа к текстовым фразам (например, `"welcome"`, `"main_menu"`).
            *   Значения: Строки, представляющие текстовые фразы на соответствующем языке.

2.  **`CATEGORIES`**
    *   **Сущность:** Словарь, содержащий информацию о категориях товаров/блюд.
    *   **Тип:** `dict`
    *   **Структура:**
        *   Ключи: Строки, представляющие идентификаторы категорий (например, `"main_course"`, `"salad"`).
        *   Значения: Словари, где:
            *   `"name"` (dict): Словарь с названиями категории на разных языках (структура аналогична `LANGUAGES`).
            *   `"items"` (list): Список словарей, представляющих элементы (товары/блюда) в этой категории. Каждый элемент имеет структуру:
                *   `"name"` (dict): Словарь с названиями элемента на разных языках.
                *   `"price"` (float): Цена элемента.
                *   `"extras"` (list, *optional*): Список словарей, представляющих добавки к элементу. Каждый элемент имеет структуру:
                    *   `"name"` (dict): Словарь с названиями добавки на разных языках.
                    *   `"price"` (float): Цена добавки.
                *   `"max_extras"` (int, *optional*): Максимальное количество добавок, которое можно выбрать для этого элемента.

**Переменные внутри функций:**

1.  **`choose_language()`**
    *   `choice` (str): Строка, содержащая ввод пользователя (выбранный язык).

2.  **`choose_item(items, category_name, lang, selected_language, show_back=True)`**
    *   `items` (list): Список словарей, представляющий элементы меню.
    *   `category_name` (str): Название категории.
    *   `lang` (dict): Словарь с текстовыми строками для выбранного языка.
    *   `selected_language` (str): Выбранный язык.
    *    `show_back` (bool): Определяет, показывать ли опцию "9. Назад".
    *   `i` (int): Индекс текущего элемента в цикле.
    *   `item` (dict): Словарь, представляющий текущий элемент меню.
    *   `choice` (str): Строка, содержащая ввод пользователя (выбранный элемент).
    *   `selected_item` (dict): Словарь, представляющий выбранный элемент меню.
     *  `extras` (list): Список словарей, представляющий выбранные добавки для блюда.

3.  **`choose_extras(extras, lang, selected_language, max_extras=0)`**
    *   `extras` (list): Список словарей, представляющий доступные добавки.
    *   `lang` (dict): Словарь с текстовыми строками для выбранного языка.
    *   `selected_language` (str): Выбранный язык.
    *   `max_extras` (int): Максимальное количество добавок, которое можно выбрать
    *   `selected_extras` (list): Список словарей, содержащий выбранные добавки.
    *   `i` (int): Индекс текущей добавки в цикле.
    *   `extra` (dict): Словарь, представляющий текущую добавку.
    *   `choice` (str): Строка, содержащая ввод пользователя (выбранная добавка).

4.  **`confirm_order(order, lang, selected_language)`**
    *   `order` (list): Список словарей, представляющий заказ.
    *   `lang` (dict): Словарь с текстовыми строками для выбранного языка.
    *   `selected_language` (str): Выбранный язык.
    *   `total_price` (float): Общая стоимость заказа.
    *   `i` (int): Индекс текущего элемента в заказе.
    *   `item` (dict): Словарь, представляющий текущий элемент заказа.
    *   `extra` (dict): Словарь, представляющий текущую добавку.

5.  **`change_order(order, lang, selected_language)`**
    *    `order` (list): Список словарей, представляющий заказ.
    *   `lang` (dict): Словарь с текстовыми строками для выбранного языка.
    *   `selected_language` (str): Выбранный язык.
    *   `i` (int): Индекс текущего элемента в заказе.
    *   `item` (dict): Словарь, представляющий текущий элемент заказа.
    *    `choice` (str): Строка, содержащая ввод пользователя (выбранный пункт меню).

6.  **`start_order(selected_language, order=None)`**
    *   `selected_language` (str): Выбранный язык.
    *    `order` (list, *optional*): Список словарей, представляющий текущий заказ.
    *   `lang` (dict): Словарь с текстовыми строками для выбранного языка.
    *    `history` (list): Список для хранения истории заказов
    *   `choice` (str): Строка, содержащая ввод пользователя (выбранная категория или действие).
    *   `category_index` (int): индекс выбранной категории
     *  `category_name` (str): имя выбранной категории
    *   `category` (dict): Словарь, представляющий выбранную категорию.
    *    `dish` (dict): Словарь, представляющий выбранный элемент.

7.  **Основной вход в программу**
    *   `selected_language` (str): Выбранный язык.
