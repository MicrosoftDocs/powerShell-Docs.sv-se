---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-clixml?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Clixml
ms.openlocfilehash: d33b74101301ec5806f456ddd9cc73bd8b6bb3e1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264320"
---
# Import-Clixml

## SAMMANFATTNING
Importerar en CLIXML-fil och skapar motsvarande objekt i PowerShell.

## SYNTAX

### ByPath (standard)

```
Import-Clixml [-Path] <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

### ByLiteralPath

```
Import-Clixml -LiteralPath <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

## BESKRIVNING

`Import-Clixml`Cmdleten importerar en XML-fil med Common Language Infrastructure (CLI) till data som representerar Microsoft .net Ramverks objekt och skapar PowerShell-objekt. Mer information om CLI finns i [språk oberoende](/dotnet/standard/language-independence).

En värdefull användning av `Import-Clixml` Windows-datorer är att importera autentiseringsuppgifter och säkra strängar som har exporter ATS som säker XML med `Export-Clixml` . Ett exempel finns i exempel 2.

`Import-Clixml` använder byte-order-markering (BOM) för att identifiera filens kodnings format. Om filen saknar struktur antas kodningen vara UTF8.

## EXEMPEL

### Exempel 1: importera en serialiserad fil och återskapa ett objekt

I det här exemplet används `Export-Clixml` cmdleten för att spara en serialiserad kopia av den process information som returnerades av `Get-Process` . `Import-Clixml` hämtar den serialiserade filens innehåll och återskapar ett objekt som lagras i `$Processes` variabeln.

```powershell
Get-Process | Export-Clixml -Path .\pi.xml
$Processes = Import-Clixml -Path .\pi.xml
```

### Exempel 2: importera ett säkert objekt för autentiseringsuppgifter

I det här exemplet har du fått en autentiseringsuppgift som du har lagrat i `$Credential` variabeln genom `Get-Credential` att köra cmdleten, så du kan köra `Export-Clixml` cmdleten för att spara autentiseringsuppgifterna på disken.

> [!IMPORTANT]
> `Export-Clixml` exporterar endast krypterade autentiseringsuppgifter i Windows. På andra operativ system än Windows, till exempel macOS och Linux, exporteras autentiseringsuppgifterna som oformaterad text.

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

`Export-Clixml`Cmdleten krypterar Credential-objekt med hjälp av Windows [Data Protection-API](/previous-versions/windows/apps/hh464970(v=win.10)).
Krypteringen säkerställer att endast ditt användar konto kan dekryptera innehållet i Credential-objektet. Den exporterade `CLIXML` filen kan inte användas på en annan dator eller av en annan användare.

I exemplet representeras filen där autentiseringsuppgiften lagras av `TestScript.ps1.credential` . Ersätt **TestScript** med namnet på skriptet som du läser in autentiseringsuppgiften med.

Du skickar Credential-objektet ned till pipelinen till `Export-Clixml` och sparar det på den sökväg, `$Credxmlpath` som du angav i det första kommandot.

Kör de sista två kommandona om du vill importera autentiseringsuppgiften automatiskt till ditt skript. Kör `Import-Clixml` för att importera det skyddade objektet Credential till skriptet. Den här importen eliminerar risken att exponera lösen ord i klartext i skriptet.

## PARAMETRAR

### – Första

Hämtar endast det angivna antalet objekt. Ange antalet objekt som ska hämtas.

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeTotalCount

Rapporterar det totala antalet objekt i data uppsättningen följt av de valda objekten. Om cmdleten inte kan avgöra det totala antalet, visar den det **okända totala antalet**. Heltalet har en **precisions** egenskap som anger tillförlitligheten för det totala Count-värdet. Värdet för **precisions** intervall från `0.0` till `1.0` `0.0` anger att cmdleten inte kunde räkna objekten, `1.0` innebär att antalet är exakt och ett värde mellan `0.0` och `1.0` indikerar en allt mer tillförlitlig uppskattning.

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

### -LiteralPath

Anger sökvägen till XML-filerna. Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det skrivs. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Anger sökvägen till XML-filerna.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Hoppa över

Ignorerar det angivna antalet objekt och hämtar kvarvarande objekt. Ange antalet objekt som ska hoppas över.

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan pipelina en sträng som innehåller en sökväg till `Import-Clixml` .

## UTDATA

### PSObject

`Import-Clixml` returnerar objekt som har deserialiserats från de lagrade XML-filerna.

## ANTECKNINGAR

Använd kommatecken för att avgränsa värdena när du anger flera värden för en parameter. Till exempel `<parameter-name> <value1>, <value2>`.

## RELATERADE LÄNKAR

[Exportera – CliXml](Export-Clixml.md)

[Introduktion till XML-serialisering](/dotnet/standard/serialization/introducing-xml-serialization)

[Anslut till sökväg](../Microsoft.PowerShell.Management/Join-Path.md)

[Lagra autentiseringsuppgifter på ett säkert sätt på disken](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[Använd PowerShell för att skicka autentiseringsuppgifter till äldre system](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

