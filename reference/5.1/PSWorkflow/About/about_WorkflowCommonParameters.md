---
description: I det här avsnittet beskrivs de parametrar som är giltiga för alla Windows PowerShell-arbetsflöden-kommandon. Eftersom Windows PowerShell-motorn lägger till dem i arbets flöden kan du använda dessa parametrar på alla arbets flöden och de aktive ras automatiskt på de arbets flöden som du skapar.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflowcommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WorkflowCommonParameters
ms.openlocfilehash: c371666d4f58386848e7ef715b7c804dc1e8f28e
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387795"
---
# <a name="about-workflowcommonparameters"></a>Om WorkflowCommonParameters

## <a name="short-description"></a>KORT BESKRIVNING

I det här avsnittet beskrivs de parametrar som är giltiga för alla Windows PowerShell-arbetsflöden-kommandon. Eftersom Windows PowerShell-motorn lägger till dem i arbets flöden kan du använda dessa parametrar på alla arbets flöden och de aktive ras automatiskt på de arbets flöden som du skapar.

## <a name="long-description"></a>LÅNG BESKRIVNING

Gemensamma parametrar för Windows PowerShell-arbetsflöde är en uppsättning cmdlet-parametrar som du kan använda med alla Windows PowerShell-arbetsflöden och-aktiviteter. De läggs till av arbets flödes motorn för Windows PowerShell, inte av arbets flödets författare, och de är automatiskt tillgängliga i arbets flöden och aktiviteter. Arbets flöden som är kapslade tre nivåer har dock inte stöd för några gemensamma parametrar, inklusive vanliga arbets flödes parametrar.

Alla arbets flödes parametrar är valfria och namngivna (inte positions). De tar inga inmatade från pipelinen.

De flesta av de gemensamma parametrarna för arbets flödet har ett PS-prefix, till exempel `PSComputerName` och `PSCredential` . De PS-fasta parametrarna konfigurerar anslutningen och körnings miljön för mål datorerna, även kallade "fjärrnoder".

Många av de gemensamma parametrarna för arbets flödet, till exempel `PSAllowRedirection` och `AsJob` , har namn som liknar parametrar som används i Windows PowerShell-fjärrkommunikationer och bakgrunds jobb. De här parametrarna fungerar på samma sätt som de parametrar som liknar varandra för fjärr kommunikation och jobb, så att du kan använda den kunskap som du utvecklade i fjärr kommunikation och jobb för att hantera arbets flöden.

Arbets flöden introduceras i Windows PowerShell 3,0.

### <a name="parameter-descriptions"></a>PARAMETER BESKRIVNINGAR

I det här avsnittet beskrivs de gemensamma parametrarna för arbets flödet.

#### <a name="-asjob-switchparameter"></a>– AsJob \<SwitchParameter\>

Kör arbets flödet som ett arbets flödes jobb. Arbets flödes kommandot returnerar omedelbart ett objekt som representerar ett överordnat jobb. Det överordnade jobbet innehåller de underordnade jobb som körs på var och en av mål datorerna. Använd jobb-cmdletar för att hantera jobbet. Använd [Receive-Job](xref:Microsoft.PowerShell.Core.Receive-Job)för att hämta jobb resultatet.

#### <a name="-jobname-string"></a>– JobName \<String\>

Anger ett eget namn för arbets flödes jobbet. Som standard kallas jobb "Job \<n\> ", där \<n\> är ett ordnings tal.

Om du använder parametern JobName i ett arbets flödes kommando körs arbets flödet som ett jobb och arbets flödes kommandot returnerar ett jobb objekt, även om du inte inkluderar `AsJob` parametern i kommandot.

Mer information om bakgrunds jobb i Windows PowerShell finns [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).

#### <a name="-psallowredirection-switchparameter"></a>-PSAllowRedirection \<SwitchParameter\>

Tillåter omdirigering av anslutningen till mål datorerna.

När du använder `PSConnectionURI` -parametern kan fjärrdestinationen returnera en instruktion för att omdirigera till en annan URI. Som standard omdirigerar Windows PowerShell inte anslutningar, men du kan använda `PSAllowRedirection` parametern för att tillåta omdirigering av anslutningen till mål datorn.

Du kan också begränsa antalet gånger som anslutningen ska omdirigeras genom att ange `MaximumConnectionRedirectionCount` egenskapen för `$PSSessionOption` variabeln Preference, eller `MaximumConnectionRedirectionCount` egenskapen för värdet för `PSSessionOption parameter` . Standardvärdet är 5. Mer information finns i Beskrivning av `PSSessionOption` parametern och [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).

#### <a name="-psapplicationname-string"></a>-PSApplicationName \<String\>

Anger program namns segmentet för den anslutnings-URI som används för att ansluta till mål datorerna. Använd den här parametern för att ange program namnet när du inte använder `ConnectionURI` parametern i kommandot.

Standardvärdet är värdet för Preference- `$PSSessionApplicationName` variabeln på den lokala datorn. Om den här preferens variabeln inte definieras är standardvärdet WSMAN. Det här värdet är lämpligt för de flesta användnings områden. Mer information finns i [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

WinRM-tjänsten använder program namnet för att välja en lyssnare som ska betjäna anslutningsbegäran. Värdet för den här parametern ska matcha värdet på `URLPrefix` egenskapen för en lyssnare på fjärrdatorn.

#### <a name="-psauthentication-authenticationmechanism"></a>-PSAuthentication \<AuthenticationMechanism\>

Anger den mekanism som används för att autentisera användarens autentiseringsuppgifter vid anslutning till mål datorerna.

Giltiga värden är:

- **Standard**
- **Basic**
- **CredSSP**
- **Digest**
- **Kerberos**
- **Fram**
- **NegotiateWithImplicitCredential**

Standardvärdet är **default**.

Information om värdena för den här parametern finns i beskrivningen av `System.Management.Automation.Runspaces.AuthenticationMechanism` uppräkningen i POWERSHELL SDK.

> [!WARNING]
> Autentisering av Credential Security Service Provider (CredSSP), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs. Den här mekanismen ökar säkerhets risken för Fjärråtgärden. Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.

#### <a name="-psauthenticationlevel-authenticationlevel"></a>-PSAuthenticationLevel \<AuthenticationLevel\>

Anger autentiseringsnivån för anslutningarna till mål datorerna.
Standardvärdet är **default**.

Giltiga värden är:

|Name |Beskrivning |
|---------|---------|
|**Oförändrade** | Autentiseringsnivån är samma som föregående kommando. |
|**Standard** | Windows-autentisering. |
|**Inga** | Ingen COM-autentisering.   |
|**Anslut** | COM-autentisering på anslutnings nivå.|
|**Anropa** | COM-autentisering på anrops nivå.   |
|**Åtkomstaccepterande** | COM-autentisering på paket nivå.|
|**PacketIntegrity** | COM-autentisering på paket integritets nivå.  |
|**PacketPrivacy** | COM-autentisering på paketets integritets nivå. |

#### <a name="-pscertificatethumbprint-string"></a>-PSCertificateThumbprint \<String\>

Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden. Ange certifikatets tumavtryck.

Certifikat används i klient certifikat-baserad autentisering. De kan bara mappas till lokala användar konton. de fungerar inte med domän konton.

Hämta ett certifikat med hjälp av [Get-item](xref:Microsoft.PowerShell.Management.Get-Item) eller [Get-ChildItem] (.. /.. /Microsoft.PowerShell.Management/Get-Childitem.md)-cmdletar i Windows PowerShell-certifikatet: enhet.

#### <a name="-pscomputername-string"></a>– PSComputerName \<String[]\>

Anger listan över datorer som är mål-noderna i arbets flödet.
Kommandon eller aktiviteter i ett arbets flöde körs på de datorer som anges med hjälp av den här parametern. Standard är den lokala datorn.

Ange NETBIOS-namn, IP-adress eller fullständigt kvalificerat domän namn för en eller flera datorer i en kommaavgränsad lista. Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.).

Om du vill inkludera den lokala datorn i värdet för `PSComputerName` parametern öppnar du Windows PowerShell med alternativet "kör som administratör".

Om den här parametern utelämnas från kommandot, eller om värdet är `$null` eller en tom sträng, är arbets flödets mål den lokala datorn och Windows PowerShell-fjärrkommunikation används inte för att köra kommandot.

Om du vill använda en IP-adress i värdet för `ComputerName` parametern måste kommandot innehålla `PSCredential` parametern. Dessutom måste datorn konfigureras för HTTPS-transport eller fjärrdatorns IP-adress måste ingå i listan WinRM TrustedHosts på den lokala datorn. Instruktioner för att lägga till ett dator namn i listan TrustedHosts finns i avsnittet om *hur du lägger till en dator i listan över betrodda värdar* i [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).

#### <a name="-psconfigurationname-string"></a>-PSConfigurationName \<String\>

Anger de sessionsinställningar som används för att konfigurera sessioner på mål datorerna. Ange en sessionsinformation på mål datorerna (inte arbets flödes serverns dator). Standardvärdet är `Microsoft.PowerShell.Workflow`.

#### <a name="-psconnectionretrycount-uint"></a>– PSConnectionRetryCount \<UInt\>

Anger det maximala antalet försök att ansluta till varje måldator om det första anslutnings försöket Miss lyckas. Ange ett tal mellan 1 och 4 294 967 295 (UInt. MaxValue). Standardvärdet noll (0) representerar inga nya försök.

#### <a name="-psconnectionretryintervalsec-uint"></a>-PSConnectionRetryIntervalSec \<UInt\>

Anger fördröjningen mellan anslutnings försök på några sekunder. Standardvärdet är noll (0). Den här parametern är endast giltig när värdet för PSConnectionRetryCount är minst 1.

#### <a name="-psconnectionuri-systemuri"></a>-PSConnectionURI \<System.Uri\>

Anger en Uniform Resource Identifier (URI) som definierar anslutnings slut punkten för arbets flödet på mål datorn. URI: n måste vara fullständigt kvalificerad.

Formatet för den här strängen är följande:

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

Standardvärdet är `http://localhost:5985/WSMAN`.

Om du inte anger någon `PSConnectionURI` kan du använda `PSUseSSL` parametrarna,, `PSComputerName` `PSPort` och `PSApplicationName` för att ange `PSConnectionURI` värdena.

Giltiga värden för URI: n i transport segmentet är **http** och **https**.
Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med standard portar: 80 för HTTP och 443 för HTTPS. Om du vill använda standard portarna för Windows PowerShell-fjärrkommunikation, anger du Port 5985 för HTTP eller 5986 för HTTPS.

#### <a name="-pscredential-pscredential"></a>– PSCredential \<PSCredential\>

Anger ett användar konto som har behörighet att köra ett arbets flöde på mål datorn. Standard är den aktuella användaren. Den här parametern är endast giltig om parametern PSComputerName ingår i kommandot.

Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange en variabel som innehåller ett `PSCredential` objekt, till exempel en som `Get-Credential` cmdleten returnerar. Om du bara anger ett användar namn uppmanas du att ange ett lösen ord.

#### <a name="-pselapsedtimeoutsec-uint32"></a>-PSElapsedTimeoutSec \<UInt32\>

Anger hur länge arbets flödet och alla relaterade resurser finns kvar i systemet. När tids gränsen går ut tas arbets flödet bort, även om det fortfarande bearbetas. Ange ett värde mellan 10 och 4 294 967 295. Standardvärdet, 0 (noll), innebär att det inte finns något tids gräns värde.

#### <a name="-psparametercollection-hashtable"></a>-PSParameterCollection \<Hashtable[]\>

Anger olika gemensamma parameter värden för arbets flödet för olika mål datorer.

Ange en kommaavgränsad lista med hash-tabeller med en hash-tabell för varje måldator. I varje hash-tabell är den första nyckeln `PSComputerName` och dess värde namnet på mål datorn. Jokertecken tillåts i dator namnet. För återstående nycklar i hash-tabellen är nyckeln parameter namnet och värdet är parametervärdet.

Till exempel:

```powershell
-PSParameterCollection @{PSComputerName="*"; PSElapsedTimeoutSec=20},
@{PSComputerName="Server02"},
@{PSComputerName="Server03"},
@{PSComputerName="Server01"; PSElapsedTimeoutSec=10}
```

I exemplet ovan kommer alla anslutningar att ha en standard-PSElapsedTimeoutSec på 20 sekunder, förutom för Server01 som åsidosätter standardvärdet genom att ange en egen tids gräns på 10 sekunder.

#### <a name="-pspersist-boolean"></a>– PSPersist \<Boolean\>

Lägger till kontroll punkter i arbets flödet, förutom de kontroll punkter som anges i arbets flödet.

Den här parametern kan inte utelämna kontroll punkter i ett arbets flöde, till exempel de som anges med hjälp av den `PSPersist` gemensamma aktivitets parametern, `Checkpoint-Workflow` aktiviteten eller `$PSPersistPreference` variabeln.

En "kontroll punkt" eller "beständighet" är en ögonblicks bild av arbets flödets tillstånd och data som samlas in medan arbets flödet körs och sparas i ett beständigt arkiv på disk eller i en SQL-databas. Windows PowerShell-arbetsflöde använder sparade data för att återuppta ett pausat eller avbrutet arbets flöde från den senaste beständiga punkten, i stället för att starta om arbets flödet.

Giltiga värden:

- ( *Standard* ) Om du utelämnar den här parametern läggs en kontroll punkt till i början och i slutet av arbets flödet, förutom de kontroll punkter som anges i arbets flödet.

- `$True`. Lägger till en kontroll punkt i början och i slutet av arbets flödet och en kontroll punkt efter varje aktivitet, utöver de kontroll punkter som anges i arbets flödet.

- `$False`. Inga kontroll punkter har lagts till. Kontroll punkter utförs endast när de anges i arbets flödet.

#### <a name="-psport-int32"></a>-PSPort \<Int32\>

Anger nätverks porten på mål datorerna. Standard portarna är 5985 (WinRM-porten för HTTP) och 5986 (WinRM-porten för HTTPS).

Använd inte parametern PSPort om du inte behöver det. Porten som anges i kommandot gäller för alla datorer eller sessioner där kommandot körs. En alternativ port inställning kan hindra kommandot från att köras på alla datorer. Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten.

#### <a name="-psprivatemetadata-hashtable"></a>-PSPrivateMetadata \<Hashtable\>

Tillhandahåller anpassad information till arbets flödes jobb. Ange en hash-tabell. Nycklar och värden anpassas för varje arbets flöde. Information om de privata metadata för ett arbets flöde finns i hjälp avsnittet för arbets flödet.

Den här parametern bearbetas inte av Windows PowerShell Workflow Engine.
I stället skickar motorn hash-tabellen direkt till arbets flödet.

#### <a name="-psrunningtimeoutsec-uint32"></a>-PSRunningTimeoutSec \<UInt32\>

Anger körnings tiden för arbets flödet i sekunder, med undantag för hur länge arbets flödet har pausats. Om körningen av arbets flödet inte är slutförd när tiden går ut stoppar Windows PowerShell Workflow Engine körningen av arbets flödet.

#### <a name="-pssessionoption-pssessionoption"></a>-PSSessionOption \<PSSessionOption\>

Anger avancerade alternativ för sessionerna till mål datorerna. Ange ett `PSSessionOption` objekt, till exempel ett som du skapar med hjälp av `New-PSSessionOption` cmdleten.

Standardvärdena för session alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts. Annars använder sessionen de värden som anges i konfigurationen för sessionen.

En beskrivning av sessions alternativen, inklusive standardvärdena, finns i hjälp avsnittet för `New-PSSessionOption` cmdleten (.. /.. /Microsoft.PowerShell.Core/New-PSSessionOption.md). Information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

#### <a name="-psusessl-switchparameter"></a>-PSUseSSL \<SwitchParameter\>

Använder Secure Sockets Layer-protokollet (SSL) för att upprätta en anslutning till mål datorn. Som standard används inte SSL.

WS-Management krypterar allt Windows PowerShell-innehåll som överförs via nätverket. UseSSL är ett ytterligare skydd som skickar data via HTTPS i stället för HTTP. Om du använder den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.

## <a name="see-also"></a>SE ÄVEN

- [about_ActivityCommonParameters](about_ActivityCommonParameters.md)
- [about_Workflows](about_Workflows.md)
- [Invoke-arbetsflöde](xref:PSWorkflowUtility.Invoke-AsWorkflow)
- [New-PSWorkflowExecutionOption](xref:PSWorkflow.New-PSWorkflowExecutionOption)
- [New-PSWorkflowSession](xref:PSWorkflow.New-PSWorkflowSession)
