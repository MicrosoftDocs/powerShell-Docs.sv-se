---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Module
ms.openlocfilehash: 487fd85bdcc918b7fb360f9c9d23388a06b35f86
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710501"
---
# New-Module

## SAMMANFATTNING
Skapar en ny dynamisk modul som bara finns i minnet.

## SYNTAX

### Script block (standard)

```
New-Module [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>] [-ReturnResult]
 [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### Namn

```
New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>]
 [-ReturnResult] [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## BESKRIVNING

`New-Module`Cmdleten skapar en dynamisk modul från ett skript block. Medlemmarna i den dynamiska modulen, till exempel Functions och variabler, är omedelbart tillgängliga i sessionen och förblir tillgängliga tills du stänger sessionen.

Precis som statiska moduler exporteras som standard cmdletarna och funktionerna i en dynamisk modul, och variablerna och aliasen är inte. Du kan dock använda Export-ModuleMember-cmdleten och parametrarna för `New-Module` för att åsidosätta standardvärdena.

Du kan också använda **AsCustomObject** -parametern för `New-Module` för att returnera den dynamiska modulen som ett anpassat objekt. Medlemmarna i modulerna, till exempel functions, implementeras som skript metoder för det anpassade objektet i stället för att importeras till sessionen.

Dynamiska moduler finns bara i minnet, inte på disk. Precis som alla moduler körs medlemmarna i dynamiska moduler i en privat modul som är underordnad det globala omfånget. Get-Module kan inte hämta en dynamisk modul, men Get-Command kan hämta de exporterade medlemmarna.

Om du vill göra en dynamisk modul tillgänglig för, kan du skicka ett `Get-Module` `New-Module` kommando till import-module eller skicka en pipe till-objektet som `New-Module` returneras till `Import-Module` . Den här åtgärden lägger till den dynamiska modulen i `Get-Module` listan, men den sparar inte modulen på disken eller gör den beständig.

## EXEMPEL

### Exempel 1: skapa en dynamisk modul

I det här exemplet skapas en ny dynamisk modul med en funktion som kallas `Hello` . Kommandot returnerar ett modul-objekt som representerar den nya dynamiska modulen.

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

### Exempel 2: arbeta med dynamiska moduler och Get-Module och Get-Command

Det här exemplet visar att dynamiska moduler inte returneras av `Get-Module` cmdleten. De medlemmar som exporteras returneras av `Get-Command` cmdleten.

```powershell
new-module -scriptblock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Module

Get-Command Hello
```

```Output
CommandType     Name   Definition
-----------     ----   ----------
Function        Hello  "Hello!"
```

### Exempel 3: exportera en variabel till den aktuella sessionen

I det här exemplet används `Export-ModuleMember` cmdleten för att exportera en variabel till den aktuella sessionen.
Utan `Export-ModuleMember` kommandot exporteras endast funktionen.

```powershell
New-Module -ScriptBlock {$SayHelloHelp="Type 'SayHello', a space, and a name."; function SayHello ($name) { "Hello, $name" }; Export-ModuleMember -function SayHello -Variable SayHelloHelp}
$SayHelloHelp
```

```Output
Type 'SayHello', a space, and a name.
```

```powershell
SayHello Jeffrey
```

```Output
Hello, Jeffrey
```

Resultatet visar att både variabeln och funktionen exporterades till sessionen.

### Exempel 4: gör en dynamisk modul tillgänglig för Get-Module

Det här exemplet visar att du kan göra en dynamisk modul tillgänglig för genom att skicka `Get-Module` den dynamiska modulen till `Import-Module` .

`New-Module` skapar ett modul-objekt som är skickas till `Import-Module` cmdleten. Parametern **Name** i `New-Module` tilldelar modulen ett eget namn. Eftersom inte `Import-Module` returnerar några objekt som standard, finns det inga utdata från det här kommandot. `Get-Module` att **GreetingModule** har importer ATS till den aktuella sessionen.

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}} -name GreetingModule | Import-Module
Get-Module
```

```Output
Name              : GreetingModule
Path              : d54dfdac-4531-4db2-9dec-0b4b9c57a1e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Command hello
```

```Output
CommandType     Name                                                               Definition
-----------     ----                                                               ----------
Function        Hello                                                              "Hello!"
```

`Get-Command`Cmdleten visar den `Hello` funktion som den dynamiska modulen exporterar.

### Exempel 5: generera ett anpassat objekt som har exporterade funktioner

Det här exemplet visar hur du använder **AsCustomObject** -parametern för `New-Module` för att skapa ett anpassat objekt som har skript metoder som representerar de exporterade funktionerna.

`New-Module`Cmdleten skapar en dynamisk modul med två funktioner `Hello` och `Goodbye` . Parametern **AsCustomObject** skapar ett anpassat objekt i stället för **PSModuleInfo** -objektet som `New-Module` genererar som standard. Det här anpassade objektet sparas i `$m` variabeln.
`$m`Variabeln verkar inte ha ett tilldelat värde.

```powershell
$m = New-Module -ScriptBlock {
  function Hello ($name) {"Hello, $name"}
  function Goodbye ($name) {"Goodbye, $name"}
} -AsCustomObject
$m
$m | Get-Member
```

```Output
TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Goodbye     ScriptMethod System.Object Goodbye();
Hello       ScriptMethod System.Object Hello();
```

```powershell
$m.goodbye("Jane")
```

```Output
Goodbye, Jane
```

```powershell
$m.hello("Manoj")
```

```Output
Hello, Manoj
```

I- `$m` `Get-Member` cmdleten visas egenskaper och metoder för det anpassade objektet. Utdata visar att objektet har skript metoder som representerar-och- `Hello` `Goodbye` funktionerna.
Slutligen anropar vi dessa skript metoder och visar resultatet.

### Exempel 6: Hämta resultatet från skript blocket

I det här exemplet används parametern **ReturnResult** för att begära resultatet av att köra skript blocket i stället för att begära ett modul-objekt. Skript blocket i den nya modulen definierar `SayHello` funktionen och anropar sedan funktionen.

```powershell
New-Module -ScriptBlock {function SayHello {"Hello, World!"}; SayHello} -ReturnResult
```

```Output
Hello, World!
```

## PARAMETRAR

### – Argument List

Anger en matris med argument som är parameter värden som skickas till skript blocket. Mer information om beteendet för **argument List** finns [about_Splatting](about/about_Splatting.md#splatting-with-arrays).

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

### -AsCustomObject

Anger att denna cmdlet returnerar ett anpassat objekt som representerar den dynamiska modulen. Modulens medlemmar implementeras som skript metoder för det anpassade objektet, men de importeras inte till sessionen. Du kan spara det anpassade objektet i en variabel och använda punkt notation för att anropa medlemmarna.

Om modulen har flera medlemmar med samma namn, till exempel en funktion och en variabel som både heter A, kan bara en medlem med varje namn nås från det anpassade objektet.

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

### -Cmdlet

Anger en matris med cmdletar som denna cmdlet exporterar från modulen till den aktuella sessionen.
Ange en kommaavgränsad lista med cmdletar. Jokertecken är tillåtna. Som standard exporteras alla cmdletar i modulen.

Det går inte att definiera cmdletar i ett-skript block, men en dynamisk modul kan innehålla cmdletar om den importerar cmdlets från en binär modul.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Funktion

Anger en matris med funktioner som denna cmdlet exporterar från modulen till den aktuella sessionen.
Ange en kommaavgränsad lista med funktioner. Jokertecken är tillåtna. Som standard exporteras alla funktioner som definierats i en modul.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

Anger ett namn för den nya modulen. Du kan också skicka ett modulnamn till en ny modul.

Standardvärdet är ett automatiskt genererat namn som börjar med `__DynamicModule_` och följt av ett GUID som anger sökvägen till den dynamiska modulen.

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ReturnResult

Anger att den här cmdleten kör skript blocket och returnerar skript block resultatet i stället för att returnera ett modul objekt.

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

### – Script block

Anger innehållet i den dynamiska modulen. Omge innehållet i klammerparenteser ( `{}` ) för att skapa ett skript block. Den här parametern är obligatorisk.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare ett modulnamn till denna cmdlet.

## UTDATA

### System. Management. Automation. PSModuleInfo, system. Management. Automation. PSCustomObject eller none

Denna cmdlet genererar ett **PSModuleInfo** -objekt som standard. Om du använder parametern **AsCustomObject** genereras ett **PSCustomObject** -objekt. Om du använder parametern **ReturnResult** , returnerar den resultatet av att utvärdera skript blocket i den dynamiska modulen.

## ANTECKNINGAR

Du kan också referera till `New-Module` baserat på dess alias `nmo` . Mer information finns i [about_Aliases](About/about_Aliases.md).

## RELATERADE LÄNKAR

[Exportera – ModuleMember](Export-ModuleMember.md)

[Hämta modul](Get-Module.md)

[Importera-modul](Import-Module.md)

[Ta bort modul](Remove-Module.md)

