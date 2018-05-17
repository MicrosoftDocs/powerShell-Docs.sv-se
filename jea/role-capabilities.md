---
ms.date: 06/12/2017
keywords: jea powershell säkerhet
title: JEA roll funktioner
ms.openlocfilehash: 0531baa284e66a42a162329ea20ecfdca6d0b526
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="jea-role-capabilities"></a>JEA roll funktioner

> Gäller för: Windows PowerShell 5.0

När du skapar en JEA slutpunkt, behöver du definiera minst en ”roll funktioner” som beskriver *vad* någon kan göra i en JEA-session.
En roll-funktion är en fil med filnamnstillägget .psrc med en lista över alla cmdlets, funktioner, leverantörer och externa program som ska göras tillgängliga för att ansluta användare PowerShell.

Det här avsnittet beskriver hur du skapar en fil PowerShell rollen kapaciteten för användarnas JEA.

## <a name="determine-which-commands-to-allow"></a>Bestämma vilka kommandon för att tillåta

Det första steget när du skapar en roll kapaciteten fil är att tänka på vad de användare som har tilldelats rollen behöver åtkomst till.
Detta krav Insamlingsprocessen kan ta en stund, men det är mycket viktigt att.
Ge användare åtkomst till för få cmdletar och funktioner kan hindra dem från att få sitt jobb.
Att tillåta åtkomst till för många cmdletar och funktioner kan leda till användare göra mer än du tänkt med deras implicit administratörsrättigheter minskad säkerhet-behöver.

Hur du går om den här processen beror på din organisation och mål, men följande tips kan hjälpa dig att se till att du är på rätt väg.

1. **Identifiera** kommandon användare använder för att jobbet. Detta kan innebära prospektering av IT-personal, kontrollerar automatiseringsskript eller analysera loggarna eller PowerShell-session betyg.
2. **Uppdatera** använder kommandoradsverktyg till PowerShell-motsvarighet, där det är möjligt, för bästa gransknings- och JEA anpassning upplevelse. Externa program kan inte begränsas som granularly som ursprunglig PowerShell-cmdletar och funktioner i JEA.
3. **Begränsa** omfattning cmdlets om nödvändigt att endast tillåta att specifika parametrar eller parametervärden. Detta är särskilt viktigt om användare bara ska kunna hantera en del av ett system.
4. **Skapa** anpassade funktioner att ersätta komplexa kommandon eller kommandon som är svåra att begränsa i JEA. En enkel funktion som omsluter kommandot komplexa eller tillämpar logik för ytterligare verifiering kan erbjuda ytterligare kontroll för enkelhetens skull administratörer och slutanvändare.
5. **Testa** begränsade listan över tillåtna kommandon med användare och/eller automation services och justera vid behov.

Det är viktigt att komma ihåg att kommandona i en session JEA är ofta kör med admin (eller på annat sätt upphöjd) behörighet.
Noggrann val av tillgängliga kommandon är viktigt att säkerställa JEA slutpunkten inte tillåter den anslutande användaren vill höja deras behörigheter.
Nedan följer några exempel på kommandon som kan användas medvetet om tillåts i en obegränsad tillstånd.
Observera att detta inte är en komplett lista och bör endast användas som utgångspunkt vara avstängda.

### <a name="examples-of-potentially-dangerous-commands"></a>Exempel på potentiellt skadliga kommandon

Risk | Exempel | Relaterade kommandon
-----|---------|-----------------
Bevilja den anslutande användaren admin-privilegier för att kringgå JEA | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`
Köra godtycklig kod, till exempel skadlig kod, kryphål eller anpassade skript för att kringgå skydd | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>Skapa en roll kapaciteten fil

Du kan skapa en ny fil med funktionen för roll av PowerShell på [ny PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Den resulterande roll kapaciteten filen kan öppnas i en textredigerare och ändras så att kommandona för rollen.
I PowerShell-hjälpen innehåller flera exempel på hur du kan konfigurera filen.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Gör att PowerShell-cmdletar och funktioner

Om du vill tillåta användare att köra PowerShell-cmdlets eller funktioner, lägger du till cmdlet eller funktionen namnet VisbibleCmdlets eller VisibleFunctions fält.
Om du är osäker på om ett kommando är en cmdlet eller funktionen, kan du köra `Get-Command <name>` och kontrollera egenskapen ”CommandType” i utdata.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Ibland är omfånget för en viss cmdlet eller funktion för breda för användarnas behov.
En DNS-admin exempelvis antagligen bara måste ha åtkomst för att starta om tjänsten DNS.
I en miljö med flera innehavare där klienter har åtkomst till självbetjäning hanteringsverktyg, begränsas hyresgäster till att hantera med sina egna resurser.
I dessa fall kan du begränsa vilka parametrar som är tillgängliga från den cmdlet eller funktionen.

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

I mer avancerade scenarier, kan du också behöva begränsa vilka värden som någon kan ange att dessa parametrar.
Rollen funktioner kan du definiera en uppsättning tillåtna värden eller ett mönster för reguljärt uttryck som utvärderas för att avgöra om en viss inmatning är tillåten.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> Den [vanliga PowerShell-parametrar](https://technet.microsoft.com/library/hh847884.aspx) tillåts alltid, även om du begränsar tillgängliga parametrar.
> Du bör inte explicit lista dem i fältet parametrar.

I tabellen nedan beskrivs de olika sätt som du kan anpassa en synlig cmdlet eller funktion.
Du kan blanda och matcha någon av de nedan i VisibleCmdlets fältet.

Exempel                                                                                      | Användningsfall
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` eller `@{ Name = 'My-Func' }`                                                       | Tillåter användaren att köra `My-Func` utan begränsningar på parametrar.
`'MyModule\My-Func'`                                                                         | Tillåter användaren att köra `My-Func` från modulen `MyModule` utan begränsningar på parametrar.
`'My-*'`                                                                                     | Tillåter användaren att köra en cmdlet eller funktion med verbet `My`.
`'*-Func'`                                                                                   | Tillåter användaren att köra en cmdlet eller funktion med substantivet `Func`.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | Tillåter användaren att köra `My-Func` med den `Param1` och/eller `Param2` parametrar. Alla värden kan anges till parametrarna.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | Tillåter användaren att köra `My-Func` med den `Param1` parameter. Endast ”Value1” och ”Value2” kan anges i parametern.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | Tillåter användaren att köra `My-Func` med den `Param1` parameter. Ett värde som börjar med ”contoso” kan anges i parametern.


> [!WARNING]
> Metodtips för säkerhet rekommenderas det inte att använda jokertecken när du definierar synliga cmdletar eller funktioner.
> I stället en lista med varje betrodda kommando för att se till att inga andra kommandon som delar samma namngivningsschemat oavsiktligt har behörighet.

Du kan inte använda både en ValidatePattern och ValidateSet samma cmdlet eller funktion.

Om du gör åsidosätter ValidatePattern ValidateSet.

Mer information om ValidatePattern kolla [detta *artikel från Hey, Scripting Guy!* efter](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) och [PowerShell reguljära uttryck](https://technet.microsoft.com/library/hh847880.aspx) refererar till innehåll.

### <a name="allowing-external-commands-and-powershell-scripts"></a>Att tillåta externa kommandon och PowerShell-skript

Du måste lägga till den fullständiga sökvägen till varje program i fältet VisibleExternalCommands så att användare köra körbara filer och PowerShell-skript (.ps1) i en session JEA.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Det är bäst, där det är möjligt att använda PowerShell-cmdlet eller funktion motsvarigheter till alla externa programfiler som tillåter du eftersom du har kontroll över vilka parametrar tillåts med PowerShell-cmdlet: ar/funktioner.

Många körbara filer kan du att både läsa det aktuella tillståndet och ändra den genom att tillhandahålla olika parametrar.

Anta till exempel att rollen för fil serveradministratör som vill kontrollera vilka nätverksresurser hanteras av den lokala datorn.
Ett sätt att kontrollera är att använda `net share`.
Dock tillåter net.exe är mycket farliga eftersom administratören kan lika enkelt använda kommandot för att få administratörsrättigheter med `net group Administrators unprivilegedjeauser /add`.
Är det bättre att [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) som ger samma resultat, men som har mycket mer begränsad omfattning.

När du gör externa kommandon tillgängliga för användare i en JEA session kan du alltid ange den fullständiga sökvägen till den körbara filen så ett liknande namn (och potentiellt malicous) program som placeras på en annan plats i systemet inte körs i stället.

### <a name="allowing-access-to-powershell-providers"></a>Att tillåta åtkomst till PowerShell-providers

Som standard finns inga PowerShell-leverantörer i JEA sessioner.

Detta är främst att minska risken för konfigurationsinställningar som avslöjas för den anslutande användaren och känslig information.

Vid behov, kan du tillåta åtkomst till PowerShell-leverantörer som använder den `VisibleProviders` kommando.
En fullständig lista över providers, köra `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

För enkla uppgifter som kräver åtkomst till filsystemet, registret, certifikatarkivet eller andra leverantörer av känsliga kan du också överväga att skriva en egen funktion som fungerar med providern för användarens räkning.
Funktioner, cmdletar och externa program som är tillgängliga i en session JEA är inte samma begränsningar som JEA – de kan använda valfri provider som standard.
Överväga att använda den [enheten](session-configurations.md#user-drive) när filer kopieras till/från en slutpunkt för JEA krävs.

### <a name="creating-custom-functions"></a>Skapa anpassade funktioner

Du kan skapa anpassade funktioner i en roll kapaciteten fil till att förenkla komplexa för dina slutanvändare.
Anpassade funktioner är också användbara när du behöver avancerad verifiering logik för cmdlet parametervärden.
Du kan skriva enkla funktioner den **FunctionDefinitions** fält:

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
> Glöm inte att lägga till namnet på din anpassade funktioner till den **VisibleFunctions** så att de kan köras av JEA användare.


Texten (skriptblock) för egna funktioner körs i standardläget för språk för systemet och är inte begränsningar för JEAS språk.
Det innebär att funktioner kan komma åt filsystem och register, och köra kommandon som inte har skapats visas i filen rollen kapaciteten.
Var noga med för att undvika att tillåta att skadlig kod som ska köras när du använder parametrar och undvika rörnät användarindata direkt till cmdlets som `Invoke-Expression`.

I exemplet ovan ska du Observera att det fullständigt kvalificerade namnet (FQMN) `Microsoft.PowerShell.Utility\Select-Object` användes i stället för shorthand `Select-Object`.
Funktioner som är definierade i rollen funktionsfiler regleras fortfarande omfattning JEA sessioner, som innehåller funktioner för proxy JEA skapar för att begränsa befintliga kommandon.

Select-Object är en standard begränsad cmdlet i alla JEA-sessioner som inte tillåter att du kan välja valfri egenskaper för objekt.
Om du vill använda obegränsad Select-Object i funktioner, måste du uttryckligen begära fullständigt genomförande genom att ange FQMN.
Alla begränsad cmdlet i en session JEA kommer att få samma beteende när den anropades från en funktion i enlighet med PowerShells [kommandot prioritet](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).

Om du skriver en mängd anpassade funktioner, kan det vara lättare att placera dem i en [PowerShell-skriptet modulen](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).
Du kan göra de här funktionerna i JEA sessionen med fältet VisibleFunctions sätt som med inbyggda och tredjeparts-moduler.

## <a name="place-role-capabilities-in-a-module"></a>Placera rollen funktioner i en modul

För PowerShell för att hitta en roll kapaciteten fil måste den lagras i en mapp för ”RoleCapabilities” i en PowerShell-modul.
Modulen kan lagras i en mapp som ingår i den `$env:PSModulePath` miljövariabeln, men du bör inte placera den i System32 (reserverad för inbyggda moduler) eller en mapp där den betrodd, ansluter användare kan ändra filerna.
Nedan visas ett exempel på att skapa en grundläggande PowerShell skriptmodul kallas *ContosoJEA* i sökvägen ”programfiler”.

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

Se [förstå PowerShell-modulen](https://msdn.microsoft.com/en-us/library/dd878324.aspx) mer information om PowerShell-moduler, modulmanifest och PSModulePath miljövariabeln.

## <a name="updating-role-capabilities"></a>Uppdatera rollen funktioner


Du kan uppdatera en roll kapaciteten fil när som helst genom att helt enkelt sparar ändringarna i filen rollen kapaciteten.
Alla nya JEA sessioner igång när kapaciteten för rollen har uppdaterats visar de nya funktionerna.

Det är därför det är så viktigt att kontrollera åtkomst till mappen rollen funktioner.
Endast betrodda administratörer ska kunna ändra roll funktionsfiler.
Om en icke betrodd användare kan ändra funktionsfiler för rollen, kan de enkelt ge sig åtkomst till cmdlets som gör det möjligt för dem att öka sina privilegier.


Kontrollera lokalt System har läsbehörighet till rollen funktionsfiler och som innehåller moduler för administratörer som behöver låsa åtkomst till funktionerna för rollen.

## <a name="how-role-capabilities-are-merged"></a>Hur rollen funktioner kombineras

Användare kan få åtkomst till flera rollen funktioner när de anger en JEA session beroende på roll-avbildningar i den [session konfigurationsfilen](session-configurations.md).
När detta sker JEA försök att ge användaren den *mest Tillåtande* uppsättning kommandon som tillåts av någon av rollerna.

**VisibleCmdlets och VisibleFunctions**

Den mest komplexa merge logiken påverkar cmdletar och funktioner som kan ha sina parametrar och parametervärden som är begränsad i JEA.

Reglerna är följande:

1. Om en cmdlet görs endast visas i en roll, kan det vara synliga för användare med alla tillämpliga tillgodosetts.
2. Om en cmdlet görs visas i mer än en roll, och varje roll har samma begränsningar för cmdleten, vara cmdlet synliga för användare med dessa begränsningar.
3. Om en cmdlet görs visas i mer än en roll, och varje roll kan en annan uppsättning parametrar, visas cmdlet: en och alla parametrar som definierats för varje roll för användaren. Om en roll inte har begränsningar för parametrarna, kommer alla parametrar att tillåtas.
4. Om en roll som definierar en verifiera uppsättning eller verifiera mönster för en cmdlet-parameter, och den andra rollen ger parametern men inte begränsa parametervärden, kommer verifiera uppsättning eller mönster att ignoreras.
5. Om en uppsättning verifiera har definierats för samma cmdlet-parameter i mer än en roll, får alla värden från alla verifiera uppsättningar.
6. Om ett mönster för verifiera har definierats för samma cmdlet-parameter i mer än en roll, tillåts värden som matchar någon av mönster.
7. Om en uppsättning verifiera har definierats i en eller flera roller och ett mönster för verifiera har definierats i en annan roll för samma cmdlet-parameter, verifiera uppsättningen ignoreras och regeln (6) gäller för de återstående verifiera mönster.

Nedan visas ett exempel på hur roller kombineras enligt reglerna:

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



**VisibleExternalCommands VisibleAliases VisibleProviders, ScriptsToProcess**

Alla andra fält i filen rollen kapaciteten läggs bara till en kumulativ uppsättning med tillåtna externa kommandon, alias, leverantörer och startskript.
Alla kommandot alias, provider eller skript som är tillgängliga i en roll-funktionen kommer att kunna JEA användaren.

Var noga med att kontrollera att den kombinerade uppsättningen providers från en roll kapaciteten och kommandon/cmdlets/funktioner från en annan tillåter inte anslutning användare oavsiktlig åtkomst till systemresurser.
Om en roll kan till exempel den `Remove-Item` cmdlet och en annan tillåter den `FileSystem` provider, du riskerar att JEA användaren ta bort godtyckliga filer från datorn.
Mer information om hur du identifierar användarnas gällande behörigheter finns i den [granskning JEA avsnittet](audit-and-report.md).

## <a name="next-steps"></a>Nästa steg

- [Skapa en konfigurationsfil för session](session-configurations.md)