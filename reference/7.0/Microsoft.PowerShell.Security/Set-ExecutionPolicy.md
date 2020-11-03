---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ExecutionPolicy
ms.openlocfilehash: d3724c79f5864295c70d5addd46a8a133862d0ec
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93263031"
---
# Set-ExecutionPolicy

## SAMMANFATTNING
Anger PowerShell-körnings principer för Windows-datorer.

## SYNTAX

### Alla

```
Set-ExecutionPolicy [-ExecutionPolicy] <ExecutionPolicy> [[-Scope] <ExecutionPolicyScope>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Set-ExecutionPolicy`Cmdleten ändrar PowerShell-körnings principer för Windows-datorer. Mer information finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).

Från och med PowerShell 6,0 för datorer som inte är Windows-datorer är standard körnings principen **obegränsad** och kan inte ändras. `Set-ExecutionPolicy`Cmdleten är tillgänglig, men PowerShell visar ett konsol meddelande som inte stöds.

En körnings princip är en del av säkerhets strategin för PowerShell. Körnings principer avgör om du kan läsa in konfigurationsfiler, till exempel din PowerShell-profil eller köra skript. Och om skripten måste signeras digitalt innan de körs.

`Set-ExecutionPolicy`Cmdletens standard omfång är **LocalMachine** , som påverkar alla som använder datorn. Om du vill ändra körnings principen för **LocalMachine** startar du PowerShell med **Kör som administratör**.

Använd om du vill visa körnings principerna för varje omfång i prioritetsordning `Get-ExecutionPolicy -List` . Om du vill se den effektiva körnings principen för PowerShell-sessionen använder du utan `Get-ExecutionPolicy` parametrar.

## EXEMPEL

### Exempel 1: Ange en körnings princip

I det här exemplet visas hur du anger körnings principen för den lokala datorn.

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
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy`Cmdleten använder parametern **ExecutionPolicy** för att ange **RemoteSigned** -principen. Parametern **omfattning** Anger standardvärdet för omfattning, **LocalMachine**. Om du vill visa inställningarna för körnings principen använder du `Get-ExecutionPolicy` cmdleten med **list** parametern.

### Exempel 2: Ange en princip för körning som står i konflikt med en grupprincip

Med det här kommandot försöker du ange **LocalMachine** -Omfattningens körnings princip till **begränsad**.
**LocalMachine** är mer restriktiv, men är inte den effektiva principen eftersom den står i konflikt med en Grupprincip. Den **begränsade** principen skrivs till registrerings data filen **HKEY_LOCAL_MACHINE**.

```
PS> Set-ExecutionPolicy -ExecutionPolicy Restricted -Scope LocalMachine

Set-ExecutionPolicy : PowerShell updated your local preference successfully, but the setting is
overridden by the Group Policy applied to your system. Due to the override, your shell will retain
its current effective execution policy of "AllSigned". Contact your Group Policy administrator for
more information. At line:1 char:20 + Set-ExecutionPolicy <<<< restricted

PS> Get-ChildItem -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds

Name                    Property
----                    --------
Microsoft.PowerShell    Path            : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
                        ExecutionPolicy : Restricted
ScriptedDiagnostics     ExecutionPolicy : Unrestricted
```

`Set-ExecutionPolicy`Cmdleten använder parametern **ExecutionPolicy** för att ange den **begränsade** principen. Parametern **omfattning** Anger standardvärdet för omfattning, **LocalMachine**.
`Get-ChildItem`Cmdleten använder parametern **Path** med **HKLM** -providern för att ange register plats.

### Exempel 3: tillämpa körnings principen från en fjärrdator på en lokal dator

Det här kommandot hämtar objektet för körnings principen från en fjärrdator och anger principen på den lokala datorn. `Get-ExecutionPolicy` skickar ett **Microsoft.PowerShell.ExecutionPolicy** -objekt nedåt i pipelinen. `Set-ExecutionPolicy` accepterar pipeline-ininformation och kräver inte parametern **ExecutionPolicy** .

```
PS> Invoke-Command -ComputerName Server01 -ScriptBlock { Get-ExecutionPolicy } | Set-ExecutionPolicy
```

`Invoke-Command`Cmdleten körs på den lokala datorn och skickar **script block** till fjärrdatorn. Parametern **computername** anger fjärran sluten dator, **Server01**. Parametern **script block** körs `Get-ExecutionPolicy` på fjärrdatorn. `Get-ExecutionPolicy`Objektet skickas ned pipelinen till `Set-ExecutionPolicy` .
`Set-ExecutionPolicy` tillämpar körnings principen på den lokala datorns standard omfång, **LocalMachine**.

### Exempel 4: ange omfånget för en körnings princip

I det här exemplet visas hur du anger en körnings princip för en angiven omfattning, **CurrentUser**. **CurrentUser** -omfånget påverkar endast den användare som anger det här omfånget.

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope CurrentUser
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

`Set-ExecutionPolicy` använder parametern **ExecutionPolicy** för att ange **AllSigned** -principen.
Parametern **omfattning** anger **CurrentUser**. Om du vill visa inställningarna för körnings principen använder du `Get-ExecutionPolicy` cmdleten med **list** parametern.

Den effektiva körnings principen för användaren blir **AllSigned**.

### Exempel 5: ta bort körnings principen för den aktuella användaren

Det här exemplet visar hur använder den **odefinierade** körnings principen för att ta bort en körnings princip för en angiven omfattning.

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy` använder parametern **ExecutionPolicy** för att ange den **odefinierade** principen.
Parametern **omfattning** anger **CurrentUser**. Om du vill visa inställningarna för körnings principen använder du `Get-ExecutionPolicy` cmdleten med **list** parametern.

### Exempel 6: Ange körnings principen för den aktuella PowerShell-sessionen

**Process** omfånget påverkar endast den aktuella PowerShell-sessionen. Körnings principen sparas i miljö variabeln `$env:PSExecutionPolicyPreference` och tas bort när sessionen stängs.

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope Process
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       AllSigned
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy`Använder parametern **ExecutionPolicy** för att ange **AllSigned** -principen. Parametern **omfattning** anger värde **processen**. Om du vill visa inställningarna för körnings principen använder du `Get-ExecutionPolicy` cmdleten med **list** parametern.

### Exempel 7: avblockera ett skript för att köra det utan att ändra körnings principen

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

### – ExecutionPolicy

Anger körnings principen. Om det inte finns några grup principer och varje omfattnings körnings princip är inställd på **Odefinierad** , blir det **begränsade** principen för alla användare.

De acceptabla värdena för körnings principen är följande:

- **AllSigned**. Kräver att alla skript och konfigurationsfiler signeras av en betrodd utgivare, inklusive skript som skrivits på den lokala datorn.
- **Kringgå**. Inget blockeras och det finns inga varningar eller prompter.
- **Standard**. Anger standard körnings principen. **Begränsat** för Windows-klienter eller **RemoteSigned** för Windows-servrar.
- **RemoteSigned**. Kräver att alla skript och konfigurationsfiler som hämtas från Internet signeras av en betrodd utgivare. Standard körnings principen för Windows Server-datorer.
- **Begränsad**. Läser inte in konfigurationsfiler eller kör skript. Standard körnings principen för Windows-klientdatorer.
- **Odefinierat**. Ingen körnings princip har angetts för omfånget. Tar bort en tilldelad körnings princip från en omfattning som inte har angetts av en grupprincip. Om körnings principen i alla omfattningar är **Odefinierad** är den effektiva körnings principen **begränsad**.
- **Obegränsad**. Från och med PowerShell 6,0 är detta standard körnings principen för datorer som inte är Windows-datorer och kan inte ändras. Läser in alla konfigurationsfiler och kör alla skript. Om du kör ett osignerat skript som hämtades från Internet tillfrågas du om behörighet innan det körs.

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: AllSigned, Bypass, Default, RemoteSigned, Restricted, Undefined, Unrestricted

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Force

Ignorerar alla bekräftelse meddelanden. Använd försiktighet med den här parametern för att undvika oväntade resultat.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Omfattning

Anger det omfång som påverkas av en körnings princip. Standard omfånget är **LocalMachine**.

Den gällande körnings principen bestäms av prioritetsordningen enligt följande:

- **MachinePolicy**. Anges av en grupprincip för alla användare av datorn.
- **UserPolicy**. Anges av en grupprincip för datorns aktuella användare.
- **Processen**. Påverkar endast den aktuella PowerShell-sessionen.
- **CurrentUser**. Påverkar endast den aktuella användaren.
- **LocalMachine**. Standard omfattning som påverkar alla användare av datorn.

**Process** omfånget påverkar endast den aktuella PowerShell-sessionen. Körnings principen sparas i miljövariabeln i `$env:PSExecutionPolicyPreference` stället för registret. När PowerShell-sessionen stängs raderas variabeln och värdet.

Körnings principer för **CurrentUser** -omfånget skrivs till registrerings data filen **HKEY_LOCAL_USER**.

Körnings principer för **LocalMachine** -omfånget skrivs till registrerings data filen **HKEY_LOCAL_MACHINE**.

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 1
Default value: LocalMachine
Accept pipeline input: True (ByPropertyName)
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

## INDATA

### Microsoft.PowerShell.ExecutionPolicy, system. String

Du kan skicka vidare ett körnings princip objekt eller en sträng som innehåller namnet på en körnings princip till `Set-ExecutionPolicy` .

## UTDATA

### Inget

`Set-ExecutionPolicy` returnerar inga utdata.

## ANTECKNINGAR

`Set-ExecutionPolicy` ändrar inte **MachinePolicy** -och **UserPolicy** -omfattningarna eftersom de anges av grup principer.

`Set-ExecutionPolicy` åsidosätter inte en grupprincip, även om användar preferensen är mer restriktiv än principen.

Om grupprincip **Aktivera skript körning** har Aktiver ATS för datorn eller användaren, sparas användar inställningen, men den är inte effektiv. PowerShell visar ett meddelande som förklarar konflikten.

## RELATERADE LÄNKAR

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Group_Policy_Settings](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-ExecutionPolicy](Get-ExecutionPolicy.md)

[Invoke-kommando](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Avblockera – fil](../Microsoft.PowerShell.Utility/Unblock-File.md)
