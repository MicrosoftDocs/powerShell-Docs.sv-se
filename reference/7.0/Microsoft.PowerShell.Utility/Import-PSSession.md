---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: c64a59300cdaffe71de04c7843bf644df49530d5
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390124"
---
# Import-PSSession

## SAMMANFATTNING
Importerar kommandon från en annan session till den aktuella sessionen.

## SYNTAX

```
Import-PSSession [-Prefix <String>] [-DisableNameChecking] [[-CommandName] <String[]>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-FormatTypeName] <String[]>]
 [-Certificate <X509Certificate2>] [-Session] <PSSession> [<CommonParameters>]
```

## BESKRIVNING

`Import-PSSession`Cmdleten importerar kommandon, till exempel cmdlets, Functions och alias, från en PSSession på en lokal eller fjärran sluten dator till den aktuella sessionen. Du kan importera alla kommandon som `Get-Command` cmdleten kan hitta i PSSession.

Använd ett `Import-PSSession` kommando för att importera kommandon från ett anpassat gränssnitt, till exempel ett Microsoft Exchange Server-gränssnitt eller från en-session som innehåller Windows PowerShell-moduler och snapin-moduler eller andra element som inte finns i den aktuella sessionen.

Om du vill importera kommandon använder du först `New-PSSession` cmdleten för att skapa en PSSession. Använd sedan `Import-PSSession` cmdleten för att importera kommandona. Som standard `Import-PSSession` importerar alla kommandon utom kommandon som har samma namn som kommandon i den aktuella sessionen. Om du vill importera alla kommandon använder du parametern **AllowClobber** .

Du kan använda importerade kommandon precis som med alla kommandon i sessionen. När du använder ett importerat kommando körs den importerade delen av kommandot implicit i den session som det importerades från. Fjärråtgärder hanteras dock helt av Windows PowerShell. Du behöver inte ens vara medveten om dem, förutom att du måste hålla anslutningen till den andra sessionen (PSSession) öppen. Om du stänger den är de importerade kommandona inte längre tillgängliga.

Eftersom importerade kommandon kan ta längre tid att köra än lokala kommandon, `Import-PSSession` lägger till en **AsJob** -parameter till alla importerade kommandon. Med den här parametern kan du köra kommandot som ett bakgrunds jobb i Windows PowerShell. Mer information finns i artikeln [om jobb](../Microsoft.PowerShell.Core/about/about_Jobs.md).

När du använder `Import-PSSession` lägger Windows PowerShell till de importerade kommandona i en tillfällig modul som bara finns i din session och returnerar ett objekt som representerar modulen. Använd cmdleten för att skapa en beständig modul som du kan använda i framtida sessioner `Export-PSSession` .

`Import-PSSession`Cmdleten använder funktionen implicit fjärr kommunikation i Windows PowerShell. När du importerar kommandon till den aktuella sessionen körs de implicit i den ursprungliga sessionen eller i en liknande session på den ursprungliga datorn.

Från och med Windows PowerShell 3,0 kan du använda `Import-Module` cmdleten för att importera moduler från en fjärrsession till den aktuella sessionen. Den här funktionen använder implicit fjärr kommunikation. Det motsvarar att använda `Import-PSSession` för att importera valda moduler från en fjärrsession till den aktuella sessionen.

## EXEMPEL

### Exempel 1: importera alla kommandon från en PSSession

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

Det här kommandot importerar alla kommandon från en PSSession på Server01-datorn till den aktuella sessionen, förutom kommandon som har samma namn som kommandon i den aktuella sessionen.

Eftersom det här kommandot inte använder **commandname** -parametern importeras även all formatering som krävs för de importerade kommandona.

### Exempel 2: importera kommandon som slutar med en angiven sträng

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

Kommandona importerar kommandona med namn som slutar med "-test" från en PSSession till den lokala sessionen, och sedan visar de hur man använder en importerad cmdlet.

Det första kommandot använder `New-PSSession` cmdleten för att skapa en PSSession. Den sparar PSSession i `$S` variabeln.

Det andra kommandot använder `Import-PSSession` cmdleten för att importera kommandon från PSSession i `$S` till den aktuella sessionen. Parametern **commandname** används för att ange kommandon med parametern test Substantiv och parametern **FormatTypeName** för att importera formateringsinformationen för test kommandona.

De tredje och fjärde kommandona använder de importerade kommandona i den aktuella sessionen. Eftersom importerade kommandon faktiskt läggs till i den aktuella sessionen använder du den lokala syntaxen för att köra dem. Du behöver inte använda `Invoke-Command` cmdleten för att köra ett importerat kommando.

### Exempel 3: importera cmdletar från en PSSession

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

Det här exemplet visar att du kan använda importerade cmdlets på samma sätt som du använder lokala cmdlets.

Kommandona importerar `New-Test` `Get-Test` cmdletarna och från en PSSession på Server01-datorn och `Set-Test` cmdleten från en PSSession på Server02-datorn.

Även om cmdletarna har importer ATS från olika PSSessions kan du skicka ett objekt från en cmdlet till en annan utan fel.

### Exempel 4: kör ett importerat kommando som bakgrunds jobb

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

Det här exemplet visar hur du kör ett importerat kommando som bakgrunds jobb.

Eftersom importerade kommandon kan ta längre tid att köra än lokala kommandon, `Import-PSSession` lägger till en **AsJob** -parameter till alla importerade kommandon. Med parametern **AsJob** kan du köra kommandot som ett bakgrunds jobb.

Det första kommandot skapar en PSSession på Server01-datorn och sparar PSSession-objektet i `$S` variabeln.

Det andra kommandot använder `Import-PSSession` för att importera test-cmdletarna från PSSession i `$S` till den aktuella sessionen.

Det tredje kommandot använder parametern **AsJob** för den importerade `New-Test` cmdleten för att köra ett `New-Test` kommando som bakgrunds jobb. Kommandot sparar jobbobjektet som `New-Test` returneras i `$batch` variabeln.

Det fjärde kommandot använder `Receive-Job` cmdleten för att hämta resultatet av jobbet i `$batch` variabeln.

### Exempel 5: importera cmdlets och Functions från en Windows PowerShell-modul

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

Det här exemplet visar hur du importerar cmdlets och Functions från en Windows PowerShell-modul på en fjärrdator till den aktuella sessionen.

Det första kommandot skapar en PSSession på Server01-datorn och sparar den i `$S` variabeln.

Det andra kommandot använder `Invoke-Command` cmdleten för att köra ett `Import-Module` kommando i PSSession i `$S` .

Normalt läggs modulen till i alla sessioner med ett `Import-Module` kommando i en Windows PowerShell-profil, men profiler körs inte i PSSessions.

Det tredje kommandot använder **modulen modul** för `Import-PSSession` för att importera cmdlets och Functions i modulen till den aktuella sessionen.

### Exempel 6: skapa en modul i en temporär fil

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

Det här exemplet visar att `Import-PSSession` skapar en modul i en temporär fil på disk. Det visar också att alla kommandon konverteras till funktioner innan de importeras till den aktuella sessionen.

Kommandot använder `Import-PSSession` cmdleten för att importera en `Get-Date` cmdlet och en SearchHelp-funktion till den aktuella sessionen.

`Import-PSSession`Cmdleten returnerar ett **PSModuleInfo** -objekt som representerar den temporära modulen. Värdet för egenskapen **Path** visar att `Import-PSSession` en psm1-fil har skapats på en tillfällig plats. Egenskapen **ExportedFunctions** visar att `Get-Date` cmdleten och funktionen SearchHelp både har importer ATS som funktioner.

### Exempel 7: köra ett kommando som är dolt av ett importerat kommando

```
PS C:\> Import-PSSession $S -CommandName Get-Date -FormatTypeName * -AllowClobber

PS C:\> Get-Command Get-Date -All

CommandType   Name       Definition
-----------   ----       ----------
Function      Get-Date   ...
Cmdlet        Get-Date   Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>]

PS C:\> Get-Date
09074

PS C:\> (Get-Command -Type Cmdlet -Name Get-Date).PSSnapin.Name
Microsoft.PowerShell.Utility

PS C:\> Microsoft.PowerShell.Utility\Get-Date
Sunday, March 15, 2009 2:08:26 PM
```

Det här exemplet visar hur du kör ett kommando som är dolt av ett importerat kommando.

Det första kommandot importerar en `Get-Date` cmdlet från PSSession i `$S` variabeln. Eftersom den aktuella sessionen innehåller en `Get-Date` cmdlet krävs **AllowClobber** -parametern i kommandot.

Det andra kommandot använder parametern **all** för `Get-Command` cmdlet: en för att hämta alla `Get-Date` kommandon i den aktuella sessionen. Utdata visar att sessionen innehåller den ursprungliga `Get-Date` cmdleten och en `Get-Date` funktion. `Get-Date`Funktionen kör den importerade `Get-Date` cmdleten i PSSession i `$S` .

Det tredje kommandot kör ett `Get-Date` kommando. Eftersom funktioner prioriteras över cmdletar kör Windows PowerShell den importerade `Get-Date` funktionen, som returnerar ett Juliansk-datum.

De fjärde och femte kommandona visar hur du använder ett kvalificerat namn för att köra ett kommando som är dolt av ett importerat kommando.

Det fjärde kommandot hämtar namnet på Windows PowerShell-snapin-modulen som lade till den ursprungliga `Get-Date` cmdleten i den aktuella sessionen.

Det femte kommandot använder det Snap-i-kvalificerade namnet för `Get-Date` cmdleten för att köra ett `Get-Date` kommando.

Mer information om kommando prioritet och dolda kommandon finns [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).

### Exempel 8: importera kommandon som har en angiven sträng i sina namn

```
PS C:\> Import-PSSession -Session $S -CommandName **Item** -AllowClobber
```

Det här kommandot importerar kommandon vars namn innehåller objekt från PSSession i `$S` . Eftersom kommandot innehåller parametern **commandname** men inte parametern **FormatTypeData** , importeras bara kommandot.

Använd det här kommandot när du använder `Import-PSSession` för att köra ett kommando på en fjärrdator och du redan har format data för kommandot i den aktuella sessionen.

### Exempel 9: Använd parametern module för att identifiera vilka kommandon som har importer ATS till sessionen

```
PS C:\> $M = Import-PSSession -Session $S -CommandName *bits* -FormatTypeName *bits*
PS C:\> Get-Command -Module $M
CommandType     Name
-----------     ----
Function        Add-BitsFile
Function        Complete-BitsTransfer
Function        Get-BitsTransfer
Function        Remove-BitsTransfer
Function        Resume-BitsTransfer
Function        Set-BitsTransfer
Function        Start-BitsTransfer
Function        Suspend-BitsTransfer
```

Det här kommandot visar hur du använder **modulen modul** för `Get-Command` för att ta reda på vilka kommandon som har importer ATS till sessionen med ett `Import-PSSession` kommando.

Det första kommandot använder `Import-PSSession` cmdleten för att importera kommandon vars namn innehåller "bitar" från PSSession i `$S` variabeln. `Import-PSSession`Kommandot returnerar en tillfällig modul och kommandot sparar modulen i `$m` variabeln.

Det andra kommandot använder `Get-Command` cmdleten för att hämta de kommandon som exporteras av modulen i `$M` variabeln.

Parametern **module** använder ett sträng värde, vilket är utformat för modulnamnet. Men när du skickar ett modul-objekt använder Windows PowerShell metoden **toString** i objektet module, som returnerar modulnamnet.

`Get-Command`Kommandot motsvarar `Get-Command $M.Name` ".

## PARAMETRAR

### -AllowClobber

Anger att denna cmdlet importerar de angivna kommandona, även om de har samma namn som kommandon i den aktuella sessionen.

Om du importerar ett kommando med samma namn som ett kommando i den aktuella sessionen, döljer det importerade kommandot eller ersätter de ursprungliga kommandona. Mer information finns i [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).

Som standard `Import-PSSession` importerar inte kommandon som har samma namn som kommandon i den aktuella sessionen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Argument List

Anger en matris med kommandon som resulterar från att använda de angivna argumenten (parameter värden).

För att till exempel importera `Get-Item` kommandots variant i certifikatet (cert:) enhet i PSSession i `$S` skriver du `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Certifikat

Anger det klient certifikat som används för att signera format-filer (* .Format.ps1XML) eller psm1 (.) i den temporära modul som `Import-PSSession` skapas.

Ange en variabel som innehåller ett certifikat eller ett kommando eller uttryck som hämtar certifikatet.

Om du vill söka efter ett certifikat använder du `Get-PfxCertificate` cmdleten eller använder `Get-ChildItem` cmdleten i certifikatet (cert:) kombinationsenhet. Om certifikatet inte är giltigt eller inte har tillräcklig behörighet, Miss lyckas kommandot.

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – CommandName

Anger kommandon med angivna namn eller namn mönster. Jokertecken är tillåtna. Använd **commandname** eller dess alias, **namn**.

Som standard `Import-PSSession` importerar alla kommandon från sessionen, förutom kommandon som har samma namn som kommandon i den aktuella sessionen. Detta förhindrar att importerade kommandon döljer eller ersätter kommandon i sessionen. Om du vill importera alla kommandon, även de som döljer eller ersätter andra kommandon, använder du parametern **AllowClobber** .

Om du använder parametern **commandname** importeras inte formateringsattribut för kommandona om du inte använder parametern **FormatTypeName** . På liknande sätt importeras inga kommandon om du använder parametern **FormatTypeName** , om du inte använder parametern **commandname** .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandType

Anger typ av kommando objekt. Standardvärdet är cmdlet. Använd **CommandType** eller dess alias och **Skriv**. De acceptabla värdena för den här parametern är:

- Aliasuppsättning. Windows PowerShell-alias i fjärrsessionen.
- Vissa. Cmdlets och Functions i fjärrsessionen.
- Applicering. Alla filer utom Windows-PowerShell filer i Sök vägarna som anges i miljövariabeln PATH ( `$env:path` ) i fjärrsessionen, inklusive. txt-,. exe-och. dll-filer.
- Kommandon. Cmdletarna i fjärrsessionen. "Cmdlet" är standardvärdet.
- ExternalScript. . Ps1-filerna i Sök vägarna som anges i miljövariabeln PATH ( `$env:path` ) i fjärrsessionen.
- Filter och funktion. Windows PowerShell-funktionerna i fjärrsessionen.
- Över. Skript block i fjärrsessionen.

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableNameChecking

Anger att denna cmdlet undertrycker meddelandet som varnar dig när du importerar en cmdlet eller funktion vars namn innehåller ett ej godkänt verb eller ett otillåtet Character.

Som standard visas följande varnings meddelande när en modul som du importerar exporterar cmdlets eller funktioner som har icke godkända verb i sina namn:

"Varning! vissa importerade kommando namn innehåller icke godkända verb som kan göra dem mindre synliga. Använd verbose-parametern för mer information eller Skriv `Get-Verb` om du vill visa en lista över godkända verb. "

Det här meddelandet är bara en varning. Den kompletta modulen importeras fortfarande, inklusive kommandon som inte överensstämmer. Även om meddelandet visas för modulen användare, bör namngivnings problemet åtgärdas av den som skapade modulen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatTypeName

Anger formateringsregler för de angivna Microsoft .NET Ramverks typerna.
Ange typ namn.
Jokertecken är tillåtna.

Värdet för den här parametern måste vara namnet på en typ som returneras av ett `Get-FormatData` kommando i den session som kommandona importeras från. Om du vill hämta alla formaterings data i fjärrsessionen skriver du `*` .

Om kommandot inte innehåller någon av **commandname** -eller **FormatTypeName** -parametern `Import-PSSession` importeras instruktioner för alla .NET Framework typer som returneras av ett `Get-FormatData` kommando i fjärrsessionen.

Om du använder parametern **FormatTypeName** importeras inga kommandon om du inte använder parametern **commandname** .

Om du använder parametern **commandname** importeras inte filerna för kommandona om du inte använder parametern **FormatTypeName** .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedModule

Anger moduler med namn som anges i form av **ModuleSpecification** -objekt (beskrivs i avsnittet anmärkningar i ModuleSpecification- [konstruktorn (hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) i PowerShell SDK. Parametern **FullyQualifiedModule** accepterar till exempel ett modulnamn som anges i formatet:

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}` eller
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`.

**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt.

Det går inte att ange parametern **FullyQualifiedModule** i samma kommando som en **modul** -parameter. De två parametrarna kan inte anges samtidigt.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Modul

Anger och en matris med kommandon i Windows PowerShell snapin-moduler och moduler. Ange namnet på snapin-modulen och-modulen. Jokertecken är inte tillåtna.

`Import-PSSession` Det går inte att importera providrar från en snapin-modul.

Mer information finns i [about_PSSnapins](/powershell/module/Microsoft.PowerShell.Core/About/about_PSSnapins) och [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Prefix

Anger ett prefix till substantiven i namnen på importerade kommandon.

Använd den här parametern för att undvika namn konflikter som kan uppstå när olika kommandon i sessionen har samma namn.

Om du till exempel anger prefixet Remote och sedan importerar en `Get-Date` cmdlet, är cmdleten känd i sessionen som `Get-RemoteDate` och den förväxlas inte med den ursprungliga `Get-Date` cmdleten.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Session

Anger **PSSession** som cmdletarna importeras från. Ange en variabel som innehåller ett session-objekt eller ett kommando som hämtar ett sessionsobjekt, till exempel ett `New-PSSession` eller- `Get-PSSession` kommando. Du kan bara ange en session. Den här parametern är obligatorisk.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Det går inte att skicka pipe-objekt till denna cmdlet.

## UTDATA

### System. Management. Automation. PSModuleInfo

`Import-PSSession` returnerar samma modul-objekt som `New-Module` och `Get-Module` cmdlets returnerar.
Den importerade modulen är dock tillfällig och finns bara i den aktuella sessionen. Använd cmdleten för att skapa en permanent modul på disk `Export-PSSession` .

## ANTECKNINGAR

- `Import-PSSession` förlitar sig på PowerShell-infrastrukturen för fjärr kommunikation. Om du vill använda denna cmdlet måste datorn konfigureras för WS-Management fjärr kommunikation. Mer information finns i [about_Remote](../Microsoft.PowerShell.Core/about/about_Remote.md) och [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).
- `Import-PSSession` importerar inte variabler eller PowerShell-leverantörer.
- När du importerar kommandon som har samma namn som kommandon i den aktuella sessionen kan de importerade kommandona dölja alias, funktioner och cmdlets i sessionen och de kan ersätta funktioner och variabler i sessionen. Använd parametern **prefix** för att förhindra namn konflikter. Mer information finns i [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).
- `Import-PSSession` konverterar alla kommandon till funktioner innan de importeras. Det innebär att importerade kommandon fungerar lite annorlunda än om de behåller sin ursprungliga kommando typ. Om du t. ex. importerar en cmdlet från en PSSession och sedan importerar en cmdlet med samma namn från en modul eller snapin-modul, körs den cmdlet som importeras från PSSession alltid som standard eftersom Functions prioriteras över cmdletar. Om du importerar ett alias till en-session som har ett alias med samma namn, används alltid det ursprungliga aliaset, eftersom alias har företräde framför funktioner. Mer information finns i [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).
- `Import-PSSession` använder `Write-Progress` cmdleten för att visa förloppet för kommandot. Du kan se förlopps indikatorn när kommandot körs.
- För att hitta de kommandon som ska importeras `Import-PSSession` använder `Invoke-Command` cmdleten för att köra ett `Get-Command` kommando i PSSession. För att hämta formatering av data för kommandona används `Get-FormatData` cmdleten. Du kan se fel meddelanden från dessa cmdletar när du kör ett `Import-PSSession` kommando. `Import-PSSession`Det går inte heller att importera kommandon från en PSSession som inte innehåller `Get-Command` `Get-FormatData` `Select-Object` cmdletarna,, och `Get-Help` .
- Importerade kommandon har samma begränsningar som andra fjärrkommandon, inklusive möjligheten att starta ett program med ett användar gränssnitt, t. ex. anteckningar.
- Eftersom Windows PowerShell-profiler inte körs i PSSessions är kommandona som en profil lägger till i en session inte tillgängliga för `Import-PSSession` . Om du vill importera kommandon från en profil använder du ett `Invoke-Command` kommando för att köra profilen i PSSession manuellt innan du importerar kommandon.
- Den temporära modul som `Import-PSSession` skapar kan innehålla en formateringsinformation, även om kommandot inte importerar formaterings data. Om kommandot inte importerar dataformaterade data kommer eventuella filer som skapas inte att innehålla formatering.
- För att kunna använda `Import-PSSession` kan körnings principen i den aktuella sessionen inte vara begränsad eller AllSigned, eftersom den temporära modul som `Import-PSSession` skapar innehåller osignerade skriptfiler som är förbjudna av dessa principer. Om du vill använda `Import-PSSession` utan att ändra körnings principen för den lokala datorn använder du **omfattnings** parametern för `Set-ExecutionPolicy` att ange en mindre begränsande körnings princip för en enda process.
- I Windows PowerShell 2,0 innehåller hjälp avsnitten för kommandon som importeras från en annan session inte det prefix som du tilldelar med hjälp av parametern **prefix** . Om du vill ha hjälp med ett importerat kommando i Windows PowerShell 2,0 använder du det ursprungliga kommando namnet (icke-förfixet).

## RELATERADE LÄNKAR

[Exportera – PSSession](Export-PSSession.md)
