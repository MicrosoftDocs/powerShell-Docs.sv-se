---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-PSSnapin
ms.openlocfilehash: a21c2974fd66a9b02929752ae487c8995579b8a7
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388832"
---
# Add-PSSnapin

## SAMMANFATTNING
Lägger till en eller flera Windows PowerShell-snapin-moduler i den aktuella sessionen.

## SYNTAX

```
Add-PSSnapin [-Name] <String[]> [-PassThru] [<CommonParameters>]
```

## BESKRIVNING

`Add-PSSnapin`Cmdleten lägger till registrerade Windows PowerShell-snapin-moduler i den aktuella sessionen. När snapin-modulerna har lagts till kan du använda de cmdlets och providers som snapin-modulerna har stöd för i den aktuella sessionen.

Lägg till ett `Add-PSSnapin` kommando i Windows PowerShell-profilen för att lägga till snapin-modulen i alla framtida Windows PowerShell-sessioner. Mer information finns i [about_Profiles](about/about_Profiles.md).

Från och med Windows PowerShell 3,0 paketeras de grundläggande kommandon som ingår i Windows PowerShell i moduler. Undantaget är **Microsoft. PowerShell. Core** , som är en snapin-modul (PSSnapin).
Som standard läggs bara snapin-modulen **Microsoft. PowerShell. Core** till i sessionen. Moduler importeras automatiskt vid första användningen och du kan använda Import-Module-cmdlet för att importera dem.

## EXEMPEL

### Exempel 1: Lägg till snapin-moduler

```powershell
PS C:\> Add-PSSnapIn -Name Microsoft.Exchange, Microsoft.Windows.AD
```

Detta kommando lägger till Microsoft Exchange och Active Directory snapin-moduler till den aktuella sessionen.

### Exempel 2: Lägg till alla registrerade snapin-moduler

```powershell
PS C:\> Get-PSSnapin -Registered | Add-PSSnapin -Passthru
```

Med det här kommandot läggs alla registrerade Windows PowerShell-snapin-moduler till i sessionen. Den använder Get-PSSnapin-cmdlet med den **registrerade** parametern för att hämta objekt som representerar var och en av de registrerade snapin-modulerna. Pipeline-operatorn (|) skickar resultatet till `Add-PSSnapin` , som lägger till dem i sessionen. Parametern **Passthru** returnerar objekt som representerar var och en av de tillagda snapin-modulerna.

### Exempel 3: registrera en snapin-modul och Lägg till den

Det första kommandot hämtar snapin-moduler som har lagts till i den aktuella sessionen och innehåller snapin-moduler som installeras med Windows PowerShell. I det här exemplet returneras inte ManagementFeatures. Detta anger att den inte har lagts till i sessionen.

Det andra kommandot hämtar snapin-moduler som har registrerats i systemet, inklusive de som redan har lagts till i sessionen. Den omfattar inte snapin-modulerna som installeras med Windows PowerShell. I det här fallet returnerar kommandot inga snapin-moduler. Detta anger att snapin-modulen ManagementFeatures inte har registrerats i systemet.

Det tredje kommandot skapar ett alias, InstallUtil, för sökvägen till InstallUtil-verktyget i .NET Framework.

Det fjärde kommandot använder verktyget InstallUtil för att registrera snapin-modulen. Kommandot anger sökvägen till ManagementCmdlets.dll, fil namnet eller modulnamnet för snapin-modulen.

Det femte kommandot är samma som det andra kommandot. Den här gången använder du det för att kontrol lera att snapin-modulen ManagementCmdlets är registrerad.

Det sjätte kommandot använder `Add-PSSnapin` cmdleten för att lägga till snapin-modulen ManagementFeatures i sessionen. Den anger namnet på snapin-modulen, ManagementFeatures, inte fil namnet.

För att verifiera att snapin-modulen har lagts till i sessionen använder det sjunde kommandot parametern **module** i Get-Command-cmdleten. Den visar de objekt som har lagts till i sessionen av en snapin-modul eller modul.

Du kan också använda egenskapen **PSSnapin** för objektet som `Get-Command` cmdleten returnerar för att hitta snapin-modulen eller modulen där en cmdlet kommer. Det åttonde kommandot använder punkt notation för att hitta värdet för egenskapen PSSnapin i Set-Alias-cmdleten.

```powershell
PS C:\> Get-PSSnapin
PS C:\> Get-PSSnapin -Registered
PS C:\> Set-Alias installutil $env:windir\Microsoft.NET\Framework\v2.0.50727\installutil.exe
PS C:\> installutil C:\Dev\Management\ManagementCmdlets.dll
PS C:\> Get-PSSnapin -Registered
PS C:\> add-pssnapin ManagementFeatures
PS C:\> Get-Command -Module ManagementFeatures
PS C:\> (Get-Command Set-Alias).pssnapin
```

Det här exemplet visar hur du registrerar en snapin-modul på systemet och sedan lägger till den i sessionen. Den använder ManagementFeatures, en fiktiv snapin-modul som implementerats i en fil med namnet ManagementCmdlets.dll.

## PARAMETRAR

### -Name

Anger namnet på snapin-modulen. Detta är namnet, inte AssemblyName eller modulnamn. Jokertecken är tillåtna.

Om du vill hitta namnen på de registrerade snapin-modulerna i systemet skriver du `Get-PSSnapin -Registered` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### – PassThru

Anger att denna cmdlet returnerar ett objekt som representerar varje tillagd snapin-modul. Som standard genererar denna cmdlet inga utdata.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget
Det går inte att skicka pipe-objekt till denna cmdlet.

## UTDATA

### Ingen eller system. Management. Automation. PSSnapInInfo

Denna cmdlet returnerar ett PSSnapInInfo-objekt som representerar snapin-modulen om du anger parametern **Passthru** . Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

- Från och med Windows PowerShell 3,0 paketeras de grundläggande kommandon som installeras med Windows PowerShell i moduler. I Windows PowerShell 2,0 och i värd program som skapar äldre sessioner i senare versioner av Windows PowerShell är huvud kommandona förpackade i snapin-moduler (PSSnapins). Undantaget är **Microsoft. PowerShell. Core** , som alltid är en snapin-modul. Fjärrsessioner, till exempel de som startas av New-PSSession-cmdleten, är äldre sessioner som inkluderar grundläggande snapin-moduler.

  Information om **CreateDefault2** -metoden som skapar nyare sessioner med Core-moduler finns i CreateDefault2- [metoden](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2).

- Mer information om snapin-moduler finns i [about_PSSnapins](About/about_PSSnapins.md) och [hur du skapar en Windows PowerShell-snapin-modul](/powershell/scripting/developer/cmdlet/how-to-create-a-windows-powershell-snap-in).
- `Add-PSSnapin` lägger bara till snapin-modulen till den aktuella sessionen. Lägg till snapin-modulen till alla Windows PowerShell-sessioner genom att lägga till den i Windows PowerShell-profilen. Mer information finns i about_Profiles.
- Du kan lägga till en snapin-modul som har registrerats med installations verktyget för Microsoft .NET Framework. Mer information finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).
- Om du vill hämta en lista över snapin-moduler som är registrerade på datorn skriver du `Get-PSSnapin -Registered` .
- Innan du lägger till en snapin-modul `Add-PSSnapin` kontrollerar du vilken version av snapin-modulen som ska användas för att kontrol lera att den är kompatibel med den aktuella versionen av Windows PowerShell. Om snapin-modulen inte uppfyller versions kontrollen rapporterar Windows PowerShell ett fel.

## RELATERADE LÄNKAR

[Get-PSSnapin](Get-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)
