---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 10/15/2020
online version: ''
schema: 2.0.0
ms.openlocfilehash: 34998e7c4a6876821df949019970dc1d87297397
ms.sourcegitcommit: c9e56ec489522c706b8d6b8733f3f015d6d7e893
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272919"
---
# Get-PSSubsystem

## SAMMANFATTNING
Hämtar information om de under system som registrerats i PowerShell.

## SYNTAX

### GetAllSet (standard)

```
Get-PSSubsystem [<CommonParameters>]
```

### GetByKindSet

```
Get-PSSubsystem -Kind <SubsystemKind> [<CommonParameters>]
```

### GetByTypeSet

```
Get-PSSubsystem -SubsystemType <Type> [<CommonParameters>]
```

## BESKRIVNING

Hämtar information om de under system som registrerats i PowerShell.

> [!NOTE]
> Det här är en experimentell funktion. Den här cmdleten är endast tillgänglig om `PSSubsystemPluginModel` funktionen är aktive rad. Mer information finns i [använda experimentella funktioner](/powershell/scripting/learn/experimental-features).

Funktionen gör det möjligt att separera komponenter i `System.Management.Automation.dll` enskilda under system som finns i en egen sammansättning. Den här separationen minskar den grundläggande PowerShell-motorns disk utrymme och gör att dessa komponenter blir valfria funktioner för en minimal PowerShell-installation.

För närvarande stöds endast under systemet **CommandPredictor** . Det här del systemet används tillsammans med PSReadLine-modulen för att tillhandahålla anpassade förutsägelse-plugin-program. I framtiden kan **jobb** , **CommandCompleter** , **fjärr kommunikation** och andra komponenter delas upp i del system sammansättningar utanför `System.Management.Automation.dll` .

## EXEMPEL

### Exempel 1 – Visa alla tillgängliga under system

```powershell
Get-PSSubsystem
```

```Output
Kind              SubsystemType     IsRegistered Implementations
----              -------------     ------------ ---------------
CommandPredictor  ICommandPredictor        False {}
```

### Exempel 2 – Visa alla tillgängliga del system av en viss typ

```powershell
PS> Get-PSSubsystem -Kind CommandPredictor | Format-List
```

```Output
Kind                      : CommandPredictor
SubsystemType             : System.Management.Automation.Subsystem.ICommandPredictor
AllowUnregistration       : True
AllowMultipleRegistration : True
RequiredCmdlets           : {}
RequiredFunctions         : {}
IsRegistered              : False
Implementations           : {}
```

## PARAMETRAR

### – Typ


Anger vilken typ av under system som ska returneras. Giltiga värden är: `CommandPredictor` .

```yaml
Type: System.Management.Automation.Subsystem.SubsystemKind
Parameter Sets: GetByKindSet
Aliases:
Accepted values: CommandPredictor

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -SubsystemType

Anger vilken typ av under system som ska returneras.

```yaml
Type: System.Type
Parameter Sets: GetByTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. Subsystem. SubsystemKind

### System. Type

## UTDATA

### System. Management. Automation. Subsystem. SubsystemInfo

## ANTECKNINGAR

## RELATERADE LÄNKAR

[about_experimental_features](about/about_experimental_features.md)

[Disable-ExperimentalFeature](Disable-ExperimentalFeature.md)

[Aktivera – ExperimentalFeature](Get-ExperimentalFeature.md)

[Get-ExperimentalFeature](Get-ExperimentalFeature.md)

[Använda experimentella funktioner](/powershell/scripting/learn/experimental-features)
