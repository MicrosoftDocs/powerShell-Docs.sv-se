---
description: Förklarar hur du installerar, importerar och använder PowerShell-moduler.
Locale: en-US
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Modules
ms.openlocfilehash: aebebc3f41a091151fbbecd9925a4ebc063e678e
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564610"
---
# <a name="about-modules"></a>Om moduler

## <a name="short-description"></a>Kort beskrivning
Förklarar hur du installerar, importerar och använder PowerShell-moduler.

## <a name="long-description"></a>Lång beskrivning

En modul är ett paket som innehåller PowerShell-medlemmar, till exempel cmdlets, providrar, funktioner, arbets flöden, variabler och alias.

Personer som skriver kommandon kan använda moduler för att organisera sina kommandon och dela dem med andra. Personer som tar emot moduler kan lägga till kommandon i modulerna i sina PowerShell-sessioner och använda dem precis som de inbyggda kommandona.

I det här avsnittet beskrivs hur du använder PowerShell-moduler. Information om hur du skriver PowerShell-moduler finns i [skriva en PowerShell-modul](/powershell/scripting/developer/module/writing-a-windows-powershell-module).

## <a name="what-is-a-module"></a>Vad är en modul?

En modul är ett paket som innehåller PowerShell-medlemmar, till exempel cmdlets, providrar, funktioner, arbets flöden, variabler och alias. Medlemmarna i det här paketet kan implementeras i ett PowerShell-skript, en kompilerad DLL-fil eller en kombination av båda. De här filerna grupperas vanligt vis i en enda katalog. Mer information finns i [förstå en Windows PowerShell-modul](/powershell/scripting/developer/module/understanding-a-windows-powershell-module) i SDK-dokumentationen.

## <a name="module-auto-loading"></a>Automatisk inläsning av modul

Från och med PowerShell 3,0 importerar PowerShell moduler automatiskt första gången du kör ett kommando i en installerad modul. Du kan nu använda kommandona i en modul utan konfigurations konfiguration eller profil, så du behöver inte hantera moduler när du har installerat dem på din dator.

Kommandona i en modul är också lättare att hitta. `Get-Command`Cmdleten hämtar nu alla kommandon i alla installerade moduler, även om de inte är i sessionen än. Du kan hitta ett kommando och använda det utan att importera behöver importera modulen först.

Vart och ett av följande exempel orsakar CimCmdlets-modulen, som innehåller, som ska `Get-CimInstance` importeras till sessionen.

- Kör kommandot

  ```powershell
  Get-CimInstance Win32_OperatingSystem
  ```

- Hämta kommandot

  ```powershell
  Get-Command Get-CimInstance
  ```

- Få hjälp med kommandot

  ```powershell
  Get-Help Get-CimInstance
  ```

`Get-Command` kommandon som innehåller ett jokertecken ( `*` ) anses vara för identifiering, används inte och importerar inte några moduler.

Endast moduler som lagras på den plats som anges av PSModulePath-miljövariabeln importeras automatiskt. Moduler på andra platser måste importeras genom att köra `Import-Module` cmdleten.

Kommandon som använder PowerShell-leverantörer importerar dessutom inte automatiskt en modul. Om du till exempel använder ett kommando som kräver WSMan:-enheten, till exempel `Get-PSSessionConfiguration` cmdleten, kan du behöva köra `Import-Module` cmdleten för att importera **Microsoft. WSMan. Management** -modulen som innehåller `WSMan:` enheten.

Du kan fortfarande köra `Import-Module` kommandot för att importera en modul och använda `$PSModuleAutoloadingPreference` variabeln för att aktivera, inaktivera och konfigurera automatisk import av moduler. Mer information finns i [about_Preference_Variables](about_Preference_Variables.md).

## <a name="how-to-use-a-module"></a>Använda en modul

Utför följande uppgifter om du vill använda en modul:

1. Installera modulen. (Detta görs ofta åt dig.)
1. Hitta de kommandon som modulen har lagt till.
1. Använd de kommandon som modulen har lagt till.

I det här avsnittet beskrivs hur du utför dessa uppgifter. Den innehåller även annan användbar information om hur du hanterar moduler.

## <a name="how-to-install-a-module"></a>Så här installerar du en modul

Om du får en modul som en mapp med filer i den måste du installera den på datorn innan du kan använda den i PowerShell.

De flesta moduler är installerade åt dig. PowerShell innehåller flera förinstallerade moduler, ibland kallade _Core_ -moduler. På Windows-baserade datorer, om funktioner som ingår i operativ systemet har cmdlets för att hantera dem, förinstalleras dessa moduler. När du installerar en Windows-funktion med hjälp av, till exempel guiden Lägg till roller och funktioner i Serverhanteraren eller i dialog rutan Aktivera eller inaktivera Windows-funktioner på kontroll panelen, installeras alla PowerShell-moduler som ingår i funktionen. Många andra moduler ingår i ett installations program eller installations program som installerar modulen.

Använd följande kommando för att skapa en **modul** -katalog för den aktuella användaren:

```powershell
New-Item -Type Directory -Path $HOME\Documents\PowerShell\Modules
```

Kopiera hela modul-mappen till katalogen modules. Du kan använda valfri metod för att kopiera mappen, inklusive Windows Explorer och Cmd.exe, samt PowerShell. I PowerShell använder du `Copy-Item` cmdleten. Om du till exempel vill kopiera mappen för mina `C:\ps-test\MyModule` moduler från till katalogen moduler skriver du:

```powershell
Copy-Item -Path C:\ps-test\MyModule -Destination `
    $HOME\Documents\PowerShell\Modules
```

Du kan installera en modul på vilken plats som helst, men om du installerar modulerna på en standardmodul blir det enklare att hantera dem. Mer information om standardmodulens platser finns i modulen för [modul-och DSC-resurser och PSModulePath-](#module-and-dsc-resource-locations-and-psmodulepath) avsnittet.

## <a name="how-to-find-installed-modules"></a>Så här hittar du installerade moduler

Om du vill hitta moduler som är installerade på en standardmodul, men som ännu inte har importer ATS till din session, skriver du:

```powershell
Get-Module -ListAvailable
```

Om du vill hitta de moduler som redan har importer ATS till din-session skriver du följande i PowerShell-prompten:

```powershell
Get-Module
```

Mer information om `Get-Module` cmdleten finns i [Get-module](xref:Microsoft.PowerShell.Core.Get-Module).

## <a name="how-to-find-the-commands-in-a-module"></a>Så här hittar du kommandon i en modul

Använd `Get-Command` cmdleten för att hitta alla tillgängliga kommandon. Du kan använda parametrarna för `Get-Command` cmdlet: en för att filtrera kommandon som till exempel efter modul, namn och substantiv.

Om du vill söka efter alla kommandon i en modul skriver du:

```powershell
Get-Command -Module <module-name>
```

Om du till exempel vill hitta kommandona i BitsTransfer-modulen skriver du:

```powershell
Get-Command -Module BitsTransfer
```

Mer information om `Get-Command` cmdleten finns i [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command).

## <a name="how-to-get-help-for-the-commands-in-a-module"></a>Så här får du hjälp med kommandon i en modul

Om modulen innehåller hjälpfiler för de kommandon som den exporterar, `Get-Help` visas hjälp avsnitten i cmdleten. Använd samma `Get-Help` kommando format som du kan använda för att få hjälp med kommandon i PowerShell.

Från och med PowerShell 3,0 kan du hämta hjälpfiler för en modul och ladda ned uppdateringar till hjälpfilerna så att de aldrig är föråldrade.

Om du vill ha hjälp med kommandon i en modul skriver du:

```powershell
Get-Help <command-name>
```

Om du vill få hjälp online för kommandot i en modul skriver du:

```powershell
Get-Help <command-name> -Online
```

Om du vill hämta och installera hjälpfilerna för kommandon i en modul skriver du:

```powershell
Update-Help -Module <module-name>
```

Mer information finns i [få hjälp](xref:Microsoft.PowerShell.Core.Get-Help) och [Uppdatera – hjälp](xref:Microsoft.PowerShell.Core.Update-Help).

## <a name="how-to-import-a-module"></a>Så här importerar du en modul

Du kan behöva importera en modul eller importera en modul-fil. Import krävs när en modul inte är installerad på de platser som anges av **PSModulePath** -miljövariabeln, `$env:PSModulePath` eller om modulen består av en fil, till exempel en. dll-eller. psm1-fil, i stället för en typisk modul som levereras som en mapp.

Du kan också välja att importera en modul så att du kan använda parametrarna för `Import-Module` kommandot, till exempel parametern prefix, som lägger till ett särskiljande prefix till Substantiv namnen för alla importerade kommandon, eller parametern **NoClobber** , som förhindrar att modulen lägger till kommandon som döljer eller ersätter befintliga kommandon i sessionen.

Använd cmdleten för att importera moduler `Import-Module` .

Om du vill importera moduler på en PSModulePath plats till den aktuella sessionen använder du följande kommando format.

```powershell
Import-Module <module-name>
```

Följande kommando importerar till exempel modulen BitsTransfer till den aktuella sessionen.

```powershell
Import-Module BitsTransfer
```

Om du vill importera en modul som inte finns på en standardmodul, använder du den fullständiga sökvägen till mappen modul i kommandot.

Om du till exempel vill lägga till modulen TestCmdlets i `C:\ps-test` katalogen i din session skriver du:

```powershell
Import-Module C:\ps-test\TestCmdlets
```

Om du vill importera en modul som inte finns i en modul-mapp använder du den fullständiga sökvägen till filen i kommandot.

Om du till exempel vill lägga till modulen TestCmdlets.dll i `C:\ps-test` katalogen i din session skriver du:

```powershell
Import-Module C:\ps-test\TestCmdlets.dll
```

Mer information om hur du lägger till moduler i din session finns i [import-module](xref:Microsoft.PowerShell.Core.Import-Module).

## <a name="how-to-import-a-module-into-every-session"></a>Så här importerar du en modul till varje session

`Import-Module`Kommandot importerar moduler till din aktuella PowerShell-session. Om du vill importera en modul till varje PowerShell-session som du startar lägger du till `Import-Module` kommandot i din PowerShell-profil.

Mer information om profiler finns [about_Profiles](about_Profiles.md).

## <a name="how-to-remove-a-module"></a>Ta bort en modul

När du tar bort en modul tas de kommandon som läggs till i modulen bort från sessionen.

Om du vill ta bort en modul från sessionen använder du följande kommando format.

```powershell
Remove-Module <module-name>
```

Följande kommando tar till exempel bort modulen BitsTransfer från den aktuella sessionen.

```powershell
Remove-Module BitsTransfer
```

Om du tar bort en modul ångras åtgärden för att importera en modul. Att ta bort en modul avinstallerar inte modulen. Mer information finns i [Remove-module](xref:Microsoft.PowerShell.Core.Remove-Module).

## <a name="module-and-dsc-resource-locations-and-psmodulepath"></a>Modul-och DSC-resurs platser och PSModulePath

`$env:PSModulePath`Miljövariabeln innehåller en lista över mappar som genomsöks för att hitta moduler och resurser.

Som standard är de effektiva platser som `$env:PSModulePath` är tilldelade:

- Platser i hela systemet: `$PSHOME\Modules`

  Dessa mappar innehåller moduler som levereras med Windows och PowerShell.

  DSC-resurser som ingår i PowerShell lagras i `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` mappen.

- Användarspecifika moduler: de här är moduler som installeras av användaren i användarens omfång. `Install-Module` har en **omfattnings** parameter som gör att du kan ange om modulen är installerad för den aktuella användaren eller för alla användare. Mer information finns i [install-module](xref:PowerShellGet.Install-Module).

  Den användarspecifika **CurrentUser** -platsen i Windows är `PowerShell\Modules` mappen som finns på **dokument** platsen i din användar profil. Den angivna sökvägen till platsen varierar efter Windows-version och om du använder mappomdirigering. Microsoft OneDrive kan också ändra platsen för mappen **dokument** .

  Som standard är den platsen i Windows 10 `$HOME\Documents\PowerShell\Modules` . På Linux eller Mac är **CurrentUser** -platsen `$HOME/.local/share/powershell/Modules` .

  > [!NOTE]
  > Du kan kontrol lera platsen för mappen **dokument** med hjälp av följande kommando: `[Environment]::GetFolderPath('MyDocuments')` .

- **Allusers** -platsen finns `$env:PROGRAMFILES\PowerShell\Modules` i Windows. I Linux eller Mac lagras modulerna på `/usr/local/share/powershell/Modules` .

> [!NOTE]
> Om du vill lägga till eller ändra filer i `$env:Windir\System32` katalogen startar du PowerShell med alternativet **Kör som administratör** .

Du kan ändra standard platserna för modulen i systemet genom att ändra värdet för **PSModulePath** -miljövariabeln `$Env:PSModulePath` . Miljövariabeln **PSModulePath** är modellerad i miljövariabeln PATH och har samma format.

Om du vill visa standard platserna för modulen skriver du:

```powershell
$Env:PSModulePath
```

Använd följande kommando format om du vill lägga till en standard-modul.

```powershell
$Env:PSModulePath = $Env:PSModulePath + ";<path>"
```

Semikolon ( `;` ) i kommandot avgränsar den nya sökvägen från den sökväg som föregår den i listan.

Om du till exempel vill lägga till `C:\ps-test\Modules` katalogen skriver du:

```powershell
$Env:PSModulePath + ";C:\ps-test\Modules"
```

Om du vill lägga till en standard-modul på Linux eller MacOS, använder du följande kommando format:

```powershell
$Env:PSModulePath += ":<path>"
```

Om du till exempel vill lägga till `/usr/local/Fabrikam/Modules` katalogen till värdet för **PSModulePath** -miljövariabeln, skriver du:

```powershell
$Env:PSModulePath += ":/usr/local/Fabrikam/Modules"
```

Kolon () i kommandot på Linux eller MacOS `:` separerar den nya sökvägen från den sökväg som föregår den i listan.

När du lägger till en sökväg i PSModulePath `Get-Module` och `Import-Module` kommandon innehåller moduler i den sökvägen.

Värdet som du anger påverkar endast den aktuella sessionen. Om du vill göra ändringen permanent lägger du till kommandot i din PowerShell-profil eller använder system på kontroll panelen för att ändra värdet för **PSModulePath** -miljövariabeln i registret.

Om du vill göra ändringen beständig kan du också använda metoden **SetEnvironmentVariable** i klassen **system. Environment** för att lägga till en sökväg till **PSModulePath** -miljövariabeln.

Mer information om variabeln **PSModulePath** finns i [about_Environment_Variables](about_Environment_Variables.md).

## <a name="modules-and-name-conflicts"></a>Moduler och namn konflikter

Namn konflikter uppstår när mer än ett kommando i sessionen har samma namn. Om du importerar en modul uppstår en namn konflikt när kommandon i modulen har samma namn som kommandon eller objekt i sessionen.

Namn konflikter kan resultera i att kommandon döljs eller ersätts.

### <a name="hidden"></a>Dold

Ett kommando är dolt när det inte är det kommando som körs när du skriver kommandots namn, men du kan köra det med en annan metod, till exempel genom att kvalificera kommando namnet med namnet på modulen eller snapin-modulen där det kom.

### <a name="replaced"></a>Ersätter

Ett kommando ersätts när du inte kan köra det eftersom det har skrivits över av ett kommando med samma namn. Även om du tar bort modulen som orsakade konflikten kan du inte köra ett ersatt kommando om du inte startar om sessionen.

`Import-Module` kan lägga till kommandon som döljer och ersätter kommandon i den aktuella sessionen. Dessutom kan kommandon i din session dölja kommandon som har lagts till i modulen.

Använd parametern **all** för cmdleten om du vill identifiera namn konflikter `Get-Command` . Från och med PowerShell 3,0 `Get-Command` hämtas bara kommandon som körs när du skriver kommandots namn. Parametern **all** hämtar alla kommandon med det angivna namnet i sessionen.

Om du vill förhindra namn konflikter använder du **NoClobber** -eller **prefixvärde** -parametrarna för `Import-Module` cmdleten. Parametern **prefix** lägger till ett prefix till namnen på importerade kommandon så att de är unika i sessionen. **NoClobber** -parametern importerar inte några kommandon som döljer eller ersätter befintliga kommandon i sessionen.

Du kan också använda **alias**-, **cmdlet**-, **Function**-och **Variable** -parametrarna för `Import-Module` för att välja de kommandon som du vill importera, och du kan utesluta kommandon som orsakar namn konflikter i sessionen.

Modulens författare kan förhindra namn konflikter genom att använda **DefaultCommandPrefix** -egenskapen för modulens manifest för att lägga till ett standardprefix i alla kommando namn.
Värdet för parametern **prefix** har företräde framför värdet för **DefaultCommandPrefix**.

Även om ett kommando är dolt kan du köra det genom att kvalificera kommando namnet med namnet på modulen eller snapin-modulen där det kom.

Regel reglerna för PowerShell-kommandot avgör vilket kommando som körs när sessionen innehåller kommandon med samma namn.

Till exempel, när en session innehåller en funktion och en cmdlet med samma namn, kör PowerShell funktionen som standard. När sessionen innehåller kommandon av samma typ med samma namn, till exempel två cmdlets med samma namn, körs det senast tillagda kommandot som standard.

Mer information, inklusive en förklaring av prioritets reglerna och instruktioner för att köra dolda kommandon, finns [about_Command_Precedence](about_Command_Precedence.md).

## <a name="modules-and-snap-ins"></a>Moduler och snapin-moduler

Du kan lägga till kommandon i-sessionen från moduler och snapin-moduler. Moduler kan lägga till alla typer av kommandon, inklusive cmdlet: ar, providers och funktioner och objekt, till exempel variabler, alias och PowerShell-enheter. Snapin-moduler kan bara lägga till cmdlets och providers.

Innan du tar bort en modul eller snapin-modul från din session kan du använda följande kommandon för att avgöra vilka kommandon som ska tas bort.

Om du vill hitta källan till en cmdlet i din-session använder du följande kommando format:

```powershell
Get-Command <cmdlet-name> | Format-List -Property verb,noun,pssnapin,module
```

Om du till exempel vill hitta källan till `Get-Date` cmdleten skriver du:

```powershell
Get-Command Get-Date | Format-List -Property verb,noun,module
```

## <a name="module-related-warnings-and-errors"></a>Moduler-relaterade varningar och fel

De kommandon som en modul exporterar till följer PowerShell-kommandot namngivnings regler. Om modulen som du importerar exporterar cmdletar eller funktioner som har icke godkända verb i sina namn, `Import-Module` visar cmdleten följande varnings meddelande.

> Varning! vissa importerade kommando namn innehåller icke-godkända verb som kan göra dem mindre synliga. Använd verbose-parametern för mer information eller Skriv Get-Verb om du vill visa en lista över godkända verb.

Det här meddelandet är bara en varning. Den kompletta modulen importeras fortfarande, inklusive kommandon som inte överensstämmer. Även om meddelandet visas för modulen användare, bör namngivnings problemet åtgärdas av den som skapade modulen.

Om du vill utelämna varnings meddelandet använder du parametern **DisableNameChecking** för `Import-Module` cmdleten.

## <a name="built-in-modules-and-snap-ins"></a>Inbyggda moduler och snapin-moduler

I PowerShell 2,0 och i äldre värd program i PowerShell 3,0 och senare, paketeras de grundläggande kommandon som installeras med PowerShell i snapin-moduler som läggs till automatiskt till varje PowerShell-session.

Från och med PowerShell 3,0, för värd program som implementerar det `InitialSessionState.CreateDefault2` inledande session State-API: t, läggs Microsoft. PowerShell. Core-snapin-modulen till i varje session som standard. Moduler läses in automatiskt vid första användning.

> [!NOTE]
> Fjärrsessioner, inklusive sessioner som startas med hjälp av `New-PSSession` cmdleten, är äldre sessioner där de inbyggda kommandona paketeras i snapin-moduler.

Följande moduler (eller snapin-moduler) installeras med PowerShell.

- CimCmdlets
- Microsoft. PowerShell. Archive
- Microsoft. PowerShell. Core
- Microsoft. PowerShell. Diagnostics
- Microsoft. PowerShell. Host
- Microsoft. PowerShell. Management
- Microsoft. PowerShell. Security
- Microsoft.PowerShell.Utility
- Microsoft. WSMan. Management
- PackageManagement
- PowerShellGet
- PSDesiredStateConfiguration
- PSDiagnostics
- PSReadline

## <a name="logging-module-events"></a>Loggning av module-händelser

Från och med PowerShell 3,0 kan du registrera körnings händelser för cmdlets och Functions i PowerShell-moduler och snapin-moduler genom att ange egenskapen **LogPipelineExecutionDetails** för moduler och snapin-moduler till `$True` .
Du kan också använda en grupprincip inställning, aktivera modulreferensen för att aktivera modul loggning i alla PowerShell-sessioner. Mer information finns i artikeln om loggning och grup principer.

## <a name="see-also"></a>Se även

[about_Logging_Windows](about_Logging_Windows.md)

[about_Logging_Non-Windows](about_Logging_Non-Windows.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Command_Precedence](about_Command_Precedence.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)

[Get – hjälp](xref:Microsoft.PowerShell.Core.Get-Help)

[Hämta modul](xref:Microsoft.PowerShell.Core.Get-Module)

[Importera-modul](xref:Microsoft.PowerShell.Core.Import-Module)

[Ta bort modul](xref:Microsoft.PowerShell.Core.Remove-Module)
