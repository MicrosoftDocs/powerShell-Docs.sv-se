---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Starta PowerShell på tidigare versioner av Windows"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: 52e3acc1fd3009ecad3b7134008e38d4edfb5ca7
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/08/2018
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a>Starta PowerShell på tidigare versioner av Windows
Det här avsnittet beskrivs hur du startar Windows PowerShell och Windows PowerShell Integrated Scripting Environment (ISE) på Windows 7, Windows Server® 2008 R2 och Windows Server® 2008. Det beskriver även hur du aktiverar valfri funktion för Windows PowerShell ISE i Windows PowerShell 2.0 på Windows Server® 2008 R2 och Windows Server® 2008.

Om du vill installera Windows PowerShell 4.0 på system som stöds, hämta och installera [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881). Mer information finns i [installera Windows PowerShell](Installing-Windows-PowerShell.md).

Om du vill installera Windows PowerShell 3.0 på system som stöds, hämta och installera [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290). Mer information finns i [installera Windows PowerShell](Installing-Windows-PowerShell.md).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Så här startar du Windows PowerShell på tidigare versioner av Windows
Använd någon av följande metoder för att starta den installerade versionen av Windows PowerShell 3.0 eller Windows PowerShell 4.0, i tillämpliga fall.

#### <a name="from-the-start-menu"></a>Från Start-menyn

- Klicka på **starta**, typen **PowerShell**, och klicka sedan på **Windows PowerShell**.

- Från den **starta** -menyn klickar du på **starta**, klickar du på **alla program**, klickar du på **tillbehör**, klicka på den **Windows PowerShell**  mappen och klicka sedan på **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>I Kommandotolken

- I Cmd.exe, Windows PowerShell eller Windows PowerShell ISE för att starta Windows PowerShell skriver du:

    ```
    PowerShell
    ```

    Du kan också använda parametrarna för PowerShell.exe-programmet för att anpassa sessionen. Mer information finns i [PowerShell.exe-hjälpen](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Med administrativa privilegier (”Kör som administratör”)

1. Klicka på **starta**, typen **PowerShell**, högerklicka på **Windows PowerShell**, och klicka sedan på **kör som administratör**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Så här startar du Windows PowerShell ISE på tidigare versioner av Windows
Använd någon av följande metoder för att starta Windows PowerShell ISE.

#### <a name="from-the-start-menu"></a>Från Start-menyn

- Klicka på **starta**, typen **ISE**, och klicka sedan på **Windows PowerShell ISE**.

- Från den **starta** -menyn klickar du på **starta**, klickar du på **alla program**, klickar du på **tillbehör**, klicka på den **Windows PowerShell**  mappen och klicka sedan på **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>I Kommandotolken

- I Cmd.exe, Windows PowerShell eller Windows PowerShell ISE för att starta Windows PowerShell skriver du:

    ```
    PowerShell_ISE
    ```

    eller

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Med administrativa privilegier (”Kör som administratör”)

1. Klicka på **starta**, typen **ISE**, högerklicka på **Windows PowerShell ISE**, och klicka sedan på **kör som administratör**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Så här aktiverar du Windows PowerShell ISE på tidigare versioner av Windows
I Windows PowerShell 4.0 och Windows PowerShell 3.0, är Windows PowerShell ISE aktiverad som standard på alla versioner av Windows. Om den inte redan är aktiverad, kan Windows Management Framework 4.0 eller Windows Management Framework 3.0 den.

I Windows PowerShell 2.0, är Windows PowerShell ISE aktiverad som standard på Windows 7. Det kan dock är en valfri funktion i Windows Server 2008 R2 och Windows Server 2008.

Använd följande procedur för att aktivera Windows PowerShell ISE i Windows PowerShell 2.0 på Windows Server 2008 R2 eller Windows Server 2008.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Så här aktiverar du Windows PowerShell Integrated Scripting Environment (ISE)

1. Starta Serverhanteraren.

2. Klicka på **funktioner** och klicka sedan på **Lägg till funktioner**.

3. I Välj funktioner klickar du på Windows PowerShell Integrated Scripting Environment (ISE).

