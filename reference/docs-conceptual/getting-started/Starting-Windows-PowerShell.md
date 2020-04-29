---
ms.date: 12/05/2019
keywords: PowerShell, cmdlet
title: Starta Windows Powershell
ms.openlocfilehash: 97b15a4cd79c77a391451ba917f985f9d99db3f5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "74953831"
---
# <a name="starting-windows-powershell"></a>Starta Windows Powershell

Windows PowerShell är en skript motor `.DLL` som är inbäddad i flera värdar. De vanligaste värdarna som du kommer igång är de interaktiva kommando rads **PowerShell. exe** och den interaktiva skript miljön **powershell_ise. exe**.

För att starta Windows PowerShell® på Windows Server® 2012 R2, Windows® 8,1, Windows Server 2012 och Windows 8, se [vanliga hanterings uppgifter och navigering i Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).

## <a name="powershell-core-has-renamed-binary"></a>PowerShell-kärnan har bytt namn till binär

PowerShell Core, som kallas PowerShell, är version 6 och högre som är öppen källkod och använder .NET Core. Versioner som stöds finns i Windows, macOS och Linux.

Från och med PowerShell 6 har PowerShell-binärfilen bytt namn till **pwsh. exe** för Windows och **pwsh** för MacOS och Linux. Du kan starta PowerShell Preview-versioner med **pwsh-Preview**. Mer information finns i [Vad är nytt i PowerShell Core 6,0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) och [om pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).

Använd följande länkar för att hitta cmdlet-referensen och installations dokumentationen för PowerShell 7:

| Dokument | Länk |
| ----- | ----- |
| Cmdlet-referens | [PowerShell Module Browser](/powershell/module/?view=powershell-7) |
| Windows-installation | [Installera PowerShell Core i Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7) |
| macOS-installation | [Installera PowerShell Core på macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) |
| Linux-installation | [Installera PowerShell Core på Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) |

Information om hur du visar innehåll för andra PowerShell-versioner finns i [så här använder du PowerShell-dokumentationen](../how-to-use-docs.md).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Starta Windows PowerShell i tidigare versioner av Windows

I det här avsnittet beskrivs hur du startar Windows PowerShell och Windows PowerShell ISE (Integrated Scripting Environment) på Windows® 7, Windows Server® 2008 R2 och Windows Server® 2008. Den innehåller också information om hur du aktiverar den valfria funktionen för Windows PowerShell ISE i Windows PowerShell 2,0 på Windows Server® 2008 R2 och Windows Server® 2008.

Använd någon av följande metoder för att starta den installerade versionen av Windows PowerShell 3,0 eller Windows PowerShell 4,0, där det är tillämpligt.

#### <a name="from-the-start-menu"></a>Från Start-menyn

- Klicka på **Start**, Skriv **PowerShell**och klicka sedan på **Windows PowerShell**.
- Gå till **Start** -menyn, klicka på **Start**, klicka på **alla program**, klicka på **tillbehör**, klicka på **Windows PowerShell** -mappen och klicka sedan på **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>I kommando tolken

I **cmd. exe**, Windows PowerShell eller Windows PowerShell ISE startar du Windows PowerShell genom att skriva:

```
PowerShell
```

Du kan också använda parametrarna för **PowerShell. exe** -programmet för att anpassa sessionen. Mer information finns i [kommando rads hjälpen för PowerShell. exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Med administratörs behörighet (kör som administratör)

Klicka på **Start**, Skriv **PowerShell**, högerklicka på **Windows PowerShell**och klicka sedan på **Kör som administratör**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Så här startar du Windows PowerShell ISE på tidigare versioner av Windows

Använd någon av följande metoder för att starta Windows PowerShell ISE.

#### <a name="from-the-start-menu"></a>Från Start-menyn

- Klicka på **Start**, Skriv **ISE**och klicka sedan på **Windows PowerShell ISE**.
- Gå till **Start** -menyn, klicka på **Start**, klicka på **alla program**, klicka på **tillbehör**, klicka på **Windows PowerShell** -mappen och klicka sedan på **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>I kommando tolken

I **cmd. exe**, Windows PowerShell eller Windows PowerShell ISE startar du Windows PowerShell genom att skriva:

```
PowerShell_ISE
```

eller

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Med administratörs behörighet (kör som administratör)

Klicka på **Start**, Skriv **ISE**, högerklicka på **Windows PowerShell ISE**och klicka sedan på **Kör som administratör**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Så här aktiverar du Windows PowerShell ISE på tidigare versioner av Windows

I Windows PowerShell 4,0 och Windows PowerShell 3,0 är Windows PowerShell ISE aktiverat som standard i alla versioner av Windows. Om den inte redan är aktive rad kan du använda Windows Management Framework 4,0 eller Windows Management Framework 3,0.

I Windows PowerShell 2,0 är Windows PowerShell ISE aktiverat som standard i Windows 7. Men på Windows Server 2008 R2 och Windows Server 2008 är det en valfri funktion.

Använd följande procedur om du vill aktivera Windows PowerShell ISE i Windows PowerShell 2,0 på Windows Server 2008 R2 eller Windows Server 2008.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Aktivera Windows PowerShell ISE (Integrated Scripting Environment)

1. Starta Serverhanteraren.
2. Klicka på **funktioner** och sedan på **Lägg till funktioner**.
3. I Välj funktioner klickar du på Windows PowerShell ISE (Integrated Scripting Environment).

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>Starta 32-bitars versionen av Windows PowerShell

När du installerar Windows PowerShell på en 64-bitars dator installeras **Windows PowerShell (x86)** och en 32-bitars version av Windows PowerShell installeras förutom 64-bitars versionen. När du kör Windows PowerShell körs 64-bitars versionen som standard.

Du kan dock ibland behöva köra **Windows PowerShell (x86)**, till exempel när du använder en modul som kräver 32-bitars versionen eller när du ansluter fjärran slutet till en 32-bitars dator.

Använd någon av följande procedurer för att starta en 32-bitars version av Windows PowerShell.

#### <a name="in-windows-server-2012-r2"></a>I Windows Server® 2012 R2

- Skriv **Windows PowerShell (x86)** på **Start** skärmen. Klicka på **Windows PowerShell x86** -panelen.
- I **Serverhanteraren**väljer du **Windows PowerShell (x86)** från **verktyg** -menyn.
- Flytta markören till det övre högra hörnet på Skriv bordet, klicka på **Sök**, Skriv **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)**.
- Via kommando rad anger du:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>I Windows Server® 2012

- På **Start** skärmen skriver du **PowerShell** och klickar sedan på **Windows PowerShell (x86)**.
- I **Serverhanteraren**väljer du **Windows PowerShell (x86)** från **verktyg** -menyn.
- Flytta markören till det övre högra hörnet på Skriv bordet, klicka på **Sök**, Skriv **PowerShell** och klicka sedan på **Windows PowerShell (x86)**.
- Via kommando rad anger du:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>I Windows® 8,1

- Skriv **Windows PowerShell (x86)** på **Start** skärmen. Klicka på **Windows PowerShell x86** -panelen.
- Om du kör [verktyg för fjärrserveradministration](https://go.microsoft.com/fwlink/?LinkID=304145) för Windows 8,1 kan du också öppna Windows PowerShell x86 från menyn **Server ManagerTools** . Välj **Windows PowerShell (x86)**.
- Flytta markören till det övre högra hörnet på Skriv bordet, klicka på **Sök**, Skriv **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)**.
- Via kommando rad anger du:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>I Windows® 8

- På **Start** skärmen flyttar du markören till det övre högra hörnet, klickar på **Inställningar**, klickar på **paneler**och flyttar sedan skjutreglaget **Visa administrations verktyg** till **Ja**. Skriv sedan **PowerShell** och klicka på **Windows PowerShell (x86)**.
- Om du kör [verktyg för fjärrserveradministration](https://www.microsoft.com/download/details.aspx?id=28972) för Windows 8 kan du också öppna Windows PowerShell x86 från menyn **Server ManagerTools** . Välj **Windows PowerShell (x86)**.
- Skriv **PowerShell (x86)** på **Start** skärmen eller Skriv bordet och klicka sedan på **Windows PowerShell (x86)**.
- Via kommando rad anger du:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`
