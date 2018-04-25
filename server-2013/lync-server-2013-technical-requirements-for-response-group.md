﻿---
title: 'Lync Server 2013: технические требования для групп ответа'
TOCTitle: Технические требования для групп ответа
ms:assetid: 477488bd-124f-437b-9327-732a0d7271ca
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ204863(v=OCS.15)
ms:contentKeyID: 49309640
ms.date: 07/21/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Технические требования для групп ответа в Lync Server 2013

 

_**Дата изменения раздела:** 2016-12-08_

В этом разделе описываются следующие типы технических требований для "Группа ответа".

  - Требования к оборудованию

  - Требования к программному обеспечению

  - Требования к портам

  - Требования к аудиофайлам

  - Требования к средствам настройки конфигурации группы ответа

## Требования к оборудованию

"Группа ответа" предъявляет те же требования к оборудованию, что и переднего плана. Дополнительные сведения о требованиях к оборудованию см. в разделе [Аппаратные серверные платформы для Lync Server 2013](lync-server-2013-server-hardware-platforms.md) документации по обеспечению поддержки.

## Требования к программному обеспечению

"Группа ответа" предъявляет те же требования к операционной системе и обязательным программным компонентам, что и переднего плана. Дополнительные сведения о требованиях к программному обеспечению см. в разделе [Поддержка сервера и средств в операционной системе в Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md) документации по обеспечению поддержки.

Если вы используете файлы Windows Media Audio (.wma) для оповещений и музыки приложения группы ответа, на всех серверах переднего плана или серверах Standard Edition с приложением "Группа ответа" необходимо установить Windows Media Format Runtime для серверов под управлением Windows Server 2008 R2 или Microsoft Media Foundation для серверов под управлением Windows Server 2012 или Windows Server 2012 R2. Для Windows Server 2008 R2 Windows Media Format Runtime устанавливается как часть Windows Desktop Experience.

Дополнительные сведения о требованиях к звуку см. ниже в подразделе "Требования к звуковым файлам".

## Требования к портам

Приложение "Группа ответа" использует следующие порты:

  - **Порт 5071** – используется для запросов прослушивания SIP.

  - **порт 8404** – используется для межсерверного взаимодействия.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Этот порт используется для службы Match Making и требуется при развертывании приложения &quot;Группа ответа&quot; в пул с несколькими серверами переднего плана.</td>
    </tr>
    </tbody>
    </table>


<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Эти порты являются установками по умолчанию, которые можно изменить с помощью командлета <strong>Set-CsApplicationServer</strong>. Сведения об этом командлете см. в документации по командной консоли Командная консоль Lync Server.</td>
</tr>
</tbody>
</table>


## Требования к аудиофайлам

Приложение "Группа ответа" поддерживает форматы файлов WAV и WMA для сообщений группы ответа, музыки для воспроизведения при удержании звонка или вопросов интерактивного автоответчика.

Для использования формата файлов WMA требуется установка Windows Media Format Runtime на серверы переднего плана с Windows Server 2008 R2 и Windows Server 2008. Дополнительные сведения см. выше в подразделе "Требования к программному обеспечению".

## Поддерживаемые форматы файлов WAV

Все файлы WAV должны удовлетворять следующим требованиям:

  - 8-разрядный или 16-разрядный файл

  - Формат линейной импульсно-кодовой модуляции, A-Law или mu-Law

  - Моно или стерео

  - 4 МБ или меньше

Для обеспечения наилучшей производительности файлов WAV рекомендуется использовать монофонический 16-разрядный файл WAV с частотой 16 кГц.

## Поддерживаемые форматы файлов WMA

Если вы используете файл WMA рекомендуется применять низкие скорости и проверить производительность системы под нагрузкой.

Преобразовать файл в формат WMA вы можете с помощью Microsoft Expression Encoder 4. Чтобы загрузить Expression Encoder 4, см. страницу [http://go.microsoft.com/fwlink/?linkid=202843\&clcid=0x419](http://go.microsoft.com/fwlink/?linkid=202843%26clcid=0x419).

## Требования к средствам настройки группы ответа

Средство настройки группы ответа поддерживает сочетания операционной системы и веб-браузера, перечисленные в следующей таблице.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Поддерживаются 32-разрядная или 64-разрядная версии операционных систем. Поддерживаются только 32-разрядные версии Internet Explorer.</td>
</tr>
</tbody>
</table>


### Поддерживаемые операционные системы и веб-браузеры

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Операционная система</th>
<th>Веб-браузер</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows Vista с пакетом обновления 2 (SP2)</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8 (основной режим)</p>
<p>Internet Explorer 9 (основной режим)</p></td>
</tr>
<tr class="even">
<td><p>Windows 7</p>
<p>Windows 7 с пакетом обновления 1 (SP1)</p></td>
<td><p>Internet Explorer 8 (основной режим)</p>
<p>Internet Explorer 9 (основной режим)</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2008 с пакетом обновления 2 (SP2)</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8 (основной режим)</p>
<p>Internet Explorer 9 (основной режим)</p></td>
</tr>
<tr class="even">
<td><p></p>
<p></p>
<p></p>
<p>Windows Server 2008 R2</p>
<p>Windows Server 2008 R2 с пакетом обновления 1 (SP1)</p></td>
<td><p>Internet Explorer 8 (основной режим)</p>
<p>Internet Explorer 9 (основной режим)</p></td>
</tr>
</tbody>
</table>


## Консоль агента группы ответа

Консоль агента поддерживает сочетания операционной системы и веб-браузера, перечисленные в следующей таблице.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Поддерживаются 32-разрядная или 64-разрядная версии операционных систем. Поддерживаются только 32-разрядные версии Internet Explorer.</td>
</tr>
</tbody>
</table>


### Поддерживаемые операционные системы и веб-браузеры

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Операционная система</th>
<th>Веб-браузер</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows Vista с пакетом обновления 2 (SP2)</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8 (основной режим)</p>
<p>Internet Explorer 9 (основной режим)</p></td>
</tr>
<tr class="even">
<td><p>Windows 7</p>
<p>Windows 7 с пакетом обновления 1 (SP1)</p></td>
<td><p>Internet Explorer 8 (основной режим)</p>
<p>Internet Explorer 9 (основной режим)</p>
<p>Firefox 10.0</p>
<p>Chrome 18.0</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2008 с пакетом обновления 2 (SP2)</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8 (основной режим)</p>
<p>Internet Explorer 9 (основной режим)</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2008 R2</p>
<p>Windows Server 2008 R2 с пакетом обновления 1 (SP1)</p></td>
<td><p>Internet Explorer 8 (основной режим)</p>
<p>Internet Explorer 9 (основной режим)</p>
<p>Firefox 10.0</p>
<p>Chrome 18.0</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td></td>
</tr>
</tbody>
</table>
