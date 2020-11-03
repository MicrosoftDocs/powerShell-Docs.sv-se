---
description: Beskriver de parametrar som Windows PowerShell-arbetsflöde lägger till i aktiviteter.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_activitycommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_ActivityCommonParameters
ms.openlocfilehash: b745bf17e4ae26156042ecdc25211830177bc692
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270962"
---
# <a name="about-activitycommonparameters"></a>Om ActivityCommonParameters

## <a name="short-description"></a>KORT BESKRIVNING

Beskriver de parametrar som Windows PowerShell-arbetsflöde lägger till i aktiviteter.

## <a name="long-description"></a>LÅNG BESKRIVNING

Windows PowerShell-arbetsflöde lägger till de gemensamma aktivitets parametrarna i aktiviteter som härleds från Bask Lassen för PSActivity. Den här kategorin omfattar InlineScript-aktiviteten och Windows PowerShell-cmdletar som implementeras som aktiviteter, till exempel Get-Process och get-WinEvent.

De gemensamma aktivitets parametrarna är inte giltiga på Suspend-Workflow och Checkpoint-Workflow aktiviteter och de läggs inte till i cmdletar eller uttryck som Windows PowerShell-arbetsflöde körs automatiskt i ett InlineScript-skript block eller liknande aktivitet. De gemensamma aktivitets parametrarna är tillgängliga på InlineScript-aktiviteten, men inte på kommandon i InlineScript-skript blocket.

Flera av de gemensamma aktivitets parametrarna är också gemensamma arbets flödes parametrar eller vanliga parametrar för Windows PowerShell. Andra gemensamma aktivitets parametrar är unika för aktiviteter.

Information om gemensamma parametrar för arbets flöden finns i about_WorkflowCommonParameters. Information om vanliga Windows PowerShell-parametrar finns about_CommonParameters.

### <a name="list-of-activity-common-parameters"></a>LISTA ÖVER GEMENSAMMA AKTIVITETS PARAMETRAR

```
AppendOutput                      PSDebug
Debug                             PSDisableSerialization
DisplayName                       PSDisableSerializationPreference
ErrorAction                       PSError
Input                             PSPersist
MergeErrorToOutput                PSPort
PSActionRetryCount                PSProgress
PSActionRetryIntervalSec          PSProgressMessage
PSActionRunningTimeoutSec         PSRemotingBehavior
PSApplicationName                 PSRequiredModules
PSAuthentication                  PSSessionOption
PSCertificateThumbprint           PSUseSSL
PSComputerName                    PSVerbose
PSConfigurationName               PSWarning
PSConnectionRetryCount            Result
PSConnectionRetryIntervalSec      UseDefaultInput
PSConnectionURI                   Verbose
PSCredential                      WarningAction
```

### <a name="parameter-descriptions"></a>PARAMETER BESKRIVNINGAR

I det här avsnittet beskrivs gemensamma aktivitets parametrar.

#### <a name="appendoutput-boolean"></a>AppendOutput \<Boolean\>

Värdet `$True` lägger till utdata för aktiviteten till värdet för variabeln.
Värdet `$False` har ingen påverkan. Som standard ersätter variabeln värdet variabeln genom att tilldela ett värde till en variabel.

Följande kommandon lägger till exempel till ett process objekt till serviceobjektet i `$x` variabeln.

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x = Get-Process -AppendOutput $true
}
```

Den här parametern är utformad för XAML-baserade arbets flöden. I skript arbets flöden kan du också använda operatorn + = tilldelning för att lägga till utdata till värdet för en variabel, som du ser i följande exempel.

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x += Get-Process
}
```

#### <a name="debug-switchparameter"></a>Förbigå \<SwitchParameter\>

Visar information om program nivå om den åtgärd som utförs av kommandot.
Parametern debug åsidosätter värdet för variabeln $DebugPreference för det aktuella kommandot. Den här parametern fungerar bara när kommandot genererar fel söknings meddelanden. Den här parametern är också en gemensam Windows PowerShell-parameter.

#### <a name="displayname-string"></a>DisplayName \<String\>

Anger ett eget namn för aktiviteten. Värdet DisplayName visas i förlopps indikatorn medan arbets flödet körs och i värdet för egenskapen Progress i arbets flödes jobbet. När PSProgressMessage-parametern också ingår i kommandot visas förlopps indikatorns innehåll i \<DisplayName\> : \<PSProgressMessage\> format.

#### <a name="erroraction-actionpreference"></a>ErrorAction \<ActionPreference\>

Anger hur aktiviteten reagerar på ett icke-avslutande fel från kommandot. Det har ingen inverkan på avslutnings fel. Den här parametern fungerar bara när kommandot genererar ett icke-avslutande fel, till exempel från Write-Error-cmdleten. Parametern ErrorAction åsidosätter värdet för variabeln $ErrorActionPreference för det aktuella kommandot. Den här parametern är också en gemensam Windows PowerShell-parameter.

Giltiga värden:

- Bestå. Visar fel meddelandet och fortsätter att köra kommandot. "Fortsätt" är standardvärdet.

- Ignorera. Ignorerar fel meddelandet och fortsätter att köra kommandot.
  Till skillnad från SilentlyContinue lägger ignorera inte till fel meddelandet till den automatiska variabeln $Error. Ignorera-värdet introduceras i Windows PowerShell 3,0.

- Inquire. Visar fel meddelandet och du uppmanas att bekräfta innan du fortsätter körningen. Det här värdet används sällan.

- Koppla. Pausar automatiskt ett arbets flödes jobb för att tillåta ytterligare undersökning. Efter undersökningen kan arbets flödet återupptas.

- SilentlyContinue. Ignorerar fel meddelandet och fortsätter att köra kommandot.

- Stop (Stoppa). Visar fel meddelandet och slutar att köra kommandot.

#### <a name="input-object"></a>Inleveranstransport \<Object[]\>

Skickar en samling objekt till en aktivitet. Detta är ett alternativ till att skicka objekt till aktiviteten en i taget.

#### <a name="mergeerrortooutput-boolean"></a>MergeErrorToOutput \<Boolean\>

Värdet `$True` lägger till fel i utdataströmmen. Värdet `$False` har inte påverkats. Använd den här parametern med Parallel och `ForEach -Parallel` keywords för att samla in fel och utdata från flera parallella kommandon i en enda samling.

#### <a name="psactionretrycount-int32"></a>PSActionRetryCount \<Int32\>

Försök upprepade gånger att köra aktiviteten om det första försöket Miss lyckas. Standardvärdet 0, försöker inte igen.

#### <a name="psactionretryintervalsec-int32"></a>PSActionRetryIntervalSec \<Int32\>

Anger intervallet mellan åtgärds försök i sekunder. Standardvärdet, 0, gör om åtgärden omedelbart. Den här parametern är endast giltig om parametern PSActionRetryCount också används i kommandot.

#### <a name="psactionrunningtimeoutsec-int32"></a>PSActionRunningTimeoutSec \<Int32\>

Anger hur länge aktiviteten kan köras på varje måldator. Om aktiviteten inte slutförs innan tids gränsen löper ut genererar Windows PowerShell-arbetsflöde ett avslutande fel och stoppar bearbetningen av arbets flödet på den berörda mål datorn.

#### <a name="psallowredirection-boolean"></a>PSAllowRedirection \<Boolean\>

Värdet $True tillåter omdirigering av anslutningen till mål datorerna.
Värdet $False har ingen påverkan. Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.

När du använder PSConnectionURI-parametern kan fjärrdestinationen returnera en instruktion för att omdirigera till en annan URI. Som standard omdirigerar Windows PowerShell inte anslutningar, men du kan använda parametern PSAllowRedirection med värdet $True för att tillåta omdirigering av anslutningen till mål datorn.

Du kan också begränsa antalet gånger som anslutningen ska omdirigeras genom att ange egenskapen MaximumConnectionRedirectionCount för `$PSSessionOption` variabeln Preference, eller egenskapen MaximumConnectionRedirectionCount för värdet för parametern SSessionOption för cmdletar som skapar en session. Standardvärdet är 5.

#### <a name="psapplicationname-string"></a>PSApplicationName \<String\>

Anger program namns segmentet för den anslutnings-URI som används för att ansluta till mål datorerna. Använd den här parametern för att ange program namnet när du inte använder parametern ConnectionURI i kommandot. Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.

Standardvärdet är värdet för Preference- `$PSSessionApplicationName` variabeln på mål datorn. Om den här preferens variabeln inte definieras är standardvärdet WSMAN. Det här värdet är lämpligt för de flesta användnings områden. Mer information finns i [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

WinRM-tjänsten använder program namnet för att välja en lyssnare som ska betjäna anslutningsbegäran. Värdet för den här parametern ska matcha värdet på egenskapen URLPrefix för en lyssnare på fjärrdatorn.

#### <a name="psauthentication-authenticationmechanism"></a>PSAuthentication \<AuthenticationMechanism\>

Anger den mekanism som används för att autentisera användarens autentiseringsuppgifter vid anslutning till mål datorerna. Giltiga värden är standard, Basic, CredSSP, Digest, Kerberos, Negotiate och NegotiateWithImplicitCredential. Standardvärdet är default. Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.

Information om värdena för den här parametern finns i beskrivningen av uppräkningen **system. Management. Automation. körnings utrymmen. AuthenticationMechanism** i MSDN.

> [!WARNING]
> Autentisering av Credential Security Service Provider (CredSSP), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs. Den här mekanismen ökar säkerhets risken för Fjärråtgärden. Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.

#### <a name="pscertificatethumbprint-string"></a>PSCertificateThumbprint \<String\>

Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden. Ange certifikatets tumavtryck. Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.

Certifikat används i klient certifikat-baserad autentisering. De kan bara mappas till lokala användar konton. de fungerar inte med domän konton.

För att hämta ett certifikat använder du cmdletarna [Get-item](xref:Microsoft.PowerShell.Management.Get-Item) eller [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) i Windows PowerShell-certifikatet: enhet.

#### <a name="pscomputername-string"></a>PSComputerName \<String[]\>

Anger de mål datorer som aktiviteten körs på. Standard är den lokala datorn. Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.

Ange NETBIOS-namn, IP-adress eller fullständigt kvalificerat domän namn för en eller flera datorer i en kommaavgränsad lista. Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.).

Om du vill inkludera den lokala datorn i värdet för parametern PSComputerName, öppnar du Windows PowerShell med alternativet "kör som administratör".

Om den här parametern utelämnas från kommandot, eller om värdet är $null eller en tom sträng, är arbets flödets mål den lokala datorn och Windows PowerShell-fjärrkommunikation används inte för att köra kommandot.

Om du vill använda en IP-adress i värdet för parametern ComputerName måste kommandot innehålla parametern PSCredential. Dessutom måste datorn konfigureras för HTTPS-transport eller fjärrdatorns IP-adress måste ingå i listan WinRM TrustedHosts på den lokala datorn. Instruktioner för att lägga till ett dator namn i listan TrustedHosts finns i avsnittet om hur du lägger till en dator i listan över betrodda värdar i [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).

#### <a name="psconfigurationname-string"></a>PSConfigurationName \<String\>

Anger de sessionsinställningar som används för att skapa sessioner på mål datorerna. Ange namnet på en session konfiguration på mål datorerna (inte på den dator som kör arbets flödet. Standardvärdet är Microsoft. PowerShell. Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.

#### <a name="psconnectionretrycount-uint"></a>PSConnectionRetryCount \<UInt\>

Anger det maximala antalet försök att ansluta till varje måldator om det första anslutnings försöket Miss lyckas. Ange ett tal mellan 1 och 4 294 967 295 (UInt. MaxValue). Standardvärdet noll (0) representerar inga nya försök.
Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.

#### <a name="psconnectionretryintervalsec-uint"></a>PSConnectionRetryIntervalSec \<UInt\>

Anger fördröjningen mellan anslutnings försök på några sekunder. Standardvärdet är noll (0). Den här parametern är endast giltig när värdet för PSConnectionRetryCount är minst 1. Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.

#### <a name="psconnectionuri-systemuri"></a>PSConnectionURI \<System.Uri\>

Anger en Uniform Resource Identifier (URI) som definierar anslutnings slut punkten för aktiviteten på mål datorn. URI: n måste vara fullständigt kvalificerad. Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.

Formatet för den här strängen är följande:

```
<Transport>://<ComputerName>:<Port>/<ApplicationName>
```

Standardvärdet är `http://localhost:5985/WSMAN`.

Om du inte anger en PSConnectionURI kan du använda parametrarna PSUseSSL, PSComputerName, PSPort och PSApplicationName för att ange PSConnectionURI-värden.

Giltiga värden för URI: n i transport segmentet är HTTP och HTTPS. Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med standard portar: 80 för HTTP och 443 för HTTPS. Om du vill använda standard portarna för Windows PowerShell-fjärrkommunikation, anger du Port 5985 för HTTP eller 5986 för HTTPS.

#### <a name="pscredential-pscredential"></a>PSCredential \<PSCredential\>

Anger ett användar konto som har behörighet att köra aktiviteten på mål datorn. Standard är den aktuella användaren. Den här parametern är endast giltig om parametern PSComputerName ingår i kommandot. Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.

Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange en variabel som innehåller ett PSCredential-objekt, till exempel ett som Get-Credential cmdlet returnerar. Om du bara anger ett användar namn uppmanas du att ange ett lösen ord.

#### <a name="psdebug-psdatacollectiondebugrecord"></a>PSDebug \<PSDataCollection[DebugRecord]\>

Lägger till fel söknings meddelanden från aktiviteten till den angivna fel söknings post samlingen i stället för att skriva fel söknings meddelandena till konsolen eller till värdet för egenskapen fel sökning för arbets flödes jobbet. Du kan lägga till fel söknings meddelanden från flera aktiviteter i samma samlings objekt för fel söknings poster.

Använd New-Object cmdlet för att skapa ett PSDataCollection-objekt med en typ av DebugRecord och spara objektet i en variabel, om du vill använda den här gemensamma aktivitets parametern. Använd sedan variabeln som värde för parametern PSDebug för en eller flera aktiviteter, som du ser i följande exempel.

```powershell
Workflow Test-Workflow
{
    $debugCollection = New-Object -Type `
    System.Management.Automation.PSDataCollection[System.Management.Automation.DebugRecord]
    InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    if ($debugCollection -like "Missing") { ...}
}
```

#### <a name="psdisableserialization-boolean"></a>PSDisableSerialization \<Boolean\>

Dirigerar aktiviteten så att den returnerar "Live"-objekt (inte serialiserade) till arbets flödet.
De resulterande objekten har metoder, samt egenskaper, men de kan inte sparas när en kontroll punkt tas.

#### <a name="psdisableserializationpreference-boolean"></a>PSDisableSerializationPreference \<Boolean\>

Tillämpar motsvarande PSDisableSerialization-parameter i hela arbets flödet, inte bara på aktiviteten. Det rekommenderas vanligt vis inte att lägga till den här parametern, eftersom ett arbets flöde som inte serialiserar sina objekt inte kan återupptas eller sparas.

Giltiga värden:

- Objekt Om detta utelämnas och du inte har lagt till parametern PSDisableSerialization i en aktivitet, serialiseras objekten.

- `$True`. Dirigerar alla aktiviteter i ett arbets flöde för att returnera "Live"-objekt (inte serialiserade). De resulterande objekten har metoder, samt egenskaper, men de kan inte sparas när en kontroll punkt tas.
- `$False`. Arbets flödes objekt serialiseras.

#### <a name="pserror-psdatacollectionerrorrecord"></a>PSError \<PSDataCollection[ErrorRecord]\>

Lägger till fel meddelanden från aktiviteten till den angivna fel post samlingen, i stället för att skriva fel meddelandena till konsolen eller till värdet för egenskapen Error för arbets flödes jobbet. Du kan lägga till fel meddelanden från flera aktiviteter i samma fel post samlings objekt.

Använd `New-Object` cmdleten för att skapa ett PSDataCollection-objekt med en typ av ErrorRecord och spara objektet i en variabel om du vill använda den här gemensamma parametern för aktiviteten. Använd sedan variabeln som värde för parametern PSError för en eller flera aktiviteter, som du ser i följande exempel.

```powershell
Workflow Test-Workflow
{
   $typeName = "System.Management.Automation.PSDataCollection"
   $typeName += '[System.Management.Automation.ErrorRecord]'
   $ec = New-Object $typeName
   InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSError $ec
   InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSError $ec
   if ($ec.Count -gt 2)
   {
      # Do Some Work.
   }
}
```

#### <a name="pspersist-boolean"></a>PSPersist \<Boolean\>

Tar en kontroll punkt efter aktiviteten. Den här kontroll punkten är utöver de kontroll punkter som anges i arbets flödet. Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.

En "kontroll punkt" eller "beständighet" är en ögonblicks bild av arbets flödets tillstånd och data som samlas in medan arbets flödet körs och sparas i ett beständigt arkiv på disk. Windows PowerShell-arbetsflöde använder sparade data för att återuppta ett pausat eller avbrutet arbets flöde från den senaste beständiga punkten, i stället för att starta om arbets flödet.

Giltiga värden:

- Objekt Om du utelämnar den här parametern läggs inga kontroll punkter till. Kontroll punkter utförs baserat på inställningarna för arbets flödet.

- `$True`. Tar en kontroll punkt när aktiviteten har slutförts.
  Den här kontroll punkten är utöver de kontroll punkter som anges i arbets flödet.

- `$False`. Inga kontroll punkter har lagts till. Kontroll punkter utförs endast när de anges i arbets flödet.

#### <a name="psport-int32"></a>PSPort \<Int32\>

Anger nätverks porten på mål datorerna. Standard portarna är 5985 (WinRM-porten för HTTP) och 5986 (WinRM-porten för HTTPS). Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.

Använd inte parametern PSPort om du inte behöver det. Porten som anges i kommandot gäller för alla datorer eller sessioner där kommandot körs. En alternativ port inställning kan hindra kommandot från att köras på alla datorer. Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten.

#### <a name="psprogress-psdatacollectionprogressrecord"></a>PSProgress \<PSDataCollection[ProgressRecord]\>

Lägger till förlopps meddelanden från aktiviteten till den angivna förlopps post samlingen i stället för att skriva förlopps meddelanden till konsolen eller till värdet för egenskapen Progress för arbets flödes jobbet. Du kan lägga till förlopps meddelanden från flera aktiviteter till samma förlopps post samlings objekt.

#### <a name="psprogressmessage-string"></a>PSProgressMessage \<String\>

Anger en egen beskrivning av aktiviteten. PSProgressMessage-värdet visas i förlopps indikatorn medan arbets flödet körs. När DisplayName också ingår i kommandot visas förlopps indikatorns innehåll i \<DisplayName\> : \<PSProgressMessage\> format.

Den här parametern är särskilt användbar för att identifiera aktiviteter i en förgrunds-parallell skript block. Utan det här meddelandet identifieras aktiviteter i alla parallella grenar med samma namn.

#### <a name="psremotingbehavior-remotingbehavior"></a>PSRemotingBehavior \<RemotingBehavior\>

Anger hur fjärr kommunikation hanteras när aktiviteten körs på mål datorerna.
PowerShell är standardinställningen.

Giltiga värden är:

- Ingen: aktiviteten körs inte på fjärrdatorer.

- PowerShell: Windows PowerShell-fjärrkommunikation används för att köra aktiviteten på mål datorerna.

- Anpassad: aktiviteten stöder sin egen typ av fjärr kommunikation. Det här värdet är giltigt när den cmdlet som implementeras som en aktivitet anger värdet för attributet RemotingCapability till SupportedByCommand och kommandot innehåller parametern ComputerName.

#### <a name="psrequiredmodules-string"></a>PSRequiredModules \<String[]\>

Importerar de angivna modulerna innan kommandot körs. Ange namnen på modulerna. Modulerna måste vara installerade på mål datorn.

Moduler som är installerade i en sökväg som anges i miljövariabeln PSModulePath importeras automatiskt vid första användningen av ett kommando i modulen.
Använd den här parametern för att importera moduler som inte finns på en PSModulePath plats.

Eftersom varje aktivitet i ett arbets flöde körs i sin egen session importerar ett Import-Module-kommando bara en modul till den session där den körs. Modulen importerar inte modulen till sessioner där andra aktiviteter körs.

#### <a name="pssessionoption-pssessionoption"></a>PSSessionOption \<PSSessionOption\>

Anger avancerade alternativ för sessionerna till mål datorerna. Ange ett PSSessionOption-objekt, till exempel ett som du skapar med hjälp av New-PSSessionOption cmdlet. Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.

Standardvärdena för session alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts. Annars använder sessionen de värden som anges i konfigurationen för sessionen.

En beskrivning av sessionsinformation, inklusive standardvärdena, finns i hjälp avsnittet för New-PSSessionOption cmdlet [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).

Mer information om variabeln $PSSessionOption finns [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

#### <a name="psusessl-boolean"></a>PSUseSSL \<Boolean\>

Värdet $True använder protokollet Secure Sockets Layer (SSL) för att upprätta en anslutning till mål datorn. Som standard används inte SSL. Värdet $False har ingen påverkan. Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.

WS-Management krypterar allt Windows PowerShell-innehåll som överförs via nätverket. UseSSL är ett ytterligare skydd som skickar data via HTTPS i stället för HTTP. Om du använder den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.

#### <a name="psverbose-psdatacollectionverboserecord"></a>PSVerbose \<PSDataCollection[VerboseRecord]\>

Lägger till utförliga meddelanden från aktiviteten till den angivna utförliga post samlingen, i stället för att skriva utförliga meddelanden till konsolen eller till värdet för egenskapen utförligt för arbets flödes jobbet. Du kan lägga till utförliga meddelanden från flera aktiviteter till samma utförlig post samlings objekt.

#### <a name="pswarning-psdatacollectionwarningrecord"></a>PSWarning \<PSDataCollection[WarningRecord]\>

Lägger till varnings meddelanden från aktiviteten till den angivna varnings post samlingen i stället för att skriva varnings meddelandena till konsolen eller till värdet för egenskapen varning för arbets flödes jobbet. Du kan lägga till varnings meddelanden från flera aktiviteter i samma varnings post samlings objekt.

#### <a name="result"></a>Resultat

Den här parametern är endast giltig i XAML-arbetsflöden.

#### <a name="usedefaultinput-boolean"></a>UseDefaultInput \<Boolean\>

Accepterar alla arbets flödes indatatyper som ininformation till aktiviteten efter värde.

Till exempel använder Get-Process-aktiviteten i följande exempel arbets flöde den gemensamma parametern UseDefaultInput-aktivitet för att hämta ininformation som skickas till arbets flödet. När du kör arbets flödet med indatamängd används indatamängden av aktiviteten.

```powershell
workflow Test-Workflow
{
    Get-Service -UseDefaultInput $True
}

PS C:> Test-Workflow -InputObject WinRm
```

```output
Status   Name        DisplayName                            PSComputerName
------   ----        -----------                            --------------
Running  winrm       Windows Remote Management (WS-Manag... localhost
```

#### <a name="verbose-switchparameter"></a>Utförlig \<SwitchParameter\>

Visar detaljerad information om den åtgärd som utförs av kommandot.
Den här informationen liknar informationen i en spårning eller i en transaktions logg.
Den utförliga parametern åsidosätter värdet för variabeln $VerbosePreference för det aktuella kommandot. Den här parametern fungerar bara när kommandot genererar ett utförligt meddelande. Den här parametern är också en gemensam Windows PowerShell-parameter.

#### <a name="warningaction-actionpreference"></a>WarningAction \<ActionPreference\>

Anger hur aktiviteten svarar på en varning. "Fortsätt" är standardvärdet. Parametern WarningAction åsidosätter värdet för variabeln $WarningPreference för det aktuella kommandot. Den här parametern fungerar bara när kommandot genererar ett varnings meddelande. Den här parametern är också en gemensam Windows PowerShell-parameter.

Giltiga värden:

- SilentlyContinue. Undertrycker varnings meddelandet och fortsätter att köra kommandot.

- Bestå. Visar varnings meddelandet och fortsätter att köra kommandot.
  "Fortsätt" är standardvärdet.

- Inquire. Visar varnings meddelandet och du uppmanas att bekräfta innan du fortsätter körningen. Det här värdet används sällan.

- Stop (Stoppa). Visar varnings meddelandet och stoppar körningen av kommandot.

> [!NOTE]
> Parametern WarningAction åsidosätter inte värdet för inställnings variabeln $WarningAction när parametern används i ett kommando för att köra ett skript eller en funktion.

### <a name="examples"></a>EXEMPEL

De gemensamma aktivitets parametrarna är mycket användbara. Du kan till exempel använda parametern PSComputerName för att köra vissa aktiviteter bara på en delmängd av mål datorerna.

Eller så kan du använda parametrarna PSConnectionRetryCount och PSConnectionRetryIntervalSec för att justera värdena för återförsök för vissa aktiviteter.

I följande exempel visas hur du använder de gemensamma parametrarna för PSComputerName-aktivitet för att köra en Get-EventLog-aktivitet enbart på datorer som är en viss domän.

```powershell
Workflow Test-Workflow
{
    $UserDomain = Get-Content -Path '.\UserComputers.txt'
    $Log = (Get-EventLog -LogName "Windows PowerShell" `
      -PSComputerName $UserDomain)

    if ($Log)
    {
        # Do Work Here.
    }
}
```

<!--
# KEYWORDS
[about_Activity_Common_Parameters](about_Activity_Common_Parameters.md)
[about_Activity_Parameters](about_Activity_Parameters.md)
[about_ActivityParameters]()about_ActivityParameters.md) -->

## <a name="see-also"></a>SE ÄVEN

[about_Workflows](about_workflows.md) 
 [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)
