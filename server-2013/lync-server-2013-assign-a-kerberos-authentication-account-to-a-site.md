﻿---
title: 'Lync Server 2013: назначение учетной записи проверки подлинности Kerberos для сайта'
TOCTitle: Назначение учетной записи проверки подлинности Kerberos для сайта
ms:assetid: 3d9c587c-c8b8-4f81-8ed9-1458a31fc292
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg425901(v=OCS.15)
ms:contentKeyID: 49309521
ms.date: 04/20/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Назначение учетной записи проверки подлинности Kerberos для сайта в Lync Server 2013

 

_**Дата изменения раздела:** 2017-04-18_

Чтобы успешно выполнить данную процедуру, необходимо войти в систему с учетной записью пользователя, являющегося членом группы RTCUniversalServerAdmins.

После создания учетной записи Kerberos вам следует назначить ее сайту. Это сайт системы Lync Server 2013, а не сайт Active Directory. Для одного развертывания вы можете создать несколько учетных записей для проверки подлинности Kerberos, однако сайту можно назначить всего одну из них. Используйте описанную ниже процедуру, чтобы назначить сайту ранее созданную учетную запись для проверки подлинности Kerberos. Дополнительные сведения о создании учетной записи Kerberos см. в разделе [Создание учетной записи для проверки подлинности Kerberos в Lync Server 2013](lync-server-2013-create-a-kerberos-authentication-account.md).

## Назначение учетной записи для проверки подлинности Kerberos сайту

1.  Используя учетную запись члена группы RTCUniversalServerAdmins, выполните вход в систему компьютера в домене, в котором выполняется Lync Server 2013, или в систему компьютера, на котором установлены средства администрирования.

2.  Запустите командную консоль Lync Server: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Командная консоль Lync Server**.

3.  В командной строке выполните следующие две команды:
    
        New-CsKerberosAccountAssignment -UserAccount "Domain\UserAccount" -Identity "site:SiteName"
    
        Enable-CsTopology
    
    Например:
    
        New-CsKerberosAccountAssignment -UserAccount "contoso\kerbauth" -Identity "site:redmond"
    
        Enable-CsTopology
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Вам следует указать параметр UserAccount, используя формат «домен\пользователь». Использование формата «пользователь@домен.расширение» для ссылки на объекты-компьютеры, созданные для проверки подлинности Kerberos, не поддерживается.</td>
    </tr>
    </tbody>
    </table>
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>После внесения любых изменений в систему проверку подлинности Kerberos (например, после добавления или удаления учетной записи) необходимо выполнить <strong>Enable-CsTopology</strong> в командной строке Командная консоль Lync Server.</td>
    </tr>
    </tbody>
    </table>

