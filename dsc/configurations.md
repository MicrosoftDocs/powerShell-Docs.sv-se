---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC-konfigurationer
ms.openlocfilehash: b0868a276dbf5cdb566ce1f35a96b3372cf49be1
ms.sourcegitcommit: 60c6f9d8cf316e6d5b285854e6e5641ac7648f3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2017
---
# <a name="dsc-configurations"></a>DSC-konfigurationer

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC-konfigurationer är PowerShell-skript som definierar en särskild typ av funktionen. Om du vill definiera en konfiguration, använder du nyckelordet PowerShell **Configuration**.

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
} 

```

Spara skriptet som en .ps1-fil.

## <a name="configuration-syntax"></a>Syntax för konfiguration

Ett konfigurationsskript består av följande delar:

- Den **Configuration** block. Det här är det yttersta skriptblocket. Du kan definiera den med hjälp av den **Configuration** nyckelord och ange ett namn. I det här fallet är namnet på konfigurationen ”MyDscConfiguration”.
- En eller flera **nod** block. De definierar noderna (datorer eller virtuella datorer) som du konfigurerar. I konfigurationen ovan finns en **nod** block som riktar sig till en dator med namnet ”TEST-PC1”.
- En eller flera resurs-block. Detta är där konfigurationen anger egenskaperna för de resurser som den konfigurerar. I det här fallet finns två resurs-block, där varje anropa resursen ”WindowsFeature”.

Inom en **Configuration** block, kan du göra allt som du normalt kan i ett PowerShell-funktionen. Till exempel i föregående exempel, om du inte vill hård code namnet på måldatorn i konfigurationen, du kan lägga till en parameter för nodnamnet på:

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}

```

I det här exemplet, ange namnet på noden genom att skicka den som den **ComputerName** parameter när du kompilerar Configuration. Namnet som standard ”localhost”.

## <a name="compiling-the-configuration"></a>Kompilera konfiguration

Innan du kan tillämpar en konfiguration som du behöver kompileras till en MOF-dokument. Det gör du genom att anropa konfigurationen som en PowerShell-funktionen.  
Den sista raden i exemplet som innehåller namnet på konfigurationen, anropar konfigurationen.

>**Obs:** för att anropa en konfiguration, funktionen måste vara i globalt scope (precis som med andra PowerShell funktioner). 
>Du kan göra detta hända antingen av ”dot-källa” skriptet, eller genom att köra skriptet konfiguration genom att använda F5 eller klicka på den **kör skriptet** knappen i ISE. 
>Till dot-källa skriptet, kör du kommandot `. .\myConfig.ps1` där `myConfig.ps1` är namnet på den skriptfil som innehåller din konfiguration.

När du anropar konfigurationen, är det:

- Matchar alla variabler 
- Skapar en mapp i den aktuella katalogen med samma namn som konfigurationen.
- Skapar en fil med namnet _NodeName_MOF i den nya katalogen där _nodnamn_ är namnet på målnoden av konfigurationen. 
    Om det finns flera noder, skapas en MOF-fil för varje nod.

>**Obs**: I MOF-filen innehåller all konfigurationsinformation för målnoden. Därför är det viktigt att skydda den. 
>Mer information finns i [skydda MOF-filen](secureMOF.md).

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

Om konfigurationen tar en parameter i det andra exemplet som anges vid kompileringen. Här är hur som ser ut:

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

## <a name="using-dependson"></a>Använder DependsOn

Ett användbart DSC-nyckelord är **DependsOn**. Vanligtvis (men inte nödvändigtvis), DSC gäller resurser i den ordning som de visas i konfigurationen. Dock **DependsOn** anger vilken resurser är beroende av andra resurser och MGM säkerställer att tillämpas de i rätt ordning, oavsett ordningen i vilken resurs som instanser har definierats. En konfiguration kan till exempel ange att en instans av den **användare** resurs beror på förekomsten av en **grupp** instans:

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

```

## <a name="using-new-resources-in-your-configuration"></a>Med nya resurser i din konfiguration

Om du körde i föregående exempel kanske såg du att du har en varning att du använder en resurs utan att uttryckligen importera den.
Idag DSC levereras med 12 resurser som en del av modulen PSDesiredStateConfiguration. Andra resurser i externa moduler måste placeras i `$env:PSModulePath` för att kunna identifieras av MGM. En ny cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), kan användas för att avgöra vilka resurser som är installerade i systemet och kan användas av MGM. När dessa moduler har placerats i `$env:PSModulePath` och kan identifieras av [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), de behöver inte läsas in i din konfiguration. 
**Importera DscResource** är en dynamisk nyckelord som kan endast identifieras inom en **Configuration** block (dvs. det inte är en cmdlet). 
**Importera DscResource** stöder två parametrar:
- **Modulnamn** är det rekommenderade sättet att använda **importera DscResource**. Namnet på den modul som innehåller resurser som ska importeras (samt en strängmatris Modulnamnen) accepteras. 
- **Namnet** är namnet på resursen som ska importeras. Detta är inte ett eget namn som ”namn” som returneras av [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), men Klassnamnet används när definierar resursschemat (returneras som **ResourceType** av [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)). 

## <a name="see-also"></a>Se även
* [Windows PowerShell Desired State Configuration-översikt](overview.md)
* [DSC-resurser](resources.md)
* [Konfigurera den lokala Configuration Manager](metaConfig.md)

