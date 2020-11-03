---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-ControlPanelItem
ms.openlocfilehash: 368e385d51437f9ac93b700c929b185dce30a644
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265370"
---
# Show-ControlPanelItem

## SAMMANFATTNING
Öppnar kontroll panels objekt.

## SYNTAX

### RegularName (standard)

```
Show-ControlPanelItem [-Name] <String[]> [<CommonParameters>]
```

### CanonicalName

```
Show-ControlPanelItem -CanonicalName <String[]> [<CommonParameters>]
```

### ControlPanelItem

```
Show-ControlPanelItem [[-InputObject] <ControlPanelItem[]>] [<CommonParameters>]
```

## BESKRIVNING

`Show-ControlPanelItem`Cmdlet: en öppnar objekt på kontroll panelen på den lokala datorn. Du kan använda den för att öppna kontroll panels objekt efter namn, kategori eller beskrivning, även på system som inte har något användar gränssnitt. Du kan skicka vidare till kontroll panels objekt från `Get-ControlPanelItem` cmdleten till `Show-ControlPanelItem` .

`Show-ControlPanelItem` söker endast efter objekt på kontroll panelen som kan öppnas i systemet. På datorer som inte har **kontroll panelen** eller **Utforskaren** `Show-ControlPanelItem` söker sökningen endast på kontroll panelens objekt som kan öppnas utan de här komponenterna.

Denna cmdlet introducerades i Windows PowerShell 3,0 och fungerar på Windows 8, Windows Server 2012 och senare versioner.

## EXEMPEL

### Exempel 1: Visa ett kontroll panels objekt

I det här exemplet öppnas alternativet **spela upp automatiskt** på kontroll panelen.

```powershell
Show-ControlPanelItem -Name "AutoPlay"
```

### Exempel 2: Skicka ett objekt till en kontroll panel till denna cmdlet

I det här exemplet öppnas objekt på kontroll panelen i **Windows Defender-brandväggen** på den lokala datorn.
Namnet på kontroll panelens objekt i Windows-brandväggen har ändrats i Windows-brandväggens versioner. Det här exemplet använder ett mönster för jokertecken för att hitta kontroll panelens objekt.

```powershell
Get-ControlPanelItem -Name "*Firewall" | Show-ControlPanelItem
```

`Get-ControlPanelItem` hämtar kontroll panels objekt och `Show-ControlPanelItem` cmdlet: en öppnar den.

### Exempel 3: Använd ett fil namn för att öppna ett kontroll panels objekt

I det här exemplet öppnas objekt på kontroll panelen **program och funktioner** med hjälp av dess program namn.

```powershell
appwiz.cpl
```

Den här metoden är ett alternativ till att använda ett `Show-ControlPanelItem` kommando.

> [!NOTE]
> I PowerShell kan du utelämna fil namns tillägget. cpl för kontroll panels filer eftersom det ingår i värdet för `$env:PathExt` miljövariabeln.

## PARAMETRAR

### – CanonicalName

Anger objekt på kontroll panelen genom att använda de angivna kanoniska namnen eller namn mönstren. Jokertecken är tillåtna. Om du anger flera namn öppnar denna cmdlet kontroll panels objekt som matchar något av namnen, som om objekten i namn listan skiljdes åt av en **or** -operator.

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

### – InputObject

Anger vilka kontroll panels objekt som ska öppnas genom att skicka objekt på kontroll panelen. Ange en variabel som innehåller objekt på kontroll panelen eller Skriv ett kommando eller uttryck som hämtar objekt på kontroll panelen, till exempel `Get-ControlPanelItem` .

```yaml
Type: Microsoft.PowerShell.Commands.ControlPanelItem[]
Parameter Sets: ControlPanelItem
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Anger namn på kontroll panels objekt. Jokertecken är tillåtna. Om du anger flera namn öppnar denna cmdlet kontroll panels objekt som matchar något av namnen, som om objekten i namn listan skiljdes åt av en **or** -operator.

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String, Microsoft. PowerShell. commands. ControlPanelItem

Du kan skicka ett objekt av namnet eller kontroll panelen objekt till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-ControlPanelItem](Get-ControlPanelItem.md)
