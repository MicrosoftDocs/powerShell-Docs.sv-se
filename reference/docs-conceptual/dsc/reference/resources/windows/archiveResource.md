---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-Arkiv resurs
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942519"
---
# <a name="dsc-archive-resource"></a>DSC-Arkiv resurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

Arkiv resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att packa upp arkiv (zip-filer) vid en angiven sökväg.

## <a name="syntax"></a>Syntax

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Mål |Anger den plats där du vill se till att Arkiv innehållet extraheras. |
|Sökväg |Anger Arkiv filens käll Sök väg. |
|Kontrollsumma |Definierar den typ som ska användas för att avgöra om två filer är identiska. Om ingen **kontroll Summa** anges används bara fil-eller katalog namnet för jämförelse. Giltiga värden är: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**. Om du anger **kontroll Summa** utan att validera, kommer konfigurationen att Miss **förklaras**. |
|Force |Vissa fil åtgärder (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel. Om du använder **Force** -egenskapen åsidosätts sådana fel. Standardvärdet är **false**. |
|Verifiera| Använder egenskapen **kontroll Summa** för att avgöra om arkivet matchar signaturen. Om du anger **kontroll Summa** utan att validera, kommer konfigurationen att Miss **förklaras**. Om du anger **Verifiera** utan **kontroll Summa**används en _SHA-256-_ **kontrollsumma** som standard. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. |
|Kontrol |Avgör om du ska kontrol lera om arkivets innehåll finns vid **målet**. Ange att den här egenskapen **finns för att** se till att innehållet finns. Ange det som **frånvarande** för att se till att de inte finns. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

Följande exempel visar hur du använder Arkiv resursen för att kontrol lera att innehållet i en arkivfil som heter `Test.zip` finns och extraheras vid ett angivet mål.

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```