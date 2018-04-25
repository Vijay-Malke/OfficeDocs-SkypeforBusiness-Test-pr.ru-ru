﻿---
title: Регистрация пользователей для проверки подлинности с помощью смарт-карты
TOCTitle: Регистрация пользователей для проверки подлинности с помощью смарт-карты
ms:assetid: a6445a83-a94b-423f-ba2a-12b5f84c5d75
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn308570(v=OCS.15)
ms:contentKeyID: 56270600
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Регистрация пользователей для проверки подлинности с помощью смарт-карты

 

_**Дата изменения раздела:** 2016-12-08_

Зарегистрировать пользователей для проверки подлинности с помощью смарт-карты можно двумя способами. Простой вариант — поручить пользователям самостоятельно зарегистрироваться с помощью функции регистрации через Интернет, в то время как сложный связан с использованием агента регистрации. В этом разделе рассматривается процедура самостоятельной регистрации для использования сертификатов смарт-карт.

Дополнительные сведения о регистрации в качестве агента регистрации от имени пользователей см. в статье "Регистрация для использования сертификатов от имени других пользователей" (на английском языке) на странице [http://go.microsoft.com/fwlink/p/?LinkID=313367](http://go.microsoft.com/fwlink/p/?linkid=313367).

## Порядок регистрации пользователей для проверки подлинности с помощью смарт-карты

1.  Войдите на рабочую станцию Windows 8 с использованием учетных данных пользователя Lync.

2.  Запустите браузер Internet Explorer.

3.  Откройте страницу **регистрации сертификатов через Интернет** (например, https://MyCA.contoso.com/certsrv).
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>В браузере Internet Explorer 10 эту страницу, возможно, потребуется открыть в режиме совместимости.</td>
    </tr>
    </tbody>
    </table>


4.  На странице **приветствия** выберите пункт **Запросить сертификат**.

5.  Далее выберите пункт **Расширенный запрос**.

6.  Выберите команду **Создать и выдать запрос к этому ЦС**.

7.  В разделе **Шаблон сертификата** выберите вариант **Пользователь смарт-карты** и заполните расширенный запрос на получение сертификата указанными ниже значениями.
    
      - В разделе **Параметры ключа** задайте перечисленные ниже значения.
        
          - Установите переключатель **Создать новый набор ключей**.
        
          - Для параметра **Поставщик служб шифрования** выберите значение **Microsoft Base Smart Card Crypto Provider**.
        
          - Для параметра **Использование ключа** выберите значение **Exchange** (единственное доступное).
        
          - Для параметра **Размер ключа** введите значение **2048**.
        
          - Убедитесь, чтоб выбран параметр **Автоматическое имя контейнера ключа**.
        
          - Оставьте остальные флажки снятыми.
    
      - В разделе **Дополнительные параметры** задайте перечисленные ниже значения.
        
          - Для параметра **Формат запроса** выберите вариант **CMC**.
        
          - Для параметра **Хэш-алгоритм** выберите вариант **sha1**.
        
          - Для параметра **Понятное имя** введите значение **Сертификат смарт-карты**.

8.  Если используется физическое устройство считывания смарт-карт, вставьте смарт-карту в устройство.

9.  Нажмите кнопку **Отправить**, чтобы отправить запрос на получение сертификата.

10. Когда будет предложено, введите ПИН-код, использовавшийся при создании виртуальной смарт-карты.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Значение ПИН-кода виртуальной смарт-карты по умолчанию — 12345678.</td>
    </tr>
    </tbody>
    </table>


11. После выдачи сертификата выберите команду **Установить этот сертификат**, чтобы завершить процесс регистрации.
    
    <table>
    <colgroup>
    <col style="width: 100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если запрос на получение сертификата завершается неудачей с ошибкой &quot;Этот веб-браузер не поддерживает создание запросов на сертификат&quot;, устранить эту ошибку можно тремя способами.
    <ol>
    <li><p>Включите режим совместимости в браузере Internet Explorer.</p></li>
    <li><p>Включите параметр &quot;Включить параметры интрасети&quot; в браузере Internet Explorer.</p></li>
    <li><p>Выберите параметр &quot;Выбрать уровень безопасности по умолчанию для всех зон&quot; на вкладке &quot;Безопасность&quot; в меню параметров Internet Explorer.</p></li>
    </ol></td>
    </tr>
    </tbody>
    </table>
