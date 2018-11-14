---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Med hjälp av konfigurationsdata
ms.openlocfilehash: f2d25b9ced805fb4c91378ebfe840104eb6ce52a
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619185"
---
# <a name="using-configuration-data-in-dsc"></a>Med hjälp av konfigurationsdata i DSC

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Med hjälp av inbyggda DSC **ConfigurationData** parameter, kan du definiera data som kan användas i en konfiguration.
På så sätt kan du skapa en enda konfiguration som kan användas för flera noder eller för olika miljöer.
Exempelvis om du utvecklar ett program, kan du använda en konfiguration för utvecklings-och produktionsmiljöer och Använd konfigurationsdata för att ange data för varje miljö.

Det här avsnittet beskriver strukturen för de **ConfigurationData** hash-tabell.
Exempel på hur du använder konfigurationsdata finns [att avgränsa konfigurations- och miljödata](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>Parametern ConfigurationData vanliga

En DSC-konfiguration tar en parameter för vanliga **ConfigurationData**, som du anger när du kompilera konfigurationen.
Läs om hur kompilera konfigurationer [DSC-konfigurationer](configurations.md).

Den **ConfigurationData** parametern är en hash-tabell som måste ha minst en nyckel med namnet **AllNodes**.
Det kan också ha en eller flera nycklar.

> [!NOTE]
> Exemplen i det här avsnittet använder en enda ytterligare nyckel (förutom de namngivna **AllNodes** nyckel) med namnet `NonNodeData`, men du kan innehålla valfritt antal ytterligare nycklar och kalla dem vad som helst.

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

Värdet för den **AllNodes** nyckel är en matris. Varje element i den här matrisen är också en hash-tabell som måste ha minst en nyckel med namnet **nodnamn**:

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

Du kan lägga till andra nycklar till varje hash-tabell:

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

Om du vill använda en egenskap för alla noder, du kan skapa en medlem i den **AllNodes** matris som har en **nodnamn** av `*`.
Till exempel för att ge varje nod en `LogPath` egenskapen, kan du göra detta:

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

Det här är detsamma som att lägga till en egenskap med namnet `LogPath` med värdet `"C:\Logs"` till var och en av de andra blocken (`VM-1`, `VM-2`, och `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>Definiera ConfigurationData hash-tabell

Du kan definiera **ConfigurationData** antingen som en variabel i samma skriptfilen som en konfiguration (som i vårt tidigare exempel) eller i en separat `.psd1` fil.
Definiera **ConfigurationData** i en `.psd1` fil, skapa en fil som innehåller bara den hash-tabell som representerar konfigurationsdata.

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

För att kompilera en konfiguration som du har definierat konfigurationsdata, skicka konfigurationsdata som värdet för den **ConfigurationData** parametern.

Detta skapar en MOF-fil för varje post i den **AllNodes** matris.
Varje MOF-fil kommer att namnges med den `NodeName` egenskapen för motsvarande Matrisposten.

Exempel: Om du definierar konfigurationsdata som i den `MyData.psd1` filen ovan, kompilera en konfiguration skulle skapa dessa `VM-1.mof` och `VM-2.mof` filer.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Kompilera en konfiguration med konfigurationsdata med hjälp av en variabel

Att använda konfigurationsdata som har definierats som en variabel i samma `.ps1` filen som konfigurationen du skickar variabelnamnet som värde för den **ConfigurationData** parameter när kompilera konfigurationen:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Kompilera en konfiguration med konfigurationsdata med hjälp av en datafil

För att använda konfigurationsdata som har definierats i en .psd1-fil måste du skicka sökvägen och namnet på filen som värde för den **ConfigurationData** parameter när kompilera konfigurationen:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Använda ConfigurationData variabler i en konfiguration

DSC tillhandahåller följande särskilda variabler som kan användas i ett konfigurationsskript:

- **$AllNodes** refererar till hela uppsättningen av noder som definierats i **ConfigurationData**. Du kan filtrera den **AllNodes** samlingen med hjälp av **. WHERE ()** och **. ForEach()**.
- **ConfigurationData** refererar till hela hash-tabellen som skickas som parametern när kompilera en konfiguration.
- **MyTypeName** innehåller den [configuration](configurations.md) variabeln används i namnet. Till exempel i konfigurationen `MyDscConfiguration`, `$MyTypeName` har värdet `MyDscConfiguration`.
- **Noden** refererar till en viss post i den **AllNodes** samling när den har filtrerats med hjälp av **. WHERE ()** eller **. ForEach()**.
  - Du kan läsa mer om de här metoderna i [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)

## <a name="using-non-node-data"></a>Använda icke-nod-data

Som vi har sett i föregående exempel kan den **ConfigurationData** hash-tabell kan ha en eller flera nycklar utöver de nödvändiga **AllNodes** nyckel.
I exemplen i det här avsnittet har vi används endast en extra nod och namnet `NonNodeData`.
Du kan dock ange valfritt antal ytterligare nycklar och kalla dem vad du vill.

Ett exempel på hur du använder icke-noddatat finns i [att avgränsa konfigurations- och miljödata](separatingEnvData.md).

## <a name="see-also"></a>Se även

- [Alternativ för autentiseringsuppgifter i konfigurationsdata](configDataCredentials.md)
- [DSC-konfigurationer](configurations.md)