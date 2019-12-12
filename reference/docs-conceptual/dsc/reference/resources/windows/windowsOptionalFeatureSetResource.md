---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsOptionalFeatureSet-resurs
ms.openlocfilehash: f378006a6c362ee9890d70dd76fb552dd262a544
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941189"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>DSC WindowsOptionalFeatureSet-resurs

> Gäller för: Windows PowerShell 5. x

**WindowsOptionalFeatureSet** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att säkerställa att valfria funktioner aktive ras på en målnod. Den här resursen är en [sammansatt resurs](../../../resources/authoringResourceComposite.md) som anropar [WindowsOptionalFeature-resursen](windowsOptionalFeatureResource.md) för varje funktion som anges i egenskapen **Name** .

Använd den här resursen när du vill konfigurera ett antal Windows-valfria funktioner till samma tillstånd.

## <a name="syntax"></a>Syntax

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Namn |Anger namnet på de funktioner som du vill se är aktiverade eller inaktiverade. |
|Källa |Inte implementerat. |
|NoWindowsUpdateCheck |Anger om DISM-kontakter Windows Update (WU) vid sökning efter källfiler för att aktivera funktioner. Om `$true`kan DISM inte kontakta WU. |
|RemoveFilesOnDisable |Ange till `$true` om du vill ta bort alla filer som är associerade med funktionerna när **Se** till att de har angetts som **frånvarande**. |
|Loggnivå |Den högsta utmatnings nivån som visas i loggarna. Godkända värden är: **ErrorsOnly**, **ErrorsAndWarning**och **ErrorsAndWarningAndInformation**. |
|LogPath |Sökvägen till logg filen där du vill att resurs leverantören ska logga åtgärden. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"`. |
|Kontrol |Anger om funktionerna är aktiverade. För att se till att funktionerna är aktiverade ställer du in egenskapen på **Aktivera**. För att se till att funktionerna är inaktiverade ställer du in egenskapen på **inaktivera**. Standardvärdet är **Enable**. |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).