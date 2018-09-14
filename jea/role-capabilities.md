---
ms.date: 06/12/2017
keywords: jea, powershell, säkerhet
title: JEA rollfunktioner
ms.openlocfilehash: bd0a995adc60e50049ff99d6b23e7c2aeb745a18
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522954"
---
# <a name="jea-role-capabilities"></a>JEA rollfunktioner

> Gäller för: Windows PowerShell 5.0

När du skapar en JEA-slutpunkt, behöver du definiera en eller flera ”rollfunktioner” som beskriver *vad* någon kan göra i en JEA-session.
En roll-funktionen är en PowerShell-datafil med tillägget .psrc som visar en lista över alla cmdlet: ar, funktioner, leverantörer och externa program som ska göras tillgängliga för användare att ansluta.

Det här avsnittet beskriver hur du skapar en fil PowerShell roll funktionen för dina JEA-användare.

## <a name="determine-which-commands-to-allow"></a>Avgöra vilka kommandon för att tillåta

Det första steget när du skapar en fil för roll-funktionen är att tänka på vad de användare som tilldelas rollen som behöver åtkomst till.
Den här krav Insamlingsprocessen kan ta en stund, men det är en viktig process.
Ge användare åtkomst till tillräckligt många cmdletar och funktioner kan hindra dem från att få sitt jobb.
Att tillåta åtkomst till för många cmdletar och funktioner kan leda till användare som gör mer än den du avsåg med sina implicit administratörsprivilegier minskad din säkerhet effekten av åtgärder.

Hur du går tillväga för den här processen beror på din organisation och mål, men följande tips kan hjälpa att kontrollera att du befinner dig på rätt väg.

1. **Identifiera** kommandon användare använder för att få sitt arbete. Detta kan omfatta överblick över IT-personal, kontrollerar automatiseringsskript eller analysera PowerShell-session betyg eller loggar.
2. **Uppdatera** användning av kommandoradsverktyg till PowerShell-motsvarighet, där det är möjligt, för bästa gransknings- och JEA anpassning upplevelse. Vara det går inte att begränsad till externa program som detaljerat som interna PowerShell-cmdletar och funktioner i JEA.
3. **Begränsa** omfånget för cmdletar om behövs för att endast tillåta att specifika parametrar eller parametervärden. Detta är särskilt viktigt om användare ska bara kunna hantera en del av ett system.
4. **Skapa** egna funktioner för att ersätta komplexa kommandon eller kommandon som är svåra att begränsa i JEA. En enkel funktion som omsluter ett kommando som komplexa eller gäller ytterligare validering av logik kan erbjuda ytterligare kontroll för enkelhetens skull administratörer och slutanvändare.
5. **Testa** begränsade listan över tillåtna kommandon med dina användare och/eller automation services och justera efter behov.

Det är viktigt att komma ihåg att kommandona i en JEA-session är ofta kör med administratör (eller på annat sätt utökad) privilegier.
Försiktig med tillgängliga kommandon är viktigt att se till att JEA-slutpunkt inte tillåter den anslutande användaren att utöka sina behörigheter.
Nedan följer några exempel på kommandon som du kan använda medvetet om tillåts i en obegränsad tillstånd.
Observera att detta är inte en fullständig förteckning och bör endast användas som utgångspunkt systemprinciper.

### <a name="examples-of-potentially-dangerous-commands"></a>Exempel på potentiellt skadliga kommandon

Risk | Exempel | Relaterade kommandon
-----|---------|-----------------
Bevilja den anslutande användaren administratörsbehörigheter för att kringgå JEA | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`
Köra godtycklig kod, till exempel skadlig kod, trojaner eller anpassade skript att kringgå skydd | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>Skapa en roll funktionen fil

Du kan skapa en ny fil med funktionen för rollen av PowerShell i [New PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Den resulterande roll funktion filen kan öppnas i en textredigerare och ändras för att tillåta de önskade kommandona för rollen.
I PowerShell-hjälpen innehåller flera exempel på hur du kan konfigurera filen.

### <a name="allowing-powershell-cmdlets-and-functions"></a>PowerShell-cmdletar och funktioner

Om du vill tillåta användare att köra PowerShell-cmdletar eller funktioner, lägger du till cmdlet eller funktionen namnet VisbibleCmdlets eller VisibleFunctions fält.
Om du är osäker på om ett kommando är en cmdlet eller funktion, kan du köra `Get-Command <name>` och kontrollera egenskapen ”CommandType” i utdata.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Ibland är omfånget för en specifik cmdlet eller funktion för breda för dina användares behov.
En DNS-administratör kan till exempel förmodligen bara behöver åtkomst till för att starta om DNS-tjänsten.
I en miljö med flera klientorganisationer där klienter beviljas åtkomst till själva hanteringsverktyg begränsas klienter till att hantera med sina egna resurser.
För dessa fall kan begränsa du vilka parametrar som exponeras från cmdlet eller funktion.

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

I mer avancerade scenarier kan du också behöva begränsa vilka värden som någon kan tillhandahålla till dessa parametrar.
Rollfunktioner kan du definiera en uppsättning tillåtna värden eller ett mönster för reguljärt uttryck som utvärderas för att avgöra om en viss inmatning är tillåten.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> Den [vanliga PowerShell-parametrar](https://technet.microsoft.com/library/hh847884.aspx) tillåts alltid, även om du begränsar tillgängliga parametrar.
> Du bör inte uttryckligen ange dem i fältet parametrar.

Tabellen nedan beskrivs de olika metoder som du kan anpassa en synlig cmdlet eller funktion.
Du kan blanda och matchar någon av de nedan i VisibleCmdlets fältet.

Exempel                                                                                      | Användningsfall
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` eller `@{ Name = 'My-Func' }`                                                       | Tillåter användaren att köra `My-Func` utan begränsningar på parametrarna.
`'MyModule\My-Func'`                                                                         | Tillåter användaren att köra `My-Func` från modulen `MyModule` utan begränsningar på parametrarna.
`'My-*'`                                                                                     | Gör att användaren kan köra alla cmdlet eller funktion med verbet `My`.
`'*-Func'`                                                                                   | Gör att användaren kan köra alla cmdlet eller funktion med substantivet `Func`.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | Tillåter användaren att köra `My-Func` med den `Param1` och/eller `Param2` parametrar. Vilket värde som kan anges till parametrar.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | Tillåter användaren att köra `My-Func` med den `Param1` parametern. Endast ”Value1” och ”Value2” kan anges för parametern.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | Tillåter användaren att köra `My-Func` med den `Param1` parametern. Ett värde som börjar med ”contoso” kan anges för parametern.


> [!WARNING]
> Metodtips för säkerhet rekommenderas inte att använda jokertecken när du definierar synliga cmdletar eller funktioner.
> I stället en lista med varje betrodd kommando för att kontrollera att inga andra kommandon som delar samma namngivningsschemat oavsiktligt har behörighet.

Du kan inte använda både ValidatePattern och ValidateSet samma cmdlet eller funktion.

Om du gör åsidosätter ValidatePattern ValidateSet.

Mer information om ValidatePattern Kolla in [detta *Hey, Scripting Guy!* publicera](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) och [PowerShell reguljära uttryck](https://technet.microsoft.com/library/hh847880.aspx) Referensinnehåll.

### <a name="allowing-external-commands-and-powershell-scripts"></a>Vilket gör att externa kommandon och PowerShell-skript

Du måste lägga till den fullständiga sökvägen till varje program i fältet VisibleExternalCommands för att tillåta användare köra körbara filer och PowerShell-skript (.ps1) i en JEA-session.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Det är bäst, där det är möjligt att använda PowerShell-cmdlet eller funktion som motsvarar alla externa programfiler som tillåter du eftersom du har kontroll över vilka parametrar tillåts med PowerShell-cmdlet: ar/funktioner.

Många körbara filer kan du både läsa det aktuella tillståndet och ändra den genom att ange olika parametrar.

Anta exempelvis att rollen för en filen server-administratör som vill kontrollera vilka nätverksresurser finns på den lokala datorn.
Ett sätt att kontrollera är att använda `net share`.
Dock tillåter net.exe är mycket farliga eftersom administratören kan lika enkelt använda kommandot för att få administratörsprivilegier med `net group Administrators unprivilegedjeauser /add`.
En bättre metod är att tillåta [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) som ger samma resultat men har en mycket mer begränsad omfattning.

När du gör externa kommandon tillgängliga för användare i en JEA-session kan du alltid ange den fullständiga sökvägen till den körbara filen för att säkerställa att ett liknande namn (och eventuellt malicous) program som placeras någon annanstans i systemet inte körs i stället.

### <a name="allowing-access-to-powershell-providers"></a>Att tillåta åtkomst till PowerShell-providers

Som standard finns inga PowerShell-providers i JEA-sessioner.

Detta är främst att minska risken för känslig information och konfigurationsinställningar som avslöjas för anslutande användaren.

Om det behövs kan du tillåta åtkomst till PowerShell-providers med hjälp av den `VisibleProviders` kommando.
En fullständig lista över providers, köra `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

För enkla uppgifter som kräver åtkomst till filsystemet, registret, certifikatarkivet eller andra leverantörer av känsliga, kan du också överväga skriva en egen funktion som fungerar med providern för användarens räkning.
Funktioner, cmdletar och externa program som är tillgängliga i en JEA-session är inte samma begränsningar som JEA – de kan komma åt valfri provider som standard.
Överväga att använda den [enheten](session-configurations.md#user-drive) när kopierar filer till och från en JEA-slutpunkt krävs.

### <a name="creating-custom-functions"></a>Skapa anpassade funktioner

Du kan skapa egna funktioner i en roll funktionen fil att förenkla komplexa uppgifter för dina slutanvändare.
Anpassade funktioner är också användbara när du behöver avancerade validering av logik för cmdleten parametervärden.
Du kan skriva enkla funktioner i den **FunctionDefinitions** fält:

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> Glöm inte att lägga till namnet på din anpassade funktioner till den **VisibleFunctions** fältet så att de kan köras av JEA-användare.


Brödtext (skriptblock) för egna funktioner körs i standardläget för språk för systemet och som inte omfattas av JEAS språk begränsningar.
Det innebär att funktioner kan komma åt filsystem och register och köra kommandon som inte gjordes synliga i filen roll funktionen.
Var noga med för att undvika att tillåta godtycklig kod som ska köras när du använder parametrarna och undvika rörnät indata från användaren direkt till cmdlets som `Invoke-Expression`.

I exemplet ovan ska du Observera att det fullständigt kvalificerade modulnamnet (FQMN) `Microsoft.PowerShell.Utility\Select-Object` användes i stället för snabbformat `Select-Object`.
Funktionerna som definieras i rollen funktionsfiler omfattas fortfarande JEA-sessioner,-omfattning som innehåller funktioner för proxy JEA skapar för att begränsa befintliga kommandon.

Select-Object är en standard begränsad cmdlet i alla JEA-sessioner som inte tillåter att du kan välja valfri egenskaper för objekt.
För att använda obegränsad Select-Object i funktioner, måste du uttryckligen begära detta fullständigt implementerat genom att ange FQMN.
En begränsad cmdlet i en JEA-sessionen kommer att få samma beteende när anropas från en funktion, i enlighet med PowerShell- [kommandot prioritet](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).

Om du skriver en massa egna funktioner, kan det vara enklare att placera dem i en [PowerShell skriptmodul](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).
Du kan sedan göra dessa funktioner synliga i JEA-sessionen med hjälp av fältet VisibleFunctions precis som med inbyggda och tredjeparts-moduler.

## <a name="place-role-capabilities-in-a-module"></a>Placera rollfunktioner i en modul

För PowerShell för att hitta en roll funktionen fil, måste den vara lagrad i en ”RoleCapabilities”-mapp i en PowerShell-modul.
Modulen kan lagras i valfri mapp som ingår i den `$env:PSModulePath` miljövariabeln, men du bör inte placera den i System32 (reserverade för inbyggda moduler) eller en mapp där den ej betrodda, ansluter användare kan ändra filerna.
Nedan visas ett exempel för att skapa en grundläggande PowerShell skriptmodul kallas *ContosoJEA* i sökvägen ”programfiler”.

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

Se [förstå en PowerShell-modul](https://msdn.microsoft.com/library/dd878324.aspx) för mer information om PowerShell-moduler, modulmanifest och PSModulePath-miljövariabeln.

## <a name="updating-role-capabilities"></a>Uppdaterar rollfunktioner


Du kan uppdatera en roll funktionen fil när som helst genom att bara spara ändringar i filen roll funktionen.
Alla nya JEA-sessioner som startas när funktionen för rollen har uppdaterats visas de ändrade funktionerna.

Det är därför det är så viktigt att kontrollera åtkomst till mappen rollen funktioner.
Endast betrodda administratörer ska kunna ändra rollen funktionsfiler.
Om en icke betrodd användare kan ändra rollen funktionsfiler, ge enkelt sig själva åtkomst till cmdlet: ar som att de kan utöka sina privilegier.


Kontrollera att lokalt System har läsbehörighet till rollen funktionsfiler och som innehåller moduler för administratörer som vill låsa åtkomst till rollfunktioner för.

## <a name="how-role-capabilities-are-merged"></a>Hur rollfunktioner slås samman

Användare kan få åtkomst till flera rollfunktioner när de kommer in en JEA-session beroende på roll-avbildningar i den [session konfigurationsfilen](session-configurations.md).
När detta sker JEA försöker ge användaren den *mest Tillåtande* uppsättning kommandon som tillåts av någon av rollerna.

**VisibleCmdlets och VisibleFunctions**

Den mest avancerade merge logiken påverkar cmdletar och funktioner som kan ha sina parametrar och parametervärden som är begränsad i JEA.

Reglerna är följande:

1. Om en cmdlet syns bara i en enda roll, blir synliga för användaren med tillämpliga parametern villkor.
2. Om en cmdlet syns i mer än en roll, och varje roll har samma begränsningar i cmdleten, blir cmdleten synliga för användare med dessa begränsningar.
3. Om en cmdlet syns i mer än en roll, och varje roll kan en annan uppsättning parametrar, ska cmdlet: en och alla de parametrar som definierats för varje roll vara synliga för användaren. Om en roll inte har begränsningar i parametrarna, får alla parametrar.
4. Om en roll definierar verifiera set eller verifiera mönster för en cmdlet-parameter och annan roll kan parametern men begränsar inte parametervärdena, kommer verifiera set eller mönster att ignoreras.
5. Om en uppsättning verifiera har definierats för samma cmdlet-parametern i mer än en roll, får alla värden från alla verifiera uppsättningar.
6. Om ett verifiera mönster har definierats för samma cmdlet-parametern i mer än en roll, får alla värden som matchar någon av mönster.
7. Om en uppsättning verifiera har definierats i en eller flera roller och ett verifiera mönster har definierats i en annan roll för samma cmdlet-parameter, verifiera uppsättningen ignoreras och regeln (6) gäller för de återstående verifiera mönster.

Nedan visas ett exempel på hur roller slås samman enligt reglerna:

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**

Alla andra fält i filen roll funktionen läggs bara till en kumulativ uppsättning med tillåtna externa kommandon, alias, leverantörer och startskript.
Alla kommandot, alias, provider eller skript som är tillgängliga i en roll funktionen kommer att kunna JEA-användaren.

Var noga med att kontrollera att en kombinerad uppsättning-provider från en roll funktions- och kommandon/cmdlets/funktioner från en annan Tillåt inte att ansluta användare oavsiktlig åtkomst till systemresurser.
Om en roll kan till exempel den `Remove-Item` cmdlet och ett annat kan den `FileSystem` provider, du kan vara utsatta för en JEA-användare som tar bort godtyckliga filer på datorn.
Mer information om hur du identifierar användarnas gällande behörigheter finns i den [granskning JEA avsnittet](audit-and-report.md).

## <a name="next-steps"></a>Nästa steg

- [Skapa en konfigurationsfil för session](session-configurations.md)