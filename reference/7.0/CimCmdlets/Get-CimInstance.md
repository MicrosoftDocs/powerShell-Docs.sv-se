---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/21/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-ciminstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimInstance
ms.openlocfilehash: edc67596bdb446b18635339255376a17d3f67843
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268437"
---
# Get-CimInstance

## SAMMANFATTNING
Hämtar CIM-instanser för en klass från en CIM-server.

## SYNTAX

### ClassNameComputerSet (standard)

```
Get-CimInstance [-ClassName] <String> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### ResourceUriSessionSet

```
Get-CimInstance -CimSession <CimSession[]> -ResourceUri <Uri> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### QuerySessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

### ClassNameSessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ClassName] <String> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### CimInstanceSessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### CimInstanceComputerSet

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### ResourceUriComputerSet

```
Get-CimInstance -ResourceUri <Uri> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### QueryComputerSet

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

## BESKRIVNING

`Get-CimInstance`Cmdlet: en hämtar CIM-instanser för en klass från en CIM-server. Du kan ange antingen klass namnet eller en fråga för denna cmdlet. Denna cmdlet returnerar ett eller flera CIM-instanser som representerar en ögonblicks bild av CIM-instanserna på CIM-servern.

Om parametern **InputObject** inte anges fungerar cmdleten på något av följande sätt:

- Om varken parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet på lokala Windows Management Instrumentation (WMI) med en Component Object Model (com)-session.
- Om antingen parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet mot CIM-servern som anges av parametern **computername** eller parametern **CimSession** .

Om parametern **InputObject** anges fungerar cmdleten på något av följande sätt:

- Om varken parametern **computername** eller parametern **CimSession** anges, använder denna cmdlet CIM-sessionen eller dator namnet från det indata-objektet.
- Om antingen parametern **computername** eller parametern **CimSession** anges använder den här cmdleten antingen parametern CimSession eller värdet **computername** .

## EXEMPEL

### Exempel 1: Hämta CIM-instanser för en angiven klass

I det här exemplet hämtas CIM-instanser för en klass med namnet **Win32_Process**.

```powershell
Get-CimInstance -ClassName Win32_Process
```

### Exempel 2: Hämta en lista över namn områden från en WMI-Server

I det här exemplet hämtas en lista över namn områden under **rot** namn området på en WMI-Server.

```powershell
Get-CimInstance -Namespace root -ClassName __Namespace
```

### Exempel 3: Hämta instanser av en klass filtrerad med hjälp av en fråga

I det här exemplet hämtas alla CIM-instanser som börjar med bokstaven **P** i en klass med namnet **Win32_Process** med hjälp av frågan som anges av en **frågeparameter** .

```powershell
Get-CimInstance -Query "SELECT * from Win32_Process WHERE name LIKE 'P%'"
```

### Exempel 4: Hämta instanser av en klass filtrerad med hjälp av ett klass namn och ett filter uttryck

I det här exemplet hämtas alla CIM-instanser som börjar med bokstaven **P** i en klass med namnet **Win32_Process** med hjälp av filter parametern.

```powershell
Get-CimInstance -ClassName Win32_Process -Filter "Name like 'P%'"
```

### Exempel 5: Hämta CIM-instanserna med endast nyckel egenskaper ifyllda

Det här exemplet skapar en ny CIM-instans i minnet för en klass med namnet **Win32_Process** med nyckel egenskapen `@{ "Handle"=0 }` och lagrar den i en variabel med namnet `$x` . Variabeln skickas som en CIM-instans till `Get-CimInstance` cmdleten för att hämta en viss instans.

```powershell
$x = New-CimInstance -ClassName Win32_Process -Namespace root\cimv2 -Property @{ "Handle"=0 } -Key Handle -ClientOnly
Get-CimInstance -CimInstance $x
```

### Exempel 6: Hämta CIM-instanser och återanvänd dem

Det här exemplet hämtar CIM-instanser av en klass med namnet **Win32_Process** och lagrar dem i variablerna `$x` och `$y` . Variabeln `$x` formateras sedan i en tabell som endast innehåller egenskaperna **Name** och **KernelModeTime** , vilken tabell som ska anpassas till **AutoSize**.

```powershell
$x,$y = Get-CimInstance -ClassName Win32_Process
$x | Format-Table -Property Name,KernelModeTime -AutoSize
```

```Output
Name                 KernelModeTime
----                 --------------
System Idle Process 157238797968750
```

### Exempel 7: Hämta CIM-instanser från fjärran sluten dator

I det här exemplet hämtas CIM-instanser för en klass med namnet **Win32_ComputerSystem** från fjärrdatorerna med namnet **Server01** och **Server02**.

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName Server01,Server02
```

### Exempel 8: Hämta bara nyckel egenskaperna, i stället för alla egenskaper

I det här exemplet hämtas bara nyckel egenskaperna, vilket minskar storleken på objektet och nätverks trafiken.

```powershell
$x = Get-CimInstance -Class Win32_Process -KeyOnly
$x | Invoke-CimMethod -MethodName GetOwner
```

### Exempel 9: bara hämta en delmängd av egenskaperna, i stället för alla egenskaper

I det här exemplet hämtas endast en del av egenskaperna, vilket minskar storleken på objektet och nätverks trafiken.

```powershell
Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x = Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x | Invoke-CimMethod -MethodName GetOwner
```

Instansen som hämtades med **egenskaps** parametern kan användas för att utföra andra CIM-åtgärder, till exempel `Set-CimInstance` eller `Invoke-CimMethod` .

### Exempel 10: Hämta CIM-instansen med CIM-sessionen

I det här exemplet skapas en CIM-session på datorerna med namnet **Server01** och **Server02** med hjälp av `New-CimSession` cmdleten och lagras sessionsinformation i en variabel med namnet `$s` . Innehållet i variabeln skickas sedan till `Get-CimInstance` med hjälp av parametern **CimSession** för att hämta CIM-instanser av klassen med namnet **Win32_ComputerSystem**.

```powershell
$s = New-CimSession -ComputerName Server01,Server02
Get-CimInstance -ClassName Win32_ComputerSystem -CimSession $s
```

## PARAMETRAR

### – CimSession

Anger den CIM-session som ska användas för denna cmdlet. Ange en variabel som innehåller CIM-sessionen eller ett kommando som skapar eller hämtar CIM-sessionen, till exempel `New-CimSession` `Get-CimSession` cmdletarna eller. Mer information finns i [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, CimInstanceSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

Anger namnet på CIM-klassen som CIM-instanserna ska hämtas för. Du kan använda TABB-slutförande för att bläddra i listan över klasser, eftersom PowerShell hämtar en lista över klasser från den lokala WMI-servern för att tillhandahålla en lista över klass namn.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ComputerName

Anger den dator där du vill köra CIM-åtgärden. Du kan ange ett fullständigt kvalificerat domän namn (FQDN), ett NetBIOS-namn eller en IP-adress. Om du inte anger den här parametern utför cmdleten åtgärden på den lokala datorn med hjälp av Component Object Model (COM).

Om du anger den här parametern skapar cmdleten en tillfällig session till den angivna datorn med hjälp av WsMan-protokollet.

Om flera åtgärder utförs på samma dator ansluter du med en CIM-session för bättre prestanda.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, CimInstanceComputerSet, ResourceUriComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Filter

Anger en WHERE-sats som ska användas som ett filter. Ange satsen i antingen **WQL** -eller **CQL** -frågespråket. Ta inte med `WHERE` nyckelordet i parameterns värde.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – InputObject

Anger ett CIM-instansnamn som ska användas som indatakälla.

Om du redan arbetar med ett CIM-instansnamn kan du använda den här parametern för att skicka CIM-instansnamnet för att hämta den senaste ögonblicks bilden från CIM-servern. När du skickar ett CIM-instansnamn som inmatat, `Get-CimInstance` returnerar objektet från servern med hjälp av en get CIM-åtgärd, i stället för en uppräknings-eller fråga-åtgärd. Att använda en get CIM-åtgärd är mer effektivt än att hämta alla instanser och sedan filtrera dem.

Om CIM-klassen inte implementerar get-åtgärden returnerar **InputObject** -parametern ett fel.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceSessionSet, CimInstanceComputerSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -KeyOnly

Anger att endast objekt med nyckel egenskaper som är ifyllda returneras. Om du anger parametern för **endast** parametern minskas mängden data som överförs över nätverket.

Använd parametern **endast** tangenten om du bara vill returnera en liten del av objektet, som kan användas för andra åtgärder, t `Set-CimInstance` . ex. eller- `Get-CimAssociatedInstance` cmdletar.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Namnrymd

Anger namn området för CIM-klassen.

Standard namn området är **rot-/cimv2**. Du kan använda TABB-slutförande för att bläddra i listan över namn områden, eftersom PowerShell hämtar en lista över namn områden från den lokala WMI-servern för att tillhandahålla listan över namn områden.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

Anger hur lång tid cmdleten väntar på ett svar från datorn. Som standard är värdet för den här parametern 0, vilket innebär att cmdleten använder standardvärdet för timeout för servern.

Om **OperationTimeoutSec** -parametern har angetts till ett värde som är lägre än det stabila anslutnings försöket på 3 minuter, går det inte att återställa nätverks fel som sist mer än värdet för parametern **OperationTimeoutSec** , eftersom åtgärden på servern överskrider innan klienten kan återansluta.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Egenskap

Anger en uppsättning instans egenskaper som ska hämtas. Använd den här parametern när du behöver minska storleken på det returnerade objektet, antingen i minnet eller i nätverket. Det returnerade objektet innehåller också nyckel egenskaperna även om du inte har listat dem med **egenskaps** parametern. Andra egenskaper för klassen finns, men de är inte ifyllda.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases: SelectProperties

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Fråga

Anger en fråga som ska köras på CIM-servern. Om det angivna värdet innehåller dubbla citat tecken `"` , enkla citat tecken `'` eller ett omvänt snedstreck `\` måste du kringgå dessa tecken genom att prefixet med omvänt snedstreck. Om värdet som anges använder WQL-operatorn **som** operator måste du undanta följande tecken genom att omge dem med hakparenteser `[]` : procent `%` , under streck `_` eller inledande hak paren tes `[` .

Du kan inte använda en fråga för metadata för att hämta en lista över klasser eller en händelse fråga. Använd cmdleten om du vill hämta en lista över klasser `Get-CimClass` . Om du vill hämta en händelse fråga använder du `Register-CimIndicationEvent` cmdleten.

Du kan ange dialekten med hjälp av parametern **QueryDialect** .

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -QueryDialect

Anger frågespråket som används för Frågeparametern. De acceptabla värdena för den här parametern är: **WQL** eller **CQL**. Standardvärdet är **WQL**.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QuerySessionSet, ClassNameSessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – ResourceUri

Anger resurs-URI (Uniform Resource Identifier) för resurs klassen eller-instansen. URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.

En URI består av ett prefix och en sökväg till en resurs. Ett exempel:

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

Om du inte anger den här parametern används DMTF-standardresurs-URI som standard `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` och klass namnet läggs till i den.

**ResourceURI** kan endast användas med CIM-sessioner som skapats med WSMan-protokollet, eller när du anger parametern **computername** , som skapar en CIM-session med hjälp av WSMan. Om du anger den här parametern utan att ange parametern **computername** , eller om du anger en CIM-session som skapats med DCOM-protokollet, får du ett fel meddelande eftersom DCOM-protokollet inte stöder parametern **ResourceURI** .

Om både den **ResourceUri** -parametern och **filter** parametern anges, ignoreras **filter** parametern.

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet, QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Lite

Anger att instanserna av en klass returneras utan att inkludera instanser av underordnade klasser. Som standard returnerar cmdleten instanserna för en klass och dess underordnade klasser.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
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

### CIM-instans

Denna cmdlet accepterar ett inobjekt som anges med parametern InputObject.

## UTDATA

### CIM-instans

Denna cmdlet returnerar ett eller flera CIM-instanser som representerar en ögonblicks bild av CIM-instanserna på CIM-servern.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Format-Table](../microsoft.powershell.utility/format-table.md)

[Get-CimAssociatedInstance](Get-CimAssociatedInstance.md)

[Get-CimClass](Get-CimClass.md)

[Invoke-CimMethod](invoke-cimmethod.md)

[New-CimInstance](New-CimInstance.md)

[Registrera – CimIndicationEvent](Register-CimIndicationEvent.md)

[Remove-CimInstance](remove-ciminstance.md)

[Set-CimInstance](Set-CimInstance.md)
