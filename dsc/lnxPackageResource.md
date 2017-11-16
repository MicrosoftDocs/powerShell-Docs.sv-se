---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "DSC för Linux nxPackage resurs"
ms.openlocfilehash: 11019b1cd12f23b0b498b7cb9a06e02c46c3c279
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxpackage-resource"></a>DSC för Linux nxPackage resurs

Den **nxPackage** resurs i PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att hantera paket på en Linux-nod.

## <a name="syntax"></a>Syntax

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]
    
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap |  Beskrivning | 
|---|---|
| Namn| Namnet på paketet som du vill se till att ett visst tillstånd.| 
| Se till att| Anger om du vill kontrollera att paketet finns. Ange egenskapen ”aktuella” för att säkerställa att paketet finns. Ange den till ”saknas” så paketet inte finns. Standardvärdet är ”saknas”.|  
| PackageManager| Värden som stöds är ”yum”, ”lgh” och ”zypper”. Anger package manager att använda vid installation av paket. Om **FilePath** anges den angivna sökvägen används för att installera paketet. Annars används en Package Manager för att installera paketet från en förkonfigurerad databas. Om varken **PackageManager** eller **FilePath** tillhandahålls standard package manager för systemet används.| 
| filePath| Sökvägen till filen där paketet finns| 
| PackageGroup| Om **$true**, **namn** förväntas vara namnet på en paketeringsgrupp för användning med en **PackageManager**. **PacakgeGroup** är inte giltig när de tillhandahåller en **FilePath**.| 
| Argument| En sträng med argument som exakt så som kommer att skickas till paketet.| 
| Returkod| Förväntade returkoden. Om den faktiska returkod matchar inte det förväntade värdet som anges här, konfigurationen returneras ett fel.| 
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** resursens configuration skriptblock som du vill köra först är **ResourceName** och dess typ är **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Exempel

I följande exempel säkerställer att paketet med namnet ”httpd” är installerad på en Linux-dator med hjälp av ”Yum” package manager.

```
Import-DSCResource -Module nx 

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```

