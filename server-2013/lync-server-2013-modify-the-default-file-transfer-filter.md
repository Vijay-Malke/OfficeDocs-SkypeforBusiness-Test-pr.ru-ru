﻿---
title: Изменение фильтра передачи файлов по умолчанию
TOCTitle: Изменение фильтра передачи файлов по умолчанию
ms:assetid: 791774a2-0bb6-4b5b-aeb0-ff69abb170f4
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg521017(v=OCS.15)
ms:contentKeyID: 49310243
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Изменение фильтра передачи файлов по умолчанию

 

_**Дата изменения раздела:** 2012-11-01_

Система Lync Server 2013 предоставляет глобальный фильтр передачи файлов, который блокирует определенные типы файлов во время выполнения в развертывании системы Lync Server 2013 следующих операций с файлами:

  - Запросы на передачу файлов во время бесед с обменом мгновенными сообщениями

  - Отправки и загрузки файлов во время использования функции выдачи в клиенте Office Live Meeting 2007

  - Воспроизведение мультимедиа во время конференций

В зависимости от типов файлов, которые требуется блокировать или разрешать, вы можете использовать для изменения глобального фильтра панель управления Lync Server. Дополнительные сведения о фильтрации передачи файлов см. в разделе [Настройка фильтрации передачи файлов и URL-адресов для обмена мгновенными сообщениями в Lync Server 2013](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md).

## Изменение фильтра передачи файлов по умолчанию

1.  Войдите на любой компьютер во внутреннем развертывании с использованием учетной записи пользователя, назначенной роли CsUserAdministrator или CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой области навигации щелкните пункт **Мгновенные сообщения и присутствие**, а затем **Фильтр файлов**.

4.  На странице **File Filter** (Фильтр файлов) дважды щелкните фильтр **Global** (Глобальный).

5.  В окне **Edit File Filter** (Изменение фильтра файлов) установите флажок **Enable file filter** (Включить фильтр файлов).

6.  В раскрывающемся списке **Передача файлов** выберите пункт **Блокировать все** или **Block specific file types** (Блокировать определенные типы файлов).

7.  При выборе варианта **Блокировать все** перейдите к действию 9.

8.  При выборе варианта **Блокировать определенные типы файлов** выполните следующие действия.
    
    1.  Щелкните **Выбрать**, чтобы изменить список блокируемых расширений файлов по умолчанию.
    
    2.  В окне **Select File Type** (Выбор типа файла) выберите типы файлов, которые требуется блокировать или разрешить, добавив или удалив их расширения из категорий в разделе **File type extensions** (Расширения типов файлов).
    
    3.  Если расширения типов файлов, которые необходимо заблокировать, не отображаются, введите расширение в текстовое поле **Add file type extensions to the list** (Добавить расширения типов файлов в список), а затем нажмите кнопку **Добавить**.
    
    4.  Нажмите кнопку **ОК**.

9.  Щелкните **Исполнить**.

## См. также

#### Задачи

[Настройка фильтрации передачи файлов и URL-адресов для обмена мгновенными сообщениями в Lync Server 2013](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md)  
[Создание нового фильтра передачи файлов для определенного сайта](lync-server-2013-create-a-new-file-transfer-filter-for-a-specific-site.md)  
[Создание нового фильтра URL-адресов для управления гиперссылками в сеансах обмена мгновенными сообщениями](lync-server-2013-create-a-new-url-filter-to-handle-hyperlinks-in-im-conversations.md)  

#### Концепции

[Изменение фильтра URL-адресов по умолчанию](lync-server-2013-modify-the-default-url-filter.md)

