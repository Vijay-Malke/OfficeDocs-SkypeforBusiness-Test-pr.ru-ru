﻿---
title: Создание межрегиональных сетевых маршрутов в Lync Server 2013
TOCTitle: Создание межрегиональных сетевых маршрутов в Lync Server 2013
ms:assetid: 5555262a-a502-4b01-9593-836dd30064f5
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398368(v=OCS.15)
ms:contentKeyID: 49309816
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Создание межрегиональных сетевых маршрутов в Lync Server 2013

 

_**Дата изменения раздела:** 2012-10-20_

*Маршрут между регионами сети* определяет маршрут между парой регионов сети. Маршрут между регионами сети требуется для каждой пары регионов сети в развертывании службы контроля допуска звонков. Это позволяет каждому региону сети в рамках развертывания осуществлять доступ к любому другому региону.

Связи между регионами накладывают определенные ограничения на пропускную способность, доступную подключениям между регионами; маршруты же определяют путь, который должны пройти подключения от одного региона до другого.

Для получения дополнительных сведений о работе с маршрутами между регионами сети см. документацию Командная консоль Lync Server для следующих командлетов:

  - [New-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkInterRegionRoute)

  - [Get-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkInterRegionRoute)

  - [Set-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkInterRegionRoute)

  - [Remove-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkInterRegionRoute)

В этом примере топологии необходимо определить маршруты между регионами сети для каждой пары регионов из трех: Северная Америка/EMEA, APAC/EMEA и APAC/Северная Америка.

## Создание маршрутов между регионами сети с помощью панели управления сервера Командная консоль Lync Server

1.  Запустите командную консоль Lync Server: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Командная консоль Lync Server**.

2.  Выполните командлет **New-CsNetworkInterRegionRoute**, чтобы определить необходимые маршруты. Например, выполните:
    
        New-CsNetworkInterRegionRoute -Identity NorthAmerica_EMEA_Route -NetworkRegionID1 NorthAmerica -NetworkRegionID2 EMEA -NetworkRegionLinkIDs "NA-EMEA-LINK"
    
        New-CsNetworkInterRegionRoute -Identity NorthAmerica_APAC_Route -NetworkRegionID1 NorthAmerica -NetworkRegionID2 APAC -NetworkRegionLinkIDs "NA-EMEA-LINK, EMEA-APAC-LINK"
    
        New-CsNetworkInterRegionRoute -Identity EMEA_APAC_Route -NetworkRegionID1 EMEA -NetworkRegionID2 APAC -NetworkRegionLinkIDs "EMEA-APAC-LINK"
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Для маршрута между регионами «Северная Америка/APAC» требуются две связи между регионами сети, поскольку прямая сетевая связь между этими регионами отсутствует.</td>
    </tr>
    </tbody>
    </table>


## Создание маршрутов между регионами сети с помощью панели управления Lync Server

1.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  На левой панели навигации щелкните **Конфигурация сети**.

3.  Щелкните кнопку навигации **Маршрут региона**.

4.  Щелкните **Создать**.

5.  На странице **Новый маршрут региона** щелкните **Имя**, а затем введите имя для маршрута между регионами сети.

6.  Щелкните **Регион сети №1** , а затем выберите регион сети в списке, для которого нужно проложить маршрут к региону сети №2.

7.  Щелкните **Регион сети №2** , а затем выберите регион сети в списке, для которого нужно проложить маршрут к региону сети №1.

8.  Щелкните **Добавить** рядом с полем **Связи между регионами сети**, а затем добавьте связь с регионом сети, которая будет использоваться в маршруте между регионами сети.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>При создании маршрута между двумя регионами сети, между которыми отсутствует прямая связь, необходимо добавить все необходимые связи для создания полного маршрута. Например, для создания маршрута между регионами сети «Северная Америка» и «APAC» требуются две связи между сетевыми регионами, так как между ними отсутствует прямая связь.</td>
    </tr>
    </tbody>
    </table>


9.  Щелкните **Исполнить**.

10. Чтобы завершить создание маршрутов между регионами сети, повторите шаги с 4 по 9 с указанием настроек для других маршрутов между сетевыми регионами.

