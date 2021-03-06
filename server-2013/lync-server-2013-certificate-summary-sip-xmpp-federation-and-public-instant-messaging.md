﻿---
title: 'Сводка по сертификации: протокол SIP, федерация XMPP и Public Instant Messaging'
TOCTitle: 'Сводка по сертификации: протокол SIP, федерация XMPP и Public Instant Messaging'
ms:assetid: 933d6351-cfa6-4432-b3ed-1aff3ac92065
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ618372(v=OCS.15)
ms:contentKeyID: 49310527
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Сводка по сертификации: протокол SIP, федерация XMPP и Public Instant Messaging

 

_**Дата изменения раздела:** 2015-03-09_

В качестве сертификатов, необходимых для федерации с Microsoft Lync Server 2013, Lync Server 2010 и Office Communications Server, обычно подходят сертификаты, настраиваемые, запрашиваемые и назначаемые для сервер.

В сертификатах, которые используются для обеспечения связи с партнерами XMPP, требуются дополнительные записи, содержащие сведения о доменах XMPP. Запись, включаемая в сертификат в виде альтернативного имени субъекта (SAN), содержит имя домена, который может участвовать в обмене данными по протоколу XMPP. Домен может представлять собой домен корневого уровня (например, contoso.com), если необходимо включить протокол XMPP для всего домена, или набор дочерних доменов (например, corp.contoso.com, finance.contoso.com), если протокол XMPP включается для подмножества пользователей.

При настройке сертификатов для общедоступных услуг обмена мгновенными сообщениями следует учитывать, что нет никаких различий с другими типами федерации SIP или даже со стандартными сертификатами сервер, за исключением службы America Online (AOL), для которой необходимо, чтобы в сертификате или сертификатах (в случае использования пул) также содержалось расширенное использование ключа (EKU) клиента. EKU клиента — это дополнение к сертификату и часть общедоступного внешнего сертификата, который назначен серверу сервер.

Чтобы убедиться, что ваше развертывание сервер соответствует требованиям к сертификатам, ознакомьтесь с разделами, перечисленными в разделе **См. также**.



<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Компонент</th>
<th>Имя субъекта</th>
<th>Дополнительные имена субъектов (SAN)</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Внешняя пограничная служба/пограничная служба доступа</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>sip.contoso.com</p>
<p>webcon.contoso.com</p>
<p>contoso.com</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Для обслуживания пространства имен XMPP contoso.com</td>
</tr>
</tbody>
</table>

</div>
<p>sip.fabrikam.com</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Для поддержки пространства имен SIP fabrikam.com</td>
</tr>
</tbody>
</table>

</div>
<p>fabrikam.com</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Для поддержки пространства имен XMPP fabrikam.com</td>
</tr>
</tbody>
</table>

</div></td>
<td><p>Сертификат должен быть выдан общедоступным центром сертификации и иметь расширенное использование ключа &quot;клиент&quot; и &quot;сервер&quot;, если необходимо настроить взаимодействие с общедоступной системой обмена сообщениями AOL. Сертификат назначается внешним интерфейсам сервер:</p>
<ul>
<li><p>доступа</p></li>
<li><p>веб-конференций</p></li>
<li><p>аудио- и видеоконференций</p></li>
</ul>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Фактически сертификат не назначается пограничному серверу аудио- и видеоданных. Безопасным обменом данных и проверкой подлинности управляет служба Media Relay Authentication Service (MRAS). Служба MRAS использует сертификат, назначенный внутреннему интерфейсу сервер.</td>
</tr>
</tbody>
</table>

</div>
<p>Обратите внимание, что альтернативные имена субъектов добавляются в сертификат автоматически на основании ваших определений в построителе топологий. Вы по мере необходимости добавляете записи альтернативных имен субъектов для дополнительных доменов SIP и другие записи, поддержка которых необходима. Имя субъекта реплицируется в альтернативное имя субъекта и должно присутствовать для обеспечения правильной работы.</p></td>
</tr>
</tbody>
</table>


## См. также

#### Задачи

[Пример конфигурации XMPP в Lync Server 2013 — федерация XMPP с Google Talk](lync-server-2013-example-xmpp-configuration-–-xmpp-federation-with-google-talk.md)  

#### Концепции

[Планирование сертификатов пограничного сервера в Lync Server 2013](lync-server-2013-plan-for-edge-server-certificates.md)  
[Сводка по сертификатам — единая консолидированная пограничная топология с закрытыми IP-адресами и трансляцией сетевых адресов в Lync Server 2013](lync-server-2013-certificate-summary-single-consolidated-edge-with-private-ip-addresses-using-nat.md)  
[Сводка по сертификатам — единая консолидированная пограничная топология с общедоступными IP-адресами в Lync Server 2013](lync-server-2013-certificate-summary-single-consolidated-edge-with-public-ip-addresses.md)  
[Сводка по сертификатам — масштабируемая консолидированная пограничная топология, балансировка нагрузки на DNS с закрытыми IP-адресами и трансляцией сетевых адресов в Lync Server 2013](lync-server-2013-certificate-summary-scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md)  
[Сводка по сертификатам — масштабируемая консолидированная пограничная топология, балансировка нагрузки на DNS с общедоступными IP-адресами в Lync Server 2013](lync-server-2013-certificate-summary-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md)  
[Сводка по сертификатам — масштабируемая консолидированная пограничная топология с аппаратными балансировщиками нагрузки в Lync Server 2013](lync-server-2013-certificate-summary-scaled-consolidated-edge-with-hardware-load-balancers.md)

