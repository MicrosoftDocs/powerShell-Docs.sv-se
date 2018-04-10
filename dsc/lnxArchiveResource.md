---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxArchive resurs
ms.openlocfilehash: 142f0317914f1bd3a0523d706b19662f3f64c8b6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxarchive-resource"></a>DSC för Linux nxArchive resurs

Den **nxArchive** resurs i PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att packa upp (.tar, .zip) arkivfiler på en specifik sökväg på en Linux-nod.

## <a name="syntax"></a>Syntax

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap |  Beskrivning |
|---|---|
| Källsökväg| Anger källsökvägen för arkivfilen. Detta bör vara en .tar .zip, eller..GZ-filen. |
| Målsökväg| Anger den plats där du vill se till att arkivera innehåll extraheras.|
| Kontrollsumma| Definierar den typ som används när du fastställer om arkivet som källa har uppdaterats. Värden är: ”ctime”, ”mtime” eller ”md5”. Standardvärdet är ”md5”.|
| Force| Vissa åtgärder (till exempel skriver över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel. Med hjälp av den **kraft** egenskapen åsidosätter sådana fel. Standardvärdet är **$false**.|
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** resursens configuration skriptblock som du vill köra först är **ResourceName** och dess typ är **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
| Se till att| Anger om du vill kontrollera om det finns innehåll till arkivet på den **mål**. Ange egenskapen ”aktuella” för att säkerställa att innehållet finns. Ange den till ”saknas” för att säkerställa att de inte finns. Standardvärdet är ”saknas”.|

## <a name="example"></a>Exempel

I följande exempel visas hur du använder den **nxArchive** resurs så att innehållet i en fil för `website.tar` finns och har extraherats vid ett givet mål.

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```