---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-ciminstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimInstance
ms.openlocfilehash: d6eab5d6fcf1c4d983f2502465d76ad5df1db9dd
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268124"
---
# New-CimInstance

## SAMMANFATTNING
Skapar en CIM-instans.

## SYNTAX

### ClassNameComputerSet (standard)

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ClassNameSessionSet

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ResourceUriSessionSet

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ResourceUriComputerSet

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### CimClassSessionSet

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimClassComputerSet

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`New-CimInstance`Cmdleten skapar en instans av en CIM-klass baserat på klass definitionen på antingen den lokala datorn eller en fjärrdator. Som standard `New-CimInstance` skapar cmdleten en instans på den lokala datorn.

## EXEMPEL

### Exempel 1: skapa en instans av en CIM-klass

I det här exemplet skapas en instans av en CIM-klass med namnet win32_environment i namn området root/cimv2 på datorn.

```powershell
New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";VariableValue="testvalue";UserName="domain\user"}
```

Ingen verifiering på klient sidan utförs om klassen inte finns, egenskaperna är fel eller om servern avvisar anropet. Om instansen har skapats, matar cmdleten ut den nyss skapade instansen.

### Exempel 2: skapa en instans av en CIM-klass med ett klass schema

I det här exemplet hämtas ett CIM Class-objekt och lagras det i en variabel med namnet `$class` . Innehållet i variabeln skickas sedan till- `New-CimInstance` cmdleten.

```powershell
$class = Get-CimClass -ClassName Win32_Environment
New-CimInstance -CimClass $class -Property @{Name="testvar";VariableValue="testvalue";UserName="Contoso\User1"}
```

### Exempel 3: skapa en dynamisk instans på klienten

Det här exemplet skapar en dynamisk instans av en CIM-klass med namnet **Win32_Process** på klient datorn utan att hämta instansen från servern. Den nya instansen lagras i variabeln `$a` . Den här dynamiska instansen kan användas för att utföra åtgärder om instansen med den här nyckeln finns på servern.

```powershell
$a = New-CimInstance -ClassName Win32_Process -Property @{Handle=0} -Key Handle -ClientOnly
Get-CimInstance -CimInstance $a
Invoke-CimMethod -CimInstance $a -MethodName GetOwner
```

```Output
ProcessId Name                HandleCount WorkingSetSize VirtualSize
--------- ----                ----------- -------------- -----------
0         System Idle Process 0           8192           8192

Domain         :
ReturnValue    : 2
User           :
PSComputerName :
```

`Get-CimInstance`Cmdlet: en hämtar sedan en viss instans. `Invoke-CimMethod`Cmdleten anropar metoden **GetOwner** på den hämtade instansen.

### Exempel 4: skapa en instans för en CIM-klass för en angiven namnrymd

Det här exemplet hämtar en instans av en CIM-klass med namnet **MSFT_Something** i namn rymds **roten/någonstans** och lagrar den i en variabel med namnet `$class` . Variabeln skickas till cmdlet: `New-CimInstance` en för att skapa en ny CIM-instans och utföra verifieringar på klient sidan på den nya instansen.

```powershell
$class = Get-CimClass -ClassName MSFT_Something -Namespace root/somewhere
New-CimInstance -CimClass $class -Property @{"Prop1"=1;"Prop2"="value"} -ClientOnly
```

I det här exemplet kan du använda parametern **CimClass** i stället för parametern **className** för att verifiera att **Prop1** och **Prop2** faktiskt finns och att nycklarna har marker ATS som de ska.

Du kan inte använda parametern **computername** eller **CimSession** med parametern **ClientOnly** .

## PARAMETRAR

### -CimClass

Anger ett CIM-klassnamn som representerar instans typen. Använd `Get-CimClass` cmdleten för att hämta klass deklarationen från en dator. Genom att använda den här parametern resulterar det bättre verifieringar på klient sidan.

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassSessionSet, CimClassComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – CimSession

Kör kommandot med den angivna CIM-sessionen. Ange en variabel som innehåller CIM-sessionen, eller ett kommando som skapar eller hämtar CIM-sessionen, t. ex `New-CimSession` . eller- `Get-CimSession` cmdletar. Mer information finns i [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, ResourceUriSessionSet, CimClassSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

Anger namnet på CIM-klassen som åtgärden skapar en instans för. Obs! Du kan använda TABB-slutförande för att bläddra i listan över klasser, eftersom PowerShell hämtar en lista över klasser från den lokala WMI-servern för att tillhandahålla en lista över klass namn.

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

### -ClientOnly

Anger att instansen bara skapas i PowerShell utan att gå till CIM-servern. Du kan använda den här parametern för att skapa en intern CIM-instans för användning i efterföljande PowerShell-åtgärder.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, CimClassSessionSet, CimClassComputerSet
Aliases: Local

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Anger namnet på den dator som du vill köra CIM-åtgärden på. Du kan ange ett fullständigt kvalificerat domän namn (FQDN), ett NetBIOS-namn eller en IP-adress.

Om du anger den här parametern skapar cmdleten en tillfällig session till den angivna datorn med hjälp av WSMan-protokollet.

Om du inte anger den här parametern utför cmdleten åtgärden på den lokala datorn med hjälp av Component Object Model (COM).

Om flera åtgärder utförs på samma dator ger det bättre prestanda om du ansluter med en CIM-session.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Nyckel

Anger de egenskaper som används som nycklar. Det går inte att använda **CimSession** och **computername** när **nyckeln** har angetts.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Namnrymd

Anger namn området för klassen för den nya instansen. Standard namn området är **rot-/cimv2**.
Du kan använda TABB-slutförande för att bläddra i listan över namn områden, eftersom PowerShell hämtar en lista över namn områden från den lokala WMI-servern för att tillhandahålla listan över namn områden.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

Anger hur lång tid cmdleten väntar på ett svar från CIM-servern. Som standard är värdet för den här parametern 0, vilket innebär att cmdleten använder standardvärdet för timeout för servern. Om **OperationTimeoutSec** -parametern har angetts till ett värde som är lägre än det stabila anslutnings försöket på 3 minuter, går det inte att återställa nätverks fel som sist mer än värdet för parametern **OperationTimeoutSec** , eftersom åtgärden på servern överskrider innan klienten kan återansluta.

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

Anger egenskaperna för CIM-instansen med hjälp av en hash-tabell (namn-värdepar).

Om du anger parametern **CimClass** `New-CimInstance` utför cmdleten en egenskaps validering på klienten för att kontrol lera att de angivna egenskaperna är konsekventa med klass deklarationen på servern. Om parametern **CimClass** inte anges, utförs egenskaps valideringen på servern.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases: Arguments

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – ResourceUri

Anger resurs-URI (Uniform Resource Identifier) för resurs klassen eller-instansen. URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.

En URI består av ett prefix och en sökväg till en resurs. Ett exempel:

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

Om du inte anger den här parametern används DMTF-standardresurs-URI som standard `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` och klass namnet läggs till i den.

**ResourceURI** kan endast användas med CIM-sessioner som skapats med WSMan-protokollet, eller när du anger parametern **computername** , som skapar en CIM-session med hjälp av WSMan. Om du anger den här parametern utan att ange parametern **computername** , eller om du anger en CIM-session som skapats med DCOM-protokollet, får du ett fel meddelande eftersom DCOM-protokollet inte stöder parametern **ResourceURI** .

Om både den **ResourceUri** -parametern och **filter** parametern anges, ignoreras **filter** parametern.

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: True
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

### Inget

Denna cmdlet accepterar inga inobjekt.

## UTDATA

### System. Object

Den här cmdleten returnerar ett objekt som innehåller CIM-instansnamnet.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-CimClass](get-cimclass.md)

[Get-CimInstance](get-ciminstance.md)

[Remove-CimInstance](remove-ciminstance.md)

[Set-CimInstance](Set-CimInstance.md)
