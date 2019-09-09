# Задания для PHP / JS программистов

Большинство заданий - это работа с платформой [X-Cart 5](https://www.x-cart.com/download.html) и создание [модуля](https://devs.x-cart.com/getting_started/creating-module.html) под неё. При выполнении тебе поможет наша [девелоперская документация](https://devs.x-cart.com) и [мерчантский мануал](https://kb.x-cart.com). 

Саму платформу нужно скачать и установить на типовой LAMP-стек по инструкции https://kb.x-cart.com/general_setup/installation/installation_guide.html. После этого желательно включить в файле `etc/config.php` девелоперский режим, позволяющий применять изменения в коде без пересборки кэша, для этого нужно найти или добавить опцию:

```
[performance]
developer_mode = On
```

В качестве результата можно прислать [запакованный модуль](https://devs.x-cart.com/getting_started/creating-module.html#packing-up-your-module) на join@x-cart.com. Если появятся вопросы - можно писать или в [Issues](https://github.com/xcart/jobs/issues), или на daemos@x-cart.com.

Собственно, вот и сами задания:

## Интеграция VK Pixel 

Нужно написать модуль, который позволяет включить [ретаргетинг Вконтакте](https://vk.com/ads?act=office_help&oid=-19542789&p=%D0%9F%D0%B8%D0%BA%D1%81%D0%B5%D0%BB%D1%8C_%D0%B4%D0%BB%D1%8F_%D0%B4%D0%B8%D0%BD%D0%B0%D0%BC%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B3%D0%BE_%D1%80%D0%B5%D1%82%D0%B0%D1%80%D0%B3%D0%B5%D1%82%D0%B8%D0%BD%D0%B3%D0%B0) в магазине.

>Сценарий работы пользователя
>1) Сначала генерирует код пикселя в кабинете управления таргетированной рекламой Вконтакте;	
>2) Затем добавляет сгенерированный код в окно настроек модуля и сохраняет его.

Модуль "встраивает" добавленный код пикселя в исходный код магазина на все страницы. Интерфейс настроек модуля содержит следующие элементы (визуальный вид по аналогии с любым другим модулем)

1. Логотип Вконтакте	
2. Заголовок "Настройки пикселя"	
3. Инструкция для пользователя (Шаг 1, Шаг 2,...)	
4. Текстовое поле для вставки кода пикселя	
5. Кнопка "Сохранить"	

Для тестов можно взять следующий код пикселя:

```
<script type="text/javascript">!function(){var t=document.createElement("script");t.type="text/javascript",t.async=!0,t.src="https://vk.com/js/api/openapi.js?162",t.onload=function(){VK.Retargeting.Init("VK-RTRG-291604-h5EHd"),VK.Retargeting.Hit()},document.head.appendChild(t)}();</script><noscript><img src="https://vk.com/rtrg?p=VK-RTRG-291604-h5EHd" style="position:fixed; left:-999px;" alt=""/></noscript>
```

_По документации ВК для использования пикселя необходим домен и сайт в интернете, поскольку пиксель не работает с локальным сервером. Но в рамках задачи для проверки модуля достаточно будет убедиться, что код пикселя корректно вставляется в код страниц и происходит запрос к серверу vk._

## Wishlist

Нужно написать тестовый модуль для фичи списка желаний (вишлиста) покупателя. У зарегистрированного пользователя должна быть возможность добавить товар в список желаний со страницы товара (сделайте кнопку рядом с кнопкой “Добавить в корзину”).

При успешном добавлении должен появится всплывающий лейбл о том, что товар добавлен в список желаний (пример подобного лейбла здесь: https://devs.x-cart.com/basics/forms.html#adjusting-controller). 

На странице должна быть ссылка, ведущая на список желаний. Также должна быть отдельная страница списка желаний (https://devs.x-cart.com/basics/creating_new_page.html#creating-page-in-customer-area). На ней нужно просто через верстку отобразить список добавленных товаров.

Бонусные очки за:
- возможность удалить товар из списка желаний
- смену состояния кнопки “Добавить в вишлист” при добавлении

## Product recommendations

Написать модуль, который будет выводить цитаты о рекомендациях от известных источников (с ссылкой на источник) на странице товара под кратким описанием (над ценой и опциями).

Цитаты должны быть оформлены примерно как на картинке:

![Recommends](https://raw.githubusercontent.com/xcart/jobs/master/assets/product_recommends_1.png)

Цитаты будут заполняться администратором на отдельным табе страницы редактирования продукта в админке через [стандартный список с колонками](https://devs.x-cart.com/basics/itemslist_in_admin_area/) (Текст цитаты, Ссылка на источник) и кнопкой удаления.

Бонусные очки за возможность выбрать и отключить отображение некоторых цитат.