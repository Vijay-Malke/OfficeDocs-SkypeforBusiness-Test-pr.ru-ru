﻿---
title: Изменение схемы конфигурации сети в Lync Server 2013
TOCTitle: Изменение схемы конфигурации сети в Lync Server 2013
ms:assetid: 47425ab1-5645-4d6f-b202-64bcce43e3ef
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg558643(v=OCS.15)
ms:contentKeyID: 52058208
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Изменение схемы конфигурации сети в Lync Server 2013

 

_**Дата изменения раздела:** 2013-02-21_

Основная часть работы, выполняемой проектировщиком в средстве планирования Lync Server 2013, заключается в определении значений IP-адресов и полных доменных имен для записей на схеме сети. Указываемая на данной странице информация включается в состав отчетов и других сведений, доступных в средстве планирования.

![Сеть в средстве планирования (схема)](images/Gg558643.eeabee2d-698c-4b79-baa5-caa4cfb7edb3(OCS.15).jpg "Сеть в средстве планирования (схема)")

Средство планирования создает схему сети со стандартным текстом для IP-адресов и полных доменных имен.

Изменение схемы сети и входных значений:

1.  Выберите раздел сети, работу над которым хотите начать. Например, дважды щелкните текст **access1.contoso.com**. В открывшемся диалоговом окне введите фактическое полное доменное имя сервера access1.contoso.com и фактически IP-адрес, заменив значение 131.107.155.3.

2.  Нажмите кнопку **OK** (ОК), чтобы сохранить записи.

3.  Продолжайте изменять IP-адреса и полные доменные имена, указывая виртуальные IP-адреса для устройств балансировки нагрузки или записи сервера для подсистемы балансировки нагрузки службы доменных имен (DNS) для серверов в пулах.

Удобной особенность средства планирования является то, что оно может поэтапно назначать диапазон IP-адресов и имен узла сервера, не требуя от проектировщика изменения каждого отдельного сервера в пуле. Например:

1.  Дважды щелкните входящие в состав пула серверы переднего плана. После открытия диалогового окна выберите элемент **Do you want to use the IPs and FQDN as starting points for all equivalent servers in this cluster?** (Использовать IP-адреса и полное доменное имя в качестве исходных точек для всех эквивалентных серверов в этом кластере?).

2.  Например, начальное значение для первого сервера: fe0101.contoso.com и IP-адрес 192.168.21.122.

3.  Введите значение **fe0.contoso.com** в поле **Front End Server FQDN** (Полное доменное имя сервера переднего плана), введите значение **192.168.21.131** в поле **Front End Server IP address** (IP-адрес сервера переднего плана), а затем нажмите кнопку **OK** (ОК).

4.  Компонент автоматического приращения обновляет все серверы в пуле с fe01 по fe06 и все IP-адреса с 192.168.21.131 по 136.

После внесения всех правок сохраните топологию, выполнив следующие действия:

Чтобы сохранить структуру средства планирования, щелкните элемент **File** (Файл) и выберите пункт **Save Topology** (Сохранить топологию) или **Save Topology As** (Сохранить топологию как). В случае отображения диалогового окна **Save Planning Tool As** (Сохранить средство планирования как) введите имя для файла в поле **File name** (Имя файла) и нажмите кнопку **Save** (Сохранить).

## См. также

#### Концепции

[Изменение структуры в Lync Server 2013](lync-server-2013-editing-the-design.md)
