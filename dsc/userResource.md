---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "DSC-användarresurs"
ms.openlocfilehash: a4e4e8af4fcfe5c997c460613174d8583261dedf
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
#<a name="dsc-user-resource"></a>DSC-användaren resurs #

 
>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0


Den __användaren__ resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att hantera lokala användarkonton på målnoden.


##<a name="syntax"></a>Syntaxen ##

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
| Inaktiverad| Anger om kontot är aktiverad. Den här egenskapen __$true__ så att det här kontot är inaktiverad och inställd på __$false__ så att den är aktiverad.| 
| Se till att| Anger om kontot finns. Ange egenskapen ”aktuella” för att säkerställa att finns ett konto och ange den till ”saknas” så att kontot inte finns.| 
| Fullständigt namn| Representerar en sträng med det fullständiga namnet som du vill använda för användarkontot.| 
| Lösenord| Anger lösenordet som du vill använda för det här kontot. | 
| PasswordChangeNotAllowed| Anger om användaren kan ändra lösenordet. Den här egenskapen __$true__ så att användaren inte kan ändra lösenordet och Ställ in den på __$false__ att tillåta användaren att ändra lösenordet. Standardvärdet är __$false__.| 
| PasswordChangeRequired| Anger om användaren måste byta lösenord vid nästa inloggning. Den här egenskapen __$true__ om användaren måste ändra lösenordet. Standardvärdet är __$true__.| 
| PasswordNeverExpires| Anger om lösenordet upphör att gälla. Att se till att lösenordet för det här kontot upphör aldrig att gälla, ange egenskapen till __$true__, och ange det till __$false__ om lösenordet upphör att gälla. Standardvärdet är __$false__.| 
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.| 

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

