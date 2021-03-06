﻿---
title: 'Lync Server 2013: планирование емкости для парковки вызовов'
TOCTitle: Планирование емкости для парковки вызовов
ms:assetid: 75520310-760a-4b1b-bcc1-4d724d13f87a
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg416493(v=OCS.15)
ms:contentKeyID: 49310204
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Планирование емкости для парковки вызовов в Lync Server 2013

 

_**Дата изменения раздела:** 2015-03-09_

В следующей таблице описывается пользовательская модель Приостановка вызовов, которую можно взять за основу при определении требований к планированию мощности.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>При планировании мощности аварийного восстановления для парных пулов необходимо учитывать, что каждый пул, входящий в состав парного пула, должен обрабатывать рабочие нагрузки служб Приостановка вызовов в обоих пулах.</td>
</tr>
</tbody>
</table>


### Пользовательская модель парковки вызовов

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Показатель</th>
<th>Для каждого переднего плана (содержит 8 серверов переднего плана)</th>
<th>Для каждого Сервер Standard Edition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Скорость парковки</p></td>
<td><p>8 вызов в минуту</p></td>
<td><p>1 вызов в минуту</p></td>
</tr>
<tr class="even">
<td><p>Скорость извлечения паркованных вызовов</p></td>
<td><p>8 вызов в минуту</p></td>
<td><p>1 вызов в минуту</p></td>
</tr>
<tr class="odd">
<td><p>Среднее время парковки</p></td>
<td><p>60 с</p></td>
<td><p>60 с</p></td>
</tr>
</tbody>
</table>

