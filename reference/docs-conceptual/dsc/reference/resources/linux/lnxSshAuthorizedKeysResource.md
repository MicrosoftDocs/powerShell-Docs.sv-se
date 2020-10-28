---
ms.date: 07/17/2020
ms.topic: reference
title: DSC för Linux nxSshAuthorizedKeys-resurs
description: DSC för Linux nxSshAuthorizedKeys-resurs
ms.openlocfilehash: 881e94aa583a745cdac7f01b6e445352ef4ca937
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662761"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>DSC för Linux nxSshAuthorizedKeys-resurs

**NxAuthorizedKeys** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera behöriga SSH-nycklar för en angiven användare.

## <a name="syntax"></a>Syntax

```Syntax
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Kommentar |En unik kommentar för nyckeln. Detta används för att identifiera nycklar unikt. |
|Användarnamn |Användar namnet för hantering av SSH-auktoriserade nycklar för. Om den inte är definierad är standard användaren **roten** . |
|Nyckel |Nyckelns innehåll. Detta **är obligatoriskt om alternativet** är angivet som **tillgängligt** .|

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|Kontrol |Anger om nyckeln har definierats. Ange den här egenskapen som **saknas** för att se till att nyckeln inte finns i användarens auktoriserade nyckel fil. Ange att den **finns** för att säkerställa att nyckeln definieras i användarens auktoriserade nyckel fil. |

## <a name="example"></a>Exempel

I följande exempel definieras en offentlig SSH-auktoriserad nyckel för användaren "monuser".

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxSshAuthorizedKeys myKey
    {
        KeyComment = "myKey"
        Ensure = "Present"
        Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
        UserName = "monuser"
    }
}
```
