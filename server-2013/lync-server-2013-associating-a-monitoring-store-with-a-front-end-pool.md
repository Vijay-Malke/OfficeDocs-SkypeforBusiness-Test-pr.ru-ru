﻿---
title: Связь хранилища мониторинга с пулом переднего плана в Lync Server 2013
TOCTitle: Связь хранилища мониторинга с пулом переднего плана
ms:assetid: d3a20d5e-3f24-4cff-bc9b-4f84fea30e6b
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ205271(v=OCS.15)
ms:contentKeyID: 49311271
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Связь хранилища мониторинга с пулом переднего плана в Lync Server 2013

 

_**Дата изменения раздела:** 2013-04-22_

В Microsoft Lync Server 2013 данные мониторинга можно собрать в интерфейсных пулах, связанных с хранилищем мониторинга. Эта задача обычно определяется в средстве построения топологии. Чтобы связать хранилище мониторинга с новым интерфейсным пулом, установите флажок **Мониторинг (регистрация вызовов и ведение журнала показателей качества взаимодействия)** на странице **Выбор компонентов** мастера определения нового интерфейсного пула. Учтите, что если этот параметр выбран, вы также должны указать хранилище SQL для завершения работы мастера. Но это хранилище необязательно должно существовать на момент запуска мастера. Это означает, что вы сначала можете связать пул с хранилищем мониторинга и настроить это хранилище позднее.

Или же вы можете связать существующий интерфейсный пул с новым или другим хранилищем мониторинга, выполнив следующие действия.

1.  Нажмите кнопку **Пуск** и затем последовательно выберите **Все программы**, **Microsoft Lync Server 2013** и **Средство построения топологий Lync Server**.

2.  В диалоговом окне **топологий** выберите **Загрузить топологию из существующего развертывания**, а затем щелкните **ОК**.

3.  В диалоговом окне **Сохранить как** введите имя файла для текущей топологии, затем нажмите кнопку **Сохранить**. Сохраненную топологию можно позднее извлечь и опубликовать при наличии проблем с новой топологией.

4.  В средстве построения топологий разверните узел **Lync Server 2013**, разверните имя сайта с интерфейсным пулом, а затем — **Интерфейсные пулы Enterprise Edition**.

5.  Щелкните правой кнопкой имя пула, который нужно связать с хранилищем мониторинга, и выберите команду **Изменить свойства**.

6.  В диалоговом окне **Изменить свойства** на вкладке **Общие** выберите параметр **Мониторинг (показатели CDR и QoE)**, а затем выберите существующую базу данных SQL Server в раскрывающемся списке **Хранилище мониторинга SQL Server**. (Или нажмите кнопку **Создать**, чтобы связать пул с новым хранилищем базы данных.) Если вы решили использовать новое хранилище, то в диалоговом окне **Определение нового хранилища SQL** введите полное доменное имя компьютера с SQL Server в поле **Полное доменное имя SQL Server**. Если вы хотите использовать экземпляр SQL Server по умолчанию для этого хранилища, выберите параметр **Экземпляр по умолчанию**; в противном случае выберите **Именованный экземпляр** и введите имя экземпляра в поле **Именованный экземпляр**.
    
    В диалоговом окне **Изменить свойства** также представлена возможность создания зеркала SQL для базы данных мониторинга (зеркало SQL позволяет хранить две копии базы данных мониторинга, одна из которых хранится на компьютере хранилища мониторинга, а другая — на компьютере зеркала SQL). Чтобы включить зеркалирование, выберите параметр **Этот экземпляр SQL используется для зеркалирования** и введите номер порта зеркального сервера в поле **Номер порта зеркала**.

7.  В диалоговом окне **Свойства** нажмите кнопку **ОК**.

После связи хранилища мониторинга с интерфейсным пулом необходимо опубликовать новую топологию, чтобы изменения вступили в силу. Для этого выполните следующие действия в средстве построения топологии.

1.  Щелкните **Действие**, наведите указатель на пункт **Топология**, а затем нажмите кнопку **Опубликовать**.

2.  В мастере публикации топологии на странице **Опубликовать топологию** нажмите **Далее**.

3.  На странице **Завершение мастера публикации** нажмите кнопку **Готово**.

После публикации топологии вы можете установить базу данных мониторинга на компьютер, на котором будет размещено хранилище мониторинга. Базу данных мониторинга можно установить с помощью Командная консоль Lync Server и Windows PowerShell. Чтобы установить ее локально (т. е. установить базу данных на тот же компьютер, на котором выполняется Командная консоль Lync Server), откройте командную консоль на соответствующем компьютере, а затем введите следующую команду и нажмите клавишу ВВОД:

    Install-CsDatabase -LocalDatabases

После выполнения предыдущей команды командлет Install-CsDatabase читает текущую топологию Lync Server, определяет, какие базы данных нужно установить на локальный компьютер, а затем автоматически устанавливает и настраивает каждую из этих баз данных.

Чтобы установить базу данных на удаленном компьютере (т. е. на компьютере, отличном от того, на котором запущена командная консоль), вы должны указать по крайней мере два параметра: ConfiguredDatabases и SqlServerFqdn. Они сообщают командлету Install-CsDatabase о необходимости извлечения топологии Lync Server и последующей установки и настройки необходимых баз данных на компьютере, указанном параметром SqlServerFqdn. Для параметра SqlServerFqdn должно использоваться значение, представляющее полное доменное имя компьютера, на котором будут установлены базы данных.

Например, следующая команда устанавливает базу данных мониторинга на компьютер atl-sql-001.litwareinc.com:

    Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn atl-sql-001.litwareinc.com

Или же вы можете установить базу данных мониторинга, запустив мастер развертывания Lync Server на компьютере, на котором будет размещаться хранилище мониторинга. Для этого войдите на соответствующий компьютер и выполните следующие действия.

1.  Нажмите кнопку **Пуск** и последовательно выберите пункты **Программы**, **Microsoft Lync Server 2013** и **Мастер развертывания Lync Server**.

2.  В мастере развертывания выберите **Установить или обновить систему Lync Server**.

3.  На странице **Развертывание** в разделе **Шаг 2. Установка и удаление компонентов Lync Server** нажмите кнопку **Запустить снова**.

4.  В мастере настройки компонентов Lync Server на странице **Настройка компонентов Lync Server** нажмите кнопку **Далее**.

5.  На странице **Указать путь к MSI-файлам** введите путь к файлу Ocscore.msi (файлу, включенному на установочный носитель Lync Server), а затем нажмите кнопку **Далее**.

6.  На странице **выполнения команд** нажмите кнопку **Готово**.

Чтобы убедиться, что все необходимые службы Lync Server запущены, нажмите кнопку **Выполнить** под заголовком **Шаг 4. Запуск служб** на странице **Развертывание**.

