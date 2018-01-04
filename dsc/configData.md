---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Med konfigurationsdata
ms.openlocfilehash: 60c6c2d5694a03275e1a08522bdcf4b1bc5bb068
ms.sourcegitcommit: 60f06a06c2fce63024f3f4cbd7657b1dfe7fcb1a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/03/2018
---
# <a name="using-configuration-data-in-dsc"></a>Med hjälp av konfigurationsdata i DSC

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Med hjälp av inbyggda DSC **ConfigurationData** parameter, kan du definiera data som kan användas i en konfiguration. På så sätt kan du skapa en enkel konfiguration som kan användas för flera noder eller för olika miljöer. Till exempel om du utvecklar ett program, kan du använda en konfiguration för både utveckling och produktionsmiljöer och Använd konfigurationsdata för att ange data för varje miljö.

Det här avsnittet beskriver strukturen för de **ConfigurationData** hash-tabell. Exempel på hur du använder konfigurationsdata finns [avgränsa konfiguration och miljö data](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>Parametern ConfigurationData vanliga

DSC-konfigurationen tar en parameter för vanliga **ConfigurationData**, som du anger när du sammanställer konfigurationen. Information om kompilering konfigurationer finns [DSC-konfigurationer](configurations.md).

Den **ConfigurationData** parametern är en hasthtable som måste ha minst en nyckel som heter **AllNodes**. Det kan också ha en eller flera nycklar.

>**Obs:** exemplen i det här avsnittet använder en enda ytterligare nyckel (än den namngivna **AllNodes** nyckel) med namnet `NonNodeData`, men du kan innehålla valfritt antal ytterligare nycklar och ge dem vad du vill.

```powershell
$MyData = 
@{
    AllNodes = @()
    NonNodeData = ""   
}
```

Värdet för den **AllNodes** nyckeln är en matris. Varje element i denna matris är också en hash-tabell som måste ha minst en nyckel som heter **nodnamn**:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
        },

 
        @{
            NodeName = "VM-2"
        },

 
        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""   
}
```

Du kan lägga till andra nycklar varje hash-tabellen:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""   
}
```

Om du vill använda en egenskap för alla noder, du kan skapa en medlem i den **AllNodes** matris som har en **NodeName** av `*`. Till exempel för att ge varje nod en `LogPath` egenskap, kan du göra detta:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },

 
        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },

 
        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },

 
        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

Detta är detsamma som att lägga till en egenskap med namnet `LogPath` med värdet `"C:\Logs"` till var och en av de andra blocken (`VM-1`, `VM-2`, och `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>Definiera ConfigurationData hash-tabell

Du kan definiera **ConfigurationData** antingen som en variabel inom samma skriptfilen som en konfiguration (som i våra föregående exempel) eller i en separat `.psd1` fil. Definiera **ConfigurationData** i en `.psd1` fil, skapa en fil som innehåller den hash som representerar konfigurationsdata.

Du kan till exempel skapa en fil med namnet `MyData.psd1` med följande innehåll:

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a>Kompilera en konfiguration med konfigurationsdata

För att kompilera en konfiguration som du har definierat konfigurationsdata skicka konfigurationsdata som värde för den **ConfigurationData** parameter.

Detta skapar en MOF-fil för varje post i den **AllNodes** matris.
Varje MOF-filen kommer att namnges med den `NodeName` egenskapen för motsvarande post i matrisen.

Till exempel om du definierar konfigurationsdata som i den `MyData.psd1` filen ovan, kompilera en konfiguration skulle skapa båda `VM-1.mof` och `VM-2.mof` filer.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Kompilera en konfiguration med konfigurationsdata med en variabel

Att använda konfigurationsdata som har definierats som en variabel i samma `.ps1` filen som konfigurationen du skickar variabelnamnet som värde för den **ConfigurationData** parametern vid kompilering av konfigurationen:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Kompilera en konfiguration med konfigurationsdata med hjälp av en datafil

Om du vill använda konfigurationsdata som har definierats i en .psd1-fil du skickar sökvägen och namnet på filen som värde för den **ConfigurationData** parametern vid kompilering av konfigurationen:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Använda ConfigurationData variabler i en konfiguration

DSC innehåller tre särskilda variabler som kan användas i ett konfigurationsskript: **$AllNodes**, **$Node**, och **$ConfigurationData**.

- **$AllNodes** refererar till hela uppsättningen av noder som definierats i **ConfigurationData**. Du kan filtrera den **AllNodes** med hjälp av **. WHERE ()** och **. ForEach()**.
- **Noden** refererar till en särskild post i den **AllNodes** samlingen när den har filtrerats med hjälp av **. WHERE ()** eller **. ForEach()**.
- **ConfigurationData** refererar till hela hash-tabell som skickades som parametern vid kompilering av en konfiguration.

## <a name="using-non-node-data"></a>Med hjälp av data-nod

Som vi har sett i föregående exempel kan den **ConfigurationData** hash-tabellen kan ha en eller flera nycklar utöver de nödvändiga **AllNodes** nyckel.
I exemplen i det här avsnittet har vi används endast en extra nod och heter den `NonNodeData`. Du kan dock definiera valfritt antal ytterligare nycklar och namn som helst.

Ett exempel på hur nod-data finns [avgränsa konfiguration och miljö data](separatingEnvData.md).

## <a name="see-also"></a>Se även
- [Alternativ för autentiseringsuppgifter i konfigurationsdata](configDataCredentials.md)
- [DSC-konfigurationer](configurations.md)

