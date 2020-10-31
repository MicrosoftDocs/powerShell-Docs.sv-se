---
ms.date: 07/16/2020
ms.topic: reference
title: DSC ProcessSet-resurs
description: DSC ProcessSet-resurs
ms.openlocfilehash: 3e09c8c7b4ca7d8e95b36f9d4c20c2a85abad9dd
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142573"
---
# <a name="dsc-processset-resource"></a>DSC ProcessSet-resurs

> Gäller för: Windows PowerShell 5. x

**ProcessSet** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism som konfigurerar processer på en målnod.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntax

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Sökväg |Sökvägen till den körbara filen för processen. Om dessa är namnen på de körbara filerna (inte fullständigt kvalificerade sökvägar) kommer DSC-resursen att söka i `$env:Path` miljövariabeln för att hitta filerna. Om värdet för den här egenskapen är fullständigt kvalificerade sökvägar använder DSC inte `$env:Path` miljövariabeln för att hitta filerna och genererar ett fel om någon av Sök vägarna inte finns. Relativa sökvägar är inte tillåtna. |
|Autentiseringsuppgift |Anger autentiseringsuppgifterna för att starta processen. |
|StandardErrorPath |Sökvägen till vilken processerna skriver standard fel. En befintlig fil skrivs över. |
|StandardInputPath |Den data ström som processen tar emot standar in från. |
|StandardOutputPath |Sökvägen till filen som processerna skriver till standard utdata till. En befintlig fil skrivs över. |
|WorkingDirectory |Den plats som används som den aktuella arbets katalogen för processerna. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|Kontrol |Anger om processerna finns. Ange att den här egenskapen **finns** för att se till att processen finns. Annars anger du det som **frånvarande** . Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).
