---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Använda konfigurations data
ms.openlocfilehash: 5eb7fedec9a0abece1068496cdf5cb940eae3340
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557047"
---
# <a name="using-configuration-data-in-dsc"></a>Använda konfigurations data i DSC

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

Med hjälp av den inbyggda DSC **ConfigurationData** -parametern kan du definiera data som kan användas i en konfiguration.
På så sätt kan du skapa en enda konfiguration som kan användas för flera noder eller för olika miljöer.
Om du till exempel utvecklar ett program kan du använda en konfiguration för både utvecklings-och produktions miljöer och använda konfigurations data för att ange data för varje miljö.

I det här avsnittet beskrivs strukturen för **ConfigurationData** -hash-tabellen.
Exempel på hur du använder konfigurations data finns i [avgränsa konfigurations-och miljö data](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>Den gemensamma ConfigurationData-parametern

En DSC-konfiguration använder en gemensam parameter, **ConfigurationData**, som du anger när du kompilerar konfigurationen.
Information om hur du kompilerar konfigurationer finns i [DSC-konfigurationer](configurations.md).

Parametern **ConfigurationData** är en hash som måste ha minst en nyckel med namnet **AllNodes**.
Den kan också ha en eller flera andra nycklar.

> [!NOTE]
> I exemplen i det här avsnittet används en enda ytterligare nyckel (förutom den namngivna **AllNodes** -nyckeln) med namnet `NonNodeData` , men du kan ta med valfritt antal ytterligare nycklar och ge dem de namn du vill.

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

Värdet för **AllNodes** -nyckeln är en matris. Varje element i matrisen är också en hash-tabell som måste ha minst en nyckel med namnet **nodnamn**:

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

Du kan också lägga till andra nycklar till varje hash-tabell:

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

Om du vill tillämpa en egenskap på alla noder kan du skapa en medlem i **AllNodes** -matrisen som har en **nodnamn** av `*` .
Om du till exempel vill ge varje nod en `LogPath` egenskap kan du göra följande:

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

Detta är detsamma som att lägga till en egenskap med namnet `LogPath` med ett värde för `"C:\Logs"` varje av de andra blocken ( `VM-1` , `VM-2` och `VM-3` ).

## <a name="defining-the-configurationdata-hashtable"></a>Definiera ConfigurationData-hash

Du kan definiera **ConfigurationData** antingen som en variabel i samma skript fil som en konfiguration (som i våra tidigare exempel) eller i en separat `.psd1` fil.
Om du vill definiera **ConfigurationData** i en `.psd1` fil skapar du en fil som bara innehåller den hash som representerar konfigurations data.

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

## <a name="compiling-a-configuration-with-configuration-data"></a>Kompilera en konfiguration med konfigurations data

Om du vill kompilera en konfiguration för vilken du har definierat konfigurations data skickar du konfigurations data som värdet för parametern **ConfigurationData** .

Då skapas en MOF-fil för varje post i **AllNodes** -matrisen.
Varje MOF-fil får namnet med `NodeName` egenskapen för motsvarande mat ris post.

Om du till exempel definierar konfigurations data som i `MyData.psd1` filen ovan skapas både och filer när du kompilerar en konfiguration `VM-1.mof` `VM-2.mof` .

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Kompilera en konfiguration med konfigurations data med en variabel

Om du vill använda konfigurations data som har definierats som en variabel i samma `.ps1` fil som konfigurationen skickar du variabel namnet som värde för parametern **ConfigurationData** när du kompilerar konfigurationen:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Kompilera en konfiguration med konfigurations data med hjälp av en datafil

Om du vill använda konfigurations data som har definierats i en. psd1-fil skickar du sökvägen och namnet på filen som värdet för parametern **ConfigurationData** när du kompilerar konfigurationen:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Använda ConfigurationData-variabler i en konfiguration

DSC tillhandahåller följande särskilda variabler som kan användas i ett konfigurations skript:

- **$AllNodes** refererar till hela samlingen av noder som definierats i **ConfigurationData**. Du kan filtrera **AllNodes** -samlingen med hjälp av **. Där ()** och **. ()**.
- **ConfigurationData** refererar till hela hash-tabellen som skickas som parameter när en konfiguration kompileras.
- **TypeName** innehåller [konfigurations](configurations.md) namnet som variabeln används i. I-konfigurationen har till exempel `MyDscConfiguration` `$MyTypeName` värdet `MyDscConfiguration` .
- **Node** refererar till en viss post i **AllNodes** -samlingen när den filtreras med hjälp av **. Där ()** eller **. ()**.
  - Du kan läsa mer om de här metoderna i [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)

## <a name="using-non-node-data"></a>Använda data som inte är noder

Som vi har sett i föregående exempel kan **ConfigurationData** hash-tabellen ha en eller flera nycklar utöver den nödvändiga **AllNodes** -nyckeln.
I exemplen i det här avsnittet har vi bara använt en enda nod och namngett den `NonNodeData` .
Du kan dock definiera valfritt antal ytterligare nycklar och ge dem namn som du vill.

Ett exempel på hur du använder data som inte finns på en nod finns i [avgränsa konfigurations-och miljö data](separatingEnvData.md).

## <a name="see-also"></a>Se även

- [Alternativ för autentiseringsuppgifter i konfigurations data](configDataCredentials.md)
- [DSC-konfigurationer](configurations.md)
