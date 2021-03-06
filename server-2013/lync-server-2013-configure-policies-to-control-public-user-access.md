﻿---
title: 'Lync Server 2013: конфигурация политик для управления общим доступом пользователей'
TOCTitle: Конфигурация политик для управления общим доступом пользователей
ms:assetid: 090aea0f-ef0b-49da-9c80-02d9279f2fa6
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg520946(v=OCS.15)
ms:contentKeyID: 49308869
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Конфигурация политик для управления общим доступом пользователей в Lync Server 2013

 

_**Дата изменения раздела:** 2016-12-08_

Подключение к общедоступной службе обмена мгновенными сообщениями позволяет пользователям организации использовать мгновенные сообщения для взаимодействия с пользователями служб обмена мгновенными сообщениями, предоставленными поставщиками общедоступных услуг обмена мгновенными сообщениями, в том числе сеть интернет-услуг Windows Live, Yahoo\! и AOL. Чтобы управлять взаимодействием пользователей общедоступных служб с внутренними пользователями Lync Server, можно настроить одну или несколько политик доступа внешних пользователей. Подключение к общедоступной службе обмена мгновенными сообщениями – это дополнительный компонент, использующий конфигурацию среды и пользователей организации. Он также зависит от предоставления услуги поставщиком общедоступных услуг обмена мгновенными сообщениями. Сведения о предоставлении используемой среде возможности взаимодействовать с общедоступными поставщиками см. в руководстве по предоставлению подключения к общедоступной службе обмена мгновенными сообщениями для Microsoft Lync Server, Office Communications Server и Live Communications Server: <http://go.microsoft.com/fwlink/?linkid=269821>

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


Для доступа к сайту предоставления службы обмена мгновенными сообщениями Microsoft Lync Server используйте следующую ссылку: <http://go.microsoft.com/fwlink/?linkid=212638>

Для управления доступом пользователей общедоступных служб можно настроить политики на глобальном уровне, уровне сайта и пользовательском уровне. Сведения о типах настраиваемых политик см. в статье [Настройка поддержки доступа внешних пользователей в Lync Server 2013](lync-server-2013-configuring-support-for-external-user-access.md) в документации по развертыванию или в документации по планированию. Параметры политики Lync Server, которые применяются на уровне одной политики, могут переопределять параметры, применяемые на уровне другой политики. Приоритет политик Lync Server: политика пользователя (самое большое влияние) переопределяет политику сайта, а политика сайта — глобальную политику (минимальное влияние). То есть, чем ближе параметр политики к объекту, на который она влияет, тем больше влияния она оказывает на объект.

В случае приглашений к обмену мгновенными сообщениями ответ зависит от клиентского ПО. Запрос принимается, если внешние отправители не блокированы пользовательским правилом (то есть настройками пользовательских списков клиентов **Разрешить** и **Заблокировать** для клиентов). Кроме того, приглашения к обмену мгновенными сообщениями могут быть блокированы, если пользователь выбирает блокировку всех мгновенных сообщений от пользователей, не входящих в его список **Разрешить** .

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Политики управления доступом пользователей общедоступных служб можно настроить даже при отсутствии федерации в организации. Но настроенные политики действуют только при включенных федеративных отношениях для организации. Подробные сведения о включении федерации см. в статье <a href="lync-server-2013-enable-or-disable-remote-user-access.md">Включение или отключения удаленного доступа пользователей в Lync Server 2013</a> в документации по развертыванию или в документации по эксплуатации. Кроме того, если задана пользовательская политика управления доступом пользователей общедоступных служб, она применяется только к пользователям, для которых разрешено использование Lync Server и настроено использование политики. Подробные сведения о задании пользователей общедоступных служб, которые могут подключаться к Lync Server, см. в статье <a href="lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md">Назначение политики доступа внешних пользователей пользователю, разрешенному для Lync в Lync Server 2013</a> в документации по развертыванию или в документации по эксплуатации.</td>
</tr>
</tbody>
</table>


Для настройки политики, поддерживающей доступ пользователей одного или нескольких общедоступных поставщиков услуг обмена мгновенными сообщениями, используется следующая процедура.

## Настройка политики внешнего доступа для поддержки доступа пользователей общедоступных служб

1.  Войдите на любой компьютер, находящийся во внутреннем развертывании, с использованием учетной записи, входящей в группу RTCUniversalServerAdmins (или имеющей равнозначные права пользователя) либо назначенной роли CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  На левой панели навигации щелкните **Внешний доступ пользователей** , затем щелкните **Политика внешнего доступа** .

4.  На странице **Политика внешнего доступа** выполните одно из следующих действий.
    
      - Чтобы настроить глобальную политику для поддержки доступа пользователей общедоступных служб, щелкните глобальную политику, щелкните **Изменить** , а затем щелкните **Показать сведения** .
    
      - Чтобы создать новую политику сайта, щелкните **Создать** , затем щелкните **Политика сайта** . В разделе **Выбор сайта** щелкните подходящий сайт в списке и нажмите кнопку **ОК** .
    
      - Чтобы создать новую политику для пользователей, щелкните **Создать** , затем щелкните **Политика пользователей** . В окне **Создание политики внешнего доступа** задайте в поле **Имя** уникальное имя, показывающее область применения этой политики (например, **EnablePublicUsers** для пользовательской политики, разрешающей взаимодействие с пользователями общедоступных служб).
    
      - Чтобы изменить существующую политику, щелкните ее в таблице, щелкните **Изменить** , затем **Показать сведения** .

5.  (Необязательно) Если необходимо добавить или изменить описание, укажите сведения для этой политики в пункте **Описание** .

6.  Выполните одно из указанных ниже действий.
    
      - Чтобы разрешить для политики доступ пользователей общедоступных служб, установите флажок **Разрешить взаимодействие с незарегистрированными пользователями** .
    
      - Чтобы запретить для политики доступ пользователей общедоступных служб, снимите флажок **Разрешить взаимодействие с незарегистрированными пользователями** .

7.  Щелкните **Исполнить** .

Чтобы включить доступ пользователей общедоступных служб, необходимо также включить в организации поддержку федерации. Дополнительные сведения см. в разделе [Настройка политик управления доступом федеративных пользователей в Lync Server 2013](lync-server-2013-configure-policies-to-control-federated-user-access.md).

В случае пользовательской политики, также необходимо настроить и применить политику к пользователям общедоступных служб, которым требуется разрешить совместную работу с пользователями общедоступных служб. Дополнительные сведения см. в разделе [Назначение политик уровня пользователя в Lync Server 2013](lync-server-2013-assigning-per-user-policies.md).

## См. также

#### Задачи

[Создание или изменение общедоступных федеративных поставщиков SIP в Lync Server 2013](lync-server-2013-create-or-edit-public-sip-federated-providers.md)  

#### Другие ресурсы

[Управление федеративными поставщиками SIP в организации в Lync Server 2013](lync-server-2013-manage-sip-federated-providers-for-your-organization.md)

