---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-användar resurs
description: DSC-användar resurs
ms.openlocfilehash: 97e68addab7c6048b33a158473f7292f2abadb78
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661545"
---
# <a name="dsc-user-resource"></a>DSC-användar resurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**Användar** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera lokala användar konton på målnoden.

## <a name="syntax"></a>Syntax

```Syntax
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Användarnamn |Anger det konto namn som du vill säkerställa ett speciellt tillstånd för. |
|Beskrivning |Anger beskrivningen som du vill använda för användar kontot. |
|Inaktiverad |Anger om kontot är aktiverat. Ange den här egenskapen till `$true` för att säkerställa att det här kontot är inaktiverat och ange det för att `$false` säkerställa att det är aktiverat. |
|FullName |Representerar en sträng med det fullständiga namn som du vill använda för användar kontot. |
|Lösenord |Anger det lösen ord som du vill använda för det här kontot. |
|PasswordChangeNotAllowed |Anger om användaren kan ändra lösen ordet. Ange den här egenskapen till `$true` om du vill se till att användaren inte kan ändra lösen ordet och ange det som `$false` tillåter användaren att ändra lösen ordet. Standardvärdet är `$false`. |
|PasswordChangeRequired |Anger om användaren måste ändra lösen ordet vid nästa inloggning. Ange den här egenskapen till `$true` om användaren måste ändra lösen ordet. Standardvärdet är `$true`. |
|PasswordNeverExpires |Anger om lösen ordet upphör att gälla. För att se till att lösen ordet för det här kontot aldrig upphör att gälla, anger du egenskapen till `$true` . Ange det som `$false` om lösen ordet upphör att gälla. Standardvärdet är `$false`. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|Kontrol |Anger om kontot finns. Ange att den här egenskapen **finns för att** se till att kontot finns och att det inte finns **något att se** till att kontot inte finns. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```
