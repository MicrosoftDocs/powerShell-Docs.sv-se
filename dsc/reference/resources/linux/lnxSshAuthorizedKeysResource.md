---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxSshAuthorizedKeys-resurs
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048814"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>DSC för Linux nxSshAuthorizedKeys-resurs

Den **nxAuthorizedKeys** resurs i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera behörighet ssh-nycklar för en angiven användare.

## <a name="syntax"></a>Syntax

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Egenskaper

|  Egenskap |  Beskrivning |
|---|---|
| KeyComment| En unik kommentar för nyckeln. Det här används för att unikt identifiera nycklar.|
| Se till att| Anger om nyckeln har definierats. Ange den här egenskapen till ”inte” för att se till att nyckeln inte finns i användarens auktoriserad nyckelfil. Ange den ”aktuella” för att se till att nyckeln har definierats i användarens auktoriserade nyckelfilen.|
| Användarnamn| Användarnamnet för att hantera ssh behörighet nycklar för. Om du inte har definierats, är standardanvändaren ”rot”.|
| Tangent| Innehållet i nyckeln. Detta krävs om **Kontrollera** är inställd på ”tillgänglig”.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exempel

Följande exempel definierar en offentlig ssh auktoriserad nyckel för användaren ”monuser”.

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```