---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/save-help?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Help
ms.openlocfilehash: b4306807735d4ffd64850149f5558390f613976b
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387302"
---
# Save-Help

## SAMMANFATTNING
Hämtar och sparar de senaste hjälpfilerna till en fil system katalog.

## SYNTAX

### Sökväg (standard)

```
Save-Help [-DestinationPath] <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>]
 [<CommonParameters>]
```

### LiteralPath

```
Save-Help -LiteralPath <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>]
 [<CommonParameters>]
```

## BESKRIVNING

`Save-Help`Cmdlet: en laddar ned de senaste hjälpfilerna för PowerShell-moduler och sparar dem i en katalog som du anger. Med den här funktionen kan du uppdatera hjälpfilerna på datorer som inte har till gång till Internet, och det gör det enklare att uppdatera hjälpfilerna på flera datorer.

I Windows PowerShell 3,0 `Save-Help` fungerade det bara för moduler som är installerade på den lokala datorn. Även om det var möjligt att importera en modul från en fjärrdator, eller hämta en referens till ett **PSModuleInfo** -objekt från en fjärrdator med hjälp av PowerShell-fjärrkommunikation, bevaras inte egenskapen **HelpInfoUri** och `Save-Help` fungerar inte för hjälp med Fjärrhjälp.

I Windows PowerShell 4,0 bevaras egenskapen **HelpInfoUri** över PowerShell-fjärrkommunikation, som gör `Save-Help` att du kan arbeta med moduler som är installerade på fjärrdatorer. Det är också möjligt att spara ett **PSModuleInfo** -objekt på disk eller flyttbart medium genom `Export-Clixml` att köra på en dator som inte har Internet åtkomst, importera objektet på en dator som har Internet åtkomst och sedan köra `Save-Help` på **PSModuleInfo** -objektet. Den sparade hjälpen kan transporteras till fjärrdatorn med hjälp av flyttbara lagrings medier, till exempel en USB-enhet. Hjälpen kan installeras på fjärrdatorn genom att köra `Update-Help` . Den här processen kan användas för att installera hjälp på datorer som inte har någon typ av nätverks åtkomst.

Kör cmdleten om du vill installera sparade hjälpfiler `Update-Help` . Lägg till dess **SourcePath** -parameter för att ange mappen där du sparade hjälpfilerna.

Utan parametrar laddar ett `Save-Help` kommando ned den senaste hjälpen för alla moduler i sessionen och för moduler som är installerade på datorn på en plats som anges i **PSModulePath** -miljövariabeln. Den här åtgärden hoppar över moduler som inte stöder uppdaterbar hjälp utan varning.

`Save-Help`Cmdleten kontrollerar versionen för eventuella hjälpfiler i målmappen. Om det finns nyare hjälpfiler, laddar denna cmdlet ned de senaste hjälpfilerna från Internet och sparar dem sedan i mappen. `Save-Help`Cmdleten fungerar precis som `Update-Help` -cmdleten, förutom att den sparar de hämtade CAB-filerna, i stället för att extrahera hjälpfilerna från CAB-filerna och installera dem på datorn.

Den sparade hjälpen för varje modul består av en HelpInfo XML-fil (hjälp information) och en kabinett fil (. cab) för hjälpfilerna för varje GRÄNSSNITTs kultur. Du behöver inte extrahera hjälpfilerna från CAB-filen. `Update-Help`Cmdleten extraherar hjälpfilerna, validerar XML för säkerhet och installerar sedan hjälpfilerna och hjälp informations filen i en språkspecifik undermapp i mappen module.

Om du vill spara hjälpfilerna för moduler i PowerShell-installationsmappen ( `$pshome\Modules` ) startar du PowerShell med alternativet Kör som administratör. Du måste vara medlem i gruppen Administratörer på datorn för att kunna hämta hjälpfilerna för dessa moduler.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: Spara hjälpen för modulen DHCP server

```powershell
# Option 1: Run Invoke-Command to get the PSModuleInfo object for the remote DHCP Server module,
# save the PSModuleInfo object in the variable $m, and then run Save-Help.

$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock { Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 2: Open a PSSession--targeted at the remote computer that is running the DhcpServer
# module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$s = New-PSSession -ComputerName "RemoteServer"
$m = Get-Module -PSSession $s -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 3: Open a CIM session--targeted at the remote computer that is running the DhcpServer
# module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$c = New-CimSession -ComputerName "RemoteServer"
$m = Get-Module -CimSession $c -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"
```

Det här exemplet visar tre olika sätt att använda `Save-Help` för att spara hjälpen för modulen **DHCP** Server från en Internet-ansluten klient dator, utan att installera modulen DHCP server eller DHCP-serverrollen på den lokala datorn. **DhcpServer**

### Exempel 2: installera hjälp för modulen DHCP server

```powershell
# First, run Export-CliXml to export the PSModuleInfo object to a shared folder or to removable media.

$m = Get-Module -Name "DhcpServer" -ListAvailable
Export-CliXml -Path "E:\UsbFlashDrive\DhcpModule.xml" -InputObject $m

# Next, transport the removable media to a computer that has Internet access, and then import the
# PSModuleInfo object with Import-CliXml. Run Save-Help to save the Help for the imported DhcpServer
# module PSModuleInfo object.

$deserialized_m = Import-CliXml "E:\UsbFlashDrive\DhcpModule.xml"
Save-Help -Module $deserialized_m -DestinationPath "E:\UsbFlashDrive\SavedHelp"

# Finally, transport the removable media back to the computer that does not have network access, and
# then install the help by running Update-Help.

Update-Help -Module DhcpServer -SourcePath "E:\UsbFlashDrive\SavedHelp"
```

Det här exemplet visar hur du installerar hjälp som du sparade i exempel 1 för modulen **DHCP** server på en dator som inte har Internet åtkomst.

### Exempel 3: Spara hjälp för alla moduler

```powershell
Save-Help -DestinationPath "\\Server01\FileShare01"
```

Det här kommandot laddar ned de senaste hjälpfilerna för alla moduler i användar gränssnitts kulturen som angetts för Windows på den lokala datorn. Hjälpfilerna sparas i `\\Server01\Fileshare01` mappen.

### Exempel 4: Spara hjälp för en modul på datorn

```powershell
Save-Help -Module ServerManager -DestinationPath "\\Server01\FileShare01" -Credential Domain01/Admin01
```

Det här kommandot laddar ned de senaste hjälpfilerna för **servermanager** -modulen och sparar dem sedan i `\\Server01\Fileshare01` mappen.

När en modul installeras på datorn kan du ange modulnamnet som värde för parametern **module** , även om modulen inte har importer ATS till den aktuella sessionen.

Kommandot använder parametern **Credential** för att ange autentiseringsuppgifterna för en användare som har behörighet att skriva till fil resursen.

### Exempel 5: Spara hjälp för en modul på en annan dator

```powershell
Invoke-Command -ComputerName Server02 {Get-Module -Name CustomSQL -ListAvailable} | Save-Help -DestinationPath \\Server01\FileShare01 -Credential Domain01\Admin01
```

Dessa kommandon laddar ned de senaste hjälpfilerna för modulen **CustomSQL** och sparar dem i `\\Server01\Fileshare01` mappen.

Eftersom **CustomSQL** -modulen inte är installerad på datorn innehåller sekvensen ett `Invoke-Command` kommando som hämtar module-objektet för CustomSQL-modulen från Server02-datorn och sedan pipe-objektet till `Save-Help` cmdleten.

Om en modul inte är installerad på datorn, `Save-Help` behöver module-objektet, som innehåller information om platsen för de senaste hjälpfilerna.

### Exempel 6: Spara hjälp för en modul på flera språk

```powershell
Save-Help -Module Microsoft.PowerShell* -UICulture de-DE, en-US, fr-FR, ja-JP -DestinationPath "D:\Help"
```

Det här kommandot sparar hjälpen för PowerShell Core-modulerna i fyra olika användar gränssnitts kulturer. Språk paketen för dessa språk måste inte installeras på datorn.

`Save-Help` Det går bara att hämta hjälpfiler för moduler i olika användar gränssnitts kulturer när modulens ägare gör de översatta filerna tillgängliga på Internet.

### Exempel 7: Spara hjälpen mer än en gången varje dag

```powershell
Save-Help -Force -DestinationPath "\\Server3\AdminShare\Help"
```

Det här kommandot sparar hjälpen för alla moduler som är installerade på datorn. Kommandot anger **Force** -parametern för att åsidosätta regeln som förhindrar att `Save-Help` cmdlet: en hämtar hjälp mer än en gång under varje 24-timmarsperiod.

Parametern **Force** åsidosätter också begränsningen 1 GB och kringgår versions kontroll.
Därför kan du hämta filer även om versionen inte är senare än versionen i målmappen.

Kommandot använder `Save-Help` cmdleten för att ladda ned och spara hjälpfilerna i den angivna mappen.
Parametern **Force** krävs om du vill köra ett `Save-Help` kommando mer än en gång varje dag.

## PARAMETRAR

### -Credential

Anger autentiseringsuppgifter för användare. Denna cmdlet kör kommandot genom att använda autentiseringsuppgifter för en användare som har behörighet att komma åt fil system platsen som anges av parametern **DestinationPath** . Den här parametern är endast giltig om parametern **DestinationPath** eller **LiteralPath** används i kommandot.

Med den här parametern kan du köra `Save-Help` kommandon som använder parametern **DestinationPath** på fjärrdatorer. Genom att ange explicita autentiseringsuppgifter kan du köra kommandot på en fjärrdator och komma åt en fil resurs på en tredje dator utan att ha påträffat ett nekat åtkomst fel eller använda CredSSP-autentisering för att delegera autentiseringsuppgifter.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange lösen ordet.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – DestinationPath

Anger sökvägen till mappen där hjälpfilerna sparas. Ange inget fil namn eller fil namns tillägg.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Anger att denna cmdlet inte följer begränsningen en gång per dag, hoppar över versions kontroll och laddar ned filer som överskrider gränsen på 1 GB.

Utan den här parametern är endast ett `Save-Help` kommando för varje modul tillåtet under varje 24-timmarsperiod, och hämtningar är begränsade till 1 GB okomprimerat innehåll per modul och hjälp filer för en modul installeras bara när de är nyare än filerna på datorn.

Gränsen för en gång per dag skyddar de servrar som är värdar för hjälpfilerna och gör det praktiskt att lägga till ett `Save-Help` kommando i din PowerShell-profil.

Om du vill spara hjälp för en modul i flera användar gränssnitts kulturer utan **Force** -parametern inkluderar du alla användar gränssnitts kulturer i samma kommando, till exempel: `Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedModule

Anger moduler med namn som anges i form av **ModuleSpecification** -objekt. Se avsnittet anmärkningar i [ModuleSpecification-konstruktorn (hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).

**FullyQualifiedModule** -parametern accepterar till exempel ett modulnamn som anges i något av följande format:

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt. Det går inte att ange parametern **FullyQualifiedModule** i samma kommando som en **modul** -parameter. de två parametrarna kan inte anges samtidigt.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

Anger en sökväg till målmappen. Till skillnad från värdet för parametern **DestinationPath** används värdet för parametern **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Modul

Anger moduler för vilka denna cmdlet laddar ned hjälp. Ange ett eller flera Modulnamn eller namn patters i en kommaavgränsad lista eller i en fil som har ett modulnamn på varje rad. Jokertecken är tillåtna. Du kan också skicka modul objekt från `Get-Module` cmdleten till `Save-Help` .

Som standard `Save-Help` är hämtnings hjälp för alla moduler som stöder uppdaterbar hjälp och som är installerade på den lokala datorn på en plats som anges i miljövariabeln **PSModulePath** .

Om du vill spara hjälp för moduler som inte är installerade på datorn kör du ett `Get-Module` kommando på en fjärrdator. Skicka sedan de resulterande modulerna till `Save-Help` cmdlet: en eller skicka modulens objekt som värde för **modulen** eller **InputObject** -parametrarna.

Om den modul som du anger är installerad på datorn kan du ange modulens namn eller ett modul-objekt. Om modulen inte är installerad på datorn måste du ange ett modul-objekt, till exempel en som returneras av `Get-Module` cmdleten.

Parametern **module** för `Save-Help` cmdleten accepterar inte den fullständiga sökvägen till en modul-fil eller modulens manifest fil. Om du vill spara hjälp för en modul som inte finns på en **PSModulePath** -plats importerar du modulen till den aktuella sessionen innan du kör `Save-Help` kommandot.

Värdet "*" (alla) försöker att uppdatera hjälpen för alla moduler som är installerade på datorn.
Detta inkluderar moduler som inte stöder uppdaterbar hjälp. Det här värdet kan generera fel när kommandot påträffar moduler som inte stöder uppdaterings bar hjälp.

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### – Värdet

Anger GRÄNSSNITTs kultur värden för vilka denna cmdlet hämtar hjälpfiler. Ange en eller flera språk koder, till exempel `es-ES` en variabel som innehåller kultur objekt eller ett kommando som hämtar kultur objekt, till exempel ett eller- `Get-Culture` `Get-UICulture` kommando.

Jokertecken tillåts inte. Ange inte en del språk kod, till exempel "de".

Som standard `Save-Help` får hjälpfilerna i användar gränssnitts kulturen angetts för Windows eller dess reserv kultur.
Om du anger parametern **värdet** letar du `Save-Help` bara efter hjälp för den angivna användar gränssnitts kulturen, inte i någon återställnings kultur.

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: Current UI culture
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDefaultCredentials

Anger att denna cmdlet kör kommandot, inklusive webb hämtning, med autentiseringsuppgifterna för den aktuella användaren. Som standard körs kommandot utan explicita autentiseringsuppgifter.

Den här parametern är endast effektiv när webb hämtningen använder NTLM, Negotiate eller Kerberos-baserad autentisering.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Omfattning

Den här parameter gör ingenting i den här cmdleten.

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSModuleInfo

Du kan skicka ett modul-objekt från `Get-Module` cmdlet: en till **modulen modul** för `Save-Help` .

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

- Om du vill spara hjälp för moduler i mappen $pshome \Modules startar du PowerShell med alternativet Kör som administratör. Endast medlemmar i gruppen Administratörer på datorn kan hämta hjälp för moduler i mappen $pshome \Modules.
- Den sparade hjälpen för varje modul består av en HelpInfo XML-fil (hjälp information) och en kabinett fil (. cab) för hjälpfilerna för varje GRÄNSSNITTs kultur. Du behöver inte extrahera hjälpfilerna från CAB-filen. `Update-Help`Cmdleten extraherar hjälpfilerna, validerar XML och installerar sedan hjälpfilerna och hjälp informations filen i en språkspecifik undermapp i mappen module.
- `Save-Help`Cmdleten kan spara hjälp för moduler som inte är installerade på datorn. Eftersom hjälpfiler installeras i modulen modul `Update-Help` kan dock cmdleten bara installera den uppdaterade hjälp filen för moduler som är installerade på datorn.
- Om `Save-Help` det inte går att hitta uppdaterade hjälpfiler för en modul, eller om det inte går att hitta uppdaterade hjälpfiler på det angivna språket, fortsätter den tyst utan att ett fel meddelande visas. Om du vill se vilka filer som sparats med kommandot anger du **utförlig** parameter.
- Moduler är den minsta enheten för uppdaterbar hjälp. Du kan inte spara hjälp för en viss cmdlet, endast för alla cmdletar i modulen. Om du vill hitta modulen som innehåller en viss cmdlet använder du egenskapen **Modulnamn** tillsammans med `Get-Command` cmdleten, till exempel `(Get-Command \<cmdlet-name\>).ModuleName`
- `Save-Help` stöder alla moduler och snapin-moduler för PowerShell Core. Den har inte stöd för några andra snapin-moduler.
- `Update-Help` `Save-Help` Cmdletarna och använder följande portar för att hämta hjälpfiler: port 80 för http och port 443 för https.
- `Update-Help` `Save-Help` Cmdletarna och stöds inte på Windows Preinstallation Environment (Windows PE).

## RELATERADE LÄNKAR

[Get – hjälp](Get-Help.md)

[Hämta modul](Get-Module.md)

[Uppdatera – hjälp](Update-Help.md)
