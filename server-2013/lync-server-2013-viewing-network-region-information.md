﻿---
title: Просмотр сведений об области сети
TOCTitle: Просмотр сведений об области сети
ms:assetid: 665740d0-a3ed-460f-8337-5ed945f90589
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ688076(v=OCS.15)
ms:contentKeyID: 49888020
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Просмотр сведений об области сети

 

_**Дата изменения раздела:** 2013-02-23_

Область сети связывает части сети, расположенные в различных географических районах. Каждый регион сети должен быть связан с центральным сайтом. Центральный сайт — это сайт центра обработки данных, на котором выполняется служба политики пропускной способности для контроля допуска звонков. Можно использовать панель управления Lync Server для просмотра сетевых регионов. Сетевые регионы включают параметры, которые определяют, разрешены ли альтернативные пути в Интернете для аудио- и видеоподключений. С помощью инструкций, приведенных в этом разделе, можно просмотреть существующие сетевые регионы. Дополнительные сведения о создании или изменении существующих регионов см. в разделе [Создание или изменение областей сети](lync-server-2013-creating-or-modifying-network-regions.md).

## Просмотр сведений об области сети с помощью панели управления Lync Server

1.  Войдите на любой компьютер, находящийся во внутреннем развертывании, с использованием учетной записи, входящей в группу RTCUniversalServerAdmins (или имеющей равнозначные права пользователя) либо назначенной роли CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  На левой панели навигации щелкните **Конфигурация сети**, затем **Регион**.

4.  На странице **Регион** щелкните регион, который следует просмотреть.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>одновременно можно просматривать только один регион.</td>
    </tr>
    </tbody>
    </table>


5.  В меню **Изменить** щелкните **Показать сведения**.

## Просмотр сведений об области сети с помощью командлетов Windows PowerShell

Вы можете просмотреть сведения об области сети с помощью Windows PowerShell командлета **Get-CsNetworkRegion**. Для выполнения этого командлета может использоваться командная консоль Lync Server 2013 или удаленный сеанс Windows PowerShell. Дополнительные сведения об использовании Windows PowerShell в удаленном режиме для подключения к Lync Server см. статью блога Lync Server Windows PowerShell "Краткое руководство: управление Microsoft Lync Server 2010 в удаленном режиме с помощью PowerShell" по адресу [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Просмотр сведений об области сети

  - Чтобы просмотреть сведения обо всех сетевых регионах, введите следующую команду в командной консоли Командная консоль Lync Server и нажмите клавишу ВВОД:
    
        Get-CsNetworkRegion
    
    Будут возвращены сведения, аналогичные приведенным ниже:
    
        Identity         : Pacific Northwest
        Description      :
        BypassID         : 3b232b84-2c1d-4da2-8181-e9330bafebe9
        CentralSite      : Site:Redmond1
        BWAlternatePaths : {BWPolicyModality=Audio;AlternatePath=True, 
                           BWPolicyModality=Video;AlternatePath=True}
        NetworkRegionID  : Pacific Northwest

Дополнительные сведения см. в разделе справки по командлету [Get-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkRegionLink).

## См. также

#### Задачи

[Создание или изменение областей сети](lync-server-2013-creating-or-modifying-network-regions.md)  
[Удаление существующих областей сети](lync-server-2013-deleting-existing-network-regions.md)

