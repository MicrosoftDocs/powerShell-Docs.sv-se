---
title: Namngivnings hjälp filer | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: d13324871bac7ba21c0e042e8674c5996e5dba85
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810815"
---
# <a name="naming-help-files"></a>Namnge hjälpfiler

I det här avsnittet beskrivs hur du namnger en XML-baserad hjälpfil så att cmdleten [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) kan hitta den. Namn kraven varierar för varje kommando typ.

## <a name="cmdlet-help-files"></a>Cmdlet-hjälpfiler

Hjälp filen för en C#-cmdlet måste namnges för sammansättningen där cmdleten definieras. Använd följande fil namns format:

```
<AssemblyName>.dll-help.xml
```

Sammansättnings namnets format måste anges även om sammansättningen är en kapslad modul.

Till exempel [Get-WinEvent; PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdleten definieras i sammansättningen Microsoft. PowerShell. Diagnostics. dll. `Get-Help`Cmdleten söker efter ett hjälp avsnitt för `Get-WinEvent` cmdleten endast i filen Microsoft. PowerShell. Diagnostics. dll-Help. xml i modul-katalogen.

## <a name="provider-help-files"></a>Hjälp filer för Provider

Hjälp filen för en Windows PowerShell-Provider måste namnges för sammansättningen där providern definieras. Använd följande fil namns format:

```
<AssemblyName>.dll-help.xml
```

Sammansättnings namnets format måste anges även om sammansättningen är en kapslad modul.

Till exempel definieras certifikat leverantören i sammansättningen Microsoft. PowerShell. Security. dll. `Get-Help`Cmdleten söker bara efter ett hjälp avsnitt för certifikat leverantören i filen Microsoft. PowerShell. Security. dll-Help. xml i modul-katalogen.

## <a name="function-help-files"></a>Funktions hjälp filer

Funktioner kan dokumenteras med hjälp av en [kommenterad hjälp](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) eller dokumenteras i en XML-hjälpfil. När funktionen dokumenteras i en XML-fil måste funktionen ha ett `.ExternalHelp` kommentar nyckelord som associerar funktionen med XML-filen. Annars `Get-Help` kan inte cmdlet: en hitta hjälp filen.

Det finns inga tekniska krav för namnet på en funktions hjälp fil. Vi rekommenderar dock att du namnger hjälp filen för den skript-modul där funktionen definieras. Till exempel definieras följande funktion i filen psm1..

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>Hjälp filer för CIM-kommando

Hjälp filen för ett CIM-kommando måste namnges för den CDXLM-fil där CIM-kommandot definieras. Använd följande fil namns format:

```
<FileName>.cdxml-help.xml
```

CIM-kommandon definieras i CDXLM-filer som kan inkluderas i moduler som kapslade moduler. När CIM-kommandot importeras till sessionen som en funktion lägger Windows PowerShell `.ExternalHelp` till ett kommentar nyckelord till funktions definitionen som associerar funktionen med en XML-hjälpfil som heter för cdxlm-filen där CIM-kommandot definieras.

## <a name="script-workflow-help-files"></a>Hjälpfiler för skript arbets flöde

Skript arbets flöden som ingår i moduler kan dokumenteras i XML-baserade hjälpfiler. Det finns inga tekniska krav för namnet på hjälp filen. Vi rekommenderar dock att du namnger hjälp filen för den skript-modul där skript arbets flödet har definierats. Ett exempel:

```
<ScriptModule>.psm1-help.xml
```

Till skillnad från andra skriptbaserade kommandon behöver inte skript arbets flöden ett `.ExternalHelp` kommentars nyckelord för att koppla dem till en hjälp fil. I stället söker Windows PowerShell efter den UI-kulturbaserade under kataloger i modul katalogen för XML-baserade hjälpfiler och söker efter hjälp för skript arbets flödet i alla filer. `.ExternalHelp`nyckelordet comment ignoreras.

Eftersom `.ExternalHelp` nyckelordet comment ignoreras, `Get-Help` kan cmdleten bara hitta hjälp för skript arbets flöden när de ingår i moduler.
