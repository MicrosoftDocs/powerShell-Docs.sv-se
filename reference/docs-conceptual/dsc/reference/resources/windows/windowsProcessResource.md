---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsProcess-resurs
ms.openlocfilehash: e168cdebb04f7ec83b73a537a5f188299f40d8b7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941168"
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess-resurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**WindowsProcess** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism som konfigurerar processer på en målnod.

## <a name="syntax"></a>Syntax

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Argument |Anger en sträng med argument som ska skickas till processen i befintligt skick. Om du behöver skicka flera argument sätter du dem i den här strängen. |
|Sökväg |Sökvägen till den körbara filen för processen. Om detta är fil namnet på den körbara filen (inte den fullständigt kvalificerade sökvägen) kommer DSC-resursen att söka `$env:Path` i miljövariabeln för att hitta den körbara filen. Om värdet för den här egenskapen är en fullständigt kvalificerad sökväg, använder DSC inte `$env:Path` variabeln för att hitta filen och genererar ett fel om sökvägen inte finns. Relativa sökvägar är inte tillåtna. |
|Autentiseringsuppgift |Anger autentiseringsuppgifterna för att starta processen. |
|StandardErrorPath |Anger katalog Sök vägen för att skriva standard felet. En befintlig fil skrivs över. |
|StandardInputPath |Anger standard ingångs platsen. |
|StandardOutputPath |Anger den plats där standard utdata ska skrivas. En befintlig fil skrivs över. |
|WorkingDirectory |Anger den plats som ska användas som den aktuella arbets katalogen för processen. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. |
|Kontrol |Anger om processen finns. Ange att den här egenskapen **finns** för att se till att processen finns. Annars anger du det som **frånvarande**. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |