---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxScript resurs
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048657"
---
# <a name="dsc-for-linux-nxscript-resource"></a>DSC för Linux nxScript resurs

Den **nxScript** resurs i PowerShell Desired State Configuration (DSC) är en mekanism för att köra Linux-skript på en Linux-nod.

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
| GetScript| Innehåller ett skript som körs när du anropar den [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet. Skriptet måste börja med en shebang, till exempel #! / bin/bash.|
| SetScript| Innehåller ett skript. När du anropar den [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, den **TestScript** körs första. Om den **TestScript** block returnerar slutkoden än 0, den **SetScript** blocket körs. Om den **TestScript** returnerar slutkoden 0, den **SetScript** körs inte. Skriptet måste börja med en shebang som `#!/bin/bash`.|
| TestScript| Innehåller ett skript. När du anropar den [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, det här skriptet körs. Om den returnerar en slutkod än 0, körs SetScript. Om den returnerar slutkoden 0, den **SetScript** körs inte. Den **TestScript** körs även när du anropar den [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet. Men i det här fallet den **SetScript** inte körs, oavsett vilka avslutskoden returneras från den **TestScript**. Den **TestScript** måste returnera slutkoden 0 om den faktiska konfigurationen matchar aktuella önskad tillståndskonfiguration, och en avsluta code än 0 om det inte matchar. (Den aktuella konfigurationen av önskat tillstånd är den senaste konfigurationen trätt i kraft på den nod som använder DSC). Skriptet måste börja med en shebang, till exempel 1#!/bin/bash.1|
| Användare| Användaren att köra skriptet som.|
| Grupp| Gruppen att köra skriptet som.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exempel

I följande exempel visar hur du använder den **nxScript** resurs att genomföra ytterligare konfiguration.

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