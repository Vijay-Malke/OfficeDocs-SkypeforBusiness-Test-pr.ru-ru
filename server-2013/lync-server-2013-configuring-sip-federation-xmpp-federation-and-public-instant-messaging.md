﻿---
title: 'Lync Server 2013: настройка федерации SIP, федерации XMPP и общедоступных служб обмена мгновенными сообщениями'
TOCTitle: Настройка федерации SIP, федерации XMPP и общедоступных служб обмена мгновенными сообщениями
ms:assetid: a6d04f0b-5cb8-4084-a3a2-d501938971f9
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ205134(v=OCS.15)
ms:contentKeyID: 49310759
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Настройка федерации SIP, федерации XMPP и общедоступных служб обмена мгновенными сообщениями в Lync Server 2013

 

_**Дата изменения раздела:** 2015-03-09_

Федерация, подключения к общедоступным службам обмена мгновенными сообщениями и протокол XMPP обуславливают появление нового типа внешних пользователей – федеративных пользователей. Пользователи федеративного развертывания Lync Server или развертывания XMPP имеют доступ к ограниченному набору служб и проходят проверку подлинности во внешней системе. Удаленные же пользователи являются членами вашего развертывания Lync Server и имеют доступ ко всем его службам.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Поддержка служб AOL и Yahoo! завершается в июне 2014 г. Подробные сведения см. в статье <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Поддержка подключения к общедоступным службам обмена мгновенными сообщениями в Lync Server 2013</a>.</td>
</tr>
</tbody>
</table>


Подключения к общедоступным службам обмена сообщениями – это особый тип федерации, который позволяет клиенту Lync Server получать доступ к настроенным общедоступным службам обмена мгновенными сообщениями партнеров с помощью Lync 2013. В настоящее время доступны следующие партнерские службы:

  -   
    America Online

  -   
    Windows Live

  -   
    Yahoo\!;

Конфигурация подключений к общедоступным службам обмена мгновенными сообщениями обеспечивает следующие возможности связи для пользователей Lync:

  - обмен мгновенными сообщениями и сведениями о присутствии;

  - возможность просмотра контактов общедоступной службы обмена мгновенными сообщениями в клиенте Lync;

  - двусторонние текстовые беседы с контактами;

  - звуковые и видеозвонки пользователям Windows Live.

Федерация Lync Server предусматривает наличие соглашения о взаимодействии между вашим развертыванием Lync Server и другими развертываниями Office Communications Server 2007 R2 или Lync Server. Федеративная конфигурация Lync Server обеспечивает следующие возможности связи пользователей Lync с федеративными пользователями:

  - обмен мгновенными сообщениями и сведениями о присутствии;

  - создание федеративных контактов в клиенте Lync.

Федерация XMPP предусматривает наличие внешнего развертывания на основе протокола XMPP. Конфигурация XMPP обеспечивает следующие возможности связи пользователей Lync с разрешенными пользователями домена XMPP:

  - обмен мгновенными сообщениями и сведениями о присутствии (только в двустороннем режиме);

  - создание федеративных контактов XMPP в клиенте Lync.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возможность XMPP сервера Lync Server 2013 была протестирована корпорацией Microsoft и поддерживается в части федеративного обмена мгновенными сообщениями с использованием Google Talk. По вопросам использования других XMPP-систем обращайтесь к сторонним поставщикам, чтобы выяснить, поддерживают ли они федерацию с Lync Server 2013, а также чтобы получить рекомендации по вопросам, связанным с устранением неполадок и развертыванием.</td>
</tr>
</tbody>
</table>


## Развертывание внешней федерации пограничного сервера, подключения к общедоступным службам обмена мгновенными сообщениями и протокола XMPP


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Этап</th>
<th>Шаги</th>
<th>Разрешения</th>
<th>Документация</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Определение параметров, добавляемых в существующее развертывание пограничного сервера</p></td>
<td><p>Чтобы изменить параметры пограничного сервера, а также создать и опубликовать топологию, используйте топологий. Существующая пограничная топология будет реплицировать изменения с управления на пограничный сервер.</p></td>
<td><p>Группа &quot;Администраторы домена&quot; и группа RTCUniversalServerAdmins</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Вы можете изменить топологию с помощью учетной записи члена группы локальных пользователей, однако для публикации топологии требуется учетная запись члена группы &quot;Администраторы домена&quot; и группы RTCUniversalServerAdmins</td>
</tr>
</tbody>
</table>

</div></td>
<td><p><a href="lync-server-2013-building-an-edge-and-director-topology.md">Создание топологии пограничных серверов и директора в Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Подготовка к установке</p></td>
<td><ol>
<li><p>Убедитесь, что для системы выполнены необходимые условия.</p></li>
<li><p>Настройте внутренние и внешние DNS-записи для поддержки подключения к общедоступным службам обмена сообщениями, федерации Lync и федерации XMPP.</p></li>
<li><p>Настройте порты и протоколы на брандмауэре для поддержки типов развертываемой федерации.</p></li>
<li><p>Получите и установите общедоступные сертификаты. Время, требуемое для получения сертификатов, зависит от используемого центра сертификации (ЦС). На этом этапе развертывания данный этап является необязательным. Если этот шаг пропущен, то потребуется выполнить соответствующие действия в ходе настройки пограничного сервера. Служба пограничного сервера будет запущена только после получения сертификатов.</p></li>
</ol>
<p></p></td>
<td><p>Зависят от организации, поскольку эти роли обычно распределены между множеством рабочих групп</p></td>
<td><p><a href="lync-server-2013-planning-for-sip-xmpp-federation-and-public-instant-messaging.md">Планирование федерации SIP, федерации XMPP и Public Instant Messaging в Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Настройка пограничных серверов для сценариев федерации</p></td>
<td><ol>
<li><p>Добавьте экспортированный файл конфигурации топологии на каждой пограничный сервер или дождитесь завершения репликации.</p></li>
<li><p>Чтобы установить компоненты для поддержки федерации, запустите мастер развертывания повторно.</p></li>
<li><p>Настройте пограничные серверы.</p></li>
<li><p>Запросите сертификаты для каждого пограничного сервера и установите их.</p></li>
<li><p>Перезапустите службы пограничного сервера.</p></li>
</ol></td>
<td><p>Группа Администраторы</p></td>
<td><p><a href="lync-server-2013-setting-up-lync-federation.md">Настройка федерации в Lync в Lync Server 2013</a></p>
<p><a href="lync-server-2013-setting-up-public-instant-messaging-connectivity.md">Настройка соединения для общедоступных служб обмена мгновенными сообщениями в Lync Server 2013</a></p>
<p><a href="lync-server-2013-setting-up-xmpp-federation.md">Настройка федерации XMPP в Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Настройка поддержки доступа внешних пользователей</p></td>
<td><ol>
<li><p>Воспользуйтесь компонентом External User Access (Доступ внешних пользователей) на панели управления Lync Server.</p></li>
<li><p>Настройте политику внешнего доступа для включения коммуникаций с федеративными пользователями или внешними пользователями.</p></li>
<li><p>Настройте федеративные домены SIP, чтобы разрешить или заблокировать домены.</p></li>
<li><p>Включите федеративных поставщиков SIP для поставщиков общедоступных служб обмена мгновенными сообщениями.</p></li>
<li><p>Настройте федеративных партнеров XMPP для каждого домена XMPP.</p></li>
</ol></td>
<td><p>Группа RTCUniversalServerAdmins или учетная запись пользователя, назначенная роли CSAdministrator</p></td>
<td><p><a href="lync-server-2013-configuring-support-for-external-user-access.md">Настройка поддержки доступа внешних пользователей в Lync Server 2013</a></p>
<p><a href="lync-server-2013-configure-media-encryption-for-public-providers.md">Настройка шифрования мультимедиа для общедоступных поставщиков в Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Проверка конфигурации пограничного сервера</p></td>
<td><p>Проверьте возможности подключения к серверу и репликацию данных конфигурации с внутренних серверов.</p></td>
<td><p>Для проверки репликации требуется учетная запись группы RTCUniversalServerAdmins или учетная запись пользователя, назначенная роли CSAdministrator Для проверки подключения требуются учетные записи, представляющие все типы федеративных пользователей</p></td>
<td><p><a href="lync-server-2013-verifying-your-edge-deployment.md">Проверка развертывания пограничного сервера в Lync Server 2013</a></p>
<p><a href="lync-server-2013-example-xmpp-configuration-–-xmpp-federation-with-google-talk.md">Пример конфигурации XMPP в Lync Server 2013 — федерация XMPP с Google Talk</a></p></td>
</tr>
</tbody>
</table>
