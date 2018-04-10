---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Visa objekt struktur Get medlem
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: cc93e45e4306b3d623c1d3d1096dd20c1afc59c8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="viewing-object-structure-get-member"></a>Visa objekt strukturen (Get-medlem)

Eftersom spelas upp på en central roll i Windows PowerShell, finns flera inbyggda kommandon som fungerar med valfri objekttyper. Den viktigaste är den **Get-medlemmen** kommando.

Den enklaste metoden för att analysera objekten som returnerar ett kommando är att skicka utdata från kommandot den **Get-medlemmen** cmdlet. Den **Get-medlemmen** cmdlet visar formella namnet på objekttypen och en fullständig lista över dess medlemmar. Antalet element som returneras kan ibland vara överväldigande. Till exempel kan en process-objektet ha fler än 100 medlemmar.

Om du vill se alla medlemmar i en Process-objektet och sidan utdata så att du kan visa alla, skriver du:

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

Utdata från kommandot ser ut ungefär så här:

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

Vi kan göra det här lång lista med information mer användbara genom att filtrera för element som vi vill se. Den **Get-medlemmen** med kommandot kan du visa en lista med endast medlemmar som är egenskaper. Det finns flera typer av egenskaper. Cmdlet visar egenskaper för någon typ om vi har angetts i **Get-medlemmen MemberType** parametern med värdet **egenskaper**. Listan är fortfarande mycket lång, men lite mer användarvänlig:

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

Det finns över 60 egenskaper för en process. Orsaken till Windows PowerShell ofta visar bara ett fåtal av egenskaper för ett välkänt objekt som visar alla skulle skapa en svårhanterligt mängd information.

> [!NOTE]
> Windows PowerShell avgör hur du visar en objekttyp med hjälp av informationen i XML-filer som har namn som slutar på. format.ps1xml. Formatering data för process-objekt som är .NET System.Diagnostics.Process objekt, lagras i DotNetTypes.format.ps1xml.

Om du behöver titta i andra egenskaper än de som visas som standard i Windows PowerShell måste att formatera utdata själv. Detta kan göras med hjälp av format-cmdlets.