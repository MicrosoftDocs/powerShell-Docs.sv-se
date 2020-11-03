---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ControlPanelItem
ms.openlocfilehash: 51bc04b4de901a611330266b6b0f58471f998432
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266168"
---
# Get-ControlPanelItem

## SAMMANFATTNING
Hämtar objekt på kontroll panelen.

## SYNTAX

### RegularName (standard)

```
Get-ControlPanelItem [[-Name] <String[]>] [-Category <String[]>] [<CommonParameters>]
```

### CanonicalName

```
Get-ControlPanelItem -CanonicalName <String[]> [-Category <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`Get-ControlPanelItem`Cmdlet: en hämtar objekt på kontroll panelen på den lokala datorn. Du kan använda den för att hitta objekt på kontroll panelen efter namn, kategori eller beskrivning, även på system som inte har något användar gränssnitt.

Denna cmdlet hämtar bara objekt på kontroll panelen som kan öppnas i systemet. På datorer som inte har kontroll panelen eller Utforskaren, hämtar denna cmdlet endast kontroll panels objekt som kan öppnas utan dessa komponenter.

Den här cmdleten introducerades i Windows PowerShell 3,0. Det fungerar bara på Windows 8 och Windows Server 2012 och senare.

## EXEMPEL

### Exempel 1: Hämta alla objekt på kontroll panelen

Det här kommandot hämtar alla objekt på kontroll panelen på den lokala datorn.

```powershell
Get-ControlPanelItem
```

```Output
Name                          CanonicalName                 Category                      Description
----                          -------------                 --------                      -----------
Action Center                 Microsoft.ActionCenter        {System and Security}         Review recent messages and...
Administrative Tools          Microsoft.AdministrativeTools {System and Security}         Configure administrative s...
AutoPlay                      Microsoft.AutoPlay            {Hardware}                    Change default settings fo...
BitLocker Drive Encryption    Microsoft.BitLockerDriveEn... {System and Security}         Protect your computer usin...
Color Management              Microsoft.ColorManagement     {All Control Panel Items}     Change advanced color mana...
Credential Manager            Microsoft.CredentialManager   {User Accounts}               Manage your Windows Creden...
Date and Time                 Microsoft.DateAndTime         {Clock, Language, and Region} Set the date, time, and ti...
...
```

### Exempel 2: Hämta objekt på kontroll panelen efter namn

I det här exemplet får du kontroll panels objekt som har program eller appar i sina namn.

```powershell
Get-ControlPanelItem -Name "*Program*", "*App*"
```

### Exempel 3: Hämta objekt på kontroll panelen efter kategori

Det här kommandot hämtar alla kontroll panels objekt i kategorier som har säkerhet i sina namn.

```powershell
Get-ControlPanelItem -Category "*Security*"
```

### Exempel 4: öppna ett kontroll panels objekt

I det här exemplet öppnas objekt på kontroll panelen i Windows-brandväggen på den lokala datorn.

```powershell
Get-ControlPanelItem -Name "Windows Firewall" | Show-ControlPanelItem
```

`Get-ControlPanelItem`Cmdlet: en hämtar kontroll panels objekt. `Show-ControlPanelItem`Cmdlet: en öppnar den.

### Exempel 5: Hämta kontroll panels objekt på en fjärrdator

Det här exemplet hämtar BitLocker-diskkryptering kontroll panels objekt på den fjärranslutna Server01-datorn.
`Invoke-Command`Cmdlet: en Fjärrkör `Get-ControlPanelItem` cmdleten.

```powershell
Invoke-Command -ComputerName "Server01" {Get-ControlPanelItem -Name "BitLocker*" }
```

### Exempel 6: Sök efter beskrivningar av objekt på kontroll panelen

I det här exemplet genomsöks egenskapen **Beskrivning** i kontroll panels objekt så att bara de som innehåller namnet **Device** visas.

```powershell
Get-ControlPanelItem | Where-Object {$_.Description -like "*Device*"}
```

```Output
Name                    CanonicalName                 Category    Description
----                    -------------                 --------    -----------
AutoPlay                Microsoft.AutoPlay            {Hardware}  Change default settings fo...
Devices and Printers    Microsoft.DevicesAndPrinters  {Hardware}  View and manage devices, p...
Sound                   Microsoft.Sound               {Hardware}  Configure your audio devic...
```

`Get-ControlPanelItem`Cmdlet: en hämtar alla objekt på kontroll panelen. `Where-Object`Cmdleten filtrerar objekten efter värdet för egenskapen **Description** .

## PARAMETRAR

### – CanonicalName

Anger, som en sträng mat ris, objekt på kontroll panelen efter deras kanoniska namn eller namn mönster som denna cmdlet hämtar. Jokertecken är tillåtna. Om du anger flera namn hämtar denna cmdlet kontroll panels objekt som matchar något av namnen, som om objekten i namn listan avgränsades med en "or"-Operator.

Som standard hämtar denna cmdlet alla kontroll panels objekt i systemet.

```yaml
Type: System.String[]
Parameter Sets: CanonicalName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### – Kategori

Anger, som en sträng mat ris, kategorierna i kontroll panelens objekt i de angivna kategorierna som denna cmdlet hämtar. Ange ett kategori namn eller namn mönster. Jokertecken är tillåtna. Om du anger flera namn hämtar denna cmdlet kontroll panels objekt som matchar något av namnen, som om objekten i namn listan avgränsades med en "or"-Operator. Som standard hämtar denna cmdlet alla kontroll panels objekt i systemet.

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

### -Name

Anger, som en sträng mat ris, namnen eller namn mönstren på kontroll panelen som denna cmdlet hämtar.
Jokertecken är tillåtna. Du kan också skicka ett namn eller namn-mönster till denna cmdlet.

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare ett namn eller namn-mönster till denna cmdlet.

## UTDATA

### Microsoft. PowerShell. commands. ControlPanelItem

Denna cmdlet hämtar objekt på kontroll panelen på den lokala datorn.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Visa ControlPanelItem](Show-ControlPanelItem.md)
