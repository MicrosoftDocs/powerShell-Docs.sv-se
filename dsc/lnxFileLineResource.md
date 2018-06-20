---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxFileLine resurs
ms.openlocfilehash: 6b927839c23478aa9916a5d23836b31fccc58484
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219641"
---
# <a name="dsc-for-linux-nxfileline-resource"></a>DSC för Linux nxFileLine resurs

Den **nxFileLine** resurs i PowerShell önskad tillstånd Configuration (DSC) ger möjlighet till att hantera rader i en konfigurationsfil på en Linux-nod.

## <a name="syntax"></a>Syntax

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Egenskaper

|  Egenskap |  Beskrivning |
|---|---|
| filePath| Den fullständiga sökvägen till filen som ska hantera rader i på målnoden.|
| ContainsLine| En rad för att se till att det finns i filen. Den här raden läggs till filen om den inte finns i filen. **ContainsLine** är obligatorisk, men kan anges till en tom sträng (”ContainsLine = ''') om den inte behövs.|
| DoesNotContainPattern| Ett mönster för reguljärt uttryck för rader som inte ska finnas i filen. För alla rader som finns i filen som matchar den här reguljärt uttryck, kommer raden tas bort från filen.|
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** resursens configuration skriptblock som du vill köra först är **ResourceName** och dess typ är **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exempel

Det här exemplet visas hur du använder den **nxFileLine** resurs för att konfigurera den `/etc/sudoers` fil, se till att användaren: monuser är konfigurerad att inte requiretty.

```
Import-DSCResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```