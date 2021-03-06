﻿---
title: Удаление политики ПИН-кодов
TOCTitle: Удаление политики ПИН-кодов
ms:assetid: 7c378927-2e41-418e-9721-327021bd2e45
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg521020(v=OCS.15)
ms:contentKeyID: 49310272
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Удаление политики ПИН-кодов

 

_**Дата изменения раздела:** 2013-02-23_

Чтобы удалить политику персональных идентификационных номеров (политику ПИН-кодов), выполните следующие действия.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Глобальную политику ПИН-кодов удалить нельзя.</td>
</tr>
</tbody>
</table>


## Удаление политики ПИН-кодов в панели управления Lync Server 2013

1.  Войдите на любой компьютер, подключенный к сети, где развернут Lync Server 2013, с использованием учетной записи, входящей в группу RTCUniversalServerAdmins (или имеющей равнозначные права пользователя) либо назначенной роли CsServerAdministrator или CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой панели навигации последовательно выберите пункты **Security (Безопасность)** и **PIN Policy (Политика ПИН-кодов)**.

4.  На странице **PIN Policy (Политика ПИН-кодов)** в поле поиска полностью или частично введите имя политики, которую требуется удалить.

5.  В появившемся списке политик щелкните нужную политику и последовательно выберите в меню пункты **Правка** и **Удалить**.

6.  Нажмите кнопку **ОК**.

## Удаление политик ПИН-кодов с помощью Командная консоль Lync Server и командлетов

Вы можете удалить политики ПИН-кодов с помощью Windows PowerShell и командлета Remove-CsPinPolicy. Его можно выполнить в командная консоль Lync Server 2013 или в удаленном сеансе Windows PowerShell. Дополнительные сведения об использовании Windows PowerShell в удаленном режиме для подключения к Lync Server см. статью блога Lync Server Windows PowerShell "Краткое руководство: управление Microsoft Lync Server 2010 в удаленном режиме с помощью PowerShell" по адресу [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Удаление политики ПИН-кода

  - Эта команда удаляет политику ПИН-кода с идентификатором RedmondPinPolicy:
    
        Remove-CsPinPolicy -Identity "RedmondPinPolicy"

## Удаление всех политик ПИН-кодов, применяемых к области узла

  - Эта команда удаляет все политики ПИН-кода, настроенные в области действия сайта:
    
        Get-CsPinPolicy -Filter "site:*" | Remove-CsPinPolicy

## Удаление всех политик ПИН-кодов, позволяющих использовать общих шаблонов

  - А эта команда удаляет все политики ПИН-кодов, допускающие использование общих шаблонов:
    
        et-CsPinPolicy | Where-Object {$_.AllowCommonPatterns -eq $True} | Remove-CsPinPolicy

Дополнительные сведения см. в разделе справки о командлете [Remove-CsPinPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsPinPolicy).

