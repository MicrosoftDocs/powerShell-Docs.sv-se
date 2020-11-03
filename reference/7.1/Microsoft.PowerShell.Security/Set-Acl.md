---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-acl?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Acl
ms.openlocfilehash: a4c25d199b97be24277092bcb815a640a09360dd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263859"
---
# Set-Acl

## SAMMANFATTNING
Ändrar säkerhets beskrivningen för ett angivet objekt, till exempel en fil eller en register nyckel.

## SYNTAX

### ByPath (standard)

```
Set-Acl [-Path] <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByInputObject

```
Set-Acl [-InputObject] <PSObject> [-AclObject] <Object> [-Passthru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Set-Acl -LiteralPath <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Set-Acl`Cmdleten ändrar säkerhets beskrivningen för ett angivet objekt, till exempel en fil eller en register nyckel, för att matcha värdena i en säkerhets beskrivning som du anger.

Använd `Set-Acl` parametern **Path** eller **InputObject** för att identifiera det objekt vars säkerhets Beskrivning du vill ändra. Använd sedan parametrarna **AclObject** eller **adtagent** för att ange en säkerhets beskrivare som har de värden som du vill använda. `Set-Acl` använder den angivna säkerhets beskrivningen. Värdet för parametern **AclObject** används som en modell och ändrar värdena i objektets säkerhets Beskrivning så att de matchar värdena i parametern **AclObject** .

## EXEMPEL

### Exempel 1: kopiera en säkerhets beskrivning från en fil till en annan

```powershell
$DogACL = Get-Acl -Path "C:\Dog.txt"
Set-Acl -Path "C:\Cat.txt" -AclObject $DogACL
```

Dessa kommandon kopierar värdena från den Dog.txt filens säkerhets beskrivning till säkerhets beskrivningen för Cat.txts filen. När kommandona har slutförts är säkerhets beskrivarna för Dog.txt-och Cat.txt-filerna identiska.

Det första kommandot använder `Get-Acl` cmdleten för att hämta den Dog.txt filens säkerhets beskrivning.
Tilldelnings operatorn ( `=` ) lagrar säkerhets beskrivningen i värdet för variabeln $DogACL.

Det andra kommandot använder `Set-Acl` för att ändra värdena i ACL: en för Cat.txt till värdena i `$DogACL` .

Värdet för parametern **Path** är sökvägen till Cat.txt-filen. Värdet för parametern **AclObject** är modellens ACL, i det här fallet ACL: en för Dog.txt som sparas i `$DogACL` variabeln.

### Exempel 2: Använd pipeline-operatorn för att skicka en beskrivning

```powershell
Get-Acl -Path "C:\Dog.txt" | Set-Acl -Path "C:\Cat.txt"
```

Det här kommandot är nästan detsamma som kommandot i föregående exempel, förutom att det använder en pipeline-operator ( `|` ) för att skicka säkerhets beskrivningen från ett `Get-Acl` kommando till ett `Set-Acl` kommando.

Det första kommandot använder `Get-Acl` cmdleten för att hämta den Dog.txt filens säkerhets beskrivning. Pipeline-operatorn ( `|` ) skickar ett objekt som representerar den Dog.txt säkerhets beskrivningen till `Set-Acl` cmdleten.

Det andra kommandot använder `Set-Acl` för att tillämpa säkerhets beskrivningen för Dog.txt Cat.txt.
När kommandot har slutförts är ACL: erna för Dog.txt-och Cat.txt-filerna identiska.

### Exempel 3: tillämpa en säkerhets beskrivning på flera filer

```powershell
$NewAcl = Get-Acl File0.txt
Get-ChildItem -Path "C:\temp" -Recurse -Include "*.txt" -Force | Set-Acl -AclObject $NewAcl
```

Dessa kommandon tillämpar säkerhets beskrivningar i File0.txt-filen för alla textfiler i `C:\Temp` katalogen och alla dess under kataloger.

Det första kommandot hämtar säkerhets beskrivningen för File0.txt-filen i den aktuella katalogen och använder tilldelnings operatorn ( `=` ) för att lagra den i `$NewACL` variabeln.

Det första kommandot i pipelinen använder Get-ChildItem-cmdleten för att hämta alla textfiler i `C:\Temp` katalogen. Parametern **rekursivt** utökar kommandot till alla under kataloger i `C:\temp` . Parametern **include** begränsar de filer som hämtas till dem med `.txt` fil namns tillägget. Parametern **Force** hämtar dolda filer, vilket annars skulle uteslutas. (Du kan inte använda `c:\temp\*.txt` eftersom parametern **rekursivt** fungerar på kataloger, inte på filer.)

Pipelinen ( `|` ) skickar objekten som representerar de hämtade filerna till `Set-Acl` cmdleten, som använder säkerhets beskrivningen i **AclObject** -parametern för alla filer i pipelinen.

I praktiken är det bäst att använda parametern **whatIf** med alla `Set-Acl` kommandon som kan påverka fler än ett objekt. I det här fallet skulle det andra kommandot i pipelinen vara `Set-Acl -AclObject $NewAcl -WhatIf` . Det här kommandot visar de filer som skulle påverkas av kommandot. När du har granskat resultatet kan du köra kommandot igen utan parametern **whatIf** .

### Exempel 4: inaktivera arv och bevara ärvda åtkomst regler

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
$isProtected = $true
$preserveInheritance = $true
$NewAcl.SetAccessRuleProtection($isProtected, $preserveInheritance)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

Dessa kommandon inaktiverar åtkomst arv från överordnade mappar, samtidigt som befintliga ärvda åtkomst regler bevaras.

Det första kommandot använder `Get-Acl` cmdleten för att hämta den Dog.txt filens säkerhets beskrivning.

Sedan skapas variabler för att konvertera de ärvda åtkomst reglerna till explicita åtkomst regler. Om du vill skydda åtkomst reglerna som är kopplade till detta från arv ställer du in `$isProtected` variabeln på `$true` . Tillåt arv genom att ange `$isProtected` till `$false` . Mer information finns i [Ange skydd för åtkomst regler](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection).
`$preserveInheritance`Variabeln som angetts till `$true` för att bevara ärvda åtkomst regler, falskt för att ta bort ärvda åtkomst regler. Sedan uppdateras åtkomst regel skyddet med hjälp av metoden **SetAccessRuleProtection ()** .

Det sista kommandot använder `Set-Acl` för att tillämpa säkerhets beskrivningen för Dog.txt. När kommandot har slutförts kommer ACL: er för de Dog.txt som ärvts från mappen hus djur att tillämpas direkt på Dog.txt, och nya åtkomst principer som läggs till i hus djur kommer inte att ändra åtkomsten till Dog.txt.

### Exempel 5: bevilja administratörer fullständig kontroll över filen

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
# Set properties
$identity = "BUILTIN\Administrators"
$fileSystemRights = "FullControl"
$type = "Allow"
# Create new rule
$fileSystemAccessRuleArgumentList = $identity, $fileSystemRights, $type
$fileSystemAccessRule = New-Object -TypeName System.Security.AccessControl.FileSystemAccessRule -ArgumentList $fileSystemAccessRuleArgumentList
# Apply new rule
$NewAcl.SetAccessRule($fileSystemAccessRule)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

Det här kommandot ger **BUILTIN\Administrators** -gruppen fullständig kontroll över Dog.txts filen.

Det första kommandot använder `Get-Acl` cmdleten för att hämta den Dog.txt filens säkerhets beskrivning.

Next-variabler skapas för att ge **BUILTIN\Administrators** -gruppen fullständig kontroll över Dog.txt-filen. `$identity`Variabeln anges till namnet på ett [användar konto](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor).
`$fileSystemRights`Variabeln inställd på FullControl och kan vara något av [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) -värdena som anger vilken typ av åtgärd som är kopplad till åtkomst regeln. `$type`Variabeln anges till Tillåt för att ange om åtgärden ska tillåtas eller nekas. `$fileSystemAccessRuleArgumentList`Variabeln är en argument lista som ska skickas när det nya **FileSystemAccessRule** -objektet görs. Sedan skapas ett nytt **FileSystemAccessRule** -objekt och **FileSystemAccessRule** -objektet skickas till metoden **SetAccessRule ()** lägger till den nya åtkomst regeln.

Det sista kommandot använder `Set-Acl` för att tillämpa säkerhets beskrivningen för Dog.txt.
När kommandot har slutförts har **BUILTIN\Administrators** -gruppen fullständig kontroll över den Dog.txt.

## PARAMETRAR

### -AclObject

Anger en ACL med önskade egenskaps värden. `Set-Acl` ändrar ACL för objektet som anges av **sökvägen** eller parametern **InputObject** för att matcha värdena i det angivna säkerhets objektet.

Du kan spara utdata från ett `Get-Acl` kommando i en variabel och sedan använda parametern **AclObject** för att skicka variabeln eller skriva ett `Get-Acl` kommando.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClearCentralAccessPolicy

Tar bort principen för central åtkomst från det angivna objektet.

Från och med Windows Server 2012 kan administratörer använda Active Directory och grupprincip för att ange principer för central åtkomst för användare och grupper. Mer information finns i [dynamisk Access Control: Scenario översikt](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByPath, ByLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Undanta

Utesluter de angivna objekten. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` . Jokertecken är tillåtna.

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

### -Filter

Anger ett filter i providerns format eller språk. Värdet för den här parametern kvalificerar parametern **Path** . Syntaxen för filtret, inklusive användning av jokertecken, beror på providern. Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när objekten hämtas, i stället för att ha PowerShell filtrera objekten när de har hämtats.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Inkludera

Ändrar endast de angivna objekten. Värdet för den här parametern kvalificerar parametern **Path** .
Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` . Jokertecken är tillåtna.

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

### – InputObject

Ändrar säkerhets beskrivningen för det angivna objektet. Ange en variabel som innehåller objektet eller ett kommando som hämtar objektet.

Det går inte att skicka ett objekt att ändra till `Set-Acl` . Använd i stället parametern **InputObject** explicit i kommandot.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

Ändrar säkerhets beskrivningen för det angivna objektet. Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken, omger du den med enkla citat tecken ( `'` ).
Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Passthru

Returnerar ett objekt som representerar säkerhets beskrivningen som ändrades. Som standard genererar denna cmdlet inga utdata.

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

### -Path

Ändrar säkerhets beskrivningen för det angivna objektet. Ange sökvägen till ett objekt, till exempel en sökväg till en fil eller register nyckel. Jokertecken är tillåtna.

Om du skickar ett säkerhets objekt till `Set-Acl` (antingen genom att använda **AclObject** -eller **adtagent** -parametrarna eller genom att skicka ett säkerhets objekt från Get-Acl till `Set-Acl` ) och du utelämnar **Sök vägs** parametern (namn och värde), `Set-Acl` använder den sökväg som ingår i säkerhets objekt.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
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

## INDATA

### System. Security. AccessControl. ObjectSecurity, system. Security. AccessControl. CommonSecurityDescriptor

Du kan skicka ett ACL-objekt eller en säkerhets beskrivning till `Set-Acl` .

## UTDATA

### System. Security. AccessControl. FileSecurity

`Set-Acl`Genererar inga utdata som standard.
Men om du använder parametern **Passthru** genereras ett säkerhets objekt.
Vilken typ av säkerhets objekt som är beror på objektets typ.

## ANTECKNINGAR

 `Set-Acl`Cmdleten stöds av PowerShell-filsystemet och register leverantörerna. Därför kan du använda den för att ändra säkerhets beskrivare för filer, kataloger och register nycklar.

## RELATERADE LÄNKAR

[Get-ACL](Get-Acl.md)

[FileSystemAccessRule](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)

[ObjectSecurity.SetAccessRuleProtection](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)

[FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights)
