---
ms.date: 07/10/2019
keywords: Jea, PowerShell, säkerhet
title: JEA roll funktioner
ms.openlocfilehash: 7191b90e198ffb539da6870a8ddc3e449ad9e8ae
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017960"
---
# <a name="jea-role-capabilities"></a>JEA roll funktioner

När du skapar en JEA-slutpunkt måste du definiera en eller flera roll funktioner som beskriver vad någon kan göra i en JEA-session. En roll kapacitet är en PowerShell-datafil med `.psrc` tillägget som visar alla cmdletar, funktioner, providers och externa program som görs tillgängliga för att ansluta användare.

## <a name="determine-which-commands-to-allow"></a>Ta reda på vilka kommandon som tillåts

Det första steget i att skapa en roll kapacitets fil är att fundera över vad användarna behöver åtkomst till. Processen för att samla in krav kan ta en stund, men det är en viktig process. Att ge användare åtkomst till för få cmdlets och funktioner kan hindra dem från att få jobbet utfört. Att tillåta åtkomst till för många cmdletar och funktioner kan göra det möjligt för användare att göra mer än vad du avsåg och minska din säkerhets virtualiseringsprodukter från.

Hur du fortsätter med den här processen beror på din organisation och dina mål. Följande tips kan vara till hjälp för att se till att du har rätt sökväg.

1. **Identifiera** de kommandon som användare använder för att få jobben gjorda. Detta kan innebära att undersöka IT-personal, kontrol lera automatiserings skript eller analysera PowerShell-sessions avskrifter och loggar.
2. **Uppdatera** användningen av kommando rads verktyg till PowerShell-motsvarigheter, där det är möjligt, för den bästa gransknings-och Jea anpassnings upplevelsen. Externa program kan inte vara begränsade som inbyggda PowerShell-cmdlets och Functions i JEA.
3. **Begränsa** cmdlets definitions området så att endast vissa parametrar eller parameter värden tillåts. Detta är särskilt viktigt om användarna endast ska hantera en del av ett system.
4. **Skapa** anpassade funktioner för att ersätta komplexa kommandon eller kommandon som är svåra att begränsa i Jea. En enkel funktion som omsluter ett komplext kommando eller använder ytterligare validerings logik kan ge ytterligare kontroll för administratörer och slutanvändarens enkelhet.
5. **Testa** den begränsade listan över tillåtna kommandon med dina användare eller Automation-tjänster och justera efter behov.

### <a name="examples-of-potentially-dangerous-commands"></a>Exempel på potentiellt farliga kommandon

Ett noggrant urval av kommandon är viktigt för att se till att JEA-slutpunkten inte tillåter att användaren höjer sina behörigheter.

> [!IMPORTANT]
> Nödvändig information som krävs för användarens successCommands i en JEA-session körs ofta med utökade privilegier.

Följande tabell innehåller exempel på kommandon som kan användas skadligt om de tillåts i ett obegränsat tillstånd. Detta är inte en fullständig lista och bör endast användas som en varnings start punkt.

|                                            Risk                                            |                                Exempel                                |                                                                              Relaterade kommandon                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Bevilja den anslutande användar administratörs behörighet att kringgå JEA                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`                                                                                                        |
| Köra godtycklig kod, till exempel skadlig kod, sårbarheter eller anpassade skript för att kringgå skydd | `Start-Process -FilePath '\\san\share\malware.exe'`                   | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob` |

## <a name="create-a-role-capability-file"></a>Skapa en roll funktions fil

Du kan skapa en ny funktion för PowerShell-roll med cmdleten [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) .

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Den resulterande roll funktions filen bör redige ras för att tillåta de kommandon som krävs för rollen. PowerShell-hjälpens dokumentation innehåller flera exempel på hur du kan konfigurera filen.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Tillåta PowerShell-cmdlets och Functions

Om du vill auktorisera användare att köra PowerShell-cmdletar eller-funktioner lägger du till cmdleten eller funktions namnet i fälten VisibleCmdlets eller VisibleFunctions. Om du inte är säker på om ett kommando är en cmdlet eller funktion kan du `Get-Command <name>` köra och kontrol lera egenskapen **CommandType** i utdata.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Ibland är omfattningen av en speciell cmdlet eller funktion för bred för användarnas behov. En DNS-administratör, till exempel, behöver förmodligen bara åtkomst för att starta om DNS-tjänsten. I miljöer med flera klienter har klienter till gång till självbetjänings hanterings verktyg. Klienterna bör begränsas till att hantera sina egna resurser. I dessa fall kan du begränsa vilka parametrar som exponeras från cmdleten eller funktionen.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

I mer avancerade scenarier kan du också behöva begränsa de värden som en användare kan använda med dessa parametrar. Med roll funktioner kan du definiera en uppsättning värden eller ett mönster för reguljära uttryck som avgör vilka indatatyper som tillåts.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> [Vanliga PowerShell-parametrar](/powershell/module/microsoft.powershell.core/about/about_commonparameters) tillåts alltid, även om du begränsar de tillgängliga parametrarna.
> Du bör inte uttryckligen lista dem i parameter fältet.

I tabellen nedan beskrivs de olika sätt som du kan anpassa en synlig cmdlet eller funktion på.
Du kan blanda och matcha något av följande i fältet **VisibleCmdlets** .

|                                           Exempel                                           |                                                             Användningsfall                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `'My-Func'` eller `@{ Name = 'My-Func' }`                                                      | Tillåter användaren att köra `My-Func` utan begränsningar för parametrarna.                                                      |
| `'MyModule\My-Func'`                                                                        | Tillåter att användaren kör `My-Func` från modulen `MyModule` utan begränsningar för parametrarna.                           |
| `'My-*'`                                                                                    | Tillåter användaren att köra valfri cmdlet eller funktion med verbet `My`.                                                                 |
| `'*-Func'`                                                                                  | Tillåter användaren att köra valfri cmdlet eller funktion med Substantiv `Func`.                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | Tillåter användaren att köra `My-Func` `Param1` med parametrarna och `Param2` . Alla värden kan anges för parametrarna.          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | Tillåter användaren att köra `My-Func` `Param1` med parametern. Endast "värde1" och "värde2" kan anges för parametern.        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | Tillåter användaren att köra `My-Func` `Param1` med parametern. Alla värden som börjar med "contoso" kan anges för parametern. |

> [!WARNING]
> För bästa säkerhets praxis rekommenderar vi inte att jokertecken används när du definierar synliga cmdlets eller functions. I stället bör du uttryckligen lista varje betrott kommando för att se till att inga andra kommandon som delar samma namngivnings schema oavsiktligt har behörighet.

Du kan inte använda både en **ValidatePattern** och **ValidateSet** för samma cmdlet eller funktion.

Om du gör det åsidosätter **ValidatePattern** **ValidateSet**.

Mer information om **ValidatePattern**finns i [det här *Hey, Scripting Guy!* post](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) och PowerShell-referensen för [vanliga uttryck](/powershell/module/microsoft.powershell.core/about/about_regular_expressions) .

### <a name="allowing-external-commands-and-powershell-scripts"></a>Tillåta externa kommandon och PowerShell-skript

Om du vill tillåta användare att köra körbara filer och PowerShell-skript (. ps1) i en JEA-session måste du lägga till den fullständiga sökvägen till varje program i fältet **VisibleExternalCommands** .

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Om möjligt kan du använda PowerShell-cmdlet eller Function-motsvarigheter för alla externa körbara filer som du godkänner eftersom du har kontroll över de parametrar som tillåts med PowerShell-cmdlets och functions.

Med många körbara filer kan du läsa det aktuella läget och sedan ändra det genom att ange olika parametrar.

Anta till exempel rollen som en fil Server administratör som hanterar nätverks resurser som finns på ett system. Ett sätt att hantera resurser är att använda `net share`. Att tillåta **net. exe** är dock farligt eftersom användaren kan använda kommandot för att få administratörs behörighet `net group Administrators unprivilegedjeauser /add`. Ett säkrare alternativ är att tillåta [Get-SmbShare](/powershell/module/smbshare/get-smbshare), vilket ger samma resultat men har ett mycket mer begränsat omfång.

När du gör externa kommandon tillgängliga för användare i en JEA-session ska du alltid ange den fullständiga sökvägen till den körbara filen. Detta förhindrar körning av liknande namngivna och potentiellt skadliga program som finns på andra platser i systemet.

### <a name="allowing-access-to-powershell-providers"></a>Tillåta åtkomst till PowerShell-leverantörer

Som standard är inga PowerShell-leverantörer tillgängliga i JEA-sessioner. Detta minskar risken för känslig information och konfigurations inställningar som visas för den anslutande användaren.

Vid behov kan du tillåta åtkomst till PowerShell-providers med hjälp `VisibleProviders` av kommandot. För en fullständig lista över leverantörer, kör `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

För enkla uppgifter som kräver åtkomst till fil systemet, registret, certifikat arkivet eller andra känsliga leverantörer kan du överväga att skriva en anpassad funktion som fungerar med providern för användarens räkning. De funktioner, cmdletar och externa program som är tillgängliga i en JEA-session omfattas inte av samma begränsningar som JEA. De kan komma åt alla leverantörer som standard. Överväg också att använda [användar enheten](session-configurations.md#user-drive) när du kopierar filer till eller från en Jea-slutpunkt krävs.

### <a name="creating-custom-functions"></a>Skapa anpassade funktioner

Du kan skapa anpassade funktioner i en roll funktions fil för att förenkla komplexa uppgifter för slutanvändarna. Anpassade funktioner är också användbara när du behöver avancerad validerings logik för cmdlet-parametervärdena. Du kan skriva enkla funktioner i fältet **FunctionDefinitions** :

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending |
            Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> Glöm inte att lägga till namnet på dina anpassade funktioner i fältet **VisibleFunctions** så att de kan köras av Jea-användare.

Texten (skript blocket) för anpassade funktioner körs i standard språk läge för systemet och omfattas inte av JEA språk begränsningar. Det innebär att funktioner kan komma åt fil systemet och registret, och köra kommandon som inte har gjorts synliga i den roll kapacitets filen. Ta hand om att undvika att köra godtycklig kod när du använder parametrar. Undvik att skicka indata från användaren direkt till `Invoke-Expression`cmdletar som.

I exemplet ovan ser du att det fullständigt kvalificerade modulnamnet (FQMN) `Microsoft.PowerShell.Utility\Select-Object` användes i stället för kort. `Select-Object`
Funktioner som definieras i roll kapacitets filer omfattas fortfarande av omfånget för JEA-sessioner, som innehåller proxy-funktionerna JEA skapar för att begränsa befintliga kommandon.

Som standard `Select-Object` är en begränsad cmdlet i alla Jea-sessioner som inte tillåter val av godtyckliga egenskaper för objekt. Om du vill använda den obegränsade `Select-Object` funktionen i funktioner måste du uttryckligen begära fullständig implementering med hjälp av FQMN. Alla begränsade cmdlets i en JEA-session har samma begränsningar när de anropas från en funktion. Mer information finns i [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence).

Om du skriver flera anpassade funktioner är det mer praktiskt att använda dem i en PowerShell-modul för-skript. Du gör dessa funktioner synliga i JEA-sessionen med hjälp av **VisibleFunctions** -fältet på samma sätt som med inbyggda moduler och moduler från tredje part.

För att avslutning av flikar ska fungera korrekt i Jea-sessioner måste du inkludera `tabexpansion2` den inbyggda funktionen i **VisibleFunctions** -listan.

## <a name="place-role-capabilities-in-a-module"></a>Placera roll funktioner i en modul

För att PowerShell ska kunna hitta en roll funktions fil måste den lagras i en **RoleCapabilities** -mapp i en PowerShell-modul. Modulen kan lagras i alla mappar som ingår i `$env:PSModulePath` miljövariabeln, men du bör inte placera den i system32 eller en mapp där det inte är betrott, och ansluta användare kan ändra filerna. Nedan visas ett exempel på hur du skapar en grundläggande PowerShell- modul med namnet `$env:ProgramFiles` ContosoJEA i sökvägen.

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest.
# At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

Mer information om PowerShell-moduler finns i [förstå en PowerShell-modul](/powershell/developer/windows-powershell).

## <a name="updating-role-capabilities"></a>Uppdaterar roll funktioner

Du kan redigera en roll funktions fil om du vill uppdatera inställningarna när som helst. Alla nya JEA-sessioner som startas efter att roll kapaciteten har uppdaterats visar de ändrade funktionerna.

Det är därför viktigt att kontrol lera åtkomsten till mappen roll funktioner. Endast hög betrodda administratörer bör kunna ändra roll kapacitets filer. Om en ej betrodd användare kan ändra roll kapacitets filer kan de enkelt ge sig till gång till cmdletar som gör att de kan höja sina privilegier.

För administratörer som vill låsa åtkomst till roll funktionerna kontrollerar du att lokalt system har Läs behörighet till roll kapacitets filerna och innehåller moduler.

## <a name="how-role-capabilities-are-merged"></a>Så här sammanfogas roll funktioner

Användare beviljas åtkomst till alla matchande roll funktioner i konfigurations [filen för sessionen](session-configurations.md) när de anger en Jea-session. JEA försöker ge användaren den mest tillåtna uppsättningen kommandon som tillåts av någon av rollerna.

### <a name="visiblecmdlets-and-visiblefunctions"></a>VisibleCmdlets och VisibleFunctions

Den mest komplexa sammanslagnings logiken påverkar cmdletar och funktioner, vilket kan ha sina parametrar och parameter värden begränsade i JEA.

Reglerna är följande:

1. Om en cmdlet bara görs synlig i en roll, är den synlig för användaren med eventuella tillämpliga parameter begränsningar.
2. Om en cmdlet görs synlig i mer än en roll och varje roll har samma begränsningar i cmdleten, visas cmdleten för användaren med dessa begränsningar.
3. Om en cmdlet görs synlig i mer än en roll, och varje roll tillåter en annan uppsättning parametrar, visas cmdleten och alla parametrar som definierats för varje roll för användaren.
   Om en roll inte har begränsningar för parametrarna, tillåts alla parametrar.
4. Om en roll definierar en verifierad uppsättning eller verifiera mönster för en cmdlet-parameter, och den andra rollen tillåter parametern men inte begränsar parameter värden, ignoreras verifierings uppsättningen eller mönstret.
5. Om en verifierings uppsättning har definierats för samma cmdlet-parameter i mer än en roll, tillåts alla värden från alla validerings uppsättningar.
6. Om ett verifierings mönster har definierats för samma cmdlet-parameter i mer än en roll, tillåts alla värden som matchar någon av mönstren.
7. Om en verifierings uppsättning definieras i en eller flera roller, och ett verifierings mönster definieras i en annan roll för samma cmdlet-parameter, ignoreras verifierings uppsättningen och regel (6) gäller för de återstående verifierings mönstren.

Nedan visas ett exempel på hur roller slås samman enligt följande regler:

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service
#   is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use
#   ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

### <a name="visibleexternalcommands-visiblealiases-visibleproviders-scriptstoprocess"></a>VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess

Alla andra fält i roll kapacitets filen läggs till i en kumulativ uppsättning tillåtna externa kommandon, alias, providers och start skript. Alla kommandon, alias, providers och skript som är tillgängliga i en roll kapacitet är tillgängliga för JEA-användaren.

Var noga med att se till att den kombinerade uppsättningen med providers från en roll kapacitet och cmdlets/Functions/commands från andra inte tillåter användare oavsiktlig åtkomst till system resurser.
Om till exempel en roll tillåter `Remove-Item` -cmdleten och en annan `FileSystem` tillåter providern, är du utsatt för en Jea-användare som tar bort godtyckliga filer på datorn. Ytterligare information om att identifiera användares gällande behörigheter finns i artikeln [granskning Jea](audit-and-report.md) .

## <a name="next-steps"></a>Nästa steg

[Skapa en konfigurations fil för sessionen](session-configurations.md)
