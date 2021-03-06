﻿---
title: Развертывание инструмента SEFAUtil
TOCTitle: Развертывание инструмента SEFAUtil
ms:assetid: fb556e50-88dd-4404-a3d5-be36f5ba41e6
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ945659(v=OCS.15)
ms:contentKeyID: 52058541
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Развертывание инструмента SEFAUtil

 

_**Дата изменения раздела:** 2016-12-08_

Для развертывания ответа на звонок в группе и управления им необходимо использовать инструмент SEFAUtil из набора ресурсов. Этот инструмент входит в число инструментов набора ресурсов Lync Server 2013. Перед установкой SEFAUtil вы должны иметь в топологии пул доверенных приложений, указать SEFAUtil как доверенное приложение и включить топологию.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>На всех компьютерах, на которых планируется запускать инструмент SEFAUtil, должен быть установлен Microsoft Unified Communications Managed API (UCMA) 3.0 Core SDK.</td>
</tr>
</tbody>
</table>


Инструмент SEFAUtil можно запускать в любом пуле серверов переднего плана в развертывании.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Дополнительные сведения о запуске SEFAUtil см. в статье блога Technet <a href="http://go.microsoft.com/fwlink/?linkid=278940">How to get SEFAutil running? (Как запустить SEFAutil?)</a>.</td>
</tr>
</tbody>
</table>


## Развертывание SEFAUtil

1.  Войдите на компьютер, где установлена командная консоль Lync Server, как член группы RTCUniversalServerAdmins или имея необходимые права пользователя, описанные в разделе [Делегирование разрешений на установку в Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Запустите командную консоль Lync Server: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Командная консоль Lync Server**.

3.  Инструмент SEFAUtil можно запускать только на компьютере, входящем в пул доверенных приложений. При необходимости задайте пул доверенных приложений для пула серверов переднего плана, где планируется запускать SEFAUtil. В командной строке выполните следующую команду:
    
        New-CsTrustedApplicationPool -id <Pool FQDN> -Registrar <Pool Registrar FQDN> -site Site:<Pool Site>

4.  Определите инструмент SEFAUtil как доверенное приложение. В командной строке выполните следующую команду:
    
        New-CsTrustedApplication -ApplicationId sefautil -TrustedApplicationPoolFqdn <Pool FQDN>  -Port 7489
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>При необходимости можно использовать другой порт.</td>
    </tr>
    </tbody>
    </table>


5.  Включите топологию с внесенными изменениями. В командной строке выполните следующую команду:
    
        Enable-CsTopology

6.  Установите инструменты набора ресурсов Lync Server 2013 на сервере переднего плана, который находится в пуле доверенных приложений, заданном в действии 3.

7.  Проверьте правильность работы инструмента SEFAUtil следующим образом.
    
    1.  Запустите этот инструмент из командной строки Windows с привилегиями администратора, чтобы отобразить параметры переадресации звонков пользователя в текущем развертывании.
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>Этот инструмент располагается в папке \Program Files\Microsoft Lync Server 2013\Reskit.</td>
        </tr>
        </tbody>
        </table>
    
    2.  Отобразите параметры переадресации звонков пользователя. В командной строке выполните следующую команду:
        
            SEFAUtil.exe <user SIP address> /server:<Lync Server/Pool FQDN>
        
        На экране появятся параметры переадресации звонков пользователя.

