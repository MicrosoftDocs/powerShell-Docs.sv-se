---
title: Enkelriktade linjer och pipeline
description: En PowerShell-liner är en kontinuerlig pipeline, som innehåller flera kommandon, för att utföra en enskild uppgift.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: b8fd45e5e5dc408754ebac015757ef4241428978
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633353"
---
# <a name="chapter-4---one-liners-and-the-pipeline"></a>Kapitel 4 – en-liners och pipelinen

När jag först startade Learning PowerShell, och det inte gick att utföra en uppgift med en PowerShell-liner, gick jag tillbaka till det grafiska användar gränssnittet. Med tiden har jag skapat mina kunskaper för att skriva skript, funktioner och moduler. Tillåt inte att du blir överbelastad av några av de mer avancerade exempel som du kan se på Internet. Ingen är en naturlig expert med PowerShell. Vi var nybörjare på en och samma tillfälle.

Jag har fått råd för att erbjuda dem som fortfarande använder GUI-gränssnittet för administration: installera hanterings verktygen på din administratörs arbets Station och hantera dina servrar via fjärr anslutning. På så sätt spelar det ingen roll om servern kör en GUI-eller Server Core-installation av operativ systemet.
Det hjälper dig att förbereda dig för att hantera servrar via en fjärr anslutning med PowerShell.

Precis som i föregående kapitel måste du vara noga med att följa anvisningarna i Windows 10 Lab Environment-datorn.

## <a name="one-liners"></a>En-liners

En PowerShell-liner är en kontinuerlig pipeline och inte nödvändigt vis ett kommando som finns på en fysisk rad. Alla kommandon som finns på en fysisk rad är inte en-liners.

Även om följande kommando finns på flera fysiska rader, är det en PowerShell-liner eftersom det är en kontinuerlig pipeline. Det kan skrivas på en fysisk rad, men jag har valt rad brytning vid pipe-symbolen. Pipe-symbolen är en av de tecken där en naturlig rad brytning tillåts i PowerShell.

```powershell
Get-Service |
  Where-Object CanPauseAndContinue -eq $true |
    Select-Object -Property *
```

```Output
Name                : LanmanWorkstation
RequiredServices    : {NSI, MRxSmb20, Bowser}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Workstation
DependentServices   : {SessionEnv, Netlogon, Browser}
MachineName         : .
ServiceName         : LanmanWorkstation
ServicesDependedOn  : {NSI, MRxSmb20, Bowser}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : Netlogon
RequiredServices    : {LanmanWorkstation}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Netlogon
DependentServices   : {}
MachineName         : .
ServiceName         : Netlogon
ServicesDependedOn  : {LanmanWorkstation}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : vmicheartbeat
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Heartbeat Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicheartbeat
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmickvpexchange
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Data Exchange Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmickvpexchange
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicrdv
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Remote Desktop Virtualization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicrdv
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicshutdown
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Guest Shutdown Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicshutdown
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmictimesync
RequiredServices    : {VmGid}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Time Synchronization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmictimesync
ServicesDependedOn  : {VmGid}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicvss
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Volume Shadow Copy Requestor
DependentServices   : {}
MachineName         : .
ServiceName         : vmicvss
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : Winmgmt
RequiredServices    : {RPCSS}
CanPauseAndContinue : True
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Management Instrumentation
DependentServices   : {wscsvc, NcaSvc, iphlpsvc}
MachineName         : .
ServiceName         : Winmgmt
ServicesDependedOn  : {RPCSS}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :
```

Naturliga rad brytningar kan ske på vanliga tecken, inklusive kommatecken ( `,` ) och inledande hakparenteser ( `[` ), klammerparenteser ( `{` ) och parenteser ( `(` ). Andra som inte är så vanliga inkluderar semikolon ( `;` ), likhets tecken ( `=` ) och båda inledande och dubbla citat tecken ( `'` , `"` ).

Med hjälp av `` ` `` ett kontroversiellt-ämne () eller grav accent som ett linje fortsättnings avstånd. Min rekommendation är att försöka undvika det om det är möjligt. Jag ser ofta PowerShell-kommandon som skrivs med ett bakstreck direkt efter ett naturligt rad brytnings kort.
Det finns ingen anledning att det finns där.

```powershell
Get-Service -Name w32time |
>> Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

Kommandona som visas i föregående två exempel fungerar bra i PowerShell-konsolen. Men om du försöker köra dem i konsol fönstret i PowerShell ISE genereras ett fel. Konsol fönstret i PowerShell ISE väntar inte på att resten av kommandot ska anges på nästa rad som PowerShell-konsolen gör. Undvik det här problemet i konsol fönstret i PowerShell ISE genom att använda <kbd>Shift</kbd> + <kbd>Enter</kbd> i stället för att trycka på <kbd>RETUR</kbd> när du fortsätter ett kommando på en annan rad.

Det här nästa exemplet är inte en PowerShell-liner eftersom det inte är en kontinuerlig pipeline. Det är två separata kommandon på en rad, åtskilda med semikolon.

```powershell
$Service = 'w32time'; Get-Service -Name $Service
```

```powershell
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Många programmerings-och skript språk kräver ett semikolon i slutet av varje rad. Även om de kan användas på det sättet i PowerShell rekommenderas de inte eftersom de inte behövs.

## <a name="filtering-left"></a>Filtrera vänster

Resultatet av de kommandon som visas i det här kapitlet har filtrerats ned till en delmängd. Används till exempel `Get-Service` med parametern **Name** för att filtrera listan över tjänster som bara returnerats till Windows tids tjänst.

I pipelinen vill du alltid filtrera resultaten nedåt till det du söker så tidigt som möjligt. Detta görs med parametrar på det första kommandot eller längst till vänster.
Detta kallas ibland _filtrering av Left_.

I följande exempel används parametern **Name** för `Get-Service` att omedelbart filtrera resultaten till Windows tids tjänst.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Det är inte ovanligt att se exempel där kommandot är skickas för `Where-Object` att utföra filtreringen.

```powershell
Get-Service | Where-Object Name -eq w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  W32Time            Windows Time
```

Det första exemplet filtrerar på källan och returnerar bara resultatet för Windows tids tjänst.
Det andra exemplet returnerar alla tjänster och skickar dem sedan till ett annat kommando för att utföra filtreringen. Det kanske inte ser ut som ett stort avtal i det här exemplet, Tänk på att du har frågat om en lista över Active Directory användare. Vill du verkligen returnera informationen för många tusentals användar konton från Active Directory endast för att skicka dem till ett annat kommando som filtrerar dem ned till en liten delmängd? Min rekommendation är att alltid filtrera från vänster även om det inte verkar vara så viktigt. Du kommer att använda den för att automatiskt filtrera från vänster när det verkligen spelar någon roll.

När jag har haft någon talan om för mig att du har angett kommandona i spelar ingen roll. Det gick inte att göra ytterligare från sanningen. Den ordning som kommandona anges i spelar själva roll när filtreringen utförs. Anta till exempel scenariot där du använder `Select-Object` för att välja bara några få egenskaper och `Where-Object` filtrera på egenskaper som inte kommer att visas i valet. I så fall måste filtreringen först inträffa, annars finns inte egenskapen i pipelinen när du försöker utföra filtreringen.

```powershell
Get-Service |
Select-Object -Property DisplayName, Running, Status |
Where-Object CanPauseAndContinue
```

Kommandot i föregående exempel returnerar inte några resultat eftersom egenskapen **CanStopAndContinue** inte finns när resultatet av `Select-Object` är skickas till `Where-Object` . Den aktuella egenskapen har inte marker ATS. I själva verket har den filtrerats bort. Ändra ordning på `Select-Object` och `Where-Object` genererar önskade resultat.

```powershell
Get-Service |
Where-Object CanPauseAndContinue |
Select-Object -Property DisplayName, Status
```

```Output
DisplayName                                    Status
-----------                                    ------
Workstation                                    Running
Netlogon                                       Running
Hyper-V Heartbeat Service                      Running
Hyper-V Data Exchange Service                  Running
Hyper-V Remote Desktop Virtualization Service  Running
Hyper-V Guest Shutdown Service                 Running
Hyper-V Time Synchronization Service           Running
Hyper-V Volume Shadow Copy Requestor           Running
Windows Management Instrumentation             Running
```

## <a name="the-pipeline"></a>Pipelinen

Som du har sett i många av exemplen som visas hittills i denna bok, kan många gånger använda utdata från ett kommando som indata för ett annat kommando. I kapitel 3 `Get-Member` användes för att avgöra vilken typ av objekt ett kommando genererar. Kapitel 3 visar också hur du använder **ParameterType** -parametern för `Get-Command` för att avgöra vilka kommandon som godkände den typen av indatatyper, även om de inte nödvändigt vis är inaktuella.

Beroende på hur grundligt ett kommando bidrar är, kan det innehålla avsnittet **indata** och **utdata** .

```powershell
help Stop-Service -Full
```

```Output
...
INPUTS
    System.ServiceProcess.ServiceController, System.String
        You can pipe a service object or a string that contains the name of a service
        to this cmdlet.

OUTPUTS
    None, System.ServiceProcess.ServiceController
        This cmdlet generates a System.ServiceProcess.ServiceController object that
        represents the service, if you use the PassThru parameter. Otherwise, this
        cmdlet does not generate any output.
...
```

Endast det relevanta avsnittet av hjälpen visas i föregående resultat. Som du kan se anger **indata** avsnittet att ett **ServiceController** eller ett **String** -objekt kan skickas till `Stop-Service` cmdleten. Det visar inte vilka parametrar som accepterar den typen av inaktuella indatatyper. Ett av de enklaste sätten att fastställa att informationen är att titta igenom de olika parametrarna i den fullständiga versionen av hjälpen för `Stop-Service` cmdleten.

```powershell
help Stop-Service -Full
```

```powershell
...
-DisplayName <String[]>
    Specifies the display names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    named
    Default value                None
    Accept pipeline input?       False
    Accept wildcard characters?  false

-InputObject <ServiceController[]>
    Specifies ServiceController objects that represent the services to stop. Enter a
    variable that contains the objects, or type a command or expression that gets the
    objects.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByValue)
    Accept wildcard characters?  false

-Name <String[]>
    Specifies the service names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  false
...
```

Jag har återigen visat den relevanta delen av hjälpen i den föregående uppsättningen med resultat. Observera att parametern **DisplayName** inte accepterar pipeline-indatatyper, **InputObject** -parametern godkänner pipeline-inmatade **värden** för **ServiceController** -objekt och parametern **Name** accepterar pipeline-inmatade **med värde** för **sträng** objekt. Den accepterar också pipeline-inmatade **efter egenskaps namn**.

När en parameter accepterar pipeline-inmatade med både egenskaps namn och värde, försöker den alltid **med värdet** först. Om **värdet** inte kan utföras försöker det **med ett egenskaps namn**. **Värdet** är lite missvisande. Jag föredrar att anropa den **efter typ**. Det innebär att om du rör resultatet av ett kommando som skapar en **ServiceController** objekt typ till `Stop-Service` , binder det inmatade objekt till **InputObject** -parametern. Men om du rör resultatet av ett kommando som producerar **sträng** utdata till `Stop-Service` binder det till **namn** parametern. Om du lägger till resultatet av ett kommando som inte genererar ett **ServiceController** -eller **String** -objekt till `Stop-Service` , men det genererar utdata som innehåller en egenskap som heter **Name**, binder egenskapen **Name** från utdata till **Name** -parametern för `Stop-Service` .

Bestäm vilken typ av utdata som `Get-Service` kommandot genererar.

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController
```

`Get-Service`skapar en ServiceController objekt typ.

Som du såg tidigare i hjälpen, **InputObject** -parametern för `Stop-Service` accepterar **ServiceController** -objekt via pipelinen **efter värde** (efter typ). Det innebär att när resultatet av `Get-Service` cmdleten är skickas `Stop-Service` , binder de till **InputObject** -parametern för `Stop-Service` .

```powershell
Get-Service -Name w32time | Stop-Service
```

Nu kan du prova sträng inmatade. Pipe `w32time` för att `Get-Member` bara bekräfta att det är en sträng.

```powershell
'w32time' | Get-Member
```

```Output
   TypeName: System.String
```

Som tidigare har visats i hjälpen, rör sig en sträng för att `Stop-Service` binda den **efter värde** till **namn** parametern för `Stop-Service` . Testa detta genom att skicka vidare `w32time` till `Stop-Service` .

```powershell
'w32time' | Stop-Service
```

Lägg märke till att jag använde enkla citat tecken runt strängen i föregående exempel `w32time` . I PowerShell bör du alltid använda enkla citat tecken i stället för dubbla citat tecken om inte innehållet i den citerade strängen innehåller en variabel som måste utökas till det faktiska värdet. Med hjälp av enkla citat tecken behöver inte PowerShell parsa innehållet i citat tecken så att koden körs lite snabbare.

Skapa ett anpassat objekt för att testa pipeline-inmatade efter egenskaps namn för parametern **Name** i `Stop-Service` .

```powershell
$CustomObject = [pscustomobject]@{
 Name = 'w32time'
 }
```

Innehållet i **CustomObject** -variabeln är en **PSCustomObject** objekt typ och innehåller en egenskap med namnet **Name**.

```powershell
$CustomObject | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty string Name=w32time
```

Om du omger `$CustomObject` variabeln med citat tecken vill du använda dubbla citat tecken.
Annars är den litterala strängen `$CustomObject` skickas till `Get-Member` i stället för värdet som variabeln innehåller, med enkla citat tecken.

Även om innehållet i `$CustomObject` till `Stop-Service` cmdleten binds till **Name** -parametern, binds den här tiden **efter egenskaps namn** i stället för **värdet** eftersom innehållet i `$CustomObject` är ett objekt som har en egenskap med namnet **Name**.

I det här exemplet skapar jag ett annat anpassat objekt med ett annat egenskaps namn, t. ex. **tjänst**.

```powershell
$CustomObject = [pscustomobject]@{
  Service = 'w32time'
}
```

Ett fel genereras vid försök att skicka `$CustomObject` en pipe till `Stop-Service` eftersom det inte genererar ett **ServiceController** -eller **String** -objekt, och det har inte någon egenskap med namnet **Name**.

```powershell
$CustomObject | Stop-Service
```

```Output
Stop-Service : Cannot find any service with service name '@{Service=w32time}'.
At line:1 char:17
+ $CustomObject | Stop-Service
+
    + CategoryInfo          : ObjectNotFound: (@{Service=w32time}:String) [Stop-Service]
   , ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.S
   topServiceCommand
```

Om utdata från ett kommando inte raderas med inmatnings alternativen för pipelinen för ett annat kommando, `Select-Object` kan användas för att byta namn på egenskapen så att egenskaperna är korrekt.

```powershell
$CustomObject |
  Select-Object -Property @{name='Name';expression={$_.Service}} |
    Stop-Service
```

I det här exemplet `Select-Object` användes för att byta namn på **tjänst** egenskapen till en egenskap med namnet **Name**.

Syntaxen det här exemplet kan förefalla lite komplicerat vid första. Det jag har lärt dig är att du aldrig får lära dig syntaxen genom att kopiera och klistra in kod. Ta tid att ange koden i. Efter några gånger blir det andra natur. Att ha flera övervakare är en enorm förmån eftersom du kan visa exempel koden på en skärm och skriva den i en annan.

Ibland kanske du vill använda en parameter som inte accepterar pipeline-inflöden. Följande exempel visar hur du använder utdata från ett kommando som indata för ett annat. Spara först visnings namnet för ett par Windows-tjänster i en textfil.

```powershell
'Background Intelligent Transfer Service', 'Windows Time' |
Out-File -FilePath $env:TEMP\services.txt
```

Du kan köra kommandot som tillhandahåller de utdata som krävs inom parentes som värdet för parametern för kommandot som kräver indatan.

```powershell
Stop-Service -DisplayName (Get-Content -Path $env:TEMP\services.txt)
```

Detta är precis som drifts ordningen i algebra för dem som kommer ihåg hur det fungerar. Kommandot inom parentes körs alltid före den yttre delen av kommandot.

## <a name="powershellget"></a>PowerShellGet

PowerShellGet är en PowerShell-modul som innehåller kommandon för att upptäcka, installera, publicera och uppdatera PowerShell-moduler (och andra artefakter) till eller från en NuGet-lagringsplats. PowerShellGet levereras med PowerShell version 5,0 och senare. Den är tillgänglig som en separat nedladdning för PowerShell version 3,0 och högre.

Microsoft är värd för en NuGet-lagringsplats online som kallas för [PowerShell-galleriet][]. Även om den här lagrings platsen är värd för Microsoft, skrivs majoriteten av modulerna i lagrings platsen inte av Microsoft. All kod som hämtas från PowerShell-galleriet bör granskas noggrant i en isolerad test miljö innan den anses vara lämplig för användning i en produktions miljö.

De flesta företag vill ha sina egna interna privata NuGet-lagringsplatser där de bara kan publicera sina interna användnings moduler och moduler som de har laddat ned från andra källor när de har verifierat att de inte är skadliga.

Använd `Find-Module` cmdleten som är en del av PowerShellGet-modulen för att hitta en modul i PowerShell-galleriet som jag skrev med namnet MrToolkit.

```powershell
Find-Module -Name MrToolkit
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with
NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or
'C:\Users\MrAdmin\AppData\Local\PackageManagement\ProviderAssemblies'. You can also
install the NuGet provider by running 'Install-PackageProvider -Name NuGet
-MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the
NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1        MrToolkit                           PSGallery            Misc PowerShell Tools
```

Första gången du använder ett av kommandona från PowerShellGet-modulen uppmanas du att installera NuGet-providern.

Du installerar MrToolkit-modulen genom att skicka det tidigare kommandot till `Install-Module` .

```powershell
Find-Module -Name MrToolkit | Install-Module
```

```Output
Untrusted repository
You are installing the modules from an untrusted repository. If you trust this
repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet.
Are you sure you want to install the modules from
'https://www.powershellgallery.com/api/v2/'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): y
```

Eftersom PowerShell-galleriet är ett ej betrott lager, uppmanas du att godkänna installationen av modulen.

## <a name="finding-pipeline-input-the-easy-way"></a>Hitta pipeline-inmatare det enkla sättet

MrToolkit-modulen innehåller en funktion med namnet `Get-MrPipelineInput` . Denna cmdlet kan användas för att enkelt avgöra vilka parametrar i ett kommando som accepterar pipeline-inflöde, vilken typ av objekt som de accepterar, och om de accepterar pipeline-inmatade **efter värde** eller **egenskaps namn**.

```powershell
Get-MrPipelineInput -Name Stop-Service
```

```Output
ParameterName ParameterType                             ValueFromPipeline ValueFromPipelineByPropertyName
------------- -------------                             ----------------- ---------------
InputObject   System.ServiceProcess.ServiceController[]              True           False
Name          System.String[]                                        True            True
```

Som du ser kan samma information som vi tidigare fastställde genom att gå igenom hjälpen enkelt bestämmas med den här funktionen.

## <a name="summary"></a>Sammanfattning

I det här kapitlet har du lärt dig om PowerShell One-liners. Du har lärt dig att antalet fysiska rader som ett kommando är på inte har något att göra med om det är en PowerShell-liner. Du har också lärt dig om filtrering, till vänster, pipelinen och PowerShellGet.

## <a name="review"></a>Granska

1. Vad är en PowerShell-liner?
1. Vad är några av de tecken där naturliga rad brytningar kan uppstå i PowerShell?
1. Varför ska du filtrera kvar?
1. Vilka är de två sätt som ett PowerShell-kommando kan acceptera för pipeline-inmatade?
1. Varför ska du inte lita på kommandon som du hittar i PowerShell-galleriet?

## <a name="recommended-reading"></a>Rekommenderad läsning

- [about_Pipelines][]
- [about_Command_Syntax][]
- [about_Parameters][]
- [PowerShellGet: det stora enkla sättet att identifiera, installera och uppdatera PowerShell-moduler][psget]

<!-- link references-->
[about_Pipelines]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[about_Parameters]: /powershell/module/microsoft.powershell.core/about/about_parameters
[psget]: https://mikefrobbins.com/2015/04/23/powershellget-the-big-easy-way-to-discover-install-and-update-powershell-modules/
[PowerShell-galleriet]: https://www.powershellgallery.com/
