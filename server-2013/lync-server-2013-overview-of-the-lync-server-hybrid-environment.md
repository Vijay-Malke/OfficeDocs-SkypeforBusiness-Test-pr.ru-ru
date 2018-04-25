﻿---
title: 'Lync Server 2013: обзор гибридной среды Lync Server'
TOCTitle: Обзор гибридной среды Lync Server 2013
ms:assetid: 0d16ec3a-28f0-4483-96e7-8e68f30398fa
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ204669(v=OCS.15)
ms:contentKeyID: 49308927
ms.date: 06/01/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Обзор гибридной среды Lync Server 2013

 

_**Дата изменения раздела:** 2016-12-08_

Понятие гибридной среды Lync Server 2013 относится к развертыванию, в котором некоторые пользователи размещаются в локальной системе Lync Server 2013, а другие в Lync Online, хотя они совместно используют один домен, например user@contoso.com.

## Сведения о данном руководстве

В данном руководстве описываются задачи по настройке среды Lync Server 2013 для взаимодействия с Lync Online с последующим переводом пользователей из локального развертывания на использование Lync Online.

## Необходимые компоненты

Чтобы выполнить задачи по настройке развертывания для гибридной среды, вам потребуется установить указанные ниже приложения и служебные программы. Установщики для этих файлов находятся на установочном носителе, предоставленном вам для развертывания, а также по ссылкам в следующем списке.

  - [Службы федерации Active Directory (AD FS) 2.0](http://go.microsoft.com/fwlink/p/?linkid=257305)

  - [Средство синхронизации службы каталогов (Майкрософт) 9.1](http://go.microsoft.com/fwlink/p/?linkid=257307)

  - [Установите Windows PowerShell, чтобы использовать единый вход с помощью AD FS](http://go.microsoft.com/fwlink/p/?linkid=398710)

  - Помощник по входу в Microsoft Online Services (msoidcli-7.0.msi) входит в состав установщика обновлений Office 365 для настольных систем, который можно получить на странице загрузки, на которую можно перейти из портала администрирования Office 365.

## Учетные данные администратора

Если предлагается предоставить учетные данные администратора, следует указать имя пользователя и пароль для учетной записи администратора для своего клиента Office 365 tenant. Эти учетные данные также используются при настройке служб федерации Active Directory (AD FS) 2.0, синхронизации службы каталогов, единого входа, федерации и перемещении пользователей к Lync Online.

## Подключение к Lync Online PowerShell

Администраторы теперь могут использовать Windows PowerShell для управления Lync Online и учетными записями пользователей Lync Online. Для этого необходимо сначала загрузить модуль Lync Online Connector из Центра загрузки Майкрософт (http://go.microsoft.com/fwlink/?LinkId=294688), а затем установить его. Дополнительную информацию о загрузке, установке и использованию модуля Lync Online Connector, а также сведения об использовании Windows PowerShell для управления Lync Online см. в разделе [Использование Windows PowerShell для управления Lync Online](skype-for-business-online-using-windows-powershell-to-manage-your-tenant.md).
