---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimassociatedinstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimAssociatedInstance
ms.openlocfilehash: adf6c1ac6f6f9288233d530b7ea2101f4b7688e4
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268245"
---
# Get-CimAssociatedInstance

## SAMMANFATTNING
Hämtar CIM-instanser som är anslutna till en angiven CIM-instans av en Association.

## SYNTAX

### ComputerSet (standard)

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] [-ComputerName <String[]>] [-KeyOnly] [<CommonParameters>]
```

### SessionSet

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] -CimSession <CimSession[]> [-KeyOnly] [<CommonParameters>]
```

## BESKRIVNING

`Get-CimAssociatedInstance`Cmdlet: en hämtar CIM-instanser som är anslutna till en angiven CIM-instans, som kallas käll instans, av en Association.

I en Association har varje CIM-instans en namngiven roll och samma CIM-instans kan ingå i en Association i olika roller.

Om parametern InputObject inte anges fungerar cmdleten på något av följande sätt:

- Om varken parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet på lokala Windows Management Instrumentation (WMI) med en Component Object Model (com)-session.
- Om antingen parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet mot CIM-servern som anges av parametern **computername** eller parametern **CimSession** .

## EXEMPEL

### Exempel 1: Hämta alla associerade instanser av en angiven instans

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1]
```

Den här uppsättningen kommandon hämtar instanserna av klassen med namnet Win32_LogicalDisk och lagrar informationen i en variabel med namnet `$disk` med hjälp av `Get-CimInstance` cmdleten. Den första logiska disk instansen i variabeln används sedan som indataports objekt för `Get-CimAssociatedInstance` cmdleten för att hämta alla associerade CIM-instanser av den angivna CIM-instansen.

### Exempel 2: Hämta alla associerade instanser av en speciell typ

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1] -ResultClass Win32_DiskPartition
```

Den här uppsättningen kommandon hämtar alla instanser av klassen **Win32_LogicalDisk** och lagrar dem i en variabel med namnet `$disk` . Den första logiska disk instansen i variabeln används sedan som indataports objekt för `Get-CimAssociatedInstance` cmdleten för att hämta alla associerade instanser som är associerade med den angivna Associations klassen **Win32_DiskPartition**.

### Exempel 3: Hämta alla associerade instanser genom att kvalificera en speciell klass

```powershell
$s = Get-CimInstance -Query "Select * from Win32_Service where name like 'Winmgmt'"
Get-CimClass -ClassName *Service* -Qualifier "Association"
$c.CimClasName
```

```Output
Win32_LoadOrderGroupServiceDependencies
Win32_DependentService
Win32_SystemServices
Win32_LoadOrderGroupServiceMembers
Win32_ServiceSpecificationService
```

```powershell
Get-CimAssociatedInstance -InputObject $s -Association Win32_DependentService
```

Den här uppsättningen kommandon hämtar de tjänster som är beroende av WMI-tjänsten och lagrar dem i en variabel med namnet `$s` . Associations klass namnet för **Win32_DependentService** hämtas med hjälp av `Get-CimClass` cmdleten genom att ange **Association** som kvalificerare och skickas sedan med $s till `Get-CimAssociatedInstance` cmdleten för att hämta alla associerade instanser av den hämtade Associations klassen.

## PARAMETRAR

### -Association

Anger namnet på Associations klassen. Om du inte anger den här parametern, returnerar cmdleten alla befintliga Associations objekt av valfri typ.

Om klass A till exempel är associerad med klass B via två associationer, AB1 och AB2, kan den här parametern användas för att ange typ av Association, antingen AB1 eller AB2.

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

### – CimSession

Kör kommandot med den angivna CIM-sessionen. Ange en variabel som innehåller CIM-sessionen, eller ett kommando som skapar eller hämtar CIM-sessionen, till exempel `New-CimSession` eller `Get-CimSession` . Mer information finns i [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).

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

### -ComputerName

Anger namnet på den dator som du vill köra CIM-åtgärden på. Du kan ange ett fullständigt kvalificerat domän namn (FQDN) eller ett NetBIOS-namn.

Om du anger den här parametern skapar cmdleten en tillfällig session till den angivna datorn med hjälp av WsMan-protokollet.

Om du inte anger den här parametern utför cmdleten åtgärden på den lokala datorn med hjälp av Component Object Model (COM).

Om flera åtgärder utförs på samma dator ger det bättre prestanda om du ansluter med en CIM-session.

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger indatamängden för denna cmdlet. Du kan använda den här parametern, eller så kan du skicka en pipe till denna cmdlet.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -KeyOnly

Returnerar objekt med enbart nyckel egenskaper ifyllda. Detta minskar mängden data som överförs via nätverket.

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

### – Namnrymd

Anger namn området för CIM-åtgärden. Standard namn området är rot-/cimv2.

> [!NOTE]
> Du kan använda TABB-slutförande för att bläddra i listan över namn områden, eftersom PowerShell hämtar en lista över namn områden från den lokala WMI-servern för att tillhandahålla listan över namn områden.

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

### – ResourceUri

Anger resurs-URI (Uniform Resource Identifier) för resurs klassen eller-instansen. URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.

En URI består av ett prefix och en sökväg till en resurs. Ett exempel:

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

Om du inte anger den här parametern används DMTF-standardresurs-URI som standard `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` och klass namnet läggs till i den.

**ResourceURI** kan endast användas med CIM-sessioner som skapats med WSMan-protokollet, eller när du anger parametern **computername** , som skapar en CIM-session med hjälp av WSMan. Om du anger den här parametern utan att ange parametern **computername** , eller om du anger en CIM-session som skapats med DCOM-protokollet, uppstår ett fel, eftersom DCOM-protokollet inte stöder parametern **ResourceURI** .

Om både den **ResourceUri** -parametern och **filter** parametern anges, ignoreras **filter** parametern.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResultClassName

Anger klass namnet för de associerade instanserna. En CIM-instans kan associeras med en eller flera CIM-instanser. Alla associerade CIM-instanser returneras om du inte anger namnet på resultat klassen.

Som standard är värdet för den här parametern null och alla associerade CIM-instanser returneras.

Du kan filtrera kopplings resultaten så att de matchar ett angivet klass namn. Filtreringen sker på servern. Om den här parametern inte anges `Get-CIMAssociatedInstance` returnerar alla befintliga associationer. Om klass A till exempel är kopplad till klass B, C och D, kan den här parametern användas för att begränsa utdata till en specifik typ (B, C eller D).

```yaml
Type: System.String
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

Denna cmdlet accepterar inga inobjekt.

## UTDATA

### System. Object

Den här cmdleten returnerar ett objekt.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-CimClass](get-cimclass.md)

[Get-CimInstance](get-ciminstance.md)
