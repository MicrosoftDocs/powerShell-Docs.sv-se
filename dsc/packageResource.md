---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC-Paketresurs
ms.openlocfilehash: 68b996e0f51e60bc178c27e3a71f07fb7220f847
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-package-resource"></a>DSC-Paketresurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Den **paketet** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att installera eller avinstallera paket, till exempel Windows Installer och setup.exe paket på målnoden.

## <a name="syntax"></a>Syntax

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a>Egenskaper
|  Egenskap  |  Beskrivning   | 
|---|---| 
| Namn| Anger namnet på paketet som du vill se till att ett visst tillstånd.| 
| Sökväg| Anger sökvägen där paketet finns.| 
| ProductId| Anger produkt-ID som unikt identifierar paketet.| 
| Argument| Visar en sträng med argument som exakt så som kommer att skickas till paketet.| 
| autentiseringsuppgifter| Tillhandahåller åtkomst till paketet på en fjärrkälla. Den här egenskapen används inte för att installera paketet. Paketet installeras alltid på det lokala systemet.| 
| Se till att| Anger om paketet har installerats. Ange den här egenskapen till ”saknas” för att se till att paketet inte är installerat (eller avinstallera paketet om det är installerat). Ange att ”finns” (standardvärdet) för att säkerställa att paketet har installerats.| 
| LogPath| Anger den fullständiga sökvägen där du vill att providern ska spara en loggfil för att installera eller avinstallera paketet.| 
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis **ResourceName** och dess typ är **ResourceType**, syntaxen för den här egenskapen är ”DependsOn =” [ResourceType] ResourceName ”''.| 
| Returkod| Anger den förväntade kod. Om den faktiska returkod matchar inte det förväntade värdet som anges här, konfigurationen returneras ett fel.| 

## <a name="example"></a>Exempel

Det här exemplet kör MSI-installationsprogrammet som finns på den angivna sökvägen och har en angiven produkt-ID.

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    } 
}
```

