---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/unregister-packagesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PackageSource
ms.openlocfilehash: 06a4649d0d2f0912807219f25e60d85ba22564b0
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262226"
---
# Unregister-PackageSource

## SAMMANFATTNING
Tar bort en registrerad paket källa.

## SYNTAX

### SourceBySearch

```
Unregister-PackageSource [[-Source] <String>] [-Location <String>] [-Credential <PSCredential>]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### SourceByInputObject

```
Unregister-PackageSource -InputObject <PackageSource[]> [-Credential <PSCredential>] [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NuGet: SourceByInputObject

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### NuGet: SourceBySearch

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### PowerShellGet: SourceByInputObject

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### PowerShellGet: SourceBySearch

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## BESKRIVNING

`Unregister-PackageSource`Cmdleten tar bort en registrerad paket källa. Paket källor hanteras alltid av en paket leverantör. Använd cmdleten för att hitta paket källor `Get-PackageSource` .

## EXEMPEL

### Exempel 1: avregistrera en paket källa för NuGet-providern

`Unregister-PackageSource`Cmdleten avregistrerar en paket källa från den lokala datorn. Parametrarna **plats** och **Provider** kan användas för att ytterligare ange vilken källa som ska tas bort.

```
PS> Unregister-PackageSource -Source MyNuGet
```

`Unregister-PackageSource`Cmdleten använder parametern **Source** för att ange vilken källa som ska tas bort.

### Exempel 2: Använd ett PackageSource-objekt för att avregistrera ett paket

I det här exemplet används `Get-PackageSource` och `Unregister-PackageSource` för att avregistrera en paket källa. **PackageSource** -objektet lagras i en variabel.

```
PS> $pkgsource = Get-PackageSource -Name MyNuGet
PS> Unregister-PackageSource -InputObject $pkgsource
```

`$pkgsource`Variabeln lagrar de **PackageSource** som skapats av `Get-PackageSource` cmdleten.
`Unregister-PackageSource` använder `$pkgsource` som-indatamängden för parametern **InputObject** .

Alternativt `Unregister-PackageSource` kan cmdleten ange ett värde för parametern **InputObject** :

`Unregister-PackageSource -InputObject ( Get-PackageSource -Name MyNuGet )`

## PARAMETRAR

### – ConfigFile

Anger en konfigurations fil.

```yaml
Type: System.String
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att komma åt datorn och köra kommandon. Ange ett användar namn, till exempel **user01** , **Domain01\User01** , eller ange ett **PSCredential** -objekt som genereras av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange ett lösen ord.

När parametern **Credential** inte anges används det aktuella användar kontot.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Tvingar kommandot att köras utan att fråga användaren om bekräftelse. Åsidosätter begränsningar som förhindrar att `Unregister-PackageSource` de lyckas, med undantag för säkerhet.

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

### -ForceBootstrap

Anger att `Unregister-PackageSource` **PackageManagement** automatiskt ska avinstallera paket leverantören för den angivna paket källan.

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

### – InputObject

Accepterar pipeline-inflöde som anger **PackageSource** -objektet från `Get-PackageSource` cmdleten. **InputObject** accepterar **PackageSource** -objektet som ett `Get-PackageSource` värde eller en variabel som innehåller objektet.

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource[]
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – Plats

Anger den plats som paket källan pekar på. Värdet för den här parametern kan vara en URI, en fil Sök väg eller något annat mål format som stöds av paket leverantören.

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

Anger **PackageManagement** -providern.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

Anger namnet på providern.

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PublishLocation

Anger publicerings platsen.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptPublishLocation

Anger skriptets publicerings plats.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptSourceLocation

Anger sökvägen till skript källan.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipValidate

Växel som hoppar över verifiering av autentiseringsuppgifterna för en paket källa.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Anger det egna namnet på paket källan.

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Du uppmanas att bekräfta innan körs `Unregister-PackageSource` .

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

Visar vad som händer om `Unregister-PackageSource` cmdleten körs. Cmdleten körs inte.

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

### `Unregister-PackageSource` accepterar **PackageSource** -objekt från pipelinen som inmatade.

## UTDATA

### `Unregister-PackageSource` genererar inga utdata.

## ANTECKNINGAR

Att inkludera en paket leverantör i ett kommando kan göra dynamiska parametrar tillgängliga för en cmdlet. Dynamiska parametrar är speciella för en paket leverantör. `Get-Help`Cmdleten listar en cmdlets parameter uppsättningar och inkluderar providerns parameter uppsättning.

## RELATERADE LÄNKAR

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Get-PackageSource](Get-PackageSource.md)

[Registrera – PackageSource](Register-PackageSource.md)

[Set-PackageSource](Set-PackageSource.md)
