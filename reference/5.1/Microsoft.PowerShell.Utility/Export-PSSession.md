---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-PSSession
ms.openlocfilehash: 67501a78ba577f63c97e595f4bacd28160fea416
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265089"
---
# Export-PSSession

## SAMMANFATTNING

Exporterar kommandon från en annan session och sparar dem i en PowerShell-modul.

## SYNTAX

```
Export-PSSession [-Session] <PSSession> [-OutputModule] <string> [[-CommandName] <string[]>]
 [[-FormatTypeName] <string[]>] [-Force] [-Encoding <string>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <string[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-Certificate <X509Certificate2>]
 [<CommonParameters>]
```

## BESKRIVNING

`Export-PSSession`Cmdlet: en hämtar cmdlets, functions, alias och andra kommando typer från en annan PowerShell-session (PSSession) på en lokal eller fjärran sluten dator och sparar dem i en PowerShell-modul. Använd cmdleten om du vill lägga till kommandon från modulen till den aktuella sessionen `Import-Module` .

Till skillnad `Import-PSSession` från, som importerar kommandon från en annan PSSession till den aktuella sessionen, `Export-PSSession` sparar kommandona i en modul. Kommandona importeras inte till den aktuella sessionen.

Om du vill exportera kommandon använder du `New-PSSession` cmdleten för att skapa en PSSession som har de kommandon som du vill exportera. Använd sedan `Export-PSSession` cmdlet: en för att exportera kommandona.

För att förhindra kommando namns konflikter, är standardvärdet för `Export-PSSession` att exportera alla kommandon, förutom kommandon som finns i den aktuella sessionen. Du kan använda parametern **commandname** för att ange vilka kommandon som ska exporteras.

`Export-PSSession`Cmdleten använder funktionen implicit fjärr kommunikation i PowerShell. När du importerar kommandon till den aktuella sessionen körs de implicit i den ursprungliga sessionen eller i en liknande session på den ursprungliga datorn.

## EXEMPEL

### Exempel 1: exportera kommandon från en PSSession

I det här exemplet skapas en ny PSSession från den lokala datorn till Server01-datorn. Alla kommandon, förutom de som finns i den aktuella sessionen, exporteras till modulen med namnet Server01 på den lokala datorn. Exporten innehåller formaterings data för kommandona.

```powershell
$S = New-PSSession -ComputerName Server01
Export-PSSession -Session $S -OutputModule Server01
```

`New-PSSession`Kommandot skapar en PSSession på Server01-datorn. PSSession lagras i `$S` variabeln. `Export-PSSession`Kommandot exporterar `$S` variabelns kommandon och formaterar data till Server01-modulen.

### Exempel 2: exportera get-och set-kommandona

I det här exemplet exporteras alla `Get` `Set` kommandon från en server.

```powershell
$S = New-PSSession -ConnectionUri https://exchange.microsoft.com/mailbox -Credential exchangeadmin01@hotmail.com -Authentication Negotiate
Export-PSSession -Session $S -Module exch* -CommandName Get-*, Set-* -FormatTypeName * -OutputModule $PSHOME\Modules\Exchange -Encoding ASCII
```

Dessa kommandon exporterar `Get` och- `Set` kommandon från en Microsoft Exchange Server-snapin-modul på en fjärrdator till en Exchange-modul i `$PSHOME\Modules` katalogen på den lokala datorn.
Att placera modulen i `$PSHOME\Modules` katalogen gör den tillgänglig för alla användare av datorn.

### Exempel 3: exportera kommandon från en fjärrdator

Det här exemplet exporterar cmdletar från en PSSession på en fjärrdator och sparar dem i en modul på den lokala datorn. Cmdletarna från modulen läggs till i den aktuella sessionen så att de kan användas.

```powershell
$S = New-PSSession -ComputerName Server01 -Credential Server01\User01
Export-PSSession -Session $S -OutputModule TestCmdlets -Type Cmdlet -CommandName *test* -FormatTypeName *
Remove-PSSession $S
Import-Module TestCmdlets
Get-Help Test*
Test-Files
```

`New-PSSession`Kommandot skapar en PSSession på Server01-datorn och sparar den i `$S` variabeln. `Export-PSSession`Kommandot exporterar de cmdletar vars namn börjar med test från PSSession i `$S` till TestCmdlets-modulen på den lokala datorn.

`Remove-PSSession`Cmdleten tar bort PSSession i `$S` från den aktuella sessionen. Det här kommandot visar att PSSession inte behöver vara aktiv för att använda de kommandon som har importer ATS från sessionen. `Import-Module`Cmdleten lägger till cmdletarna i TestCmdlets-modulen till den aktuella sessionen. Kommandot kan köras i alla sessioner när som helst.

`Get-Help`Cmdlet: en får hjälp med cmdletar vars namn börjar med test. När du har lagt till kommandon i en modul i den aktuella sessionen kan du använda `Get-Help` `Get-Command` cmdletarna och för att lära dig mer om de importerade kommandona. `Test-Files`Cmdleten exporterades från Server01-datorn och lades till i sessionen. `Test-Files`Cmdleten körs i en fjärran sluten session på den dator där kommandot importerades. PowerShell skapar en session med information som lagras i TestCmdlets-modulen.

### Exempel 4: exportera och clobber kommandon i den aktuella sessionen

I det här exemplet exporteras kommandon som lagras i en variabel till den aktuella sessionen.

```powershell
Export-PSSession -Session $S -AllowClobber -OutputModule AllCommands
```

Detta `Export-PSSession` kommando exporterar alla kommandon och all formatering av data från PSSession i `$S` variabeln till den aktuella sessionen. Parametern **AllowClobber** innehåller kommandon med samma namn som kommandon i den aktuella sessionen.

### Exempel 5: exportera kommandon från en stängd PSSession

Det här exemplet visar hur du kör de exporterade kommandona med särskilda alternativ när PSSession som skapade de exporterade kommandona är stängd.

Om den ursprungliga fjärrsessionen stängs när en modul importeras, kommer modulen att använda alla öppna fjärrsessioner som ansluter till den ursprungliga datorn. Om det inte finns någon aktuell session för den ursprungliga datorn kommer modulen att återupprätta en session.

Om du vill köra exporterade kommandon med särskilda alternativ i en fjärrsession måste du skapa en fjärrsession med dessa alternativ innan du importerar modulen. Använd `New-PSSession` cmdleten med parametern **SessionOption**

```powershell
$Options = New-PSSessionOption -NoMachineProfile
$S = New-PSSession -ComputerName Server01 -SessionOption $Options
Export-PSSession -Session $S -OutputModule Server01
Remove-PSSession $S
New-PSSession -ComputerName Server01 -SessionOption $Options
Import-Module Server01
```

`New-PSSessionOption`Cmdleten skapar ett **PSSessionOption** -objekt och sparar objektet i `$Options` variabeln. `New-PSSession`Kommandot skapar en PSSession på Server01-datorn.
Parametern **SessionOption** använder objektet som är lagrat i `$Options` . Sessionen lagras i `$S` variabeln.

`Export-PSSession`Cmdleten exporterar kommandon från PSSession i `$S` till Server01-modulen.
`Remove-PSSession`Cmdleten tar bort PSSession i `$S` variabeln.

`New-PSSession`Cmdleten skapar en ny PSSession som ansluter till Server01-datorn. Parametern **SessionOption** använder objektet som är lagrat i `$Options` . `Import-Module`Cmdleten importerar kommandona från Server01-modulen. Kommandona i modulen körs i mappen PSSession på Server01-datorn.

## PARAMETRAR

### -AllowClobber

Exporterar de angivna kommandona, även om de har samma namn som kommandon i den aktuella sessionen.

Om du exporterar ett kommando med samma namn som ett kommando i den aktuella sessionen, döljer det exporterade kommandot eller ersätter de ursprungliga kommandona. Mer information finns i [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).

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

Exporterar kommandots variant som resulterar från att de angivna argumenten används (parameter värden).

Till exempel för att exportera `Get-Item` kommandots variant i certifikatet (cert:) enhet i PSSession i `$S` skriver du `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .

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

Anger det klient certifikat som används för att signera format-filer (* .Format.ps1XML) eller psm1 (.) i den modul som `Export-PSSession` skapar. Ange en variabel som innehåller ett certifikat eller ett kommando eller uttryck som hämtar certifikatet.

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

Exporterar endast kommandon med angivna namn eller namn mönster. Jokertecken är tillåtna. Använd **commandname** eller dess alias, **namn**.

Som standard `Export-PSSession` exporterar alla kommandon från PSSession förutom kommandon som har samma namn som kommandon i den aktuella sessionen. Detta förhindrar att kommandon döljs eller ersätts av kommandon i den aktuella sessionen. Om du vill exportera alla kommandon, även de som döljer eller ersätter andra kommandon, använder du parametern **AllowClobber** .

Om du använder parametern **commandname** exporteras inte filerna för kommandona om du inte använder parametern **FormatTypeName** . Om du använder parametern **FormatTypeName** exporteras inte heller några kommandon om du inte använder parametern **commandname** .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: True
```

### -CommandType

Exporterar endast de angivna typerna av kommando objekt. Använd **CommandType** eller dess alias och **Skriv**.

De acceptabla värdena för den här parametern är följande:

- Aliasuppsättning. Alla PowerShell-alias i den aktuella sessionen.
- Vissa. Alla kommando typer. Det motsvarar `Get-Command -Name *` .
- Applicering. Alla filer förutom PowerShell-filer i sökvägar som anges i miljövariabeln PATH ( `$env:path` ), inklusive. txt-,. exe-och. dll-filer.
- Kommandon. Cmdletarna i den aktuella sessionen. Cmdlet är standard.
- Inställningarna. En PowerShell-konfiguration. Mer information finns i [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).
- ExternalScript. Alla. ps1-filer i Sök vägarna som anges i miljövariabeln PATH ( `$env:path` ).
- Filter och funktion. Alla PowerShell-funktioner.
- Över. Skript block i den aktuella sessionen.
- Arbets flöde. Ett PowerShell-arbetsflöde. Mer information finns i [about_Workflows](../PSWorkflow/About/about_Workflows.md).

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, All, Application, Cmdlet, Configuration, ExternalScript, Filter, Function, Script, Workflow

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Anger typ av kodning för mål filen. Standardvärdet är `UTF8`.

De acceptabla värdena för den här parametern är följande:

- `ASCII` Använder ASCII-teckenuppsättning (7-bitars).
- `BigEndianUnicode` Använder UTF-16 med big-endian byte-ordningen.
- `Default` Använder den kodning som motsvarar systemets aktiva tecken tabell.
- `OEM` Använder kodningen som motsvarar systemets aktuella OEM Code-sida.
- `Unicode` Använder UTF-16 med en liten-endian-order.
- `UTF7` Använder UTF-7.
- `UTF8` Använder UTF-8.
- `UTF32` Använder UTF-32 med en liten-endian-order.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: UTF8
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Skriver över en eller flera befintliga utdatafiler, även om filen har attributet skrivskyddad.

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

Exporterar bara formateringsregler för de angivna Microsoft .NET Ramverks typerna. Ange typ namn. Som standard `Export-PSSession` exporterar formaterings instruktioner för alla .NET Framework typer som inte finns i namn området **system. Management. Automation** .

Värdet för den här parametern måste vara namnet på en typ som returneras av ett `Get-FormatData` kommando i den session som kommandona importeras från. Om du vill hämta alla formaterings data i fjärrsessionen skriver du `*` .

Om du använder parametern **FormatTypeName** exporteras inga kommandon om du inte använder parametern **commandname** .

Om du använder parametern **commandname** exporteras inte filerna för kommandona om du inte använder parametern **FormatTypeName** .

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

Anger moduler med namn som anges i form av **ModuleSpecification** -objekt.
Se avsnittet anmärkningar i [ModuleSpecification-konstruktorn (hash)](https://msdn.microsoft.com/library/jj136290).

**FullyQualifiedModule** -parametern accepterar till exempel ett modulnamn som anges i något av följande format:

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt. Det går inte att ange parametern **FullyQualifiedModule** i samma kommando som en **modul** parameter. de två parametrarna kan inte anges samtidigt.

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

Exporterar endast kommandona i de angivna PowerShell-snapin-modulerna och modulerna. Ange namnet på snapin-modulen och-modulen. Jokertecken är inte tillåtna.

Mer information finns i `Import-Module` och [about_PSSnapins](../Microsoft.PowerShell.Core/About/about_PSSnapins.md).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputModule

Anger en valfri sökväg och ett namn för modulen som skapats av `Export-PSSession` . Standard Sök vägen är `$home\Documents\WindowsPowerShell\Modules` . Den här parametern är obligatorisk.

Om modulens under katalog eller någon av de filer som `Export-PSSession` skapas redan finns, Miss lyckas kommandot. Använd parametern **Force** om du vill skriva över befintliga filer.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, ModuleName

Required: True
Position: 1
Default value: $home\Documents\WindowsPowerShell\Modules
Accept pipeline input: False
Accept wildcard characters: False
```

### – Session

Anger den PSSession som kommandona exporteras från. Ange en variabel som innehåller ett session-objekt eller ett kommando som hämtar ett sessionsobjekt, till exempel ett `Get-PSSession` kommando. Den här parametern är obligatorisk.

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

Det går inte att skicka pipe-objekt till `Export-PSSession` .

## UTDATA

### System. IO. FileInfo

`Export-PSSession` Returnerar en lista med filer som utgör den modul som den skapade.

## ANTECKNINGAR

`Export-PSSession` förlitar sig på PowerShell-infrastrukturen för fjärr kommunikation. Om du vill använda denna cmdlet måste datorn konfigureras för fjärr kommunikation. Mer information finns i [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).

Du kan inte använda `Export-PSSession` för att exportera en PowerShell-Provider.

Exporterade kommandon körs implicit i PSSession som de exporterades från. Information om hur du kör fjärrkommandona hanteras helt och hållet av PowerShell. Du kan köra de exporterade kommandona på samma sätt som du kör lokala kommandon.

`Export-ModuleMember` fångar och sparar information om PSSession i den modul som den exporterar. Om PSSession som kommandona exporterades från stängs när du importerar modulen, och det inte finns några aktiva PSSessions på samma dator, försöker kommandona i modulen återskapa PSSession. Om försök att återskapa PSSession Miss lyckas kommer de exporterade kommandona inte att köras.

Sessionsinformation som `Export-ModuleMember` fångar in och sparar i modulen omfattar inte sessionsinställningar, till exempel de som du anger i `$PSSessionOption` variabeln Preference eller med hjälp av parametern **SessionOption** i `New-PSSession` `Enter-PSSession` cmdletarna,, eller `Invoke-Command` . Om den ursprungliga PSSession stängs när du importerar modulen använder modulen en annan PSSession på samma dator, om en sådan finns tillgänglig. Om du vill aktivera de importerade kommandona att köras i en korrekt konfigurerad session skapar du en PSSession med de alternativ som du vill använda innan du importerar modulen.

För att hitta de kommandon som ska exporteras `Export-PSSession` använder `Invoke-Command` cmdleten för att köra ett `Get-Command` kommando i PSSession. För att hämta och spara formaterings data för kommandona används `Get-FormatData` `Export-FormatData` cmdletarna och. Du kan se fel meddelanden från `Invoke-Command` , `Get-Command` , `Get-FormatData` och `Export-FormatData` när du kör ett `Export-PSSession` kommando. `Export-PSSession`Kan inte heller exportera kommandon från en-session som inte innehåller `Get-Command` `Get-FormatData` `Select-Object` cmdletarna,, och `Get-Help` .

`Export-PSSession` använder `Write-Progress` cmdleten för att visa förloppet för kommandot. Du kan se förlopps indikatorn när kommandot körs.

Exporterade kommandon har samma begränsningar som andra fjärrkommandon, inklusive möjligheten att starta ett program med ett användar gränssnitt, t. ex. anteckningar.

Eftersom PowerShell-profiler inte körs i PSSessions är kommandona som en profil lägger till i en session inte tillgängliga för `Export-PSSession` . Om du vill exportera kommandon från en profil använder du ett `Invoke-Command` kommando för att köra profilen i PSSession manuellt innan du exporterar kommandon.

Modulen som `Export-PSSession` skapar kan innehålla en formateringsinformation, även om kommandot inte importerar formaterings data. Om kommandot inte importerar dataformaterade data kommer eventuella filer som skapas inte att innehålla formatering.

## RELATERADE LÄNKAR

[about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)

[about_PSSessions](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[about_PSSnapins](../Microsoft.PowerShell.Core/About/about_PSSnapins.md)

[about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)

[Importera-modul](../Microsoft.PowerShell.Core/Import-Module.md)

[Importera – PSSession](Import-PSSession.md)

[Invoke-kommando](../Microsoft.PowerShell.Core/Invoke-Command.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-PSSessionOption](../Microsoft.PowerShell.Core/New-PSSessionOption.md)

[Remove-PSSession](../Microsoft.PowerShell.Core/Remove-PSSession.md)
