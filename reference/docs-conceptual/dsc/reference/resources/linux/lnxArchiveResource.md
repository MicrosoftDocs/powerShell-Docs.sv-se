---
ms.date: 07/17/2020
ms.topic: reference
title: DSC för Linux nxArchive-resurs
description: DSC för Linux nxArchive-resurs
ms.openlocfilehash: 2705829ccae0c1baa27324030433340e7f3949c1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648856"
---
# <a name="dsc-for-linux-nxarchive-resource"></a>DSC för Linux nxArchive-resurs

**NxArchive** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att packa upp arkiv (. tar. zip)-filer på en särskild sökväg på en Linux-nod.

## <a name="syntax"></a>Syntax

```Syntax
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

|Egenskap |Beskrivning |
|---|---|
|Sök |Anger Arkiv filens käll Sök väg. Detta bör vara en. tar-,. zip-eller. tar. gz-fil. |
|DestinationPath |Anger den plats där du vill se till att Arkiv innehållet extraheras. |
|Kontrollsumma |Definierar den typ som ska användas för att avgöra om käll arkivet har uppdaterats. Värdena är: **ctime** , **mtime** eller **MD5** . Standardvärdet är **MD5** . |
|Force |Vissa fil åtgärder (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel. Om du använder **Force** -egenskapen åsidosätts sådana fel. Standardvärdet är `$false`. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|Kontrol |Avgör om du ska kontrol lera om arkivets innehåll finns vid **målet** . Ange att den här egenskapen **finns för att** se till att innehållet finns. Ange det som **frånvarande** för att se till att de inte finns. Standardvärdet finns **.** |

## <a name="example"></a>Exempel

I följande exempel visas hur du använder **nxArchive** -resursen för att kontrol lera att innehållet i en arkivfil som heter `website.tar` finns och extraheras vid ett angivet mål.

```powershell
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = "http://release.contoso.com/releases/website.tar"
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = "mtime"
}

nxArchive SyncWebDir
{
   SourcePath = "/usr/release/staging/website.tar"
   DestinationPath = "/usr/local/apache2/htdocs/"
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```
