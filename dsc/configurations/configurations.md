---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: DSC-konfigurationer
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080188"
---
# <a name="dsc-configurations"></a>DSC-konfigurationer

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC-konfigurationer är PowerShell-skript som definierar en särskild typ av funktionen.
För att definiera en konfiguration, använder du nyckelordet PowerShell **Configuration**.

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

Spara skriptet som en `.ps1` fil.

## <a name="configuration-syntax"></a>Syntax för konfiguration

Ett konfigurationsskript består av följande delar:

- Den **Configuration** block. Det här är det yttersta skriptblocket. Du kan definiera den med hjälp av den **Configuration** nyckelord och att ange ett namn. I det här fallet är namnet på konfigurationen ”MyDscConfiguration”.
- En eller flera **noden** block. De definierar noderna (datorer eller virtuella datorer) som du konfigurerar. I konfigurationen ovan finns en **noden** block som riktar sig mot en dator med namnet ”TEST-PC1”. Noden blocket kan acceptera flera datornamn.
- En eller flera resurs-block. Det här är där konfigurationen anger egenskaperna för de resurser som den konfigurerar. Det finns i det här fallet två resurs-block, som anropar ”WindowsFeature”-resurs.

Inom en **Configuration** block, du kan göra allt som du normalt skulle kunna i en PowerShell-funktion. Till exempel i exemplet ovan om du inte vill hårt code namnet på måldatorn i konfigurationen, du kan lägga till en parameter för namnet på noden:

I det här exemplet anger du namnet på noden genom att skicka det som den **ComputerName** parameter när du kompilera konfigurationen. Namnet som standard ”localhost”.

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

Den **noden** block kan också acceptera flera datornamn. I exemplet ovan kan du antingen genom att använda den `-ComputerName` parameter eller pass som en kommaavgränsad lista med datorer direkt till den **noden** block.

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

När du anger en lista med datorer till den **noden** block, måste du använda matris-notation i en konfiguration.

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a>Kompilera konfigurationen

Innan du kan införa en konfiguration, har du kompilera den till en MOF-dokument.
Du kan göra detta genom att anropa konfigurationen som du vill anropa en funktion för PowerShell.
Den sista raden i exempel som endast anger namnet på konfigurationen, anropar konfigurationen.

> [!NOTE]
> För att anropa en konfiguration, måste funktionen vara i global omfattning (precis som med alla andra PowerShell-funktion).
> Du kan göra det här utförs antingen av ”dot-källa” skriptet, eller genom att köra konfigurationsskriptet genom att välja F5 eller klicka på den **kör skript** knappen i ISE.
> Till dot-källa skriptet, kör du kommandot `. .\myConfig.ps1` där `myConfig.ps1` är namnet på den skriptfil som innehåller din konfiguration.

När du anropar konfigurationen, det:

- Matchar alla variabler
- Skapar en mapp i den aktuella katalogen med samma namn som konfigurationen.
- Skapar en fil med namnet _nodnamn_.mof i den nya katalogen där _nodnamn_ är namnet på målnoden av konfigurationen.
  Om det finns fler än en nod, skapas en MOF-fil för varje nod.

> [!NOTE]
> MOF-filen innehåller alla konfigurationsinformation för målnoden. Därför är det viktigt att skydda den.
> Mer information finns i [skydda MOF-filen](../pull-server/secureMOF.md).

Kompilera den första konfigurationen ovan resulterar i följande mappstrukturen:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

Om konfigurationen tar en parameter, som i det andra exemplet som måste anges vid kompilering. Här är hur som ser ut:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a>Med nya resurser i din konfiguration

Om du har kört i föregående exempel kanske du har märkt att du har en varning att du använder en resurs utan att uttryckligen importera den.
Idag, DSC levereras med 12 resurserna som en del av modulen PSDesiredStateConfiguration.

Cmdlet: en [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), kan användas för att avgöra vilka resurser som är installerade i systemet och tillgängliga för användning av LCM.
När dessa moduler har placerats i `$env:PSModulePath` och kan identifieras av [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), de behöver för att läsas in i din konfiguration.

**Import-DscResource** är en dynamisk nyckelord som kan endast identifieras inom en **Configuration** block, det är inte en cmdlet.
**Import-DscResource** stöder två parametrar:

- **ModuleName** är det rekommendera sättet att använda **Import-DscResource**. Den godkänner namnet på den modul som innehåller resurser som ska importeras (samt en strängmatris Modulnamnen).
- **Namn på** är namnet på resursen att importera. Detta är inte det egna namnet som ”Name” som returneras av [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), men Klassnamnet används när definiera resursschemat (returneras som **ResourceType** av [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).

Mer information om hur du använder `Import-DSCResource`, se [med Import-DSCResource](import-dscresource.md)

## <a name="powershell-v4-and-v5-differences"></a>V4 och v5 skillnader i PowerShell

Det finns skillnader i där DSC-resurser måste vara lagrad i PowerShell 4.0. Mer information finns i [resursplats](import-dscresource.md#resource-location).

## <a name="see-also"></a>Se även

- [Windows PowerShell Desired State Configuration-översikt](../overview/overview.md)
- [DSC-resurser](../resources/resources.md)
- [Konfigurera den lokala Konfigurationshanteraren](../managing-nodes/metaConfig.md)
