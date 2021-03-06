﻿---
title: Проверка наличия обновлений для анализатора соответствия рекомендациям
TOCTitle: Проверка наличия обновлений для анализатора соответствия рекомендациям
ms:assetid: 06f1da8b-99a7-4871-911e-bfb7542baced
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ204645(v=OCS.15)
ms:contentKeyID: 49308832
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Проверка наличия обновлений для анализатора соответствия рекомендациям

 

_**Дата изменения раздела:** 2016-12-08_

После запуска анализатор соответствия рекомендациям представляет возможность поиска новейших обновлений этого средства. Если обновление доступно, его можно загрузить. Если выбран отказ от загрузки обновления или если для анализатора соответствия рекомендациям недоступен Интернет, можно продолжить использование версии, уже установленной на компьютере.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если для доступа в Интернет требуется проверка подлинности прокси, анализатор соответствия рекомендациям не может получить доступ к загрузке новых обновлений. Но можно вручную загрузить последнюю версию RtcBPA.msi из Центра загрузки Майкрософт по адресу <a href="http://go.microsoft.com/fwlink/?linkid=266539%26clcid=0x419" class="uri">http://go.microsoft.com/fwlink/?linkid=266539&amp;clcid=0x419</a>. Загруженный файл можно скопировать на компьютер, на котором нужно обновить анализатор соответствия рекомендациям, и использовать MSI-файл для установки на этот компьютер новой версии анализатора.</td>
</tr>
</tbody>
</table>


Чтобы обновить правила анализатора соответствия рекомендациям, необходимо запустить этот инструмент на локальном компьютере от имени администратора. Если обнаружены обновления, но учетная запись, от имени которой выполнен вход в компьютер, не является участником группы администраторов, закройте анализатор соответствия рекомендациям и воспользуйтесь для запуска программы следующей процедурой.

## Запуск анализатора соответствия рекомендациям от имени администратора для проверки обновлений

1.  На компьютере с установленным анализатором соответствия рекомендациям нажмите кнопку **Пуск**, укажите **Microsoft Lync Server 2013**, щелкните правой кнопкой мыши **Анализатор соответствия рекомендациям** и выберите в контекстном меню команду **Запуск от имени администратора**.

2.  Введите данные учетной записи, являющейся участником группы администраторов.

