---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-konfigurationer
description: DSC-konfigurationer är PowerShell-skript som definierar en särskild typ av funktion.
ms.openlocfilehash: e59ad2791055ee3ff0150c342ec621d0228c4fc1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658558"
---
# <a name="dsc-configurations"></a>DSC-konfigurationer

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

DSC-konfigurationer är PowerShell-skript som definierar en särskild typ av funktion. Om du vill definiera en konfiguration använder du nyckelords **konfigurationen** för PowerShell.

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

## <a name="configuration-syntax"></a>Konfigurationssyntax

Ett konfigurations skript består av följande delar:

- **Konfigurations** blocket. Detta är det yttersta skript blocket. Du definierar den genom att använda nyckelordet **konfiguration** och ange ett namn. I det här fallet är namnet på konfigurationen "MyDscConfiguration".
- Ett eller flera **Node** -block. Dessa definierar de noder (datorer eller virtuella datorer) som du konfigurerar.
  I ovanstående konfiguration finns ett **Node** -block som är riktat mot en dator med namnet "test-PC1".
  Node-blocket kan acceptera flera dator namn.
- Ett eller flera resurs block. Det är här som konfigurationen anger egenskaperna för de resurser som konfigureras. I det här fallet finns det två resurs block som anropar "WindowsFeature"-resursen.

I ett **konfigurations** block kan du göra allt som du normalt kan i en PowerShell-funktion. I föregående exempel, om du inte vill hårdkoda namnet på mål datorn i konfigurationen, kan du lägga till en parameter för nodnamnet:

I det här exemplet anger du namnet på noden genom att skicka den som parametern **computername** när du kompilerar konfigurationen. Namnet är som standard "localhost".

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

**Node** -blocket kan också acceptera flera dator namn. I exemplet ovan kan du antingen använda `-ComputerName` parametern eller skicka en kommaavgränsad lista med datorer direkt till **Node** -blocket.

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

När du anger en lista över datorer i **Node** -blocket, från en konfiguration, måste du använda mat ris notation.

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

Innan du kan använda en konfiguration måste du kompilera den till ett MOF-dokument. Du gör detta genom att anropa konfigurationen precis som du anropar en PowerShell-funktion. Den sista raden i exemplet som bara innehåller namnet på konfigurationen och anropar konfigurationen.

> [!NOTE]
> För att anropa en konfiguration måste funktionen vara i globalt omfång (precis som med andra PowerShell-funktioner). Du kan göra detta med hjälp av "punkt-källa"-skriptet eller genom att köra konfigurations skriptet genom att använda F5 eller klicka på knappen **Kör skript** i ISE. Kör kommandot `. .\myConfig.ps1` där `myConfig.ps1` är namnet på den skript fil som innehåller konfigurationen för att köra skriptet med punkt källa.

När du anropar konfigurationen:

- Matchar alla variabler
- Skapar en mapp i den aktuella katalogen med samma namn som konfigurationen.
- Skapar en fil med namnet _nodnamn_ . MOF i den nya katalogen där _nodnamn_ är namnet på mål-noden i konfigurationen. Om det finns fler än en nod skapas en MOF-fil för varje nod.

> [!NOTE]
> MOF-filen innehåller all konfigurations information för målnoden. Därför är det viktigt att skydda det. Mer information finns i [skydda MOF-filen](../pull-server/secureMOF.md).

Att kompilera den första konfigurationen ovan resulterar i följande mappstruktur:

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

Om konfigurationen tar en parameter, som i det andra exemplet, som måste tillhandahållas vid kompilering. Så här ser det ut:

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

## <a name="using-new-resources-in-your-configuration"></a>Använda nya resurser i konfigurationen

Om du körde föregående exempel kanske du har märkt att du har fått en varning om att du använde en resurs utan att importera den direkt. Idag levereras DSC med 12 resurser som en del av PSDesiredStateConfiguration-modulen.

Cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)kan användas för att avgöra vilka resurser som är installerade i systemet och som är tillgängliga för användning av LCM.
När de här modulerna har placerats i `$env:PSModulePath` och är korrekt identifierade av [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)måste de fortfarande läsas in i konfigurationen.

**Import-dscresource Keyword Supports** är ett dynamiskt nyckelord som bara kan identifieras i ett **konfigurations** block, men det är inte en cmdlet. **Import-dscresource Keyword Supports** stöder två parametrar:

- **Modulnamn** är det rekommenderade sättet att använda **import-dscresource Keyword Supports** . Den accepterar namnet på modulen som innehåller de resurser som ska importeras (samt en sträng mat ris med Modulnamn).
- **Namn** är namnet på den resurs som ska importeras. Detta är inte det egna namnet som returneras som "name" av [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), men det klass namn som används för att definiera resurs schema (returnerat som **resourcetype** av [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).

Mer information om hur `Import-DSCResource` du använder finns i [using import-dscresource Keyword Supports](import-dscresource.md)

## <a name="powershell-v4-and-v5-differences"></a>Skillnader mellan PowerShell v4 och v5

Det finns skillnader i var DSC-resurser måste lagras i PowerShell 4,0. Mer information finns i [resurs plats](import-dscresource.md#resource-location).

## <a name="see-also"></a>Se även

- [Översikt över önskad tillstånds konfiguration i Windows PowerShell](../overview/overview.md)
- [DSC-resurser](../resources/resources.md)
- [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md)
