---
title: Hjälpsystemet
description: Att hantera hjälp systemet är nyckeln till att lyckas med PowerShell.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: dcaa6c990e2fdf5e6cca69ca596680310940817f
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391433"
---
# <a name="chapter-2---the-help-system"></a>Kapitel 2 – hjälp systemet

Två grupper av IT-proffs har fått ett skriftligt test utan åtkomst till en dator för att fastställa deras skicklighets nivå med PowerShell. PowerShell-nybörjare placerades i en grupp och experter i en annan.
Baserat på resultatet av testet verkar det inte vara mycket skillnad på skicklighets nivån mellan de två grupperna. Båda grupperna har fått ett andra test som liknar det första. Den här gången har de fått åtkomst till en dator med PowerShell som inte hade till gång till Internet. Resultatet från det andra testet visade en stor skillnad på skicklighets nivån mellan de två grupperna. Experter vet inte alltid svaren, men de vet hur de kan ta reda på svaren.

Vad var skillnaden i resultatet från det första och andra testet mellan dessa två grupper?

Skillnaderna som observerats i de här två testerna beror på att experter inte kan komma ihåg hur man använder tusentals kommandon i PowerShell. De lär sig att använda hjälp systemet i PowerShell mycket bra.
Detta gör att de kan hitta de nödvändiga kommandona vid behov och hur du använder dessa kommandon när de har hittat dem.

Jag har hört Jeffrey Snover, inventeringen av PowerShell, anger en liknande artikel ett antal gånger.

Att hantera hjälp systemet är nyckeln till att lyckas med PowerShell.

## <a name="discoverability"></a>Identifierings möjligheten

Kompilerade kommandon i PowerShell kallas cmdlets. Cmdleten är uttalad "kommando-let" (inte CMD-let). Cmdlets-namn har formatet "verb-Substantiv"-kommandon som gör dem lättare att upptäcka. Till exempel är cmdleten för att bestämma vilka processer som körs `Get-Process` och cmdleten för att hämta en lista över tjänster och deras status `Get-Service` . Det finns andra typer av kommandon i PowerShell, till exempel alias och funktioner som kommer att täckas senare i denna bok. Termen PowerShell-kommando är en generisk term som ofta används för att referera till valfri typ av kommando i PowerShell, oavsett om det är en cmdlet, en funktion eller ett alias.

## <a name="the-three-core-cmdlets-in-powershell"></a>De tre Core-cmdletarna i PowerShell

- `Get-Command`
- `Get-Help`
- `Get-Member` (omfattas av kapitel 3)

En fråga jag är ofta ombedd Hur tar du reda på vad kommandona är i PowerShell? Både `Get-Command` och `Get-Help` kan användas för att fastställa kommandon.

## <a name="get-help"></a>Get-Help

`Get-Help` är ett kommando för flera syften. `Get-Help` hjälper dig att lära dig hur du använder kommandon när du har hittat dem. `Get-Help` kan också användas för att hitta kommandon, men på ett annat och mer indirekt sätt jämfört med `Get-Command` .

När `Get-Help` används för att hitta kommandon söker den först efter jokertecken matchningar av kommando namn baserat på angivna indata. Om ingen matchning hittas genomsöks hjälp avsnitten i själva hjälpen och om ingen matchning hittas returneras ett fel. Motsats till populär tro `Get-Help` kan användas för att hitta kommandon som inte har hjälp avsnitt.

Det första du behöver veta om hjälp systemet i PowerShell är hur du använder- `Get-Help` cmdleten. Följande kommando används för att visa hjälp avsnittet för `Get-Help` .

```powershell
Get-Help -Name Get-Help
```

```Output
Do you want to run Update-Help?
The Update-Help cmdlet downloads the most current Help files for Windows PowerShell
modules, and installs them on your computer. For more information about the Update-Help
cmdlet, see http://go.microsoft.com/fwlink/?LinkId=210614.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

Från och med PowerShell version 3 levereras PowerShell-hjälpen inte med operativ systemet. Första gången `Get-Help` körs för ett kommando visas det föregående meddelandet. Om `help` funktionen eller `man` aliaset används i stället för `Get-Help` cmdleten får du inte den här frågan.

Om du svarar ja genom att trycka på <kbd>Y</kbd> körs `Update-Help` cmdleten, vilket kräver Internet åtkomst som standard. `Y` kan anges i antingen versaler eller gemener.

När hjälpen har hämtats och uppdateringen är klar returneras hjälp avsnittet för det angivna kommandot:

```powershell
Get-Help -Name Get-Help
```

Ta en stund att köra det exemplet på datorn, granska utdata och anteckna hur informationen grupperas:

- NAMN
- SAMMANFATTNING
- SYNTAX
- BESKRIVNING
- RELATERADE LÄNKAR
- REMARKS

Som du kan se kan hjälp avsnitten innehålla en enorma mängd information och detta är inte ens hela hjälp avsnittet.

Även om den inte är speciell för PowerShell, är en parameter ett sätt att tillhandahålla inmatade för ett kommando. `Get-Help` har många parametrar som kan specificeras för att returnera hela hjälp avsnittet eller en delmängd av den.

I avsnittet syntax i hjälp avsnittet som visas i den föregående uppsättningen med resultat visas alla parametrar för `Get-Help` . Vid första inblicken visas samma parametrar i listan sex olika tider. Vart och ett av dessa olika block i avsnittet syntax är en parameter uppsättning. Det innebär att `Get-Help` cmdleten har sex olika parameter uppsättningar. Om du tar en närmare titt ser du att minst en parameter är annorlunda i varje parameter uppsättning.

Parameter uppsättningar kan inte anges samtidigt. När en unik parameter som bara finns i en av parameter uppsättningarna används kan endast parametrar som finns i den parameter uppsättningen användas. Det går till exempel inte att ange både **fullständig** och **detaljerad** parameter på samma tidpunkt eftersom de finns i olika parameter uppsättningar.

Var och en av följande parametrar finns i olika parameter uppsättningar:

- Fullständig
- Detaljerad
- Exempel
- Online
- Parameter
- ShowWindow

All den encryptiska syntaxen, till exempel fyrkantiga hakparenteser och vinkelparenteser i avsnittet syntax betyder något men kommer att tas med i bilaga A till denna bok. Det är viktigt att lära sig att lära sig den krypterade syntaxen ofta är svår att bevaras för någon som är ny för PowerShell och som inte kan använda den varje dag.

Mer information för att bättre förstå den krypterade syntaxen finns i [bilaga A][].

För nybörjare finns det ett enklare sätt att ta reda på samma information, förutom på vanligt språk.

När den **fullständiga** parametern i `Get-Help` anges returneras hela hjälp avsnittet.

```powershell
Get-Help -Name Get-Help -Full
```

Ta en stund att köra det exemplet på datorn, granska utdata och anteckna hur informationen grupperas:

- NAMN
- SAMMANFATTNING
- SYNTAX
- BESKRIVNING
- PARAMETRAR
- INDATA
- UTDATA
- ANTECKNINGAR
- EXEMPEL
- RELATERADE LÄNKAR

Observera att om du använder den **fullständiga** parametern returnerade flera ytterligare avsnitt, varav en är avsnittet parametrar som innehåller mer information än i avsnittet om syntax för kryptering.

Den **fullständiga** parametern är en switch-parameter. En parameter som inte kräver ett värde kallas för en växel parameter. När en växel parameter anges är värdet true och när det inte är det är värdet false.

Om du har arbetat genom det här kapitlet i PowerShell-konsolen har du märkt att föregående kommando visar det fullständiga hjälp avsnittet för `Get-Help` reste på skärmen utan att ge dig möjlighet att läsa det. Det finns ett bättre sätt.

`Help` är en funktion som rör `Get-Help` en funktion med namnet `more` , som är en omslutning för den `more.com` körbara filen i Windows. I PowerShell-konsolen visas `help` en sida med hjälp i taget. I ISE fungerar det på samma sätt som `Get-Help` . Min rekommendation är att använda `help` funktionen i stället för `Get-Help` cmdleten eftersom den ger en bättre upplevelse och är mindre för att skriva.

Mindre text är dock inte alltid en bra sak. Om du vill spara dina kommandon som ett skript eller dela dem med någon annan, måste du se till att använda fullständiga cmdlet-och parameter namn. De fullständiga namnen är själv dokumenterade, vilket gör dem lättare att förstå. Tänk på nästa person som måste läsa och förstå dina kommandon. Det kan vara du. Dina medarbetare och dig själv är tacksamma.

Prova att köra följande kommandon i PowerShell-konsolen på datorn för Windows 10 Lab-miljön.

```powershell
Get-Help -Name Get-Help -Full
help -Name Get-Help -Full
help Get-Help -Full
```

Har du tittat på eventuella skillnader i utdata från de tidigare listade kommandona när du körde dem på din dator med Windows 10 Lab-miljön?

Det finns inga andra skillnader än de två sista alternativen returnerar resultatet en sida i taget.
<kbd>Blank steg</kbd> används för att visa nästa sida med innehåll när du använder `Help` funktionen och <kbd>CTRL</kbd> + <kbd>C</kbd> avbryter kommandon som körs i PowerShell-konsolen.

I det första exemplet används `Get-Help` -cmdleten, den andra använder `Help` funktionen och den tredje utelämnar **namn** parametern när `Help` funktionen används. **Name** är en positions parameter och den används i samma position i det exemplet. Det innebär att värdet kan anges utan att ange parameter namnet, så länge själva värdet anges på rätt plats. Hur vet jag vilken position du ska ange värdet i? Genom att läsa hjälpen som visas i följande exempel.

```powershell
help Get-Help -Parameter Name
```

```Output
-Name <String>
    Gets help about the specified command or concept. Enter the name of a cmdlet, function,
    provider, script, or workflow, such as Get-Member, a conceptual article name, such as
    about_Objects, or an alias, such as ls. Wildcard characters are permitted in cmdlet and
    provider names, but you can't use wildcard characters to find the names of function help and
    script help articles.

    To get help for a script that isn't located in a path that's listed in the $env:Path
    environment variable, type the script's path and file name.

    If you enter the exact name of a help article, Get-Help displays the article contents.

    If you enter a word or word pattern that appears in several help article titles, Get-Help
    displays a list of the matching titles.

    If you enter a word that doesn't match any help article titles, Get-Help displays a list of
    articles that include that word in their contents.

    The names of conceptual articles, such as about_Objects, must be entered in English, even in
    non-English versions of PowerShell.

    Required?                    false
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  true
```

Observera att **parametern** parameter i föregående exempel användes med funktionen Help för att endast returnera information från hjälp avsnittet för parametern **Name** . Detta är mycket mer koncist än att försöka manuellt gå igenom vad som ibland ser ut som ett hundra sid hjälp avsnitt.

Baserat på dessa resultat kan du se att **Name** -parametern är positionerad och måste anges i position noll (den första positionen) när den används i position. Ordningen som parametrar anges i spelar ingen roll om parameter namnet har angetts.

En annan viktig del av informationen är att **namn** parametern förväntar sig att data typen för värdet ska vara en enskild sträng, som anges av `<String>` . Om du har accepterat flera strängar visas data typen som `<String[]>` .

Ibland vill du bara Visa hela hjälp avsnittet för ett kommando. Det finns ett antal andra parametrar förutom **fullständig** som kan anges med `Get-Help` eller `Help` . Prova att köra följande kommandon på datorn för Windows 10 Lab-miljön:

```powershell
Get-Help -Name Get-Command -Full
Get-Help -Name Get-Command -Detailed
Get-Help -Name Get-Command -Examples
Get-Help -Name Get-Command -Online
Get-Help -Name Get-Command -Parameter Noun
Get-Help -Name Get-Command -ShowWindow
```

Jag använder vanligt vis `help <command name>` parametern **fullständig** eller **online** . Om jag bara är intresse rad av exemplen använder jag parametern **exempel** och om jag bara är intresse rad av en speciell parameter använder jag **parametern** parameter. Parametern **ShowWindow** öppnar hjälp avsnittet i ett separat sökbart fönster som kan placeras på en annan övervakare om du har flera bildskärmar. Jag har undvikt parametern **ShowWindow** eftersom det finns ett känt fel där den inte visar hela hjälp avsnittet.

Om du vill ha hjälp i ett separat fönster, är min rekommendation att antingen använda parametern **online** eller använda den **fullständiga** parametern och skicka resultatet till `Out-GridView` , som visas i följande exempel.

```powershell
help Get-Command -Full | Out-GridView
```

Både `Out-GridView` cmdleten och **ShowWindow** -parametern för `Get-Help` cmdleten kräver ett operativ system med ett grafiskt användar gränssnitt (grafiskt användar gränssnitt). De genererar ett fel meddelande om du försöker använda någon av dem på Windows Server som har installerats med installations alternativet Server Core (utan användar gränssnitt).

Om du vill använda `Get-Help` för att söka efter kommandon använder du jokertecknet asterisk ( `*` ) med parametern **Name** . Ange en term som du söker efter kommandon på som värde för parametern **Name** enligt följande exempel.

```powershell
help *process*
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
Exit-PSHostProcess                Cmdlet    Microsoft.PowerShell.Core Closes an intera...
Get-PSHostProcessInfo             Cmdlet    Microsoft.PowerShell.Core
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-AppvVirtualProcess            Function  AppvClient                ...
Start-AppvVirtualProcess          Function  AppvClient                ...
```

I det föregående exemplet `*` behövs inte jokertecken och utelämnar dem ger samma resultat. `Get-Help` lägger automatiskt till jokertecken i bakgrunden.

```powershell
help process
```

Föregående kommando ger samma resultat som att ange `*` jokertecknet för varje process slut.

Jag vill lägga till dem eftersom det är det alternativ som alltid fungerar konsekvent. Annars krävs de i vissa scenarier och inte andra. När du lägger till ett jokertecken i mitten av värdet läggs de inte längre automatiskt till i bakgrunden till det värde som du har angett.

```powershell
help pr*cess
```

Inga resultat returneras av det kommandot om inte `*` jokertecknet läggs till i början, slutet eller både början och slutet av `pr*cess` .

Om det angivna värdet börjar med ett bindestreck, genereras ett fel eftersom PowerShell tolkar det som ett parameter namn och det inte finns något sådant parameter namn för `Get-Help` cmdleten.

```powershell
help -process
```

Om det du försöker söka efter är kommandon som slutar med `-process` , behöver du bara lägga till `*` jokertecknet i början av värdet.

```powershell
help *-process
```

När du söker efter PowerShell-kommandon med `Get-Help` , vill du vara lite mer vagt i stället för att vara för speciell med det du söker efter.

Söker efter `process` tidigare hittade endast kommandon som finns `process` i namnet på kommandot och bara returnerade resultaten. När `Get-Help` används för att söka efter `processes` hittas inga matchningar för kommando namn, så den utför en sökning i alla hjälp avsnitt i PowerShell på systemet och returnerar eventuella matchningar som hittas. Detta gör att det returnerar ett enorma antal resultat.

```powershell
Get-Help processes
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Disconnect-PSSession              Cmdlet    Microsoft.PowerShell.Core Disconnects from...
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
ForEach-Object                    Cmdlet    Microsoft.PowerShell.Core Performs an oper...
Get-PSSessionConfiguration        Cmdlet    Microsoft.PowerShell.Core Gets the registe...
New-PSTransportOption             Cmdlet    Microsoft.PowerShell.Core Creates an objec...
Out-Host                          Cmdlet    Microsoft.PowerShell.Core Sends output to ...
Where-Object                      Cmdlet    Microsoft.PowerShell.Core Selects objects ...
Clear-Variable                    Cmdlet    Microsoft.PowerShell.U... Deletes the valu...
Compare-Object                    Cmdlet    Microsoft.PowerShell.U... Compares two set...
Convert-String                    Cmdlet    Microsoft.PowerShell.U... Formats a string...
ConvertFrom-Csv                   Cmdlet    Microsoft.PowerShell.U... Converts object ...
ConvertTo-Html                    Cmdlet    Microsoft.PowerShell.U... Converts Microso...
ConvertTo-Xml                     Cmdlet    Microsoft.PowerShell.U... Creates an XML-b...
Debug-Runspace                    Cmdlet    Microsoft.PowerShell.U... Starts an intera...
Export-Csv                        Cmdlet    Microsoft.PowerShell.U... Converts objects...
Export-FormatData                 Cmdlet    Microsoft.PowerShell.U... Saves formatting...
Format-List                       Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Format-Table                      Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Get-Random                        Cmdlet    Microsoft.PowerShell.U... Gets a random nu...
Get-Unique                        Cmdlet    Microsoft.PowerShell.U... Returns unique i...
Group-Object                      Cmdlet    Microsoft.PowerShell.U... Groups objects t...
Import-Clixml                     Cmdlet    Microsoft.PowerShell.U... Imports a CLIXML...
Import-Csv                        Cmdlet    Microsoft.PowerShell.U... Creates table-li...
Measure-Object                    Cmdlet    Microsoft.PowerShell.U... Calculates the n...
Out-File                          Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Out-GridView                      Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Select-Object                     Cmdlet    Microsoft.PowerShell.U... Selects objects ...
Set-Variable                      Cmdlet    Microsoft.PowerShell.U... Sets the value o...
Sort-Object                       Cmdlet    Microsoft.PowerShell.U... Sorts objects by...
Tee-Object                        Cmdlet    Microsoft.PowerShell.U... Saves command ou...
Trace-Command                     Cmdlet    Microsoft.PowerShell.U... Configures and s...
Write-Output                      Cmdlet    Microsoft.PowerShell.U... Sends the specif...
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Get-WmiObject                     Cmdlet    Microsoft.PowerShell.M... Gets instances o...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-Counter                       Cmdlet    Microsoft.PowerShell.D... Gets performance...
Invoke-WSManAction                Cmdlet    Microsoft.WSMan.Manage... Invokes an actio...
Remove-WSManInstance              Cmdlet    Microsoft.WSMan.Manage... Deletes a manage...
Get-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Displays managem...
New-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Creates a new in...
Set-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Modifies the man...
about_Arithmetic_Operators        HelpFile                            Describes the op...
about_Arrays                      HelpFile                            Describes arrays...
about_Debuggers                   HelpFile                            Describes the Wi...
about_Execution_Policies          HelpFile                            Describes the Wi...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Foreach                     HelpFile                            Describes a lang...
about_Functions                   HelpFile                            Describes how to...
about_Language_Keywords           HelpFile                            Describes the ke...
about_Methods                     HelpFile                            Describes how to...
about_Objects                     HelpFile                            Provides essenti...
about_Parallel                    HelpFile                            Describes the Pa...
about_Pipelines                   HelpFile                            Combining comman...
about_Preference_Variables        HelpFile                            Variables that c...
about_Remote                      HelpFile                            Describes how to...
about_Remote_Output               HelpFile                            Describes how to...
about_Sequence                    HelpFile                            Describes the Se...
about_Session_Configuration_Files HelpFile                            Describes sessio...
about_Variables                   HelpFile                            Describes how va...
about_Windows_PowerShell_5.0      HelpFile                            Describes new fe...
about_WQL                         HelpFile                            Describes WMI Qu...
about_WS-Management_Cmdlets       HelpFile                            Provides an over...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Parallel                    HelpFile                            Describes the Pa...
about_Sequence                    HelpFile                            Describes the Se...
```

Använd `Help` om du vill söka efter `process` returnerade 10 resultat och använda det för att söka efter `processes` returnerade 68-resultat. Om det bara finns ett resultat visas själva hjälp avsnittet i stället för en lista med kommandon.

```powershell
get-help *hotfix*
```

```Output
NAME
    Get-HotFix

SYNOPSIS
    Gets the hotfixes that have been applied to the local and remote computers.


SYNTAX
    Get-HotFix [-ComputerName <String[]>] [-Credential <PSCredential>] [-Description
    <String[]>] [<CommonParameters>]

    Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential
    <PSCredential>] [<CommonParameters>]


DESCRIPTION
    The Get-Hotfix cmdlet gets hotfixes (also called updates) that have been installed
    on either the local computer (or on specified remote computers) by Windows Update,
    Microsoft Update, or Windows Server Update Services; the cmdlet also gets hotfixes
    or updates that have been installed manually by users.


RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821586
    Win32_QuickFixEngineering http://go.microsoft.com/fwlink/?LinkID=145071
    Get-ComputerRestorePoint
    Add-Content

REMARKS
    To see the examples, type: "get-help Get-HotFix -examples".
    For more information, type: "get-help Get-HotFix -detailed".
    For technical information, type: "get-help Get-HotFix -full".
    For online help, type: "get-help Get-HotFix -online"
```

Nu kan du Thiagarajan myten som `Help` i PowerShell bara kan hitta kommandon som har hjälp avsnitt.

```powershell
help *more*
```

```Output
NAME
    more

SYNTAX
    more [[-paths] <string[]>]


ALIASES
    None


REMARKS
    None
```

Observera att det `more` inte finns något hjälp avsnitt i föregående exempel, men `Help` systemet i PowerShell kunde hitta det. Den hittade bara en matchning och returnerade den grundläggande syntax som visas när ett kommando saknar hjälp avsnitt.

PowerShell innehåller flera koncept hjälp avsnitt (om). Följande kommando kan användas för att returnera en lista över alla **om** hjälp avsnitt i systemet.

```powershell
help About_*
```

Om du begränsar resultatet till ett enda om-hjälp avsnitt visas det faktiska hjälp avsnittet i stället för att returnera en lista.

```powershell
help about_Updatable_Help
```

Hjälp systemet i PowerShell måste uppdateras för **att det ska** gå att presentera hjälp avsnitten. Om den första uppdateringen av hjälp systemet misslyckades på din dator, kommer filerna inte att vara tillgängliga förrän `Update-Help` cmdleten har körts utan problem.

## <a name="get-command"></a>Get-Command

`Get-Command` är utformad för att hjälpa dig att hitta kommandon. Om `Get-Command` du kör utan parametrar returneras en lista över alla kommandon i systemet. Följande exempel visar hur du använder `Get-Command` cmdleten för att avgöra vilka kommandon som finns för att arbeta med processer:

```powershell
Get-Command -Noun Process
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Debug-Process                                      3.1.0.0    Microsof...
Cmdlet          Get-Process                                        3.1.0.0    Microsof...
Cmdlet          Start-Process                                      3.1.0.0    Microsof...
Cmdlet          Stop-Process                                       3.1.0.0    Microsof...
Cmdlet          Wait-Process                                       3.1.0.0    Microsof...
```

Observera i föregående exempel där kördes `Get-Command` , parametern **Substantiv** används och `Process` anges som värde för parametern **Substantiv** . Vad händer om du inte vet hur du använder `Get-Command` cmdleten? Du kan använda `Get-Help` för att visa hjälp avsnittet för `Get-Command` .

Parametrarna **Name** , **Substantiv** och **verb** accepterar jokertecken. I följande exempel visas jokertecken som används med parametern **Name** :

```Output
Get-Command -Name *service*
```

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Function        Set-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          New-Service                                        3.1.0.0    Microsof...
Cmdlet          New-WebServiceProxy                                3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
Application     AgentService.exe                                   10.0.14... C:\Windo...
Application     SensorDataService.exe                              10.0.14... C:\Windo...
Application     services.exe                                       10.0.14... C:\Windo...
Application     services.msc                                       0.0.0.0    C:\Windo...
Application     TieringEngineService.exe                           10.0.14... C:\Windo...
```

Jag är inte en fläkt med att använda jokertecken med parametern **Name** `Get-Command` , eftersom den även returnerar körbara filer som inte är ursprungliga PowerShell-kommandon.

Om du kommer att använda jokertecken med parametern **Name** rekommenderar vi att du begränsar resultatet med parametern **CommandType** .

```powershell
Get-Command -Name *service* -CommandType Cmdlet, Function, Alias
```

Ett bättre alternativ är att använda antingen **verb** -eller **Substantiv** -parametern eller båda, eftersom bara PowerShell-kommandon har både verb och substantiv.

Har du hittat något fel med hjälp avsnittet? De goda nyheterna är att hjälp avsnitten för PowerShell har öppnats och är tillgängliga i [PowerShell-dokument-][] lagringsplatsen på GitHub. Betala vidarebefordran genom att inte bara åtgärda den felaktiga informationen för dig själv, utan även för alla andra. Du behöver bara förgrening i PowerShell-dokumentationens lagrings plats på GitHub, uppdatera hjälp avsnittet och skicka en pull-begäran.
När pull-begäran har godkänts är den korrigerade dokumentationen tillgänglig för alla.

## <a name="updating-help"></a>Hjälp om uppdatering

Den lokala kopian av PowerShell-hjälpen har tidigare uppdaterat hjälp avsnittet om första gången på ett kommando begärdes. Vi rekommenderar att regelbundet uppdatera hjälp systemet, eftersom det kan finnas uppdateringar av hjälp innehållet från tid till tid. `Update-Help`Cmdleten används för att uppdatera hjälp avsnitten.
Den kräver Internet åtkomst som standard och för att köra PowerShell som administratör.

```powershell
Update-Help
```

```Output
Update-Help : Failed to update Help for the module(s) 'BitsTransfer' with UI culture(s)
{en-US} : Unable to retrieve the HelpInfo XML file for UI culture en-US. Make sure the HelpInfoUri
property in the module manifest is valid or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : InvalidOperation: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : InvalidHelpInfoUri,Microsoft.PowerShell.Commands.UpdateHel
   pCommand

Update-Help : Failed to update Help for the module(s) 'NetworkControllerDiagnostics,
StorageReplica' with UI culture(s) {en-US} : Unable to retrieve the HelpInfo XML file
for UI culture en-US. Make sure the HelpInfoUri property in the module manifest is valid
or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : ResourceUnavailable: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : UnableToRetrieveHelpInfoXml,Microsoft.PowerShell.Commands.
   UpdateHelpCommand
```

Ett par moduler returnerade fel, vilket inte är ovanligt. Om datorn inte har till gång till Internet kan du använda `Save-Help` cmdleten på en annan dator som har Internet åtkomst för att först spara den uppdaterade hjälp informationen till en fil resurs i nätverket och sedan använda **SourcePath** -parametern för `Update-Help` för att ange den här nätverks platsen för hjälp avsnitten.

Överväg att konfigurera en schemalagd aktivitet eller lägga till en del logik i ditt profil skript i PowerShell för att regelbundet uppdatera hjälp innehållet på datorn. Profil skript beskrivs i ett kommande kapitel.

## <a name="summary"></a>Sammanfattning

I det här kapitlet har du lärt dig hur du hittar kommandon med både `Get-Help` och `Get-Command` . Du har lärt dig hur du använder hjälp systemet för att ta reda på hur du använder kommandon när du har hittat dem. Du har också lärt dig hur du uppdaterar innehållet i hjälp avsnitten när det finns uppdateringar.

Mitt utmaning till dig är att lära dig ett PowerShell-kommando per dag.

```powershell
Get-Command | Get-Random | Get-Help -Full
```

## <a name="review"></a>Genomgång

1. Är **DisplayName** -parametern för `Get-Service` positional?
1. Hur många parameter uppsättningar `Get-Process` har cmdleten?
1. Vilka PowerShell-kommandon finns för att arbeta med händelse loggar?
1. Vad är PowerShell-kommandot för att returnera en lista med PowerShell-processer som körs på datorn?
1. Hur uppdaterar du hjälp innehållet för PowerShell som lagras på datorn?

## <a name="recommended-reading"></a>Rekommenderad läsning

Om du vill veta mer om de ämnen som beskrivs i det här kapitlet rekommenderar vi att du läser följande PowerShell-hjälp avsnitt.

- [Get – hjälp][]
- [Get-Command][]
- [Uppdatera – hjälp][]
- [Spara – hjälp][]
- [about_Updatable_Help][]
- [about_Command_Syntax][]

I nästa kapitel lär du dig om `Get-Member` cmdleten samt objekt, egenskaper och metoder.

<!-- link references -->
[Get – hjälp]: /powershell/module/microsoft.powershell.core/get-help
[Get-Command]: /powershell/module/microsoft.powershell.core/get-command
[Uppdatera – hjälp]: /powershell/module/microsoft.powershell.core/update-help
[Spara – hjälp]: /powershell/module/microsoft.powershell.core/save-help
[about_Updatable_Help]: /powershell/module/microsoft.powershell.core/about/about_updatable_help
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[PowerShell-dokumentation]: https://github.com/powershell/powershell
[Bilaga A]: appendix-a.md
