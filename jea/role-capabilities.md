---
ms.date: 07/10/2019
keywords: jea, powershell, säkerhet
title: JEA rollfunktioner
ms.openlocfilehash: 7191b90e198ffb539da6870a8ddc3e449ad9e8ae
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726609"
---
# <a name="jea-role-capabilities"></a>JEA rollfunktioner

När du skapar en JEA-slutpunkt som du behöver definiera en eller flera rollfunktioner som beskriver vad någon kan göra i en JEA-session. En roll-funktionen är en PowerShell-datafilen med den `.psrc` tillägg som visar en lista över alla cmdlet: ar, funktioner, leverantörer och externa program som är tillgängliga för användare att ansluta.

## <a name="determine-which-commands-to-allow"></a>Avgöra vilka kommandon för att tillåta

Det första steget i att skapa en fil för roll-funktionen är att tänka på vad användare behöver åtkomst till. Kraven Insamlingsprocessen kan ta en stund, men det är en viktig process. Ge användare åtkomst till tillräckligt många cmdletar och funktioner kan hindra dem från att få sitt jobb. Att tillåta åtkomst till för många cmdletar och funktioner kan användarna göra mer än du avsedd och begränsa effekten av din säkerhet åtgärder.

Hur du går tillväga för den här processen beror på din organisation och mål. Följande tips kan hjälpa att kontrollera att du befinner dig på rätt väg.

1. **Identifiera** kommandon användare använder för att få sitt arbete. Detta kan omfatta överblick över IT-personal, kontrollerar automatiseringsskript eller analysera loggar och betyg för PowerShell-session.
2. **Uppdatera** använda kommandoradsverktyg till PowerShell-motsvarighet, där det är möjligt, för bästa gransknings- och JEA anpassning upplevelse. Vara det går inte att begränsad till externa program som detaljerat som interna PowerShell-cmdletar och funktioner i JEA.
3. **Begränsa** omfånget för cmdletar för att endast tillåta att specifika parametrar eller parametervärden. Detta är särskilt viktigt om användare ska hantera bara en del av ett system.
4. **Skapa** egna funktioner för att ersätta komplexa kommandon eller kommandon som är svåra att begränsa i JEA. En enkel funktion som omsluter ett kommando som komplexa eller gäller ytterligare validering av logik kan erbjuda ytterligare kontroll för enkelhetens skull administratörer och slutanvändare.
5. **Testa** begränsade listan över tillåtna kommandon med dina användare eller automation-tjänster, och justera vid behov.

### <a name="examples-of-potentially-dangerous-commands"></a>Exempel på potentiellt skadliga kommandon

Försiktig med kommandon är viktigt att se till att JEA-slutpunkt inte tillåter användare att utöka sina behörigheter.

> [!IMPORTANT]
> Viktig information som krävs för användaren successCommands i en JEA-session ofta körs med förhöjd behörighet.

I följande tabell innehåller exempel på kommandon som du kan använda medvetet om tillåts i en obegränsad tillstånd. Detta är inte en fullständig förteckning och bör endast användas som utgångspunkt systemprinciper.

|                                            Risk                                            |                                Exempel                                |                                                                              Relaterade kommandon                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Bevilja den anslutande användaren administratörsbehörigheter för att kringgå JEA                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`                                                                                                        |
| Köra godtycklig kod, till exempel skadlig kod, trojaner eller anpassade skript att kringgå skydd | `Start-Process -FilePath '\\san\share\malware.exe'`                   | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob` |

## <a name="create-a-role-capability-file"></a>Skapa en roll funktionen fil

Du kan skapa en ny fil med funktionen för rollen av PowerShell i [New PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) cmdlet.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Den resulterande roll funktion filen måste redigeras för att tillåta de kommandon som krävs för rollen. I PowerShell-hjälpen innehåller flera exempel på hur du kan konfigurera filen.

### <a name="allowing-powershell-cmdlets-and-functions"></a>PowerShell-cmdletar och funktioner

Om du vill tillåta användare att köra PowerShell-cmdletar eller funktioner, lägger du till cmdlet eller funktionen namnet VisibleCmdlets eller VisibleFunctions fält. Om du är osäker på om ett kommando är en cmdlet eller funktion, kan du köra `Get-Command <name>` och kontrollera den **CommandType** -egenskapen i utdata.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Ibland är omfånget för en specifik cmdlet eller funktion för breda för dina användares behov. En DNS-administratör kan till exempel förmodligen bara behöver åtkomst till för att starta om DNS-tjänsten. Klienter har åtkomst till själva hanteringsverktyg i miljöer med flera innehavare. Klienter bör begränsas till att hantera sina egna resurser. För dessa fall kan begränsa du vilka parametrar som exponeras från cmdlet eller funktion.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

I mer avancerade scenarier kan du också behöva begränsar de värden som en användare kan använda med dessa parametrar. Rollfunktioner kan du definiera en uppsättning värden eller ett mönster för reguljärt uttryck som bestämmer vilka inmatning är tillåten.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> Den [vanliga PowerShell-parametrar](/powershell/module/microsoft.powershell.core/about/about_commonparameters) tillåts alltid, även om du begränsar tillgängliga parametrar.
> Du bör inte uttryckligen ange dem i fältet parametrar.

Tabellen nedan beskrivs de olika metoder som du kan anpassa en synlig cmdlet eller funktion.
Du kan blanda och matchar någon av de nedan i den **VisibleCmdlets** fält.

|                                           Exempel                                           |                                                             Användningsfall                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `'My-Func'` eller `@{ Name = 'My-Func' }`                                                      | Tillåter användaren att köra `My-Func` utan begränsningar på parametrarna.                                                      |
| `'MyModule\My-Func'`                                                                        | Tillåter användaren att köra `My-Func` från modulen `MyModule` utan begränsningar på parametrarna.                           |
| `'My-*'`                                                                                    | Gör att användaren kan köra alla cmdlet eller funktion med verbet `My`.                                                                 |
| `'*-Func'`                                                                                  | Gör att användaren kan köra alla cmdlet eller funktion med substantivet `Func`.                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | Tillåter användaren att köra `My-Func` med den `Param1` och `Param2` parametrar. Vilket värde som kan anges till parametrar.          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | Tillåter användaren att köra `My-Func` med den `Param1` parametern. Endast ”Value1” och ”Value2” kan anges för parametern.        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | Tillåter användaren att köra `My-Func` med den `Param1` parametern. Ett värde som börjar med ”contoso” kan anges för parametern. |

> [!WARNING]
> Metodtips för säkerhet rekommenderas inte att använda jokertecken när du definierar synliga cmdletar eller funktioner. I stället en lista med varje betrodd kommando för att kontrollera att inga andra kommandon som delar samma namngivningsschemat oavsiktligt har behörighet.

Du kan inte använda både en **ValidatePattern** och **ValidateSet** till samma cmdlet eller funktion.

Om du gör den **ValidatePattern** åsidosätter den **ValidateSet**.

Mer information om **ValidatePattern**, Kolla in [detta *Hey, Scripting Guy!* publicera](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) och [PowerShell reguljära uttryck](/powershell/module/microsoft.powershell.core/about/about_regular_expressions)Referensinnehåll.

### <a name="allowing-external-commands-and-powershell-scripts"></a>Vilket gör att externa kommandon och PowerShell-skript

Om du vill tillåta användare att köra körbara filer och PowerShell-skript (.ps1) i en JEA-session, du måste lägga till den fullständiga sökvägen till varje program i den **VisibleExternalCommands** fält.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Om möjligt, har cmdlet eller funktion som motsvarar för eventuella externa körbara filer du auktoriserar eftersom du kontroll över de parametrar som tillåts med PowerShell-cmdletar och funktioner för att använda PowerShell.

Många körbara filer kan du läsa det aktuella tillståndet och ändra den genom att ange olika parametrar.

Anta exempelvis att rollen för fil serveradministratören som hanterar nätverksresurser som finns på ett system. Ett sätt att hantera filresurser är att använda `net share`. Dock tillåter **net.exe** initieras eftersom användaren kan använda kommandot för att få administratörsprivilegier med `net group Administrators unprivilegedjeauser /add`. Ett säkrare alternativ är att tillåta [Get-SmbShare](/powershell/module/smbshare/get-smbshare), vilket ger samma resultat men har en mycket mer begränsad omfattning.

När du gör externa kommandon tillgängliga för användare i en JEA-session kan du alltid ange den fullständiga sökvägen till den körbara filen. Detta förhindrar att körningen av på samma sätt namngivna och potentiellt skadliga program som finns någon annanstans i systemet.

### <a name="allowing-access-to-powershell-providers"></a>Att tillåta åtkomst till PowerShell-providers

Som standard finns inga PowerShell-providers i JEA-sessioner. Detta minskar risken för känslig information och konfigurationsinställningar som avslöjas för anslutande användaren.

Om det behövs kan du tillåta åtkomst till PowerShell-providers med hjälp av den `VisibleProviders` kommando. En fullständig lista över providers, köra `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Överväg att skriva en egen funktion som fungerar med providern för användarens räkning för enkla uppgifter som kräver åtkomst till filsystemet, registret, certifikatarkivet eller andra leverantörer av känslig. Funktioner, cmdletar och externa program som är tillgängliga i en JEA-session är inte samma begränsningar som JEA. De kan komma åt valfri provider som standard. Överväga att använda den [enheten](session-configurations.md#user-drive) när kopierar filer till eller från en JEA-slutpunkt krävs.

### <a name="creating-custom-functions"></a>Skapa anpassade funktioner

Du kan skapa egna funktioner i en roll funktionen fil att förenkla komplexa uppgifter för dina slutanvändare. Anpassade funktioner är också användbara när du behöver avancerade validering av logik för cmdleten parametervärden. Du kan skriva enkla funktioner i den **FunctionDefinitions** fält:

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
> Glöm inte att lägga till namnet på din anpassade funktioner till den **VisibleFunctions** fältet så att de kan köras av JEA-användare.

Brödtext (skriptblock) för egna funktioner körs i standardläget för språk för systemet och är inte begränsningar för JEAS språk. Det innebär att funktioner kan komma åt filsystem och register och köra kommandon som inte görs visas i filen roll funktionen. Var noga med för att undvika att köra godtycklig kod när du använder parametrar. Undvika rörnät indata från användaren direkt till cmdlets som `Invoke-Expression`.

I exemplet ovan, Observera att det fullständigt kvalificerade modulnamnet (FQMN) `Microsoft.PowerShell.Utility\Select-Object` användes i stället för snabbformat `Select-Object`.
Funktionerna som definieras i rollen funktionsfiler omfattas fortfarande JEA-sessioner,-omfattning som innehåller funktioner för proxy JEA skapar för att begränsa befintliga kommandon.

Som standard `Select-Object` är en begränsad cmdlet i alla JEA-sessioner som inte tillåter valet av godtycklig egenskaper för objekt. Du använder den obegränsad `Select-Object` i funktioner, måste du uttryckligen begära detta fullständigt implementerat med hjälp av FQMN. En begränsad cmdlet i en JEA-session har samma begränsningar när anropas från en funktion. Mer information finns i [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence).

Om du skriver flera anpassade funktioner, är det mer praktiskt att placera dem i en modul för PowerShell-skript. Du gör dessa funktioner synliga i JEA-session med den **VisibleFunctions** fältet precis som med inbyggda och tredjeparts-moduler.

För fliken slutförande ska fungera korrekt i JEA-sessioner du inkludera den inbyggda funktionen `tabexpansion2` i den **VisibleFunctions** lista.

## <a name="place-role-capabilities-in-a-module"></a>Placera rollfunktioner i en modul

För PowerShell för att hitta en roll funktionen fil, måste den vara lagrad i en **RoleCapabilities** mapp i en PowerShell-modul. Modulen kan lagras i valfri mapp som ingår i den `$env:PSModulePath` miljövariabeln, men du bör inte placera den i System32 eller en mapp där den ej betrodda, ansluter användare kan ändra filerna. Nedan visas ett exempel för att skapa en grundläggande PowerShell skriptmodul kallas **ContosoJEA** i den `$env:ProgramFiles` sökväg.

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

## <a name="updating-role-capabilities"></a>Uppdaterar rollfunktioner

Du kan redigera en roll funktionen fil för att uppdatera inställningarna när som helst. Alla nya JEA-sessioner som startas när funktionen för rollen har uppdaterats visas de ändrade funktionerna.

Det är därför det är så viktigt att kontrollera åtkomst till mappen rollen funktioner. Endast betrodda administratörer ska kunna ändra rollen funktionsfiler. Om en icke betrodd användare kan ändra rollen funktionsfiler, ge enkelt sig själva åtkomst till cmdletar för att de kan utöka sina privilegier.

Kontrollera att lokalt System har läsbehörighet till rollen funktionsfiler och som innehåller moduler för administratörer som vill låsa åtkomst till rollfunktioner för.

## <a name="how-role-capabilities-are-merged"></a>Hur rollfunktioner slås samman

Användare som beviljas åtkomst till alla matchande rollfunktioner i den [session konfigurationsfilen](session-configurations.md) när de kommer in en JEA-session. JEA försöker ge användaren den mest Tillåtande uppsättningen kommandon som tillåts av någon av rollerna.

### <a name="visiblecmdlets-and-visiblefunctions"></a>VisibleCmdlets och VisibleFunctions

Den mest avancerade merge logiken påverkar cmdletar och funktioner som kan ha sina parametrar och parametervärden som är begränsad i JEA.

Reglerna är följande:

1. Om en cmdlet syns bara i en enda roll, är det synliga för användaren med tillämpliga parametern villkor.
2. Om en cmdlet syns i mer än en roll, och varje roll har samma begränsningar i cmdleten, är cmdlet: en synliga för användaren med dessa begränsningar.
3. Om en cmdlet syns i mer än en roll, och varje roll kan en annan uppsättning parametrar, visas cmdlet: en och alla de parametrar som definierats för varje roll för användaren.
   Om en roll inte har begränsningar i parametrarna, är alla parametrar tillåtna.
4. Om en roll definierar verifiera set eller verifiera mönster för en cmdlet-parameter och annan roll kan parametern men begränsar inte parametervärdena, ignoreras verifiera set eller mönster.
5. Om en uppsättning verifiera har definierats för samma cmdlet-parametern i mer än en roll, tillåts alla värden från alla verifiera uppsättningar.
6. Om ett verifiera mönster har definierats för samma cmdlet-parametern i mer än en roll, är värden som matchar någon av mönster som tillåtna.
7. Om en uppsättning verifiera har definierats i en eller flera roller och ett verifiera mönster har definierats i en annan roll för samma cmdlet-parameter, verifiera uppsättningen ignoreras och regeln (6) gäller för de återstående verifiera mönster.

Nedan visas ett exempel på hur roller slås samman enligt reglerna:

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

Alla andra fält i filen roll funktionen läggs till i en kumulativ uppsättning med tillåtna externa kommandon, alias, leverantörer och startskript. Alla kommandot, alias, provider eller skript som är tillgängliga i en roll-funktionen är tillgänglig för JEA-användaren.

Var noga med att kontrollera att en kombinerad uppsättning-provider från en roll funktions- och kommandon/cmdlets/funktioner från en annan inte ge användarna oavsiktlig åtkomst till systemresurser.
Om en roll kan till exempel den `Remove-Item` cmdlet och ett annat kan den `FileSystem` provider, du kan vara utsatta för en JEA-användare som tar bort godtyckliga filer på datorn. Mer information om hur du identifierar användarnas gällande behörigheter finns i den [granskning JEA](audit-and-report.md) artikeln.

## <a name="next-steps"></a>Nästa steg

[Skapa en konfigurationsfil för session](session-configurations.md)
