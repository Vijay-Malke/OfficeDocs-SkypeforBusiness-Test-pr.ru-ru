﻿---
title: 'Lync Server 2013: создание топологии пограничных серверов и директора'
TOCTitle: Создание топологии пограничных серверов и директора
ms:assetid: 11e5759e-d69f-4c39-8994-f467c279c558
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398202(v=OCS.15)
ms:contentKeyID: 49308992
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Создание топологии пограничных серверов и директора в Lync Server 2013

 

_**Дата изменения раздела:** 2012-09-08_

Построение топологии включает следующие задачи планирования и развертывания.

  - **Планирование.**   Необходимо определить соответствующую топологию для организации и компоненты, требуемые для ее развертывания. Это стандартные действия в процессе планирования. Средство планированияMicrosoft Lync Server 2013, предоставленное сервером Lync Server 2013, облегчает начало процесса планирования, а также позволяет легко вносить изменения после того, как ваши требования и планы будут окончательно сформированы.

  - **Развертывание.**   Топология, определенная с помощью средства топологий, важна для развертывания любого сервера в сервере Lync Server 2013. Если вы еще не завершили определение и публикацию топологии с помощью средства топологий в качестве части процесса планирования, то необходимо завершить и опубликовать топологию, прежде чем приступить к развертыванию пограничных серверов.

Нельзя разворачивать компоненты пограничного сервера, пока не развернут хотя бы один внутренний пул, и необходимо установить построитель топологий для развертывания внутреннего пула. В этом разделе не рассматривается установка построителя топологий, поскольку она является частью процесса установки внутреннего пула.

Подробнее об этих средствах см. в [Контрольный список развертывания для доступа внешних пользователей в Lync Server 2013](lync-server-2013-deployment-checklist-for-external-user-access.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если вам приходилось использовать построитель топологий для определения полной топологии, включая пограничную топологию, то можно пропустить задачи <a href="lync-server-2013-define-your-edge-topology.md">Определение пограничной топологии в Lync Server 2013</a> и <a href="lync-server-2013-publish-your-topology.md">Публикация топологии в Lync Server 2013</a> в этом разделе, но необходимо выполнить задачу <a href="lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md">Экспорт топологии Lync Server 2013 и ее копирование на внешние носители для установки в пограничной топологии</a>.</td>
</tr>
</tbody>
</table>


## Содержание

  - [Определение пограничной топологии в Lync Server 2013](lync-server-2013-define-your-edge-topology.md)

  - [Определение дополнительных топологий директоров в топологии для Lync Server 2013](lync-server-2013-define-optional-director-topologies-in-your-topology.md)

  - [Публикация топологии в Lync Server 2013](lync-server-2013-publish-your-topology.md)

  - [Экспорт топологии Lync Server 2013 и ее копирование на внешние носители для установки в пограничной топологии](lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md)

