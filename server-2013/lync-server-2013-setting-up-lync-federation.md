﻿---
title: 'Lync Server 2013: настройка федерации в Lync'
TOCTitle: Настройка федерации в Lync
ms:assetid: 374ddc43-26f9-499d-be68-a5158adfa49c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ204800(v=OCS.15)
ms:contentKeyID: 49309435
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Настройка федерации в Lync в Lync Server 2013

 

_**Дата изменения раздела:** 2015-03-09_

Если вы уже развернули пограничные серверы, добавление возможностей для федеративных сценариев довольно просто. Если вы не настроили пограничные серверы, это необходимо сделать. Дополнительные сведения см. в разделе [Планирование доступа внешних пользователей в Lync Server 2013](lync-server-2013-planning-for-external-user-access.md) документации по планированию и в разделе [Развертывание доступа внешних пользователей в Lync Server 2013](lync-server-2013-deploying-external-user-access.md) документации по развертыванию.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если планируется настройка какого-либо сочетания федерации XMPP, федерации Lync или подключения к общедоступным системам обмена мгновенными сообщениями, можно развернуть их одновременно или по одному. Если настроить эти параметры с помощью построителя топологии и консоли управления Lync Server, а затем запустите мастер развертывания на пограничном сервере после настройки параметров для одного, двух или всех трех типов федерации, можно сократить число необходимых действий.</td>
</tr>
</tbody>
</table>


## Настройка федерации Lync в построителе топологий и мастере развертывания

1.  На интерфейсном сервере откройте построитель топологии. Разверните "Пограничные пулы", затем щелкните правой кнопкой мыши пограничный сервер или пул пограничных серверов. Выберите "Изменить свойства".

2.  В окне "Изменение свойств" в разделе "Общие" выберите "Включить федерацию для этого пограничного пула (порт 5061)". Нажмите кнопку "ОК".

3.  Щелкните "Действие", выберите "Топология" и затем нажмите "Опубликовать". При появлении запроса о публикации топологии, нажмите кнопку "Далее". После завершения публикации нажмите кнопку "Готово".

4.  На пограничном сервере откройте мастер развертывание Lync Server. Нажмите кнопку "Установить или обновить систему Lync Server", затем нажмите кнопку "Установить или удалить компоненты Lync Server". Затем снова нажмите "Выполнить".

5.  В диалоговом окне "Установка компонентов Lync Server" нажмите кнопку "Далее". В окне сводки будут показаны действия по мере их выполнения. После завершения развертывания нажмите кнопку "Просмотр журнала", чтобы открыть доступные файлы журналов. Нажмите кнопку "Готово", чтобы завершить развертывание.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Вы можете выбрать этот параметр, но только один пограничный пул или пограничный сервер в организации может быть опубликован внешне для федерации. Весь доступ федеративных пользователей, в том числе пользователей общедоступных служб обмена мгновенными сообщениями, осуществляется через один пограничный пул или пограничный сервер. Например, если развертывание содержит пограничный пул или один пограничный сервер в Нью-Йорке, и другой пограничный сервер в Лондоне и вы включаете поддержку федерации в нью-йоркском пуле или на одном пограничном сервере, трафик для федеративных пользователей будет передаваться через нью-йоркский пул или один пограничный сервер. Это справедливо даже для взаимодействия с лондонскими пользователями, хотя внутренние пользователи из Лондона, вызывающие федеративного пользователя из Лондона, применяют лондонский пул или пограничный сервер для аудио-видео трафика.</td>
    </tr>
    </tbody>
    </table>


## Настройка федерации с партнерами

1.  Чтобы правильно настроить федерацию с другой системой Microsoft Lync Server 2013, Lync Server 2010, Office Communications Server 2007 R2 или Office Communicator 2007, выберите тип федерации в следующей таблице и определите SRV-записи DNS, узел DNS (A или AAAA для IPv6), затем настройте политики, применимые к этому типу федерации.
    
    
    <table>
    <colgroup>
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Тип федерации</th>
    <th>DNS-записи</th>
    <th>Определение политики</th>
    <th>Примечания.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Обнаруженный домен партнера</p></td>
    <td><p>Настройте запись SRV в формате format _sipfederationtls._tcp.&lt;имя внешнего домена&gt;, где значением порта для записи SRV является TCP 5061 и элемент <strong>Узел этой службы</strong> определяется как sip. &lt;имя внешнего домена&gt; - полное доменное имя доступа. Дополнительные сведения о создании записи SRV см. в разделе <a href="lync-server-2013-configure-dns-for-edge-support.md">Настройка DNS для поддержки пограничной топологии в Lync Server 2013</a></p></td>
    <td><ul>
    <li><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Включение или отключение федерации и подключение для общедоступного обмена мгновенными сообщениями в Lync Server 2013</a></p></li>
    <li><p><a href="lync-server-2013-enable-or-disable-discovery-of-federation-partners.md">Включение или отключение обнаружения федеративных партнеров в Lync Server 2013</a></p></li>
    </ul></td>
    <td><p>В предыдущих версиях этот тип федерации назывался <strong>открытой улучшенной федерацией</strong>. Создание SRV-записи необходимо для этого типа федерации, т. к. служит для нахождения другими партнерами этой федерации.</p></td>
    </tr>
    <tr class="even">
    <td><p>Разрешенный домен партнера</p></td>
    <td><p>Настройте запись SRV в формате format _sipfederationtls._tcp.&lt;имя внешнего домена&gt;, где значением порта для записи SRV является TCP 5061 и элемент <strong>Узел этой службы</strong> определяется как sip. &lt;имя внешнего домена&gt; - полное доменное имя доступа. Дополнительные сведения о создании записи SRV см. в разделе <a href="lync-server-2013-configure-dns-for-edge-support.md">Настройка DNS для поддержки пограничной топологии в Lync Server 2013</a></p></td>
    <td><ul>
    <li><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Включение или отключение федерации и подключение для общедоступного обмена мгновенными сообщениями в Lync Server 2013</a></p></li>
    </ul></td>
    <td><p>В предыдущих версиях этот тип федерации назывался <strong>улучшенной федерацией</strong>. Создание SRV-записи не является обязательным для этого типа федерации и служит для нахождения другими партнерами этой федерации. Конечно, по сути это <strong>открытая улучшенная федерация</strong> или <strong>обнаруженный домен партнера</strong></p></td>
    </tr>
    <tr class="odd">
    <td><p>Разрешенный сервер партнера</p></td>
    <td><p>Настройте в политиках имя домена SIP и полное доменное имя партнера сервер в качестве партнера федерации.</p></td>
    <td><ul>
    <li><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Включение или отключение федерации и подключение для общедоступного обмена мгновенными сообщениями в Lync Server 2013</a></p></li>
    <li><p><a href="lync-server-2013-configure-support-for-allowed-external-domains.md">Настройка поддержки для разрешенных внешних доменов в Lync Server 2013</a></p></li>
    <li><p><a href="lync-server-2013-configure-support-for-blocked-external-domains.md">Настройка поддержки заблокированных внешних доменов в Lync Server 2013</a></p></li>
    </ul></td>
    <td><p>Этот тип федерации является определением отношения один-к-одному, которое не поддерживает обнаружение других партнеров федерации. Каждый партнер федерации определяется явным образом. В предыдущих версиях такой тип назывался <strong>прямой федерацией</strong></p></td>
    </tr>
    <tr class="even">
    <td><p>Поставщик услуг размещения и общедоступный поставщик систем обмена мгновенными сообщениями</p></td>
    <td><p>Для этого типа федераций нет определенных требований к DNS</p></td>
    <td><ul>
    <li><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Включение или отключение федерации и подключение для общедоступного обмена мгновенными сообщениями в Lync Server 2013</a></p></li>
    <li><p><a href="lync-server-2013-create-or-edit-public-sip-federated-providers.md">Создание или изменение общедоступных федеративных поставщиков SIP в Lync Server 2013</a></p></li>
    <li><p><a href="lync-server-2013-create-or-edit-hosted-sip-federated-providers.md">Создание или изменение размещенных федеративных поставщиков SIP в Lync Server 2013</a></p></li>
    </ul></td>
    <td><p>Этот тип федерации определяет службы и поставщиков услуг размещения, которые следует настроить для своих пользователей. Типичное использование заключается в настройке поставщиков систем обмена мгновенными сообщениями, таких как Windows Live Messenger, Yahoo! и AOL, а также поставщиков услуг размещения, таких как Lync Online и Office 365</p>
    <div class="alert">
    <table>
    <colgroup>
    <col style="width: 100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><ul>
    <li><p>С 1 сентября 2012 г. прекращена продажа лицензий пользовательских подписок на подключение к общедоступным службам обмена мгновенными сообщениями Microsoft Lync (PIC USL) по новым или продляемым соглашениям. Клиенты с активными лицензиями смогут продолжать использование федерации с Yahoo! Messenger до отключения службы. Поддержка служб AOL и Yahoo! завершается в июне 2014 г. Дополнительные сведения см. в статье <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Поддержка подключения к общедоступным службам обмена мгновенными сообщениями в Lync Server 2013</a>.</p></li>
    <li><p>Лицензия подписки пользователя на возможность подключения к общедоступным службам обмена мгновенными сообщениями представляет собой лицензию подписки на пользователя в месяц, которая необходима для того, чтобы Lync Server или Office Communications Server могли образовывать федерацию с Yahoo! Messenger. Корпорация Майкрософт смогла предоставлять данную услугу благодаря поддержке со стороны компании Yahoo!, однако соответствующий базовый договор расторгается.</p></li>
    <li><p>Сейчас, более чем когда-либо раньше, Lync представляет собой эффективное средство для объединения организаций и отдельных пользователей по всему миру. Федерация с Windows Live Messenger не требует никаких дополнительных лицензий на пользователя/устройство, кроме Lync Standard CAL. В этот список будет добавлена федерация Skype, позволяя пользователям Lync взаимодействовать с сотнями миллионов людей посредством мгновенных сообщений и голосовой связи.</p></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

    </div></td>
    </tr>
    </tbody>
    </table>


2.  Определение и настройка любых требуемых SRV-записей узлов DNS (A или AAAA для IPv6)

3.  Определите и настройте любые политики с помощью панели управления Lync Server или Командная консоль Lync Server и соответствующих командлетов. Дополнительные сведения о командлетах Командная консоль Lync Server см. в разделе [Командлеты федерации и внешнего доступа в Lync Server 2013](https://docs.microsoft.com/en-us/powershell/module/skype/)
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>В системе комнат Lync (LRS) не отображаются кнопки «Присоединиться» для собраний, инициируемых организаторами у федеративных партнеров Lync. Для того, чтобы ссылка на присоединение к собранию отображалась в LRS, организация-инициатор должна разрешить использование TNEF с помощью следующего командлета:<br />
    <br />
    <code>New-RemoteDomain -DomainName Contoso.com -Name Contoso</code><br />
    <code>Set-RemoteDomain -Identity Contoso -TNEFEnabled $true</code><br />
    В приложениях Outlook и Lync в данном случае ссылки «Присоединиться» также не будут отображаться, если не выполнен перенос свойств MAPI, но в случае с Outlook пользователь может открывать приглашение на собрание и переходить по URL-адресу собрания. Если атрибут TNEFEnabled имеет значение true, то Exchange 2013 не сохраняет свойства MAPI, в том числе свойство OnlineMeetingExternalLink, и кнопка «Присоединиться» будет отображаться в окне напоминания.</td>
    </tr>
    </tbody>
    </table>


## См. также

#### Другие ресурсы

[Планирование федерации SIP, федерации XMPP и Public Instant Messaging в Lync Server 2013](lync-server-2013-planning-for-sip-xmpp-federation-and-public-instant-messaging.md)  
[Управление федерацией и внешним доступом к Lync Server 2013](lync-server-2013-managing-federation-and-external-access-to-lync-server-2013.md)

