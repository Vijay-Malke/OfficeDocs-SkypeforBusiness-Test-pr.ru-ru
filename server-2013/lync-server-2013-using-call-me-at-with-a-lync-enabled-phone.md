﻿---
title: Использование функции "Позвонить мне номер" с телефоном с поддержкой Lync в Lync Server 2013
TOCTitle: Использование функции "Позвонить мне номер" с телефоном с поддержкой Lync в Lync Server 2013
ms:assetid: 975a1df8-a159-4aa4-a991-5972a535998e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn383570(v=OCS.15)
ms:contentKeyID: 56558976
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Использование функции \"Позвонить мне номер\" с телефоном с поддержкой Lync в Lync Server 2013

 

_**Дата изменения раздела:** 2013-08-09_

Функция "Звонить по" в Lync позволяет пользователям присоединяться к звуковому каналу конференции с помощью сотового телефона, стационарного телефона или другого устройства, подключенного к телефонной сети общего пользования (ТСОП). При попытке присоединиться к собранию с помощью Lync обычно открывается диалоговое окно **Присоединиться к звуковому каналу собрания**.

![Снимок экрана: окно присоединения к звуковому каналу собрания с помощью Lync](images/Dn383570.e28f17f0-9f17-44ef-b893-f4ef132f47ac(OCS.15).png "Снимок экрана: окно присоединения к звуковому каналу собрания с помощью Lync")

Если выбрать пункт **Звонить по**, то затем можно выбрать в раскрывающемся списке номер телефона. Lync Server 2013 выполнит телефонный звонок на выбранный номер, и вы сможете присоединиться к звуковому каналу конференции с этого телефона.

В раскрывающемся списке приводятся номера телефонов (мобильного, домашнего или других телефонов), которые вы ввели на вкладке **Телефоны** в диалоговом окне **Lync — параметры**.

![Снимок экрана параметров настройки телефонов Lync](images/Dn383570.03d2f25d-49e2-47b4-b1e9-b1614fc0c11c(OCS.15).png "Снимок экрана параметров настройки телефонов Lync")

Если вы не ввели номера телефонов на вкладке **Телефоны**, раскрывающийся список будет пуст. Однако всегда можно выбрать пункт **Новый номер**, чтобы Lync Server выполнил звонок на указанный номер телефона.

![Снимок экрана: окно для ввода номера телефона для присоединения к звуковому каналу собранию Lync](images/Dn383570.27f2ac7a-cc1c-465c-b145-202ad03af4f2(OCS.15).png "Снимок экрана: окно для ввода номера телефона для присоединения к звуковому каналу собранию Lync")

Функция "Звонить по" работает отлично при условии, что вы используете ее по назначению, то есть для выполнения звонков из Lync Server на номера телефонов ТСОП. Однако если вы попытаетесь совершить звонок из Lync Server на конечную точку с поддержкой Lync (например, телефон в конференц-зале), может возникнуть проблема. Ниже приводится ее описание, а также два способа ее решения.

Для начала посмотрим, что произойдет, если указать в функции "Звонить по" номер телефона с поддержкой Lync. Предположим, Алексей Орехов пытается присоединиться к собранию, указывая, что Lync Server должен позвонить ему на номер 1-206-555-1219 (номер телефона с поддержкой Lync Server). Сначала Алексей присоединится к собранию, но через несколько секунд в Lync появится сообщение **Звонок не выполнен или завершен**, и будет казаться, что Алексей был отключен от собрания.

![Снимок экрана конференции со звонками с помощью Lync](images/Dn383570.c2a81727-8751-41b5-946a-03a1b75b9d95(OCS.15).png "Снимок экрана конференции со звонками с помощью Lync")

Однако обратите внимание на несоответствие в окне беседы Lync. В списке **Участники** отображается только Алексей Орехов. Но если посмотреть на заголовок окна, то можно увидеть, что в конференции участвуют четыре человека.

Аналогичным образом, если посмотреть на окно беседы любого другого участника конференции, то можно увидеть, что Алексея Орехова в списке участников нет.

![Снимок экрана: окно списка участников Lync](images/Dn383570.fa5990cf-2694-402c-ac06-946aa66b6837(OCS.15).png "Снимок экрана: окно списка участников Lync")

В то же время Алексей может участвовать в звуковом канале конференции с помощью данного телефона с поддержкой Lync. Функция "Звонить по" сработала, но немного неправильно.

Существует по крайней мере два способа решения этой проблемы. Если вы уже присоединились к конференции таким путем (как это сделал Алексей Орехов), то вы можете задействовать другой режим. Например, если отправить мгновенное сообщение, в окне беседы будут показаны все участники конференции, включая вас.

![Снимок экрана: список бесед и участников Lync](images/Dn383570.9b5ff6d6-9f73-467c-99a7-ef3aa8bd7e7a(OCS.15).png "Снимок экрана: список бесед и участников Lync")

Дальнейшее участие в конференции будет проходить как обычно.

Кроме того, вы можете вовсе избежать этой проблемы, присоединившись к собранию другим способом. Если вам нужно, чтобы Lync Server позвонил на телефон с поддержкой Lync Server, сначала присоединитесь к собранию, не подключаясь к звуковому каналу. Для этого в диалоговом окне "Присоединиться к звуковому каналу собрания" выберите пункт "Не подключать звук".

![Снимок экрана: окно отказа от присоединения к звуковому каналу собрания Lync](images/Dn383570.280a148d-cce5-4b02-87f9-9f78f17a81c1(OCS.15).png "Снимок экрана: окно отказа от присоединения к звуковому каналу собрания Lync")

Успешно присоединившись к собранию, вы можете "пригласить" телефон с поддержкой Lync Server подключиться к собранию. Для этого наведите указатель мыши на значок "Люди" и выберите пункт **Пригласить еще пользователей**.

![Снимок экрана: окно приглашения других участников Lync](images/Dn383570.69b81b29-d1d2-4ed3-acb6-e37dd18e3d86(OCS.15).png "Снимок экрана: окно приглашения других участников Lync")

Откроется диалоговое окно **Отправить мгновенное сообщение**. Не обращая внимания на его заголовок (на самом деле вы не отправляете мгновенное сообщение), введите номер телефона с поддержкой Lync.

![Снимок экрана: диалоговое окно "Отправить мгновенное сообщение"](images/Dn383570.cd67a3f0-06d8-41ba-a808-c067f64bec9f(OCS.15).png "Снимок экрана: диалоговое окно \"Отправить мгновенное сообщение\"")

После нажатия кнопки **ОК**Lync Server позвонит на номер, введенный в этом диалоговом окне. После установления подключения вы сможете использовать все возможности звуковой связи с помощью телефона с поддержкой Lync, а также просматривать полный список участников конференции и взаимодействовать с ними.

