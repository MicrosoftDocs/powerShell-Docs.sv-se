---
ms.date: 08/28/2020
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsOptionalFeature-resurs
ms.openlocfilehash: f24173c1a9ed605bac43767a9da2d4dbded78883
ms.sourcegitcommit: 06b6f4012e4eca71d414733cdba23ef75535223c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/29/2020
ms.locfileid: "89093258"
---
# <a name="dsc-windowsoptionalfeature-resource"></a>DSC WindowsOptionalFeature-resurs

> Gäller för: Windows PowerShell 5. x

**WindowsOptionalFeature** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att säkerställa att valfria funktioner aktive ras på en målnod.

> [!NOTE]
> **WindowsOptionalFeature** fungerar bara på Windows-klient datorer som Windows 10.

## <a name="syntax"></a>Syntax

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Name |Anger namnet på den funktion som du vill se är aktive rad eller inaktive rad. |
|NoWindowsUpdateCheck |Anger om DISM-kontakter Windows Update (WU) vid sökning efter källfiler för att aktivera en funktion. Om inte `$true` DISM kontaktar Wu. |
|RemoveFilesOnDisable |Ange till `$true` om du vill ta bort alla filer som är associerade med funktionen när **Se** till att den är inställd på **frånvarande**. |
|Loggnivå |Den högsta utmatnings nivån som visas i loggarna. Godkända värden är: **ErrorsOnly**, **ErrorsAndWarning**och **ErrorsAndWarningAndInformation**. |
|LogPath |Sökvägen till logg filen där du vill att resurs leverantören ska logga åtgärden. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|Kontrol |Anger om funktionen är aktive rad. För att se till att funktionen är aktive rad ställer du in den här egenskapen på _Aktivera_. För att se till att funktionen är inaktive rad ställer du in egenskapen på _inaktivera_. Standardvärdet är _Enable_. |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).
