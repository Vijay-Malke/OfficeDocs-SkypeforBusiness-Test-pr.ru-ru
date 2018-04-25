﻿---
title: 'Lync Server 2013: определение дополнительных топологий директоров в топологии'
TOCTitle: Определение дополнительных топологий директоров в топологии
ms:assetid: 8e9a659d-23b0-401d-b296-59c7df414d49
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398717(v=OCS.15)
ms:contentKeyID: 49310478
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Определение дополнительных топологий директоров в топологии для Lync Server 2013

 

_**Дата изменения раздела:** 2012-09-08_

Директоры сервера Lync Server 2013 могут быть серверами в одном экземпляре или устанавливаться как пул нескольких Директоров с балансировкой нагрузки для обеспечения более высокого уровня доступности и мощности. Поддерживается как аппаратная балансировка нагрузки, так и балансировка нагрузки на DNS. В этой статье описывается настройка балансировки нагрузки на DNS для пулов Директоров.

Чтобы успешно публиковать, включать или отключать топологию при добавлении или удалении серверной роли, необходимо войти от имени пользователя, являющегося членом групп **RTCUniversalServerAdmins** и **Domain Admins** . Можно также делегировать соответствующие административные права и разрешения для добавления серверных ролей. Подробные сведения см. в разделе [Делегирование разрешений на установку в Lync Server 2013](lync-server-2013-delegate-setup-permissions.md) документации по развертыванию сервера Standard Edition или сервера Enterprise Edition. Для других изменений конфигурации достаточно членства в группе **RTCUniversalServerAdmins** .

В этой статье описываются действия по определению и публикации топологии для двух топологий серверной роли Директор:

  - Определение Директора (единственный экземпляр)

  - Определение Директора (пул из нескольких Директоров)

## Определение Директора (единственный экземпляр)

1.  Запустите построитель топологий: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Построитель топологий Lync Server**.

2.  На странице приветствия нажмите **Download Topology from Existing Deployment (Загрузить топологию из существующего развертывания)** .

3.  В диалоговом окне **Save Topology As (Сохранить топологию как)** введите имя и расположение для локальной копии существующей топологии, а затем нажмите кнопку **Сохранить** .

4.  Разверните узел, в который планируется добавить Директор, щелкните правой кнопкой мыши пункт **Director pools (Пулы Директоров)** , а затем выберите команду **New Director Pool (Создать пул Директоров)** .

5.  В диалоговом окне **Define the Director pool FQDN (Определение полного доменного имени пула Директоров)** выполните следующие действия.
    
      - В поле **Pool FQDN (Полное доменное имя пула)** введите полное доменное имя для пула Директоров.
    
      - Выберите **Single computer pool (Пул с одним компьютером)** и нажмите кнопку **Далее** .

6.  В диалоговом окне **Define the file share (Определение общей папки)** выполните одно из следующих действий.
    
    1.  Чтобы использовать существующую общую папку, выберите **Use a previously defined file share (Использовать существующую общую папку)** , выберите общую папку из списка и нажмите кнопку **Далее** .
    
    2.  Чтобы создать новую общую папку, нажмите **Define a new file share (Задать новую общую папку)** , введите полное доменное имя для расположения этой папки в поле **File Server FQDN (Полное доменное имя файлового сервера)** , введите имя общей папки в поле **File Share (Общая папка)** и нажмите кнопку **Далее** .
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Общая папка, которая была указана или создана в этом действии, должна уже существовать, или ее необходимо создать до публикации топологии.<br />
    Назначенная Директору общая папка в действительности не используется, поэтому можно назначить общую папку из любого пула в организации.</td>
    </tr>
    </tbody>
    </table>


7.  В диалоговом окне **Specify the Web Services URL (Указание URL-адреса веб-служб)** в поле **External Base URL (Внешний базовый URL-адрес)** укажите полное доменное имя для Директоров и нажмите кнопку **Готово** .
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Это имя должно быть разрешаемо из Интернет-серверов доменных имен и указывать на общедоступный IP адрес обратного прокси-сервера, который прослушивает запросы HTTP/HTTPS на этот URL-адрес и представляет их в виртуальном каталоге внешних веб-служб в этом Директоре.</td>
    </tr>
    </tbody>
    </table>
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412910.warning(OCS.15).gif" title="warning" alt="warning" />Предупреждение</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если имеется несколько пулов переднего плана или ролей переднего плана, полное имя домена веб-служб должно быть уникальным. Например, если определить полное имя домена веб-служб для некоторой роли переднего плана как <strong>pool01.contoso.com</strong>, имя <strong>pool01.contoso.com</strong> не удастся использовать для другого пула переднего плана или иной роли переднего плана. Если выполняется также развертывание Директор, полное имя домена внешних веб-служб, определенное для любой роли Директор или любого Директоров, должно отличаться от полного имени домена для любого другого объекта Директор и Директоров, также как и от полного имени домена для любого объекта переднего плана и переднего плана. Если решено переопределить внутренние веб-службы с самоопределяемым полным именем домена, каждое полное имя домена должно отличаться от полного имени домена для любого другого объекта переднего плана, Директор и Директоров.</td>
    </tr>
    </tbody>
    </table>


8.  Опубликуйте топологию.

## Определение Директора (пул из нескольких Директоров)

1.  Запустите построитель топологий: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Построитель топологий Lync Server**.

2.  На странице приветствия нажмите **Download Topology from Existing Deployment (Загрузить топологию из существующего развертывания)** .

3.  В диалоговом окне **Save Topology As (Сохранить топологию как)** введите имя и расположение для локальной копии существующей топологии, а затем нажмите кнопку **Сохранить** .

4.  Разверните узел, в который планируется добавить Директор, щелкните правой кнопкой мыши пункт **Director pools (Пулы Директоров)** , а затем выберите команду **New Director Pool (Создать пул Директоров)** .

5.  В диалоговом окне **Define the Director pool FQDN (Определение полного доменного имени пула Директоров)** выполните следующие действия.
    
      - В поле **Pool FQDN (Полное доменное имя пула)** введите полное доменное имя для пула Директоров.
    
      - Выберите **Multiple computer pool (Пул с несколькими компьютерами)** и нажмите кнопку **Далее** .

6.  В диалоговом окне **Define the computers in this pool (Указание компьютеров в пуле)** выполните следующие действия.
    
      - Укажите полное доменное имя компьютера, который будет первым членом пула, и нажмите кнопку **Добавить** .
    
      - Повторите предыдущее действие для каждого компьютера, который требуется добавить. Закончив, нажмите кнопку **Далее** .

7.  В диалоговом окне **Define the file share (Определение общей папки)** выполните одно из следующих действий.
    
      - Чтобы использовать существующую общую папку, выберите **Use a previously defined file share (Использовать существующую общую папку)** , выберите общую папку из списка и нажмите кнопку **Далее** .
    
      - Чтобы создать новую общую папку, нажмите **Define a new file share (Задать новую общую папку)** , введите полное доменное имя для расположения этой папки в поле **File Server FQDN (Полное доменное имя файлового сервера)** , введите имя общей папки в поле **File Share (Общая папка)** и нажмите кнопку **Далее** .
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Общая папка, которая была указана или создана в этом действии, должна уже существовать, или ее необходимо создать до публикации топологии.<br />
    Назначенная Директору общая папка в действительности не используется, поэтому можно назначить общую папку из любого пула в организации.</td>
    </tr>
    </tbody>
    </table>


8.  В диалоговом окне **Specify the Web Services URL (Указание URL-адреса веб-служб)** в поле **External Base URL (Внешний базовый URL-адрес)** укажите полное доменное имя для Директоров и нажмите кнопку **Готово** .
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Это имя должно быть разрешаемо из Интернет-серверов доменных имен и указывать на общедоступный IP адрес обратного прокси-сервера, который прослушивает запросы HTTP/HTTPS, отправленные на этот URL-адрес, и представляет их в виртуальном каталоге внешних веб-служб в этом Директоре.</td>
    </tr>
    </tbody>
    </table>
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412910.warning(OCS.15).gif" title="warning" alt="warning" />Предупреждение</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если имеется несколько пулов переднего плана или ролей переднего плана, полное имя домена веб-служб должно быть уникальным. Например, если определить полное имя домена веб-служб для некоторой роли переднего плана как <strong>pool01.contoso.com</strong>, имя <strong>pool01.contoso.com</strong> не удастся использовать для другого пула переднего плана или иной роли переднего плана. Если выполняется также развертывание Директор, полное имя домена внешних веб-служб, определенное для любой роли Директор или любого Директоров, должно отличаться от полного имени домена для любого другого объекта Директор и Директоров, также как и от полного имени домена для любого объекта переднего плана и переднего плана. Если решено переопределить внутренние веб-службы с самоопределяемым полным именем домена, каждое полное имя домена должно отличаться от полного имени домена для любого другого объекта переднего плана, Директор и Директоров.</td>
    </tr>
    </tbody>
    </table>


9.  Опубликуйте топологию.
