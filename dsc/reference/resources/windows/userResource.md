---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-användarresurs
ms.openlocfilehash: 04543351df19160a2da05ccea96e5d392d8c55bf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687505"
---
# <a name="dsc-user-resource"></a>DSC-användarresurs

Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Den **användaren** resursen i Windows PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera lokala användarkonton på målnoden.

## <a name="syntax"></a>Syntax

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   |
|---|---|
| UserName| Anger namnet på kontot som du vill se till att ett visst tillstånd.|
| Beskrivning| Anger den beskrivning som du vill använda för användarkontot.|
| Inaktiverat| Anger om kontot är aktiverat. Den här egenskapen `$true` så att det här kontot är inaktiverat och ange den till `$false` så att den är aktiverad.|
| Se till att| Anger om kontot finns. Ange den här egenskapen ”aktuella” så att konton som finns och ange den till ”” så att kontot inte finns.|
| FullName| Representerar en sträng med det fullständiga namnet som du vill använda för användarkontot.|
| Lösenord| Anger det lösenord som du vill använda för det här kontot. |
| PasswordChangeNotAllowed| Anger om användaren kan ändra lösenordet. Den här egenskapen `$true` så att användaren inte kan ändra lösenordet och ange den till `$false` att tillåta användare att ändra lösenordet. Standardvärdet är `$false`.|
| PasswordChangeRequired| Anger om användaren måste byta lösenord vid nästa inloggning. Den här egenskapen `$true` om användaren måste byta lösenord. Standardvärdet är `$true`.|
| PasswordNeverExpires| Anger om lösenordet upphör att gälla. Att säkerställa att lösenordet för det här kontot upphör aldrig att gälla, ange egenskapen till `$true`, och ge den värdet `$false` om lösenordet upphör att gälla. Standardvärdet är `$false`.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|

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