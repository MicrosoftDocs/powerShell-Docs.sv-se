---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-Paketresurs
ms.openlocfilehash: 9285df71a303c9a53dd50d450272575a64e962e7
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048661"
---
# <a name="dsc-package-resource"></a>DSC-Paketresurs

_Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0_

Den **paketet** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att installera eller avinstallera paket, som till exempel Windows Installer och setup.exe paket på målnoden.

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

| Egenskap | Beskrivning |
| --- | --- |
| Namn| Anger namnet på paketet som du vill se till att ett visst tillstånd.|
| Sökväg| Anger sökvägen där paketet finns.|
| productId| Anger produkt-ID som unikt identifierar paketet.|
| Argument| Visar en sträng med argument som exakt så som kommer att skickas till paketet.|
| Autentiseringsuppgifter| Ger åtkomst till paketet på en fjärransluten källa. Den här egenskapen används inte för att installera paketet. Paketet installeras alltid på det lokala systemet.|
| Se till att| Anger om paketet har installerats. Ange den här egenskapen till ”inte” för att kontrollera att paketet inte har installerats (eller avinstallera paketet om det är installerat). Ange den till ”Visa” (standardvärdet) för att säkerställa att paketet har installerats.|
| LogPath| Anger den fullständiga sökvägen där du vill att providern ska spara en loggfil för att installera eller avinstallera paketet.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
| Returkod| Anger den förväntade kod. Om den faktiska returkod matchar inte det förväntade värdet som anges här kan ett fel returneras i konfigurationen.|

## <a name="example"></a>Exempel

Det här exemplet kör MSI-installationsprogrammet som finns på den angivna sökvägen och har angiven produkt-ID.

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