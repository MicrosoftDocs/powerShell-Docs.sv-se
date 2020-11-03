---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/set-ciminstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-CimInstance
ms.openlocfilehash: 9d68e59cf00e94a2318190800c47a4248a384e6f
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268425"
---
# Set-CimInstance

## SAMMANFATTNING
Ändrar en CIM-instans på en CIM-server genom att anropa ModifyInstance-metoden för CIM-klassen.

## SYNTAX

### CimInstanceComputerSet (standard)

```
Set-CimInstance [-ComputerName <String[]>] [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimInstanceSessionSet

```
Set-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### QuerySessionSet

```
Set-CimInstance -CimSession <CimSession[]> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### QueryComputerSet

```
Set-CimInstance [-ComputerName <String[]>] [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

Denna cmdlet ändrar en CIM-instans på en CIM-server.

Om parametern **InputObject** inte anges fungerar cmdleten på något av följande sätt:

- Om varken parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet på lokala Windows Management Instrumentation (WMI) med en Component Object Model (com)-session.
- Om antingen parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet mot CIM-servern som anges av parametern **computername** eller parametern **CimSession** .

Om parametern **InputObject** anges fungerar cmdleten på något av följande sätt:

- Om varken parametern **computername** eller parametern **CimSession** anges, använder denna cmdlet CIM-sessionen eller dator namnet från det indata-objektet.
- Om antingen parametern **computername** eller parametern **CimSession** anges använder den här cmdleten antingen parametern **CimSession** eller värdet **computername** . Detta är inte särskilt vanligt.

## EXEMPEL

### Exempel 1: Ange CIM-instansen

I det här exemplet anges värdet för egenskapen **VariableValue** till **ABCD** med **Frågeparametern** . Du kan ändra instanser som matchar en WQL-fråga (Windows Management Instrumentation Query Language).

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"}
```

### Exempel 2: Ange CIM instance-egenskapen med pipelinen

I det här exemplet hämtas CIM-instansnamnet som filtrerats av **Frågeparametern** med `Get-CimInstance` cmdleten. `Set-CimInstance`Cmdleten ändrar värdet för egenskapen **VariableValue** till **ABCD**.

```powershell
Get-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' |
  Set-CimInstance -Property @{VariableValue="abcd"}
```

### Exempel 3: Ange CIM instance-egenskapen med indatamängds objekt

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where Name="testvar"'
Set-CimInstance -InputObject $x -Property @{VariableValue="somevalue"} -PassThru
```

I det här exemplet hämtas CIM-instansnamnet som filtrerats efter frågeparametern i till en variabel `$x` med `Get-CimInstance` och skickar sedan innehållet i variabeln till- `Set-CimInstance` cmdleten. `Set-CimInstance` ändrar sedan egenskapen **VariableValue** till **someValue**. Eftersom parametern **Passthru** används, returnerar det här exemplet ett ändrat CIM-instansnamn.

### Exempel 4: Ange CIM instance-egenskapen

I det här exemplet hämtas CIM instance-objektet som anges i **Frågeparametern** till en variabel `$x` med hjälp av `Get-CimInstance` cmdleten, och egenskapen **VariableValue** för objektet ändras. CIM instans-objektet sparas sedan med `Set-CimInstance` cmdleten.
Eftersom parametern **Passthru** används, returnerar det här exemplet ett ändrat CIM-instansnamn.

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where name="testvar"'
$x.VariableValue = "Change"
Set-CimInstance -CimInstance $x -PassThru
```

### Exempel 5: Visa listan över CIM-instanser som ska ändras med WhatIf

I det här exemplet används den gemensamma parametern **whatIf** för att ange att ändringen inte ska göras, men endast utdata som skulle inträffa om den är färdig.

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -WhatIf
```

### Exempel 6: Ange CIM-instansen efter bekräftelse från användaren

I det här exemplet används den gemensamma parametern **Bekräfta** för att ange att ändringen endast ska utföras efter bekräftelse från användaren.

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -Confirm
```

### Exempel 7: Ange den skapade CIM-instansen

Det här exemplet skapar en CIM-instans med de angivna egenskaperna med hjälp av `New-CimInstance` cmdleten och hämtar dess innehåll i en variabel `$x` . Variabeln skickas sedan till `Set-CimInstance` cmdleten, som ändrar värdet för egenskapen **VariableValue** till **someValue**.
Eftersom parametern **Passthru** används, returnerar det här exemplet ett ändrat CIM-instansnamn.

```powershell
$x = New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";UserName="domain\user"} -Keys Name,UserName -ClientOnly
Set-CimInstance -CimInstance $x -Property @{VariableValue="somevalue"} -PassThru
```

## PARAMETRAR

### – CimSession

Kör cmdletarna på en fjärrdator. Ange ett dator namn eller ett sessionsobjekt, till exempel utdata för en- `New-CimSession` eller- `Get-CimSession` cmdlet.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimInstanceSessionSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName

Anger namnet på den dator som du vill köra CIM-åtgärden på. Du kan ange ett fullständigt kvalificerat domän namn (FQDN) eller ett NetBIOS-namn.

Om du inte anger den här parametern utför cmdleten åtgärden på den lokala datorn med hjälp av Component Object Model (COM).

Om du anger den här parametern skapar cmdleten en tillfällig session till den angivna datorn med hjälp av WsMan-protokollet.

Om flera åtgärder utförs på samma dator ger det bättre prestanda om du ansluter med en CIM-session.

```yaml
Type: System.String[]
Parameter Sets: CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger ett CIM-instansnamn som ska användas som indatakälla.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – Namnrymd

Anger namn området för CIM-åtgärden. Standard namn området är rot-/cimv2. Du kan använda TABB-slutförande för att bläddra i listan över namn områden, eftersom PowerShell hämtar en lista över namn områden från den lokala WMI-servern för att tillhandahålla listan över namn områden.

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
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

### – PassThru

Returnerar ett objekt som representerar det objekt som du arbetar med. Som standard genererar denna cmdlet inga utdata.

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

### – Egenskap

Anger egenskaperna för CIM-instansen som en hash-tabell (med namn-värdepar). Endast de egenskaper som anges med den här parametern ändras. Andra egenskaper för CIM-instansen ändras inte.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet, QuerySessionSet, QueryComputerSet
Aliases: Arguments

Required: True (QuerySessionSet, QueryComputerSet), False (CimInstanceComputerSet, CimInstanceSessionSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Fråga

Anger en fråga som ska köras på CIM-servern för att hämta CIM-instanser som cmdleten ska köras på. Du kan ange dialekten med hjälp av parametern QueryDialect.

Om det angivna värdet innehåller dubbla citat tecken ( `"` ), enkla citat tecken ( `'` ) eller ett omvänt snedstreck ( `\` ) måste du undanta dessa tecken genom att prefixet med omvänt snedstreck ( `\` ). Om värdet som anges använder WQL-operatorn **som** operator måste du undanta följande tecken genom att omsluta dem inom hak paren tes ( `[]` ): procent ( `%` ), under streck ( `_` ) eller inledande hak paren tes ( `[` ).

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -QueryDialect

Anger frågespråket som används för Frågeparametern. De acceptabla värdena för den här parametern är: **WQL** eller **CQL**. Standardvärdet är **WQL**.

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
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

ResourceURI kan endast användas med CIM-sessioner som skapats med WSMan-protokollet, eller när du anger parametern ComputerName, som skapar en CIM-session med hjälp av WSMan. Om du anger den här parametern utan att ange parametern ComputerName, eller om du anger en CIM-session som skapats med DCOM-protokollet, får du ett fel meddelande eftersom DCOM-protokollet inte stöder parametern ResourceURI.

Om både den **ResourceUri** -parametern och **filter** parametern anges, ignoreras **filter** parametern.

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### Microsoft. Management. Infrastructure. CimInstance

## UTDATA

### Microsoft. Management. Infrastructure. CimInstance

När parametern **Passthru** anges returnerar denna cmdlet ett ändrat CIM-instansnamn.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-CimInstance](get-ciminstance.md)

[New-CimInstance](New-CimInstance.md)

[Remove-CimInstance](remove-ciminstance.md)
