---
title: "Работа с принтерами"
ms.date: 2016-05-11
keywords: "powershell,командлет"
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
translationtype: Human Translation
ms.sourcegitcommit: 3222a0ba54e87b214c5ebf64e587f920d531956a
ms.openlocfilehash: c013124d12a551245152c1703e5f1d8a3f8f5f70

---

# Работа с принтерами
Windows PowerShell можно использовать для управления принтерами с помощью инструментария WMI и COM-объекта WScript.Network с сервера сценариев Windows. Мы будем использовать сочетание обоих средств, чтобы продемонстрировать выполнение конкретных задач.

### Вывод подключений принтеров
Самый простой способ вывести список принтеров, установленных на компьютере, — использовать класс **Win32_Printer** инструментария WMI.

```
Get-WmiObject -Class Win32_Printer -ComputerName
```

Список принтеров можно также вывести с помощью COM-объекта **WScript.Network**, который обычно используется в сценариях сервера сценариев Windows:

```
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Поскольку эта команда возвращает простую коллекцию строк из имен портов и принтеров без отличительных меток, ее непросто интерпретировать.

### Добавление сетевого принтера
Чтобы добавить сетевой принтер, используйте **WScript.Network**:

```
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### Установка принтера по умолчанию
Чтобы задать принтер по умолчанию с помощью инструментария WMI, найдите принтер в коллекции **Win32_Printer**, а затем вызовите метод **SetDefaultPrinter**.

```
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** немного проще в использовании, так как содержит метод **SetDefaultPrinter**, который принимает в качестве аргумента только имя принтера:

```
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### Удаление подключения принтера
Чтобы удалить подключение принтера, используйте метод **WScript.Network RemovePrinterConnection**:

```
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```




<!--HONumber=Aug16_HO4-->


