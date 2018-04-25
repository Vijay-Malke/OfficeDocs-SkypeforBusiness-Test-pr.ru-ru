﻿---
title: 'Lync Server 2013: делегирование разрешений на установку'
TOCTitle: Делегирование разрешений на установку
ms:assetid: 9dca1683-4c69-4534-8ebe-6bd635cbae49
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg412735(v=OCS.15)
ms:contentKeyID: 49310670
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Делегирование разрешений на установку в Lync Server 2013

 

_**Дата изменения раздела:** 2014-02-05_

Если пользователям или группам, разворачивающим сервер Lync Server 2013, не планируется предоставлять членство в группе администраторов домена, то можно разрешить членам группы RTCUniversalServerAdmins выполнять командлет **Enable-CsTopology**  Windows PowerShell на серверах с работающим сервером Lync Server 2013. По умолчанию члены группы RTCUniversalServerAdmins не имеют прав на выполнение этого командлета. Чтобы предоставить административные права и разрешения на выполнение командлета **Enable-CsTopology** на серверах, на которых работает сервер Lync Server, можно использовать командлет **Grant-CsSetupPermission** с указанием подразделения, в котором расположены объекты-компьютеры с работающим сервером Lync Server 2013.

Подготовка домена, происходящая при установке Lync Server, не добавляет автоматически права членам группы RTCUniversalServerAdmins для запуска командлета Enable-CsTopology. Это значит, что по умолчанию нужны права администратора домена для включения топологии. Чтобы дать членам группы RTCUniversalServerAdmins право включать топологию, следует запустить командлет Grant-CsSetupPermissions. Также понадобится запустить командлет для каждого контейнера Active Directory, размещающего компьютеры, на которых выполняется Lync Server.

Помните, что данный командлет дает права только членам группы RTCUniversalServerAdmins; права не могут быть предоставлены другим группам безопасности или отдельным пользователям.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Enable-CsTopology</strong> — это основной командлет, позволяющий разрешить членам группы RTCUniversalServerAdmins установку и и развертывание сервера Lync Server 2013.</td>
</tr>
</tbody>
</table>


## Добавление возможности выполнения командлета Enable-CsTopology группе RTCUniversalServerAdmins

1.  Войдите на сервер как член группы администраторов домена того домена, в котором делегированный пользователь будет выполнять командлет **Enable-CsTopology**.

2.  Откройте командную консоль командная консоль Lync Server 2013. Командная консоль командная консоль Lync Server 2013 автоматически устанавливается на каждый сервер переднего плана или на любой компьютер, на котором установлены средства администрирования сервера Lync Server 2013. Подробные сведения о командной консоли командная консоль Lync Server 2013 см. в разделе [Командная консоль Lync Server](lync-server-2013-lync-server-management-shell.md) документации по операциям.

3.  В командной консоли командная консоль Lync Server 2013 выполните следующий командлет:
    
        Grant-CsSetupPermission -ComputerOU <DN of the OU> -Domain <Domain FQDN>
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если подразделение находится не на верхнем уровне, необходимо предоставить полное доменное имя.</td>
    </tr>
    </tbody>
    </table>
    
    В следующем примере подразделение – это “Lync Servers”, и находится оно в домене contoso.com.
    
        Grant-CsSetupPermission -ComputerOU "OU=Lync Servers" -Domain contoso.com
