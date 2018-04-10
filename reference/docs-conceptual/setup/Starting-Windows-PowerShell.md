---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Starta Windows Powershell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: b56ddc2f577225646729b99f3a2abcb8cc60d307
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="starting-windows-powershell"></a>Starta Windows Powershell
PowerShell är en skriptmiljö motorn DLL-fil som är inbäddade i flera värdar.  De vanligaste värden startas är interaktiva kommandoraden PowerShell.exe och interaktiva Scripting Environment PowerShell_ISE.exe.

Om du vill starta Windows PowerShell® på Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 och Windows 8, se [vanliga hanteringsuppgifter och navigering](http://technet.microsoft.com/library/hh831491.aspx).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Så här startar du Windows PowerShell på tidigare versioner av Windows

Det här avsnittet beskrivs hur du startar Windows PowerShell och Windows PowerShell Integrated Scripting Environment (ISE) på Windows 7, Windows Server® 2008 R2 och Windows Server® 2008. Det beskriver även hur du aktiverar valfri funktion för Windows PowerShell ISE i Windows PowerShell 2.0 på Windows Server® 2008 R2 och Windows Server® 2008.

Använd någon av följande metoder för att starta den installerade versionen av Windows PowerShell 3.0 eller Windows PowerShell 4.0, i tillämpliga fall.

#### <a name="from-the-start-menu"></a>Från Start-menyn

- Klicka på **starta**, typen **PowerShell**, och klicka sedan på **Windows PowerShell**.
- Från den **starta** -menyn klickar du på **starta**, klickar du på **alla program**, klickar du på **tillbehör**, klicka på den **Windows PowerShell**  mappen och klicka sedan på **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>I Kommandotolken

I Cmd.exe, Windows PowerShell eller Windows PowerShell ISE för att starta Windows PowerShell skriver du:

```
PowerShell
```

Du kan också använda parametrarna för PowerShell.exe-programmet för att anpassa sessionen. Mer information finns i [PowerShell.exe-hjälpen](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Med administrativa privilegier (”Kör som administratör”)

Klicka på **starta**, typen **PowerShell**, högerklicka på **Windows PowerShell**, och klicka sedan på **kör som administratör**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Så här startar du Windows PowerShell ISE på tidigare versioner av Windows

Använd någon av följande metoder för att starta Windows PowerShell ISE.

#### <a name="from-the-start-menu"></a>Från Start-menyn

- Klicka på **starta**, typen **ISE**, och klicka sedan på **Windows PowerShell ISE**.
- Från den **starta** -menyn klickar du på **starta**, klickar du på **alla program**, klickar du på **tillbehör**, klicka på den **Windows PowerShell**  mappen och klicka sedan på **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>I Kommandotolken

I Cmd.exe, Windows PowerShell eller Windows PowerShell ISE för att starta Windows PowerShell skriver du:

```
PowerShell_ISE
```

eller

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Med administrativa privilegier (”Kör som administratör”)

Klicka på **starta**, typen **ISE**, högerklicka på **Windows PowerShell ISE**, och klicka sedan på **kör som administratör**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Så här aktiverar du Windows PowerShell ISE på tidigare versioner av Windows

I Windows PowerShell 4.0 och Windows PowerShell 3.0, är Windows PowerShell ISE aktiverad som standard på alla versioner av Windows. Om den inte redan är aktiverad, kan Windows Management Framework 4.0 eller Windows Management Framework 3.0 den.

I Windows PowerShell 2.0, är Windows PowerShell ISE aktiverad som standard på Windows 7. Det kan dock är en valfri funktion i Windows Server 2008 R2 och Windows Server 2008.

Använd följande procedur för att aktivera Windows PowerShell ISE i Windows PowerShell 2.0 på Windows Server 2008 R2 eller Windows Server 2008.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Så här aktiverar du Windows PowerShell Integrated Scripting Environment (ISE)

1. Starta Serverhanteraren.
2. Klicka på **funktioner** och klicka sedan på **Lägg till funktioner**.
3. I Välj funktioner klickar du på Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>Starta 32-bitarsversionen av Windows PowerShell

När du installerar Windows PowerShell på en 64-bitarsdator **Windows PowerShell (x86)**, en 32-bitarsversion av Windows PowerShell installeras förutom 64-bitarsversionen. 64-bitarsversionen körs som standard när du kör Windows PowerShell.

Men du kan ibland behöva köra **Windows PowerShell (x86)**, t.ex. när du använder en modul som kräver 32-bitarsversionen eller när du ansluter via en fjärranslutning till en 32-bitars dator.

Använd någon av följande procedurer för att starta en 32-bitarsversion av Windows PowerShell.

#### <a name="in-windows-server-2012-r2"></a>In Windows Server® 2012 R2

- På den **starta** skriver **Windows PowerShell (x86)**. Klicka på den **Windows PowerShell x86** panelen.
- I **Serverhanteraren**, från den **verktyg** väljer du **Windows PowerShell (x86)**.
- Flytta markören till det övre högra hörnet och klicka på skrivbordet, **Sök**, typen **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)**.
- Ange via kommandoraden: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>In Windows Server® 2012

- På den **starta** skriver **PowerShell** och klicka sedan på **Windows PowerShell (x86)**.
- I **Serverhanteraren**, från den **verktyg** väljer du **Windows PowerShell (x86)**.
- Flytta markören till det övre högra hörnet och klicka på skrivbordet, **Sök**, typen **PowerShell** och klicka sedan på **Windows PowerShell (x86)**.
- Ange via kommandoraden: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>I Windows® 8.1

- På den **starta** skriver **Windows PowerShell (x86)**. Klicka på den **Windows PowerShell x86** panelen.
- Om du kör [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) för Windows 8.1 kan du också öppna Windows PowerShell x86 från den **Server ManagerTools** menyn.
  Välj **Windows PowerShell (x86)**.
- Flytta markören till det övre högra hörnet och klicka på skrivbordet, **Sök**, typen **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)**.
- Ange via kommandoraden: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>In Windows® 8

- På den **starta** skärmen, flyttar markören till det övre högra hörnet, klickar du på **inställningar**, klickar du på **paneler**, och sedan flytta den **visa Administrationsverktyg** skjutreglaget till Ja. Skriv **PowerShell** och på **Windows PowerShell (x86)**.
- Om du kör [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) för Windows 8 kan du också öppna Windows PowerShell x86 från den **Server ManagerTools** menyn. Välj **Windows PowerShell (x86)**.
- På den **starta** skärmen eller skrivbordet, Skriv **PowerShell (x86)** och klicka sedan på **Windows PowerShell (x86)**.
- Ange via kommandoraden: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`