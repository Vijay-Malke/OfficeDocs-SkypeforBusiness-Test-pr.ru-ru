﻿---
title: Конфигурация страницы присоединения к собранию
TOCTitle: Конфигурация страницы присоединения к собранию
ms:assetid: a87319b7-3124-4262-8f9d-18138870ee2d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ205145(v=OCS.15)
ms:contentKeyID: 49310783
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Конфигурация страницы присоединения к собранию

 

_**Дата изменения раздела:** 2015-03-09_

Когда пользователь переходит по ссылке на собрание в приглашении на собрание, страница присоединения к собранию определяет, установлен ли клиент Lync 2013 на компьютере пользователя. Если клиент уже установлен, он открывается и выполняет присоединение к собранию. В противном случае по умолчанию открывается версия 2013 веб-приложения Microsoft Lync Web App.

Вы можете изменить поведение страницы присоединения к собранию, если вы хотите разрешить пользователям присоединяться к собраниям с помощью Office Communicator 2007 R2 или оператор Lync 2010. Соответствующие параметры конфигурации были удалены из панели управления Lync Server 2013, но вы можете настроить их с помощью командлета CsWebServiceConfiguration.

### Параметры командлета CsWebServiceConfiguration для настройки страницы присоединения к собранию

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Параметр командлета CsWebServiceConfiguration</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ShowJoinUsingLegacyClientLink</p></td>
<td><p>Если задано значение True, пользователям, присоединяющимся к собранию с помощью клиентского приложения, отличного от Lync, будет дана возможность присоединиться к собранию с помощью Office Communicator 2007 R2. Значение по умолчанию – False.</p></td>
</tr>
<tr class="even">
<td><p>ShowAlternateJoinOptionsExpanded</p></td>
<td><p>Если задано значение True, пользователям будут автоматически показаны дополнительные варианты присоединения к сетевой конференции (например, с помощью Office Communicator 2007 R2). Если параметр имеет значение False (значение по умолчанию), эти параметры будут доступны, но пользователям придется самостоятельно открывать список параметров.</p></td>
</tr>
</tbody>
</table>


## Настройка страницы присоединения к собранию с помощью командная консоль Lync Server 2013

1.  Откройте командная консоль Lync Server 2013. В меню **Пуск** последовательно выберите пункты **Все программы** , **Microsoft Lync Server 2013** и **Командная консоль Lync Server**.

2.  выполнить следующий командлет:
    
        Get-CsWebServiceConfiguration
    
    Этот командлет возвращает параметры конфигурации веб-службы.

3.  Выполните следующую команду, задав для параметров значения True или False на свой выбор (подробные сведения о параметрах этого командлета см. в документации по командная консоль Lync Server 2013).
    
        Set-CsWebServiceConfiguration -Identity global -ShowJoinUsingLegacyClientLink $True

