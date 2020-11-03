---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-xml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Xml
ms.openlocfilehash: e5bf7d5f0574b7e1503f229d2dee11f3bcaba43a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265131"
---
# ConvertTo-Xml

## SAMMANFATTNING
Skapar en XML-baserad representation av ett objekt.

## SYNTAX

```
ConvertTo-Xml [-Depth <Int32>] [-InputObject] <PSObject> [-NoTypeInformation] [-As <String>]
 [<CommonParameters>]
```

## BESKRIVNING

`ConvertTo-Xml`Cmdleten skapar en [XML-baserad](/dotnet/api/system.xml.xmldocument) representation av ett eller flera .net-objekt. Om du vill använda denna cmdlet, rör ett eller flera objekt till cmdleten eller Använd parametern **InputObject** för att ange objektet.

När du lägger till flera objekt i `ConvertTo-Xml` eller använder parametern **InputObject** för att skicka flera objekt, `ConvertTo-Xml` returnerar ett enskilt XML-dokument i minnet som innehåller representationer av alla objekt.

Den här cmdleten liknar [export-CliXml](./Export-Clixml.md) , förutom att `Export-Clixml` lagrar XML-koden i en [XML-fil med Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm) som kan importeras om som objekt med [import-CliXml](./Import-Clixml.md). `ConvertTo-Xml` Returnerar en minnes intern representation av ett XML-dokument, så du kan fortsätta att bearbeta det i PowerShell. `ConvertTo-Xml` har inget alternativ för att konvertera objekt till CLI XML.

## EXEMPEL

### Exempel 1: konvertera ett datum till XML

```
PS C:\> Get-Date | ConvertTo-Xml
```

Det här kommandot konverterar det aktuella datumet (ett **datetime** -objekt) till XML.

### Exempel 2: konvertera processer till XML

```
PS C:\> ConvertTo-Xml -As "Document" -InputObject (Get-Process) -Depth 3
```

Detta kommando konverterar de process objekt som representerar alla processer på datorn till ett XML-dokument. Objekten expanderas till ett djup på tre nivåer.

## PARAMETRAR

### – Som

Anger utdataformatet.
De acceptabla värdena för den här parametern är:

- Sträng.
Returnerar en enskild sträng.
- Skicka.
Returnerar en sträng mat ris.
- Handling.
Returnerar ett **XMLDocument** -objekt.

Standardvärdet är Document.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Stream, String, Document

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Djup

Anger hur många nivåer med objekt som ingår i XML-representationen. Standardvärdet är 1.

Om objektets egenskaper till exempel även innehåller objekt, så att du kan spara en XML-representation av egenskaperna för de objekt som finns i listan, måste du ange ett djup på 2.

Standardvärdet kan åsidosättas av objekt typen i Types.ps1XML-filer. Mer information finns i about_Types.ps1XML.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger det objekt som ska konverteras. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten. Du kan också skicka pipe-objekt till **ConvertTo-XML**.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoTypeInformation

Utesluter Typattributet från objekt-noderna.

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

### System. Management. Automation. PSObject

Du kan skicka ett objekt till **ConvertTo-XML**.

## UTDATA

### System. String eller System.Xml.Xmldokument

Värdet för parametern *as* bestämmer vilken typ av objekt som **ConvertTo-XML** returnerar.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[ConvertTo-Csv](ConvertTo-Csv.md)

[ConvertTo-Html](ConvertTo-Html.md)

[Exportera – CliXml](Export-Clixml.md)

[Hämta datum](Get-Date.md)

[Importera – CliXml](Import-Clixml.md)
