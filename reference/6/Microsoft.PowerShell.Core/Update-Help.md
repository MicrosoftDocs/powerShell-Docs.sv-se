---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/16/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/update-help?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Help
ms.openlocfilehash: 2851305f40c9805ae3f0fcc2a25a82a57a78cd23
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/04/2020
ms.locfileid: "93268886"
---
# Update-Help

## SAMMANFATTNING
Laddar ned och installerar de senaste hjälpfilerna på din dator.

## SYNTAX

### Sökväg (standard)

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-SourcePath] <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### LiteralPath

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-LiteralPath <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`Update-Help`Cmdlet: en laddar ned de senaste hjälpfilerna för PowerShell-moduler och installerar dem på din dator. Du behöver inte starta om PowerShell för att ändringen ska börja gälla. Du kan använda `Get-Help` cmdleten för att visa de nya hjälpfilerna omedelbart.

`Update-Help` kontrollerar versionen för hjälpfilerna på din dator. Om du inte har hjälp filer för en modul eller om dina hjälpfiler är inaktuella, `Update-Help` laddar ned de senaste hjälpfilerna. Hjälpfilerna kan laddas ned och installeras från Internet eller en fil resurs.

Utan parametrar `Update-Help` uppdaterar hjälpfilerna för moduler i sessionen och för alla installerade moduler som stöder uppdaterbar hjälp. Moduler som är installerade men inte inlästa i den aktuella sessionen ingår. PowerShell-moduler lagras på en plats som anges i `$env:PSModulePath` miljö variabeln. Mer information finns i [about_Updatable_Help](./About/about_Updatable_Help.md).

Du kan använda parametern **modul** för att uppdatera hjälpfiler för en viss modul. Använd parametern **värdet** för att hämta hjälpfiler på flera språk och nationella inställningar.

Du kan också använda `Update-Help` på datorer som inte är anslutna till Internet. Använd först cmdlet: en `Save-Help` för att hämta hjälpfiler från Internet och spara dem i en delad mapp som är tillgänglig för datorn som inte är ansluten till Internet. Använd sedan **SourcePath** -parametern för `Update-Help` för att ladda ned de uppdaterade hjälpfilerna från den delade och installera dem på datorn.

Du kan automatisera hjälp uppdateringar genom att lägga till `Update-Help` cmdleten i din PowerShell-profil. Som standard `Update-Help` körs bara en tid per dag på varje dator. Använd parametern **Force** om du vill åsidosätta en begränsning per dag.

`Update-Help`Cmdleten introducerades i Windows PowerShell 3,0.

> [!IMPORTANT]
> `Update-Help` kräver administratörs behörighet i PowerShell 6,0 och nedan.
> PowerShell 6,1 och högre anger standard **omfånget** till `CurrentUser` .
> Före PowerShell 6,1 var **omfångs** parametern inte tillgänglig.
>
> Du måste vara medlem i gruppen Administratörer på datorn för att kunna uppdatera hjälpfilerna för PowerShell Core-modulerna.
>
> Om du vill hämta eller uppdatera hjälpfilerna för moduler i installations katalogen för PowerShell ( `$PSHOME\Modules` ), inklusive PowerShell-modulerna, startar du PowerShell med alternativet **Kör som administratör** .
> Till exempel: `Start-Process pwsh.exe -Verb RunAs`.

## EXEMPEL

### Exempel 1: uppdatera hjälpfilerna för alla moduler

`Update-Help`Cmdleten uppdaterar hjälpfiler för installerade moduler som stöder uppdaterings bar hjälp. Kultur språket för användar gränssnittet (UI) har angetts i operativ systemet.

```powershell
Update-Help
```

### Exempel 2: uppdatera hjälpfiler för angivna moduler

`Update-Help`Cmdleten uppdaterar endast hjälp filer för Modulnamn som börjar med **Microsoft. PowerShell**.

```powershell
Update-Help -Module Microsoft.PowerShell*
```

### Exempel 3: uppdatera hjälpfiler för olika språk

`Update-Help`Cmdleten uppdaterar hjälpfilerna för japanska (ja-JP) och engelska (en-US) för alla moduler.

Om en modul inte tillhandahåller hjälp filer för en angiven användar gränssnitts kultur visas ett fel meddelande för modulen och användar gränssnitts kulturen. I det här exemplet anger fel meddelandet att hjälpfilerna för **Ja-JP** inte hittades för modulen **Microsoft. PowerShell. Utility**.

```powershell
Update-Help -UICulture ja-JP, en-US
```

```Output
Update-Help : Failed to update Help for the module(s) 'Microsoft.PowerShell.Utility' with UI culture(s) {ja-JP}
No UI culture was found that matches the following pattern: ja-JP.
```

### Exempel 4: uppdatera hjälpfiler på flera datorer från en fil resurs

I det här exemplet hämtas uppdaterade hjälpfiler från Internet och sparas i en fil resurs. Användarautentiseringsuppgifter krävs som har behörighet att komma åt fil resursen och installera uppdateringar. När en fil resurs används är det möjligt att uppdatera datorer som finns bakom brand väggar eller inte är anslutna till Internet.

```powershell
Save-Help -DestinationPath \\Server01\Share\PSHelp -Credential Domain01\Admin01
Invoke-Command -ComputerName (Get-Content Servers.txt) -ScriptBlock {
     Update-Help -SourcePath \\Server01\Share\PSHelp -Credential Domain01\Admin01
}
```

`Save-Help`Kommandot laddar ned de senaste hjälpfilerna för alla moduler som stöder uppdaterings bar hjälp.
Parametern **DestinationPath** sparar filerna i `\\Server01\Share\PSHelp` fil resursen. Parametern **Credential** anger en användare som har behörighet att komma åt fil resursen.

`Invoke-Command`Cmdleten kör `Update-Help` fjärrkommandon på flera datorer. Parametern **computername** hämtar en lista över fjärrdatorer från **Servers.txt** -filen. Parametern **script block** kör `Update-Help` kommandot och använder parametern **SourcePath** för att ange den fil resurs som innehåller de uppdaterade hjälpfilerna. Parametern **Credential** anger en användare som kan komma åt fil resursen och köra `Update-Help` fjärrkommandot.

### Exempel 5: Hämta en lista över uppdaterade hjälpfiler

`Update-Help`Cmdleten uppdaterar hjälpen för en angiven modul. Cmdleten använder den **utförliga** gemensamma parametern för att visa en lista med de hjälpfiler som uppdaterades. Du kan använda **utförligt** för att visa utdata för alla hjälpfiler eller hjälp filer för en speciell modul.

Utan **verbose** -parametern `Update-Help` visar inte kommandots resultat. Utdata för **utförlig** parameter är användbart för att verifiera att hjälpfilerna har uppdaterats eller om den senaste versionen är installerad.

```powershell
Update-Help -Module Microsoft.PowerShell.Utility -Verbose
```

### Exempel 6: hitta moduler som stöder uppdaterbar hjälp

I det här exemplet visas moduler som stöder uppdaterbar hjälp. Kommandot använder modulens **HelpInfoUri** -egenskap för att identifiera moduler som stöder uppdaterbar hjälp. Egenskapen **HelpInfoUri** innehåller en adress som omdirigeras när `Update-Help` cmdleten körs.

```powershell
Get-Module -ListAvailable | Where-Object -Property HelpInfoUri
```

```output
   Directory: C:\program files\powershell\6\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   6.1.0.0    CimCmdlets                          Core      {Get-CimAssociatedInstance... }
Manifest   1.2.2.0    Microsoft.PowerShell.Archive        Desk      {Compress-Archive... }
Manifest   6.1.0.0    Microsoft.PowerShell.Diagnostics    Core      {Get-WinEvent, New-WinEvent}

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, ... }
Script     1.0.0.0    AssignedAccess                      Core,Desk {Clear-AssignedAccess, ... }
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, ... }
```

### Exempel 7: uppdaterade hjälp filer för inventering

I det här exemplet skapar skriptet `Get-UpdateHelpVersion.ps1` en inventering av de uppdaterbara hjälpfilerna för varje modul och deras versions nummer.

Skriptet identifierar moduler som stöder uppdaterbar hjälp med hjälp av egenskapen **HelpInfoUri** för moduler. För moduler som stöder uppdaterbar hjälp söker skriptet efter och tolkar hjälp informations filen (* helpinfo.xml) för att hitta det senaste versions numret.

Skriptet använder klassen **PSCustomObject** och en hash-tabell för att skapa ett anpassat utgående objekt.

```powershell
# Get-UpdateHelpVersion.ps1
Param(
    [parameter(Mandatory=$False)]
    [String[]]
    $Module
)
$HelpInfoNamespace = @{helpInfo='http://schemas.microsoft.com/powershell/help/2010/05'}

if ($Module) { $Modules = Get-Module $Module -ListAvailable | where {$_.HelpInfoUri} }
else { $Modules = Get-Module -ListAvailable | where {$_.HelpInfoUri} }

foreach ($mModule in $Modules)
{
    $mDir = $mModule.ModuleBase

    if (Test-Path $mdir\*helpinfo.xml)
    {
        $mName=$mModule.Name
        $mNodes = dir $mdir\*helpinfo.xml -ErrorAction SilentlyContinue |
            Select-Xml -Namespace $HelpInfoNamespace -XPath "//helpInfo:UICulture"
        foreach ($mNode in $mNodes)
        {
            $mCulture=$mNode.Node.UICultureName
            $mVer=$mNode.Node.UICultureVersion

            [PSCustomObject]@{"ModuleName"=$mName; "Culture"=$mCulture; "Version"=$mVer}
        }
    }
}
```

```Output
ModuleName                              Culture                                 Version
----------                              -------                                 -------
ActiveDirectory                         en-US                                   3.0.0.0
ADCSAdministration                      en-US                                   3.0.0.0
ADCSDeployment                          en-US                                   3.0.0.0
ADDSDeployment                          en-US                                   3.0.0.0
ADFS                                    en-US                                   3.0.0.0
```

## PARAMETRAR

### -Credential

Anger autentiseringsuppgifter för en användare som har behörighet att komma åt fil system platsen som anges av **SourcePath**. Den här parametern är endast giltig när **SourcePath** -eller **LiteralPath** -parametern används i kommandot.

Med parametern **Credential** kan du köra `Update-Help` kommandon med parametern **SourcePath** på fjärrdatorer. Genom att ange explicita autentiseringsuppgifter kan du köra kommandot på en fjärrdator och komma åt en fil resurs på en tredje dator utan att ha påträffat ett nekat åtkomst fel eller använda CredSSP-autentisering för att delegera autentiseringsuppgifter.

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
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Anger att denna cmdlet inte följer begränsningen en gång per dag, hoppar över versions kontroll och laddar ned filer som överskrider gränsen på 1 GB.

Utan den här parametern `Update-Help` körs bara en gång under varje 24-timmarsperiod. Hämtningar är begränsade till 1 GB okomprimerat innehåll per modul och hjälpfiler installeras bara när de är nyare än de befintliga filerna på datorn.

Gränsen för en gång per dag skyddar de servrar som är värdar för hjälpfilerna och gör det praktiskt för dig att lägga till ett `Update-Help` kommando i din PowerShell-profil utan att kostnaden för resurs kostnaden för upprepade anslutningar eller nedladdningar debiteras.

Om du vill uppdatera hjälpen för en modul i flera användar gränssnitts kulturer utan **Force** -parametern inkluderar du alla användar gränssnitts kulturer i samma kommando, till exempel:

`Update-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

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

### -FullyQualifiedModule

Anger moduler med namn som anges i form av **ModuleSpecification** -objekt.
Dessa moduler beskrivs i avsnittet anmärkningar i [ModuleSpecification-konstruktorn (hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).

Parametern **FullyQualifiedModule** accepterar till exempel ett modulnamn som anges i formatet:

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

eller

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.`

**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt.

Du kan inte ange parametern **FullyQualifiedModule** i samma kommando som en **modul** -parameter.

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

Anger mappen för uppdaterade hjälpfiler i stället för att ladda ned dem från Internet. Använd den här parametern eller **SourcePath** om du har använt `Save-Help` cmdleten för att hämta hjälpfiler till en katalog.

Du kan pipelina ett katalog objekt, till exempel från `Get-Item` `Get-ChildItem` cmdletarna eller, till `Update-Help` .

Till skillnad från värdet för **SourcePath** , används värdet för **LiteralPath** exakt som det skrivs. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Modul

Uppdaterar hjälpen för de angivna modulerna. Ange ett eller flera Modulnamn eller namn mönster i en kommaavgränsad lista eller ange en fil som visar ett modulnamn på varje rad. Jokertecken är tillåtna. Du kan pipeline-moduler från `Get-Module` cmdlet: en till `Update-Help` cmdlet: en.

De moduler som du anger måste vara installerade på datorn, men de behöver inte importeras till den aktuella sessionen. Du kan ange vilken modul som helst i sessionen eller vilken modul som helst som är installerad på en plats som anges i `$env:PSModulePath` miljö variabeln.

Värdet `*` (alla) försöker att uppdatera hjälpen för alla moduler som är installerade på datorn.
Moduler som inte stöder uppdaterbar hjälp ingår. Det här värdet kan generera fel när kommandot påträffar moduler som inte stöder uppdaterbar hjälp. Kör i stället `Update-Help` utan parametrar.

Parametern **module** för `Update-Help` cmdleten accepterar inte den fullständiga sökvägen till en modul-fil eller modulens manifest fil. Om du vill uppdatera hjälpen för en modul som inte finns på en `$env:PSModulePath` plats importerar du modulen till den aktuella sessionen innan du kör `Update-Help` kommandot.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### – Rekursivt

Utför en rekursiv sökning efter hjälpfilerna i den angivna katalogen. Den här parametern är endast giltig om parametern **SourcePath** används i kommandot.

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

### – Omfattning

Anger system omfånget där hjälpen uppdateras. Uppdateringar i **allusers** -omfånget kräver administratörs behörighet för Windows-system. `-Scope`Parametern introducerades i PowerShell Core version 6,1.

**CurrentUser** är standard omfånget för hjälp av filer i PowerShell 6,1 och senare. **Allusers** kan anges för att installera eller uppdatera hjälpen för alla användare. Behörigheter för UNIX-system `sudo` krävs för att du ska kunna uppdatera hjälpen för alla användare. Exempelvis: `sudo pwsh -c Update-Help`

Godkända värden är:

- CurrentUser
- AllUsers

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourcePath

Anger en fil system katalog där `Update-Help` uppdaterade hjälpfiler hämtas, i stället för att de hämtas från Internet. Ange sökvägen till en mapp. Ange inte ett fil namn eller fil namns tillägg. Du kan pipelina en mapp, till exempel en från `Get-Item` -eller `Get-ChildItem` -cmdlet: ar, till `Update-Help` .

Som standard `Update-Help` hämtar de uppdaterade hjälpfilerna från Internet. Använd **SourcePath** när du har använt `Save-Help` cmdleten för att hämta uppdaterade hjälpfiler till en katalog.

Om du vill ange ett standardvärde för **SourcePath** går du till **Grupprincip** , **dator konfiguration** och **anger standard Sök vägen för uppdatering-hjälpen**. Den här grupprincip inställningen hindrar användare från `Update-Help` att använda för att hämta hjälpfiler från Internet.
Mer information finns i [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md).

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Värdet

Anger GRÄNSSNITTs språk värden som `Update-Help` används för att hämta uppdaterade hjälpfiler. Ange en eller flera språk koder, till exempel **es-es** , en variabel som innehåller kultur objekt eller ett kommando som hämtar kultur objekt, till exempel ett `Get-Culture` eller- `Get-UICulture` kommando. Jokertecken är inte tillåtna och du kan inte skicka en del språk kod, till exempel **de**.

Som standard `Update-Help` får hjälpfilerna i användar gränssnitts kulturen angetts för operativ systemet. Om du anger parametern **värdet** letar du `Update-Help` bara efter hjälp för den angivna användar gränssnitts kulturen.

> [!NOTE]
> Ubuntu 18,04 ändrade standard språk inställningen till `C.UTF.8` , vilket inte är en känd kultur för användar gränssnitt. `Update-Help` Det går tyst att ladda ned hjälpen om du inte använder den här parametern med ett språk som stöds `en-US` . Detta kan inträffa på vilken plattform som helst som använder ett värde som inte stöds.

Kommandon som använder parametern **värdet** fungerar bara när modulen tillhandahåller hjälpfiler för den angivna kulturen för användar gränssnittet. Om kommandot Miss lyckas eftersom den angivna användar gränssnitts kulturen inte stöds visas ett fel meddelande.

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDefaultCredentials

Anger att `Update-Help` Kör kommandot, inklusive hämtning av Internet, med hjälp av den aktuella användarens autentiseringsuppgifter. Som standard körs kommandot utan explicita autentiseringsuppgifter.

Den här parametern är endast effektiv när webb hämtningen använder NTLM (NT LAN Manager), Negotiate eller Kerberos-baserad autentisering.

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

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. IO. DirectoryInfo

Du kan skicka en katalog Sök väg till `Update-Help` .

### System. Management. Automation. PSModuleInfo

Du kan skicka ett modul-objekt från `Get-Module` cmdlet: en till `Update-Help` .

## UTDATA

### Inget

`Update-Help` genererar inga utdata.

## ANTECKNINGAR

Om du vill uppdatera hjälpen för PowerShell Core-modulerna som innehåller de kommandon som är installerade med PowerShell eller någon modul i `$PSHOME\Modules` katalogen startar du PowerShell med alternativet att **köra som administratör**.

Endast medlemmar i gruppen Administratörer på datorn kan uppdatera hjälpen för PowerShell Core-modulerna, kommandon som installeras tillsammans med PowerShell och för moduler i `$PSHOME\Modules` mappen. Om du inte har behörighet att uppdatera hjälpfiler kan du läsa hjälpfilerna online. Till exempel `Get-Help Update-Help -Online`.

Moduler är den minsta enheten för uppdaterbar hjälp. Du kan inte uppdatera hjälpen för en viss cmdlet. Om du vill hitta modulen som innehåller en viss cmdlet använder du egenskapen **Modulnamn** för `Get-Command` cmdleten, till exempel `(Get-Command Update-Help).ModuleName` .

Eftersom hjälpfiler installeras i modul-katalogen `Update-Help` kan cmdleten bara installera den uppdaterade hjälp filen för moduler som är installerade på datorn. Men `Save-Help` cmdleten kan spara hjälp för moduler som inte är installerade på datorn.

Om `Update-Help` det inte går att hitta uppdaterade hjälpfiler för en modul, eller om det inte går att hitta en uppdaterad hjälp på det angivna språket, fortsätter den tyst utan att ett fel meddelande visas. Använd **verbose** -parametern för att se information om status och förlopp.

`Update-Help`Cmdleten introducerades i Windows PowerShell 3,0. Den fungerar inte i tidigare versioner av PowerShell. På datorer som har både Windows PowerShell 2,0 och Windows PowerShell 3,0 använder du `Update-Help` cmdleten i en Windows PowerShell 3,0-session för att hämta och uppdatera hjälpfiler. Hjälpfilerna är tillgängliga för både Windows PowerShell 2,0 och Windows PowerShell 3,0.

`Update-Help` `Save-Help` Cmdletarna och använder följande portar för att hämta hjälpfiler: port 80 för http och port 443 för https.

`Update-Help` stöder alla moduler och snapin-moduler för PowerShell Core. Den har inte stöd för några andra snapin-moduler.

Om du vill uppdatera hjälpen för en modul på en plats som inte finns med i `$env:PSModulePath` miljövariabeln importerar du modulen till den aktuella sessionen och kör sedan ett `Update-Help` kommando. Kör `Update-Help` utan parametrar eller Använd parametern **module** för att ange modulnamnet. Parametern **module** för `Update-Help` `Save-Help` cmdletarna och accepterar inte den fullständiga sökvägen till en modul fil eller modulens manifest fil.

Alla moduler kan stödja uppdaterings bar hjälp. Instruktioner för att stödja uppdaterings bar hjälp i de moduler som du skapar finns i [support uppdaterings bara hjälp](/powershell/scripting/developer/module/supporting-updatable-help).

`Update-Help` `Save-Help` Cmdletarna och stöds inte på Windows Preinstallation Environment (Windows PE).

## RELATERADE LÄNKAR

[Get-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md)

[Get – hjälp](Get-Help.md)

[Hämta modul](Get-Module.md)

[Get-värdet](../Microsoft.PowerShell.Utility/Get-UICulture.md)

[Start – jobb](Start-Job.md)

[Spara – hjälp](Save-Help.md)
