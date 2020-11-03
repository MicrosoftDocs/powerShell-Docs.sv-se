---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-typedata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-TypeData
ms.openlocfilehash: 5f6a9014ad86ba0c80694d7cf49104b56ce27d9d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265616"
---
# Update-TypeData

## Sammanfattning
Uppdaterar den utökade data typen i sessionen.

## Syntax

### FileSet (standard)

```
Update-TypeData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DynamicTypeSet

```
Update-TypeData [-MemberType <PSMemberTypes>] [-MemberName <String>] [-Value <Object>]
 [-SecondValue <Object>] [-TypeConverter <Type>] [-TypeAdapter <Type>]
 [-SerializationMethod <String>] [-TargetTypeForDeserialization <Type>]
 [-SerializationDepth <Int32>] [-DefaultDisplayProperty <String>]
 [-InheritPropertySerializationSet <Nullable`1>] [-StringSerializationSource <String>]
 [-DefaultDisplayPropertySet <String[]>] [-DefaultKeyPropertySet <String[]>]
 [-PropertySerializationSet <String[]>] -TypeName <String> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### TypeDataSet

```
Update-TypeData [-Force] [-TypeData] <TypeData[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Beskrivning

`Update-TypeData`Cmdleten uppdaterar den utökade data typen i sessionen genom att läsa in `Types.ps1xml` filerna i minnet och lägga till nya utökade typ data.

Som standard läser PowerShell in utökade typ data när det behövs. Utan parametrar `Update-TypeData` laddar om alla `Types.ps1xml` filer som har lästs in i sessionen, inklusive alla typer av filer som du har lagt till. Du kan använda parametrarna för `Update-TypeData` för att lägga till nya filfiler och lägga till och ersätta utökade typ data.

`Update-TypeData`Cmdleten kan användas för att förinstallera alla typ data. Den här funktionen är särskilt användbar när du utvecklar typer och vill läsa in de nya typerna i test syfte.

Från och med Windows PowerShell 3,0 kan du använda `Update-TypeData` för att lägga till och ersätta utökade typ data i sessionen utan att använda en `Types.ps1xml` fil. Ange data som läggs till dynamiskt, det vill säga utan att en fil läggs till i den aktuella sessionen. Lägg till ett `Update-TypeData` kommando i din PowerShell-profil om du vill lägga till typ data till alla sessioner. Mer information finns i [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).

Från och med Windows PowerShell 3,0 kan du också använda `Get-TypeData` cmdleten för att hämta de utökade typerna i den aktuella sessionen och `Remove-TypeData` cmdleten för att ta bort utökade typer från den aktuella sessionen.

Undantag som inträffar i egenskaper, eller genom att lägga till egenskaper till ett `Update-TypeData` kommando, rapportera inte fel. Detta är att utelämna undantag som skulle uppstå i många vanliga typer vid formatering och utmatning. Om du får .NET-egenskaper kan du undvika att utelämna undantag genom att använda metoden syntax i stället, som du ser i följande exempel:

`"hello".get_Length()`

Observera att metoden syntax bara kan användas med .NET-egenskaper. Egenskaper som läggs till genom att köra `Update-TypeData` cmdleten kan inte använda Method-syntax.

Mer information om `Types.ps1xml` filerna i PowerShell finns i [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).

## Exempel

### Exempel 1: uppdatera utökade typer

```powershell
Update-TypeData
```

Det här kommandot uppdaterar den utökade typ konfigurationen från `Types.ps1xml` filerna som redan har använts i sessionen.

### Exempel 2: uppdaterings typer flera gånger

Det här exemplet visar hur du uppdaterar typerna i en typ fil flera gånger i samma session.

Det första kommandot uppdaterar den utökade typ konfigurationen från `Types.ps1xml` filerna, bearbetar `TypesA.types.ps1xml` `TypesB.types.ps1xml` filerna och först.

Det andra kommandot visar hur du kan uppdatera `TypesA.types.ps1xml` igen, till exempel om du har lagt till eller ändrat en typ i filen. Du kan antingen upprepa föregående kommando för `TypesA.types.ps1xml` filen eller köra ett `Update-TypeData` kommando utan parametrar, eftersom `TypesA.types.ps1xml` redan finns i listan typ fil för den aktuella sessionen.

```powershell
Update-TypeData -PrependPath TypesA.types.ps1xml, TypesB.types.ps1xml
Update-TypeData -PrependPath TypesA.types.ps1xml
```

### Exempel 3: lägga till en skript egenskap till DateTime-objekt

I det här exemplet används `Update-TypeData` för att lägga till egenskapen för **kvartals** skript i **system. DateTime** -objekt i den aktuella sessionen, till exempel de som returneras av `Get-Date` cmdleten.

```powershell
Update-TypeData -TypeName "System.DateTime" -MemberType ScriptProperty -MemberName "Quarter" -Value {
  if ($this.Month -in @(1,2,3)) {"Q1"}
  elseif ($this.Month -in @(4,5,6)) {"Q2"}
  elseif ($this.Month -in @(7,8,9)) {"Q3"}
  else {"Q4"}
}
(Get-Date).Quarter
```

```Output
Q1
```

`Update-TypeData`Kommandot använder parametern **TypeName** för att ange **system. DateTime** -typen, parametern **MemberName** för att ange ett namn för den nya egenskapen, egenskapen **MemberType** för att ange **ScriptProperty** -typ och **värde** parametern för att ange det skript som avgör det årliga kvartalet.

Värdet för egenskapen **Value** är ett skript som beräknar det aktuella årliga kvartalet. -Skript blocket använder den `$this` automatiska variabeln för att representera den aktuella instansen av objektet och operatorn i för att avgöra om månad svärdet visas i varje heltals mat ris. Mer information om `-in` operatorn finns i [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md).

Det andra kommandot hämtar den nya kvartals egenskapen för det aktuella datumet.

### Exempel 4: uppdatera en typ som visas i listor som standard

I det här exemplet visas hur du anger egenskaperna för en typ som visas i listor som standard, det vill säga när inga egenskaper har angetts. Eftersom typ data inte anges i en `Types.ps1xml` fil, är det bara effektivt i den aktuella sessionen.

```powershell
Update-TypeData -TypeName "System.DateTime" -DefaultDisplayPropertySet "DateTime, DayOfYear, Quarter"
Get-Date | Format-List
```

```Output
Thursday, March 15, 2012 12:00:00 AM
DayOfYear : 75
Quarter   : Q1
```

Det första kommandot använder `Update-TypeData` cmdleten för att ange standard List egenskaperna för **system. DateTime** -typen. Kommandot använder parametern **TypeName** för att ange typ och **DefaultDisplayPropertySet** -parameter för att ange standard egenskaperna för en lista. De valda egenskaperna inkluderar den nya egenskapen för **kvartals** skript som lades till i ett tidigare exempel.

Det andra kommandot använder `Get-Date` cmdleten för att hämta ett **system. DateTime** -objekt som representerar det aktuella datumet. Kommandot använder en pipeline-operator ( `|` ) för att skicka **datetime** -objektet till `Format-List` cmdleten. Eftersom `Format-List` kommandot inte anger vilka egenskaper som ska visas i listan, använder PowerShell standardvärdena som upprättats av `Update-TypeData` kommandot.

### Exempel 5: uppdatera typ data för ett skickas-objekt

```powershell
Get-Module | Update-TypeData -MemberType ScriptProperty -MemberName "SupportsUpdatableHelp" -Value {
  if ($this.HelpInfoUri) {$True} else {$False}
}
Get-Module -ListAvailable | Format-Table Name, SupportsUpdatableHelp
```

```Output
Name                             SupportsUpdatableHelp
----                             ---------------------
Microsoft.PowerShell.Diagnostics                  True
Microsoft.PowerShell.Host                         True
Microsoft.PowerShell.Management                   True
Microsoft.PowerShell.Security                     True
Microsoft.PowerShell.Utility                      True
Microsoft.WSMan.Management                        True
PSDiagnostics                                    False
PSScheduledJob                                    True
PSWorkflow                                        True
ServerManager                                     True
TroubleshootingPack                              False
```

Det här exemplet visar att när du lägger till ett objekt i `Update-TypeData` `Update-TypeData` lägger till utökade typ data för objekt typen.

Den här tekniken går snabbare än att använda- `Get-Member` cmdleten eller `Get-Type` metoden för att hämta objekt typen. Men om du skickar en samling objekt till `Update-TypeData` , uppdaterar den typ data för den första objekt typen och returnerar sedan ett fel för alla andra objekt i samlingen eftersom medlemmen redan har definierats för typen.

Det första kommandot använder `Get-Module` cmdleten för att hämta PSScheduledJob-modulen. Kommandot rör objektet module till `Update-TypeData` cmdleten, som uppdaterar typ data för typen **system. Management. Automation. PSModuleInfo** och de typer som härleds från den, till exempel den ModuleInfoGrouping-typ som `Get-Module` returneras när du använder parametern **ListAvailable** i kommandot.

`Update-TypeData`Kommandona lägger till skript egenskapen **SupportsUpdatableHelp** i alla importerade moduler. Värdet för **Value** -parametern är ett skript som returnerar `$True` om egenskapen **HelpInfoUri** för modulen är ifylld och `$False` annars.

Det andra kommandot rör modul-objekten från `Get-Module` till `Format-Table` cmdleten, som visar **namn** -och **SupportsUpdatableHelp** -egenskaperna för alla moduler i en lista.

## Parametrar

### -AppendPath

Anger sökvägen till valfria `.ps1xml` filer. De angivna filerna läses in i den ordning som de anges efter att de inbyggda filerna har lästs in. Du kan också skicka ett **AppendPath** -värde till `Update-TypeData` .

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -DefaultDisplayProperty

Anger egenskapen för den typ som visas av `Format-Wide` cmdleten när inga andra egenskaper har angetts.

Ange namnet på en standard egenskap eller utökad egenskap av typen. Värdet för den här parametern kan vara namnet på en typ som läggs till i samma kommando.

Det här värdet gäller endast när det inte finns några egna vyer definierade för typen i en `Format.ps1xml` fil.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultDisplayPropertySet

Anger en eller flera egenskaper av typen. Dessa egenskaper visas av `Format-List` cmdleten om inga andra egenskaper anges.

Skriv namnen på standard egenskaper eller utökade egenskaper av typen. Värdet för den här parametern kan vara namnen på de typer som läggs till i samma kommando.

Det här värdet gäller endast när det inte finns några definierade listvyer för typen i en `Format.ps1xml` fil.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultKeyPropertySet

Anger en eller flera egenskaper av typen. Dessa egenskaper används av `Group-Object` `Sort-Object` cmdletarna och när inga andra egenskaper anges.

Skriv namnen på standard egenskaper eller utökade egenskaper av typen. Värdet för den här parametern kan vara namnen på de typer som läggs till i samma kommando.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Anger att cmdleten använder de angivna data typerna, även om typ data redan har angetts för den typen.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DynamicTypeSet, TypeDataSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InheritPropertySerializationSet

Anger om uppsättningen med egenskaper som är serialiserad ärvs. Standardvärdet är `$Null`. De acceptabla värdena för den här parametern är:

- `$True`. Egenskaps uppsättningen ärvs.
- `$False`. Egenskaps uppsättningen ärvs inte.
- `$Null`. Arv har inte definierats.

Den här parametern är endast giltig när värdet för parametern **metoden serializationmethod** är `SpecificProperties` . När värdet för den här parametern är måste `$False` parametern **PropertySerializationSet** anges.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Nullable`1[System.Boolean]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – MemberName

Anger namnet på en egenskap eller metod.

Använd den här parametern med parametrarna **TypeName** , **MemberType** , **Value** och **SecondValue** för att lägga till eller ändra en egenskap eller metod för en typ.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – MemberType

Anger vilken typ av medlem som ska läggas till eller ändras.

Använd den här parametern med parametrarna **TypeName** , **MemberType** , **Value** och **SecondValue** för att lägga till eller ändra en egenskap eller metod för en typ. De acceptabla värdena för den här parametern är:

- AliasProperty
- CodeMethod
- CodeProperty
- Noteproperty
- ScriptMethod
- ScriptProperty

Information om dessa värden finns i [PSMemberTypes-uppräkning](/dotnet/api/system.management.automation.psmembertypes).

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: DynamicTypeSet
Aliases:
Accepted values: NoteProperty, AliasProperty, ScriptProperty, CodeProperty, ScriptMethod, CodeMethod

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PrependPath

Anger sökvägen till de valfria `.ps1xml` filerna. De angivna filerna läses in i den ordning som de anges innan de inbyggda filerna läses in.

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PropertySerializationSet

Anger namn på egenskaper som är serialiserade. Använd den här parametern när värdet för parametern **metoden serializationmethod** är **SpecificProperties**.

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecondValue

Anger ytterligare värden för **AliasProperty** -, **ScriptProperty** -, **CodeProperty** -eller **CodeMethod** -medlemmar.

Använd den här parametern med parametrarna **TypeName** , **MemberType** , **Value** och **SecondValue** för att lägga till eller ändra en egenskap eller metod för en typ.

När värdet för parametern **MemberType** är `AliasProperty` måste värdet för parametern **SecondValue** vara av data typen. PowerShell konverterar (dvs. casts) värdet för egenskapen alias till den angivna typen. Om du till exempel lägger till en aliasresurspost som ger ett alternativt namn för en sträng egenskap, kan du även ange en **SecondValue** för **system. Int32** för att konvertera det aliasna sträng svärdet till ett heltal.

När värdet för parametern **MemberType** är `ScriptProperty` kan du använda parametern **SecondValue** för att ange ytterligare ett skript block. Skript blocket i värdet för parametern **Value** hämtar värdet för en variabel. Skript blocket i värdet för parametern **SecondValue** anger värdet för variabeln.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SerializationDepth

Anger hur många nivåer av typ objekt som serialiseras som strängar. Standardvärdet `1` serialiserar objektet och dess egenskaper. Värdet `0` serialiserar objektet, men inte dess egenskaper. Värdet `2` serialiserar objektet, dess egenskaper och alla objekt i egenskaps värden.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Int32
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### – Metoden serializationmethod

Anger en serialiserings metod för typen. En serialiserings metod avgör vilka egenskaper av typen som serialiseras och den teknik som används för att serialisera dem. De acceptabla värdena för den här parametern är:

- `AllPublicProperties`. Serialisera alla offentliga egenskaper av typen. Du kan använda parametern **SerializationDepth** för att avgöra om underordnade egenskaper är serialiserade.
- `String`. Serialisera typen som en sträng. Du kan använda **StringSerializationSource** för att ange en egenskap av typen som ska användas som serialiserings resultat. Annars serialiseras typen med hjälp av objektets **toString** -metod.
- `SpecificProperties`. Serialisera endast de angivna egenskaperna av den här typen. Använd parametern **PropertySerializationSet** för att ange egenskaperna för den typ som serialiseras.
  Du kan också använda parametern **InheritPropertySerializationSet** för att avgöra om egenskaps uppsättningen ärvs och parametern **SerializationDepth** för att avgöra om underordnade egenskaper är serialiserade.

I PowerShell lagras serialiserings metoder i **PSStandardMembers** interna objekt.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StringSerializationSource

Anger namnet på en egenskap av typen. Värdet för den angivna egenskapen används som serialiserings resultat. Den här parametern är endast giltig när värdet för parametern **metoden serializationmethod** är String.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetTypeForDeserialization

Anger vilken typ av objekt av den här typen som ska konverteras när de deserialiseras.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeAdapter

Anger typ av nätverkskort, till exempel **Microsoft. PowerShell. CIM. CimInstanceAdapter**. Med ett typ kort kan PowerShell Hämta medlemmar av en typ.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – TypeConverter

Anger en typ konverterare för att konvertera värden mellan olika typer. Om en typ konverterare har definierats för en typ används en instans av typ konverteraren för konverteringen.

Ange ett **system. Type** -värde som härleds från klassen **system. ComponentModel. TypeConverter** eller **system. Management. Automation. PSTypeConverter** .

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeData

Anger en matris av typ data som denna cmdlet lägger till i sessionen. Ange en variabel som innehåller ett **TypeData** -objekt eller ett kommando som hämtar ett **TypeData** -objekt, t `Get-TypeData` . ex. ett kommando. Du kan också skicka ett **TypeData** -objekt till `Update-TypeData` .

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.TypeData[]
Parameter Sets: TypeDataSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -TypeName

Anger namnet på den typ som ska utökas.

För typer i **system** namn området anger du det korta namnet. Annars krävs det fullständiga typ namnet. Jokertecken stöds inte.

Du kan skicka pipe-typnamn till `Update-TypeData` . När du rör ett objekt till `Update-TypeData` , `Update-TypeData` hämtar typ namnet för objektet och skriver data till objekt typen.

Använd den här parametern med parametrarna **MemberName** , **MemberType** , **Value** och **SecondValue** för att lägga till eller ändra en egenskap eller metod för en typ.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Värde

Anger värdet för egenskapen eller metoden.

Om du lägger till en `AliasProperty` , `CodeProperty` , eller- `ScriptProperty` `CodeMethod` medlem kan du använda parametern **SecondValue** för att lägga till ytterligare information.

Använd den här parametern med parametrarna **MemberName** , **MemberType** , **Value** och **SecondValue** för att lägga till eller ändra en egenskap eller metod för en typ.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
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

## Indata

### System. String

Du kan skicka vidare en sträng som innehåller värdena för parametrarna **AppendPath** , **TypeName** eller **TypeData** till `Update-TypeData` .

## Utdata

### Inget

Denna cmdlet returnerar inga utdata.

## Kommentarer

## Relaterade länkar

[about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Get-TypeData](Get-TypeData.md)

[Remove-TypeData](Remove-TypeData.md)

