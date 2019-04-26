---
title: Namnge hjälpfiler | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082189"
---
# <a name="naming-help-files"></a>Namnge hjälpfiler

Det här avsnittet beskriver hur du namnger en XML-baserade hjälpfil så att den [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet kan hitta den. Krav för namnet skiljer sig åt för varje kommando.

## <a name="cmdlet-help-files"></a>Cmdlet-hjälpfiler

I hjälpfilen en C# cmdlet måste ha namnet för sammansättningen där cmdleten har definierats. Använd formatet följande namn:

```
<AssemblyName>.dll-help.xml
```

Sammansättningen namnformat krävs även när sammansättningen är en kapslad modul.

Till exempel den [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet har definierats i sammansättningen Microsoft.PowerShell.Diagnostics.dll. Den `Get-Help` cmdleten söker efter ett hjälpavsnitt för de `Get-WinEvent` cmdlet endast i filen Microsoft.PowerShell.Diagnostics.dll help.xml i modulkatalogen.

## <a name="provider-help-files"></a>Providern hjälpfiler

I hjälpfilen för en Windows PowerShell-provider måste ha namnet för sammansättningen som providern definieras. Använd formatet följande namn:

```
<AssemblyName>.dll-help.xml
```

Sammansättningen namnformat krävs även när sammansättningen är en kapslad modul.

Till exempel har certifikatleverantör definierats i sammansättningen Microsoft.PowerShell.Security.dll. Den `Get-Help` cmdleten söker efter ett hjälpavsnitt för certifikatleverantör endast i filen Microsoft.PowerShell.Security.dll help.xml i modulkatalogen.

## <a name="function-help-files"></a>Funktionen hjälpfiler

Functions kan dokumenteras med hjälp av [kommentarbaserad hjälp](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) eller dokumenterade i en XML-hjälpfilen. När funktionen dokumenteras i en XML-fil, funktionen måste ha en `.ExternalHelp` kommentera nyckelord som associerar funktionen med XML-filen. I annat fall den `Get-Help` cmdlet kan inte hitta hjälpfilen.

Det finns inga tekniska krav för namnet för en funktion hjälpfilen. Ett bra tips är dock att namnge i hjälpfilen för modulen skriptet där funktionen har definierats. Till exempel har följande funktion definierats i filen Minmodul.psm1.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>CIM-kommandot hjälpfiler

I hjälpfilen för en CIM-kommandot måste ha namnet för filen CDXLM som CIM-kommandot har definierats. Använd formatet följande namn:

```
<FileName>.cdxml-help.xml
```

CIM-kommandon har definierats i CDXLM-filer som kan tas med i moduler som kapslade moduler. När kommandot CIM har importerats till sessionen som en funktion, Windows PowerShell lägger till en `.ExternalHelp` kommentar nyckelord till funktionsdefinitionen som associerar funktionen med hjälp ett XML-fil som heter för CDXLM-filen som CIM-kommandot har definierats.

## <a name="script-workflow-help-files"></a>Skript-arbetsflöde hjälpfiler

Arbetsflöden för skript som ingår i moduler kan dokumenteras i XML-baserade hjälpfiler. Det finns inga tekniska krav för namn på hjälpfilen. Ett bra tips är dock att namnge i hjälpfilen för modulen skript som skriptarbetsflödet definieras. Till exempel:

```
<ScriptModule>.psm1-help.xml
```

Till skillnad från andra skriptkommandon skriptarbetsflöden kräver inte en `.ExternalHelp` kommentera nyckelord för att associera dem med en hjälpfilen. I stället Windows PowerShell söker UI-kultur-specifika underkataloger i modulkatalogen för XML-baserade hjälpfiler och söker efter hjälp för skriptarbetsflödet i alla filer. `.ExternalHelp` kommentera nyckelordet ignoreras.

Eftersom den `.ExternalHelp` kommentar nyckelordet ignoreras den `Get-Help` cmdlet kan få hjälp med att skriptarbetsflöden endast när de ingår i moduler.