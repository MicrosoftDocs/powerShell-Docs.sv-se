---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxFileLine-resurs
ms.openlocfilehash: 6a91db25638b09659adfabcec78f91bcb2e69dd9
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225598"
---
# <a name="dsc-for-linux-nxfileline-resource"></a>DSC för Linux nxFileLine-resurs

Den **nxFileLine** resursen i PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera rader i en fil på en Linux-nod.

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
| FilePath| Den fullständiga sökvägen till filen för att hantera rader i på målnoden.|
| ContainsLine| En rad för att se till att det finns i filen. Den här raden kommer att läggas till filen om den inte finns i filen. **ContainsLine** är obligatorisk, men kan anges till en tom sträng (`ContainsLine = ""`) om det inte behövs.|
| DoesNotContainPattern| Ett mönster för reguljärt uttryck för rader som inte ska finnas i filen. För alla rader som redan finns i filen som matchar den här reguljärt uttryck, tas raden bort från filen.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exempel

Det här exemplet visar hur du använder den **nxFileLine** resursen för att konfigurera den `/etc/sudoers` filen, vilket säkerställer att användaren: monuser är konfigurerad för att inte requiretty.

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```