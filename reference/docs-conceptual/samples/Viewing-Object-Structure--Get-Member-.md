---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Visa objekt strukturen Hämta medlem
description: Get-Member är ett kraftfullt verktyg som gör det möjligt att se objektets typ och struktur i PowerShell.
ms.openlocfilehash: 3c294fe47294e2cf8daf125aac55661dd38cf9bb
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501226"
---
# <a name="viewing-object-structure-get-member"></a>Visa objektstrukturen (Get-Member)

Eftersom objekt spelar en sådan central roll i Windows PowerShell finns det flera inbyggda kommandon som är utformade för att fungera med valfria objekt typer. Den viktigaste en är kommandot **Get-Member** .

Den enklaste metoden för att analysera de objekt som ett kommando returnerar är att skicka tillbaka kommandots utdata till cmdleten **Get-Member** . Cmdleten **Get-Member** visar det formella namnet på objekt typen och en fullständig lista över dess medlemmar. Antalet element som returneras kan ibland vara överbelastat. Ett process objekt kan till exempel ha över 100 medlemmar.

Om du vill se alla medlemmar i ett process objekt och sidan utdata så att du kan visa allt, skriver du:

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

Utdata från det här kommandot ser ut ungefär så här:

```Output
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

Vi kan göra den här långa listan över information mer användbar genom filtrering av element som vi vill se. Med kommandot **Get-Member** kan du bara lista medlemmar som är egenskaper. Det finns flera typer av egenskaper. Cmdleten visar egenskaper av valfri typ om vi ställer in parametern **Get-Member MemberType** på värde **egenskaperna**. Den resulterande listan är fortfarande mycket lång, men en lite mer hanterbar:

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> De tillåtna värdena för MemberType är AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, metoder, ParameterizedProperty, MemberSet och alla.

Det finns över 60 egenskaper för en process. Orsaken till att Windows PowerShell ofta visar att det bara finns en fåtal av egenskaperna för ett välkänt objekt är att alla kan ge en ohanterad mängd information.

> [!NOTE]
> Windows PowerShell avgör hur du visar en objekt typ genom att använda information som lagras i XML-filer med namn som slutar på .format.ps1XML. Formatering av data för process objekt, som är .NET system. Diagnostics. process-objekt, lagras i DotNetTypes.format.ps1XML.

Om du behöver titta på andra egenskaper än de som Windows PowerShell visar som standard, behöver du bara formatera utdata. Detta kan göras med hjälp av format-cmdletar.
