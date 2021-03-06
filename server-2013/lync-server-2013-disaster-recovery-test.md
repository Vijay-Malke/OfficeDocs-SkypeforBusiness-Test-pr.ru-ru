﻿---
title: 'Lync Server 2013: тест аварийного восстановления'
TOCTitle: Тест аварийного восстановления
ms:assetid: 04f5e747-d837-4350-9fc0-8605dbf025a7
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn747887(v=OCS.15)
ms:contentKeyID: 62293586
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Тест аварийного восстановления в Lync Server 2013

 

_**Дата изменения раздела:** 2015-01-26_

Выполните восстановление системы для пула серверов Lync Server 2013 для проверки задокументированного процесса аварийного восстановления. Данный тест смоделирует полный сбой в работе оборудования для одного сервера, а также поможет гарантировать, что ресурсы, планы и данные будут доступны для восстановления. Попробуйте менять ориентир теста каждый месяц, чтобы в организации каждый раз проверялись сбои в работе разных серверов или других компонентов оборудования.

Обратите внимание, что расписание выполнения организациями проверки аварийного восстановления будет отличаться. Очень важно, чтобы проверка аварийного восстановления выполнялась.


Выполните экспорт топологии, политик и параметров конфигурации Lync Server 2013 в файл. Помимо прочего, данный файл может быть использован для восстановления данной информации в центральном хранилище управления после обновления, сбоя в работе оборудования или некоторых других неполадок, в результате которых произошла потеря данных.

Выполните импорт топологии, политик и параметров конфигурации Lync Server 2013 в центральное хранилище управления или на локальный компьютер, как показано в командах ниже.

`Import-CsConfiguration -ByteInput <Byte[]> [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]`

`Import-CsConfiguration -FileName <String> [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]`

Восстановление данных производственного сервера Lync Server 2013:

  - Выполните резервное копирование баз данных RTC и LCSLog с помощью стандартного процесса копирования SQL Server для создания дампа базы данных в файле или на ленте устройства резервного копирования.

  - Используйте стороннее приложение резервного копирования для создания резервной копии данных в файле или на ленте.

  - Используйте командлет Export-CsUserData для создания экспорта XML всей базы данных RTC полностью.

  - Используйте резервное копирование файловой системы или стороннего производителя для создания резервной копии содержимого собрания и журналов соответствия.

  - Используйте инструмент командной строки Export-CsConfiguration для создания резервной копии параметров Lync Server 2013.

Первый этап процедуры обхода неисправностей содержит принудительное перемещение пользователей из производственного пула в пул аварийного восстановления.

Данное перемещение будет принудительным, потому что производственный пул не будет доступен для принятия перемещения пользователей.

Процесс перемещения пользователей Lync Server 2013 является эффективным изменением для атрибута в объекте учетной записи пользователя помимо обновления записи в SQL-базе данных RTC.

Эти данные можно восстановить с помощью двух следующих процессов.

  - Базу данных RTC можно восстановить из исходного устройства резервного копирования производственного сервера SQL Server с помощью стандартного процесса восстановления SQL Server или с помощью сторонней служебной программы резервного копирования/восстановления данных.

  - Контактные данные пользователя можно восстановить с помощью служебной программы DBIMPEXP.exe, используя файл XML, который был создан из экспорта производственного сервера SQL Server.

После восстановления этих данных пользователи могут эффективно подключаться к пулу аварийного восстановления Lync Server 2013 и работать в обычном режиме.

Для предоставления пользователям возможности подключения к пулу аварийного восстановления Lync Server 2013 потребуется изменение записи DNS.

На производственный пул Lync Server 2013 будут ссылаться клиенты с помощью автоматической конфигурации и SRV-записей DNS:

  - SRV: \_sip.\_tls.\<домен\> /CNAME: SIP.\<домен\>

  - CNAME: SIP.\<домен\> /cvc-pool-1.\<домен\>

Для облегчения процедуры отработки отказа данная запись CNAME должна быть обновлена с помощью ссылки на DROCSPool FQDN:

  - CNAME: SIP.\<домен\> /DROCSPool.\<домен\>

  - Sip.\<домен\>

  - AV.\<домен\>

  - webconf.\<домен\>

  - OCSServices.\<домен\>

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Подробные сведения по процедурам администрирования и управления см. в разделе <a href="lync-server-2013-backing-up-and-restoring-lync-server.md">Резервное копирование и восстановление Lync Server 2013</a>.</td>
</tr>
</tbody>
</table>


## См. также

#### Концепции

[Планирование высокой доступности и аварийного восстановления в Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md)  
[Командлеты резервного копирования и высокой доступности](https://docs.microsoft.com/en-us/powershell/module/skype/?view=skype-ps)  

#### Другие ресурсы

[Import-CsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Import-CsConfiguration)  
[Резервное копирование и восстановление Lync Server 2013](lync-server-2013-backing-up-and-restoring-lync-server.md)  
[Управление аварийным восстановлением, высокой доступностью и службой резервного копирования Lync Server 2013](lync-server-2013-managing-lync-server-disaster-recovery-high-availability-and-backup-service.md)

