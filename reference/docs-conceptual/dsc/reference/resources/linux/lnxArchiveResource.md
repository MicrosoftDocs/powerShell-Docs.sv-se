---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxArchive-resurs
ms.openlocfilehash: 77b52ad68344ba791501baeb585a5001cc97a126
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941511"
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

## <a name="properties"></a>properties

|Egenskap |Beskrivning |
|---|---|
|Sök |Anger Arkiv filens käll Sök väg. Detta bör vara en. tar-,. zip-eller. tar. gz-fil. |
|DestinationPath |Anger den plats där du vill se till att Arkiv innehållet extraheras. |
|Kontrollsumma |Definierar den typ som ska användas för att avgöra om käll arkivet har uppdaterats. Värdena är: **ctime**, **mtime**eller **MD5**. Standardvärdet är **MD5**. |
|Force |Vissa fil åtgärder (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel. Om du använder **Force** -egenskapen åsidosätts sådana fel. Standardvärdet är `$false`. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. |
|Kontrol |Avgör om du ska kontrol lera om arkivets innehåll finns vid **målet**. Ange att den här egenskapen **finns för att** se till att innehållet finns. Ange det som **frånvarande** för att se till att de inte finns. Standardvärdet finns **.** |

## <a name="example"></a>Exempel

I följande exempel visas hur du använder **nxArchive** -resursen för att kontrol lera att innehållet i en arkivfil som `website.tar` heter finns och extraheras vid ett angivet mål.

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