---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExecutionPolicy
ms.openlocfilehash: a846c3605c4adf469b12bfadaa3f90e585558dea
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267243"
---
# Get-ExecutionPolicy

## SAMMANFATTNING
Hämtar körnings principerna för den aktuella sessionen.

## SYNTAX

### Alla

```
Get-ExecutionPolicy [[-Scope] <ExecutionPolicyScope>] [-List] [<CommonParameters>]
```

## BESKRIVNING

Använd om du vill visa körnings principerna för varje omfång i prioritetsordning `Get-ExecutionPolicy -List` . Om du vill se den effektiva körnings principen för PowerShell-sessionen använder du utan `Get-ExecutionPolicy` parametrar.

Den effektiva körnings principen bestäms av körnings principer som ställs in av `Set-ExecutionPolicy` och Grupprincip inställningar.

Mer information finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).

## EXEMPEL

### Exempel 1: Hämta alla körnings principer

Det här kommandot visar körnings principerna för varje omfång i prioritetsordning.

```powershell
Get-ExecutionPolicy -List
```

```Output
Scope          ExecutionPolicy
-----          ---------------
MachinePolicy  Undefined
UserPolicy     Undefined
Process        Undefined
CurrentUser    AllSigned
LocalMachine   Undefined
```

`Get-ExecutionPolicy`Cmdleten använder **list parametern List** för att visa varje omfattnings körnings princip.

### Exempel 2: Ange en körnings princip

I det här exemplet visas hur du anger en körnings princip för den lokala datorn.

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy`Cmdleten använder parametern **ExecutionPolicy** för att ange **RemoteSigned** -principen. Parametern **omfattning** Anger standardvärdet för omfattning, **LocalMachine**. Om du vill visa inställningarna för körnings principen använder du `Get-ExecutionPolicy` cmdleten med **list** parametern.

### Exempel 3: hämta den effektiva körnings principen

Det här exemplet visar hur du visar den effektiva körnings principen för en PowerShell-session.

```
PS> Get-ExecutionPolicy -List

        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned

PS> Get-ExecutionPolicy

AllSigned
```

`Get-ExecutionPolicy`Cmdleten använder **list parametern List** för att visa varje omfattnings körnings princip. `Get-ExecutionPolicy`Cmdleten körs utan en parameter för att visa den effektiva körnings principen, **AllSigned**.

### Exempel 4: avblockera ett skript för att köra det utan att ändra körnings principen

Det här exemplet visar hur **RemoteSigned** -körnings principen förhindrar att osignerade skript körs.

Vi rekommenderar att du läser skript koden och kontrollerar att den är säker **innan** du använder `Unblock-File` cmdleten. `Unblock-File`Cmdleten avblockerar skripten så att de kan köras, men ändrar inte körnings principen.

```
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

.\Start-ActivityTracker.ps1 : File .\Start-ActivityTracker.ps1 cannot be loaded.
The file .\Start-ActivityTracker.ps1 is not digitally signed.
The script will not execute on the system.
For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], PSSecurityException
+ FullyQualifiedErrorId : UnauthorizedAccess

PS> Unblock-File -Path .\Start-ActivityTracker.ps1

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

Task 1:
```

`Set-ExecutionPolicy`Använder parametern **ExecutionPolicy** för att ange **RemoteSigned** -principen. Principen har angetts för standard omfånget, **LocalMachine**.

`Get-ExecutionPolicy`Cmdleten visar att **RemoteSigned** är den effektiva körnings principen för den aktuella PowerShell-sessionen.

**Start-ActivityTracker.ps1** skriptet körs från den aktuella katalogen. Skriptet blockeras av **RemoteSigned** eftersom skriptet inte har signerats digitalt.

I det här exemplet har skript koden granskats och verifierats som säker för körning. `Unblock-File`Cmdleten använder parametern **Path** för att avblockera skriptet.

För att kontrol lera att `Unblock-File` inte har ändrat körnings principen, `Get-ExecutionPolicy` visar den effektiva körnings principen, **RemoteSigned**.

Skriptet **Start-ActivityTracker.ps1** köras från den aktuella katalogen. Skriptet börjar köras eftersom det har avblockerats av `Unblock-File` cmdleten.

## PARAMETRAR

### – Lista

Hämtar alla körnings princip värden för sessionen som anges i prioritetsordning. Som standard `Get-ExecutionPolicy` hämtar endast den gällande körnings principen.

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

### – Omfattning

Anger det omfång som påverkas av en körnings princip.

Den gällande körnings principen bestäms av prioritetsordningen enligt följande:

- **MachinePolicy**. Anges av en grupprincip för alla användare av datorn.
- **UserPolicy**. Anges av en grupprincip för datorns aktuella användare.
- **Processen**. Påverkar endast den aktuella PowerShell-sessionen.
- **CurrentUser**. Påverkar endast den aktuella användaren.
- **LocalMachine**. Standard omfattning som påverkar alla användare av datorn.

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 0
Default value: Effective execution policy
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

`Get-ExecutionPolicy` accepterar inte ininformation från pipelinen.

## UTDATA

### Microsoft.PowerShell.ExecutionPolicy

## ANTECKNINGAR

En körnings princip är en del av säkerhets strategin för PowerShell. Körnings principer avgör om du kan läsa in konfigurationsfiler, till exempel din PowerShell-profil eller köra skript. Och om skripten måste signeras digitalt innan de körs.

## RELATERADE LÄNKAR

[about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)

[about_Group_Policy_Settings](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)
