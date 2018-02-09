---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Starta 32-bitarsversionen av Windows PowerShell
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: d682ce45ebc92cda3a9008ab608bacf9ef8eba57
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/08/2018
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a>Starta 32-bitarsversionen av Windows PowerShell
När du installerar Windows PowerShell på en 64-bitarsdator **Windows PowerShell (x86)**, en 32-bitarsversion av Windows PowerShell installeras förutom 64-bitarsversionen. 64-bitarsversionen körs som standard när du kör Windows PowerShell.

Men du kan ibland behöva köra **Windows PowerShell (x86)**, t.ex. när du använder en modul som kräver 32-bitarsversionen eller när du ansluter via en fjärranslutning till en 32-bitars dator.

Använd någon av följande procedurer för att starta en 32-bitarsversion av Windows PowerShell.

#### <a name="in-windows-server-2012-r2"></a>In Windows Server® 2012 R2

- På den **starta** skriver **Windows PowerShell (x86)**. Klicka på den **Windows PowerShell x86** panelen.

- I **Serverhanteraren**, från den **verktyg** väljer du **Windows PowerShell (x86)**.

- Flytta markören till det övre högra hörnet och klicka på skrivbordet, **Sök**, typen **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)**.

- Ange via kommandoraden:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>In Windows Server® 2012

- På den **starta** skriver **PowerShell** och klicka sedan på **Windows PowerShell (x86)**.

- I **Serverhanteraren**, från den **verktyg** väljer du **Windows PowerShell (x86)**.

- Flytta markören till det övre högra hörnet och klicka på skrivbordet, **Sök**, typen **PowerShell** och klicka sedan på **Windows PowerShell (x86)**.

- Ange via kommandoraden:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>I Windows® 8.1

- På den **starta** skriver **Windows PowerShell (x86)**. Klicka på den **Windows PowerShell x86** panelen.

- Om du kör [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) för Windows 8.1 kan du också öppna Windows PowerShell x86 från den **Server ManagerTools** menyn. Välj **Windows PowerShell (x86)**.

- Flytta markören till det övre högra hörnet och klicka på skrivbordet, **Sök**, typen **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)**.
   
- Ange via kommandoraden:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>In Windows® 8

- På den **starta** skärmen, flyttar markören till det övre högra hörnet, klickar du på **inställningar**, klickar du på **paneler**, och sedan flytta den **visa Administrationsverktyg** skjutreglaget till Ja. Skriv **PowerShell** och på **Windows PowerShell (x86)**.

- Om du kör [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) för Windows 8 kan du också öppna Windows PowerShell x86 från den **Server ManagerTools** menyn. Välj **Windows PowerShell (x86)**.

- På den **starta** skärmen eller skrivbordet, Skriv **PowerShell (x86)** och klicka sedan på **Windows PowerShell (x86)**.

- Ange via kommandoraden:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

