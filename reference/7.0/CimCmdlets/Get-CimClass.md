---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimclass?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimClass
ms.openlocfilehash: 2fd87935e2594a643327d2ae07fad112b1b9386f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262149"
---
# Get-CimClass

## SAMMANFATTNING
Hämtar en lista över CIM-klasser i en angiven namnrymd.

## SYNTAX

### ComputerSet (standard)

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

### SessionSet

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

## BESKRIVNING

`Get-CimClass`Cmdlet: en hämtar en lista över CIM-klasser i en angiven namnrymd. Om inget klass namn har angetts returnerar cmdleten alla klasser i namn området. Till skillnad från en CIM-instans innehåller CIM-klasser inte CIM-sessionen eller dator namnet som de hämtas från.

## EXEMPEL

### Exempel 1: Hämta alla klass definitioner

Det här exemplet hämtar alla klass definitioner under namn områdets **rot-/cimv2**.

```powershell
Get-CimClass
```

### Exempel 2: Hämta klasserna med ett angivet namn

Det här exemplet hämtar de klasser som innehåller ordet **disk** i sina namn.

```powershell
Get-CimClass -ClassName *disk*
```

### Exempel 3: Hämta klasserna med ett angivet metod namn

Det här exemplet hämtar de klasser som börjar med namnet **Win32** och har ett metod namn som börjar med **term**.

```powershell
Get-CimClass -ClassName Win32* -MethodName Term*
```

### Exempel 4: Hämta klasserna med ett angivet egenskaps namn

Det här exemplet hämtar de klasser som börjar med namnet **Win32** och har en egenskap med namnet **handle**.

```powershell
Get-CimClass -ClassName Win32* -PropertyName Handle
```

### Exempel 5: Hämta klasserna med ett angivet kvalificerande namn

Det här exemplet hämtar de klasser som börjar med namnet **Win32** , innehåller ordet **disk** i sina namn och har den angivna kvalificerande **associationen**.

```powershell
Get-CimClass -ClassName Win32*Disk* -QualifierName Association
```

### Exempel 6: Hämta klass definitionerna från ett angivet namn område

Det här exemplet hämtar klass definitionerna som innehåller ordet **net** i sina namn från den angivna **rot-/standardCimv2** för namn området.

```powershell
Get-CimClass -Namespace root/standardCimv2 -ClassName *Net*
```

### Exempel 7: Hämta klass definitionerna från en fjärrserver

I det här exemplet hämtas klass definitionerna som innehåller ordet **disk** i namnen från de angivna fjärrservrarna **Server01** och **Server02**.

```powershell
Get-CimClass -ClassName *disk* -ComputerName Server01, Server02
```

### Exempel 8: Hämta klasserna med en CIM-session

```powershell
$s = New-CimSession -ComputerName Server01, Server02
Get-CimClass -ClassName *disk* -CimSession $s
```

Den här uppsättningen kommandon skapar en session med flera datorer och lagrar den i en variabel `$s` med hjälp av `New-CimSession` cmdleten och hämtar sedan klasserna med hjälp av `Get-CimClass` cmdleten.

## PARAMETRAR

### – CimSession

Kör cmdleten i en fjärran sluten session eller på en fjärrdator. Ange ett dator namn eller ett sessionsobjekt, till exempel utdata för en- `New-CimSession` eller- `Get-CimSession` cmdlet. Standardvärdet är den aktuella sessionen på den lokala datorn.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: SessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

Anger namnet på CIM-klassen som åtgärden ska utföras för. Du kan använda TABB-slutförande för att bläddra i listan över klasser, eftersom PowerShell hämtar en lista över klasser från den lokala WMI-servern för att tillhandahålla en lista över klass namn.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ComputerName

Anger den dator som du vill köra CIM-åtgärden på. Du kan ange ett fullständigt kvalificerat domän namn (FQDN) ett NetBIOS-namn eller en IP-adress.

Om du anger den här parametern skapar cmdleten en tillfällig session till den angivna datorn med hjälp av WsMan-protokollet.

Om du inte anger den här parametern utför cmdleten åtgärden på den lokala datorn med hjälp av Component Object Model (COM).

Om flera åtgärder utförs på samma dator ger det bättre prestanda om du använder en CIM-session.

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – MethodName

Söker efter klasser som har en metod som matchar det här namnet. Du kan använda jokertecken med den här parametern.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### – Namnrymd

Anger namn området för CIM-åtgärden. Standard namn området är **rot-/cimv2**. Du kan använda TABB-slutförande för att bläddra i listan över namn områden, eftersom PowerShell hämtar en lista över namn områden från den lokala WMI-servern för att tillhandahålla listan över namn områden.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
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
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PropertyName

Söker efter klasser som har en egenskap som matchar det här namnet. Du kan använda jokertecken med den här parametern.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -QualifierName

Filtrerar klasserna efter kvalificerande namn på klass nivå. Du kan använda jokertecken med den här parametern.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Denna cmdlet accepterar inga inobjekt.

## UTDATA

### Microsoft. Management. Infrastructure. CimClass

Den här cmdleten returnerar ett CIM Class-objekt.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[New-CimSession](New-CimSession.md)
