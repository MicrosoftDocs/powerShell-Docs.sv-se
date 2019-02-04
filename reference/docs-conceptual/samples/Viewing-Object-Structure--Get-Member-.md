---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Visa objektstrukturen Get-Member
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: cc93e45e4306b3d623c1d3d1096dd20c1afc59c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687869"
---
# <a name="viewing-object-structure-get-member"></a>Visa objektstrukturen (Get-Member)

Eftersom objekt spelar en central roll i Windows PowerShell, det finns flera inbyggda kommandon som utformats för att fungera med godtyckliga objekttyper. Den viktigaste är den **Get-Member** kommando.

Den enklaste tekniken för att analysera de objekt som returnerar ett kommando är att skicka utdata från kommandot den **Get-Member** cmdlet. Den **Get-Member** cmdlet visar formella namnet på objekttypen och en fullständig lista över dess medlemmar. Antalet element som returneras kan ibland vara överväldigande. Ett processobjekt kan exempelvis ha fler än 100 medlemmar.

Om du vill se alla medlemmar i en processobjektet och sidan utdata så att du kan visa allt det, skriver du:

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

Utdata från det här kommandot ska se ut ungefär så här:

```output
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

Vi kan göra den här lång lista med information mer användbara genom att filtrera för element som vi vill se. Den **Get-Member** kommandot kan du visa endast medlemmar som är egenskaper. Det finns flera typer av egenskaper. Cmdlet visar egenskaper för alla typer av om vi ger den **Get-Member MemberType** parametern till värdet **egenskaper**. Den resulterande listan är fortfarande mycket långa, men lite mer hanterbara:

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
> Tillåtna värden för MemberType är AliasProperty, CodeProperty, egenskapen, NoteProperty, ScriptProperty, egenskaper, PropertySet, metod, CodeMethod, ScriptMethod, metoder, ParameterizedProperty, delmängd och alla.

Det finns över 60 egenskaper för en process. Orsaken till Windows PowerShell ofta visar endast ett fåtal egenskaper för alla välkända objekt som visar alla resulterar i ett svårhanterligt mängd information.

> [!NOTE]
> Windows PowerShell avgör hur du vill visa en objekttyp med hjälp av information som lagras i XML-filer som har namn som slutar på. format.ps1xml. Formatering data för process-objekt, vilket är .NET System.Diagnostics.Process objekt, lagras i DotNetTypes.format.ps1xml.

Om du vill titta på andra egenskaper än de som Windows PowerShell visar som standard kommer du behöva formatera utdata själv. Detta kan göras med hjälp av format-cmdlets.