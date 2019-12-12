---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxScript-resurs
ms.openlocfilehash: a7f2114aba47bb581cdd19168e784b79dfc5b6ad
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941413"
---
# <a name="dsc-for-linux-nxscript-resource"></a>DSC för Linux nxScript-resurs

**NxScript** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att köra Linux-skript på en Linux-nod.

## <a name="syntax"></a>Syntax

```Syntax
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

|Egenskap |Beskrivning |
|---|---|
|GetScript |Innehåller ett skript för att returnera datorns aktuella status. Det här skriptet körs när du anropar [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) -skriptet. Skriptet måste börja med en Shebang, t. ex. `#!/bin/bash`. |
|SetScript |Innehåller ett skript som placerar datorn i korrekt tillstånd. När du anropar [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) -skriptet körs **TestScript** först. Om **TestScript** -blocket returnerar en annan slutkod än 0, kommer **SetScript** -blocket att köras. Om **TestScript** returnerar slut koden 0 så körs inte **SetScript** . Skriptet måste börja med en Shebang, t. ex. `#!/bin/bash`. |
|TestScript |Innehåller ett skript som utvärderar om noden för närvarande är i rätt tillstånd. När du anropar [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) -skriptet körs det här skriptet. Om den returnerar en annan slutkod än 0, kommer **SetScript** att köras. Om den returnerar slut koden 0 körs inte **SetScript** . **TestScript** körs också när du anropar [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) -skriptet. I det här fallet kommer dock **SetScript** inte att köras, oavsett vilken slutkod som returneras från **TestScript**. **TestScript** måste innehålla innehåll och måste returnera avslutnings koden 0 om den faktiska konfigurationen matchar den aktuella önskade tillstånds konfigurationen och en annan slutkod än 0 om den inte matchar. Den aktuella önskade tillstånds konfigurationen är den sista konfigurationen som används på den nod som använder DSC. Skriptet måste börja med en Shebang, t. ex. `#!/bin/bash`. |
|Användare |Användaren att köra skriptet som. |
|Grupp |Gruppen att köra skriptet som. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"`. |

## <a name="example"></a>Exempel

I följande exempel demonstreras användningen av **nxScript** -resursen för att utföra ytterligare konfigurations hantering.

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxScript KeepDirEmpty {

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
