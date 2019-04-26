---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxArchive-resurs
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078052"
---
# <a name="dsc-for-linux-nxarchive-resource"></a>DSC för Linux nxArchive-resurs

Den **nxArchive** resurs i PowerShell Desired State Configuration (DSC) är en mekanism för att packa upp (.tar, .zip) arkivfiler på en specifik sökväg på en Linux-nod.

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
| SourcePath| Anger källsökvägen för arkivfilen. Detta bör vara en .tar .zip, eller..GZ-filen. |
| Målsökväg| Anger den plats där du vill kontrollera arkivinnehållet extraheras.|
| Kontrollsumma| Definierar den typ som ska användas när du bestämmer om käll-arkivet har uppdaterats. Värden är: ”ctime”, ”mtime” eller ”md5”. Standardvärdet är ”md5”.|
| Force| Vissa åtgärder för sammansättningsfiler (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel. Med hjälp av den **kraft** egenskapen åsidosätter sådana fel. Standardvärdet är **$false**.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
| Se till att| Avgör om du vill kontrollera om innehållet i arkivet på den **mål**. Ange egenskapen ”aktuella” för att säkerställa att innehållet finns. Ange den till ”inte” för att se till att de inte finns. Standardvärdet är ”tillgänglig”.|

## <a name="example"></a>Exempel

I följande exempel visas hur du använder den **nxArchive** resurs så att innehållet i en arkivfil heter `website.tar` finns och har extraherats vid ett givet mål.

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