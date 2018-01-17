---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "DSC för Linux nxScript resurs"
ms.openlocfilehash: c12fb3b405d84eedd13e4cbebf2b2bf0d7cfb4d3
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxscript-resource"></a>DSC för Linux nxScript resurs

Den **nxScript** resurs i PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att köra Linux-skript på en Linux-nod.

## <a name="syntax"></a>Syntax

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Egenskaper

|  Egenskap |  Beskrivning | 
|---|---|
| GetScript| Ger ett skript som körs när du anropar den [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet. Skriptet måste börja med en shebang, till exempel #! / bin/bash.| 
| SetScript| Innehåller ett skript. När du anropar den [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, den **TestScript** körs första. Om den **TestScript** block returnerar slutkoden än 0, den **SetScript** block körs. Om den **TestScript** returnerar slutkoden 0, den **SetScript** körs inte. Skriptet måste börja med en shebang som `#!/bin/bash`.| 
| TestScript| Innehåller ett skript. När du anropar den [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, det här skriptet körs. SetScript körs om den returnerar slutkoden än 0. Om den returnerar slutkoden 0, den **SetScript** körs inte. Den **TestScript** körs även när du anropar den [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet. Men i det här fallet den **SetScript** körs inte, oavsett vilken avslutskoden returneras från den **TestScript**. Den **TestScript** måste returnera slutkoden 0 om faktiska konfigurationen matchar den aktuella konfigurationen tillstånd och ett avsluta code andra än 0 om det inte matchar. (Den aktuella tillståndskonfigurationen är den senaste konfigurationen trätt i kraft på den nod som använder DSC). Skriptet måste börja med en shebang, till exempel 1#!/bin/bash.1| 
| Användare| Användaren att köra skriptet som.| 
| Grupp| Gruppen att köra skriptet som.| 
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** resursens configuration skriptblock som du vill köra först är **ResourceName** och dess typ är **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Exempel

I följande exempel visar hur du använder för den **nxScript** resurs för att utföra ytterligare konfiguration för hantering.

```
Import-DSCResource -Module nx 

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
} 
}
```

