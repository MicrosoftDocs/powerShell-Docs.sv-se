---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Starta Windows Powershell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 9184e8b0e508610e7f4775f1032f3a69c93bb8c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058360"
---
# <a name="starting-windows-powershell"></a>Starta Windows Powershell
PowerShell är en scripting motorn DLL-fil som är inbäddad i flera värdar.  De vanligaste värden startas är interaktiva kommandoraden PowerShell.exe och interaktiva Scripting Environment PowerShell_ISE.exe.

Om du vill starta Windows PowerShell® på Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 och Windows 8, se [vanliga hanteringsuppgifter och navigering](https://technet.microsoft.com/library/hh831491.aspx).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Starta Windows PowerShell på tidigare versioner av Windows

Det här avsnittet beskrivs hur du startar Windows PowerShell och Windows PowerShell Integrated Scripting Environment (ISE) på Windows® 7, Windows Server® 2008 R2 och Windows Server® 2008. Den förklarar också hur du aktiverar valfri funktion för Windows PowerShell ISE i Windows PowerShell 2.0 på Windows Server® 2008 R2 och Windows Server® 2008.

Använd någon av följande metoder för att starta den installerade versionen av Windows PowerShell 3.0 eller Windows PowerShell 4.0, om tillämpligt.

#### <a name="from-the-start-menu"></a>Från Start-menyn

- Klicka på **starta**, typ **PowerShell**, och klicka sedan på **Windows PowerShell**.
- Från den **starta** -menyn klickar du på **starta**, klickar du på **alla program**, klickar du på **tillbehör**, klickar du på den **Windows PowerShell**  mappen och klicka sedan på **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>I Kommandotolken

I Cmd.exe, Windows PowerShell eller Windows PowerShell ISE för att starta Windows PowerShell, skriver du:

```
PowerShell
```

Du kan också använda parametrarna för PowerShell.exe-programmet för att anpassa sessionen. Mer information finns i [PowerShell.exe-hjälpen](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Med administrativa behörigheter (”Kör som administratör”)

Klicka på **starta**, typ **PowerShell**, högerklicka på **Windows PowerShell**, och klicka sedan på **kör som administratör**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Starta Windows PowerShell ISE på tidigare versioner av Windows

Använd någon av följande metoder för att starta Windows PowerShell ISE.

#### <a name="from-the-start-menu"></a>Från Start-menyn

- Klicka på **starta**, typ **ISE**, och klicka sedan på **Windows PowerShell ISE**.
- Från den **starta** -menyn klickar du på **starta**, klickar du på **alla program**, klickar du på **tillbehör**, klickar du på den **Windows PowerShell**  mappen och klicka sedan på **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>I Kommandotolken

I Cmd.exe, Windows PowerShell eller Windows PowerShell ISE för att starta Windows PowerShell, skriver du:

```
PowerShell_ISE
```

eller

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Med administrativa behörigheter (”Kör som administratör”)

Klicka på **starta**, typ **ISE**, högerklicka på **Windows PowerShell ISE**, och klicka sedan på **kör som administratör**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Så här aktiverar du Windows PowerShell ISE på tidigare versioner av Windows

I Windows PowerShell 4.0 och Windows PowerShell 3.0, är Windows PowerShell ISE aktiverat som standard i alla versioner av Windows. Om den inte redan är aktiverad, Windows Management Framework 4.0 eller Windows Management Framework 3.0 gör det möjligt.

I Windows PowerShell 2.0, är Windows PowerShell ISE aktiverat som standard på Windows 7. Det kan dock är en valfri funktion i Windows Server 2008 R2 och Windows Server 2008.

Följ anvisningarna nedan om du vill aktivera Windows PowerShell ISE i Windows PowerShell 2.0 på Windows Server 2008 R2 eller Windows Server 2008.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Aktivera Windows PowerShell Integrated Scripting Environment (ISE)

1. Starta Serverhanteraren.
2. Klicka på **funktioner** och klicka sedan på **Lägg till funktioner**.
3. I Välj funktioner klickar du på Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>Starta 32-bitarsversionen av Windows PowerShell

När du installerar Windows PowerShell på en 64-bitarsdator **Windows PowerShell (x86)**, en 32-bitars version av Windows PowerShell är installerat förutom 64-bitarsversionen. När du kör Windows PowerShell, körs 64-bitars version som standard.

Men du kan ibland behöva köra **Windows PowerShell (x86)**, t.ex. när du använder en modul som kräver 32-bitarsversionen eller när du ansluter via en fjärranslutning till en 32-bitars dator.

Använd någon av följande procedurer för att starta en 32-bitars version av Windows PowerShell.

#### <a name="in-windows-server-2012-r2"></a>In Windows Server® 2012 R2

- På den **starta** skärmen, Skriv **Windows PowerShell (x86)**. Klicka på den **Windows PowerShell x86** panelen.
- I **Serverhanteraren**, från den **verktyg** menyn och välj **Windows PowerShell (x86)**.
- Flytta markören till det övre högra hörnet, klicka på skrivbordet, **Search**, typ **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)**.
- Ange via kommandoraden: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>In Windows Server® 2012

- På den **starta** skärmen, Skriv **PowerShell** och klicka sedan på **Windows PowerShell (x86)**.
- I **Serverhanteraren**, från den **verktyg** menyn och välj **Windows PowerShell (x86)**.
- Flytta markören till det övre högra hörnet, klicka på skrivbordet, **Search**, typ **PowerShell** och klicka sedan på **Windows PowerShell (x86)**.
- Ange via kommandoraden: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>I Windows® 8.1

- På den **starta** skärmen, Skriv **Windows PowerShell (x86)**. Klicka på den **Windows PowerShell x86** panelen.
- Om du kör [verktyg för fjärrserveradministration](https://go.microsoft.com/fwlink/?LinkID=304145) för Windows 8.1 kan du också öppna Windows PowerShell x86 från den **Server ManagerTools** menyn.
  Välj **Windows PowerShell (x86)**.
- Flytta markören till det övre högra hörnet, klicka på skrivbordet, **Search**, typ **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)**.
- Ange via kommandoraden: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>In Windows® 8

- På den **starta** skärmen, flyttar markören till det övre högra hörnet, klickar du på **inställningar**, klickar du på **paneler**, och flyttar den **visa Administrationsverktyg** skjutreglaget till Ja. Skriv **PowerShell** och klicka på **Windows PowerShell (x86)**.
- Om du kör [verktyg för fjärrserveradministration](https://www.microsoft.com/download/details.aspx?id=28972) för Windows 8, kan du också öppna Windows PowerShell x86 från den **Server ManagerTools** menyn. Välj **Windows PowerShell (x86)**.
- På den **starta** skärmen eller skrivbordet, Skriv **PowerShell (x86)** och klicka sedan på **Windows PowerShell (x86)**.
- Ange via kommandoraden: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`