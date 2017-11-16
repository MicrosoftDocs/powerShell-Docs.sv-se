---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
title: Nya scenarier och funktioner i WMF 5.1
ms.openlocfilehash: 430781c5c9a59fc544db4f94098313ae1e9cf610
ms.sourcegitcommit: a6ee6e64d369ecf82c730411bed9750278fdb5c1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/18/2017
---
# <a name="new-scenarios-and-features-in-wmf-51"></a>Nya scenarier och funktioner i WMF 5.1 #

> Obs: Den här informationen är preliminär och kan ändras.

## <a name="powershell-editions"></a>PowerShell-utgåvor ##
Från och med version 5.1 finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.

- **Desktop Edition:** bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows Desktop.
- **Core Edition:** bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.

**Lär dig mer om hur du använder PowerShell-versioner**
- [Fastställa körs version av PowerShell]()
- [Deklarera en modul kompatibilitet med vissa versioner av PowerShell]()
- [Filtrera Get-Module resultat av CompatiblePSEditions]()
- [Förhindra körning av skript om du inte på en kompatibel version av PowerShell]()

## <a name="catalog-cmdlets"></a>Katalog-Cmdlets  

Två nya cmdletar har lagts till i den [Microsoft.PowerShell.Security](https://technet.microsoft.com/en-us/library/hh847877.aspx) modulen; dessa generera och verifiera filer för Windows-katalogen.  

###<a name="new-filecatalog"></a>Ny FileCatalog 
--------------------------------

Ny FileCatalog skapar en Windows-katalogfil för mappar och filer. Den här katalogfilen innehåller hashvärden för alla filer i angiven sökväg. Användarna kan distribuera mapparna tillsammans med motsvarande katalogfil som representerar mapparna. Den här informationen är användbar för att kontrollera om några ändringar har gjorts till mapparna sedan tiden för skapandet av katalogen.    

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Katalogen version 1 och 2 stöds. Version 1 används SHA1-hash-algoritm för att skapa filhash; version 2 används SHA256. Katalogversion 2 stöds inte på *Windows Server 2008 R2* eller *Windows 7*. Du bör använda katalogversion 2 på *Windows 8*, *Windows Server 2012*, och senare operativsystem.  

![](../images/NewFileCatalog.jpg)

Då skapas katalogfilen. 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

Att kontrollera integriteten för katalogfil (Pester.cat i ovanstående exempel), signera den med hjälp av [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.   


###<a name="test-filecatalog"></a>Testa FileCatalog 
--------------------------------

Testa FileCatalog verifierar katalogen som representerar en uppsättning mappar. 

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Denna cmdlet Jämför filer hashvärdena och deras relativa sökvägar finns i *katalog* med de som på *disk*. Om den identifierar eventuella matchningsfel mellan värden och sökvägar returnerar status som *ValidationFailed*. Användare kan hämta den här informationen med hjälp av den *-detaljerad* parameter. Visar även signering status för katalogen i *signatur* -egenskap som motsvarar anropar [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet på katalogfilen. Användare kan också hoppa över en fil vid verifiering av med hjälp av den *- FilesToSkip* parameter. 


## <a name="module-analysis-cache"></a>Modulen analys Cache ##
Från och med WMF 5.1 ger PowerShell kontroll över den fil som används för att cachelagra data om en modul, till exempel kommandon som exporteras.

Det här cacheminnet lagras som standard i filen `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Cachen läses vanligtvis vid start vid sökning efter ett kommando och sparas på en bakgrundstråd senare när en modul har importerats.

Du kan ändra standardplatsen för cachen, ange den `$env:PSModuleAnalysisCachePath` miljövariabeln innan du startar PowerShell. Ändringar i den här miljövariabeln påverkar endast underordnade processer. Värdet ska namnge den fullständiga sökvägen (inklusive filnamnet) som har behörighet att skapa och skriva filer för PowerShell. Om du vill inaktivera filcachen det här värdet till en ogiltig plats, till exempel:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Anger sökvägen till en ogiltig enhet. Om PowerShell går inte att skriva till sökvägen inget fel returneras, men du kan se Felrapportering med hjälp av en spårning:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

När du skriver ut cacheminnet, kontrollerar PowerShell för moduler som inte längre finns för att undvika ett onödigt stor cache.
Ibland är kontrollerna inte önskvärt, då du kan inaktivera dem genom att ange:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Ange den här miljövariabeln börjar gälla omedelbart i den aktuella processen.

##<a name="specifying-module-version"></a>Ange Modulversion

I WMF 5.1 `using module` fungerar på samma sätt som andra relaterade modulen konstruktioner i PowerShell. Tidigare fick du inte vill ange en viss modul-version. Om det fanns flera versioner finns, resulterade detta i ett fel.


I WMF 5.1:

* Du kan använda [ModuleSpecification konstruktor (hash-tabell)](https://msdn.microsoft.com/library/jj136290). Den här hashtabellen har samma format som `Get-Module -FullyQualifiedName`.

**Exempel:**`using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* Om det finns flera versioner av modulen, PowerShell använder den **samma upplösning logik** som `Import-Module` och returnerar inte ett fel--samma beteende som `Import-Module` och `Import-DscResource`.


##<a name="improvements-to-pester"></a>Förbättringar av lära
I WMF 5.1 har version av Pester som levereras med PowerShell uppdaterats från 3.3.5 till 3.4.0 med tillägget för genomförande https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e som möjliggör bättre beteende för Lära på Nano Server. 

Du kan granska ändringar i versioner 3.3.5 3.4.0 genom att inspektera ChangeLog.md filen på: https://github.com/pester/Pester/blob/master/CHANGELOG.md

