---
external help file: Microsoft.PowerShell.ODataUtils-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.ODataUtils
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.odatautils/export-odataendpointproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ODataEndpointProxy
ms.openlocfilehash: 846aca6974190863a073773fe5148f0c57d77dc3
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388203"
---
# Export-ODataEndpointProxy

## SAMMANFATTNING
Genererar en modul som innehåller cmdlets för att hantera en OData-slutpunkt.

## SYNTAX

```
Export-ODataEndpointProxy [-Uri] <String> [-OutputModule] <String> [[-MetadataUri] <String>]
 [[-Credential] <PSCredential>] [[-CreateRequestMethod] <String>] [[-UpdateRequestMethod] <String>]
 [[-CmdletAdapter] <String>] [[-ResourceNameMapping] <Hashtable>] [-Force] [[-CustomData] <Hashtable>]
 [-AllowClobber] [-AllowUnsecureConnection] [[-Headers] <Hashtable>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Export-ODataEndpointProxy`Cmdlet: en använder metadata för en OData-slutpunkt för att skapa en modul som innehåller cmdletar som du kan använda för att hantera OData-slutpunkten. Modulen baseras på CDXLM. När den här cmdleten genererar modulen sparar den modulen till sökvägen och fil namnet som anges av parametern **OutputModule** .

`Export-ODataEndpointProxy` genererar cmdlets för åtgärder för att skapa, läsa, uppdatera och ta bort (CRUD), icke-CRUD åtgärder och associerings manipulering.

`Export-ODataEndpointProxy` genererar en CDXLM-fil per slut punkts resurs. Du kan redigera dessa CDXLM-filer när modulen har genererats. Om du till exempel vill ändra Substantiv-eller verbfras för cmdletarna så att de överensstämmer med rikt linjerna för Windows PowerShell-cmdlet, kan du ändra filen.

Varje cmdlet i en genererad modul måste innehålla en **ConnectionURI** -parameter för att kunna ansluta till den slut punkt som modulen hanterar.

## EXEMPEL

### Exempel 1: generera en modul för att hantera en webb tjänst slut punkt för åter försäljning

```powershell
PS C:\> Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -MetadataUri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc/$metadata' -AllowUnsecureConnection -OutputModule 'C:\Users\user\GeneratedScript.psm1' -ResourceNameMapping @{Products = 'Merchandise'}
```

Det här kommandot genererar en modul för att hantera en tjänst slut punkt för detalj handeln. Kommandot anger URI för slut punkten och URI: n för slut punktens metadata. Kommandot tillhandahåller också en sökväg för utdata och ett namn på en skript-modul som värde för parametern **OutputModule** . För värdet för parametern **ResourceNameMapping** tillhandahåller kommandot en hash-tabellen som mappar resurs samlings namnet till önskat Substantiv för cmdlet-uppsättningen. I det här exemplet är produkter resurs samlingens namn och **varorna** är substantiv. Om du vill tillåta anslutningar till icke-SSL-platser, HTTP, i stället för HTTPS, lägger du till parametern **AllowUnsecureConnection** .

## PARAMETRAR

### -AllowClobber

Anger att denna cmdlet ersätter en befintlig modul.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 10
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -AllowUnsecureConnection

Anger att den här modulen kan ansluta till URI: er som inte är SSL-säkrade. Modulen kan hantera HTTP-platser förutom HTTPS-platser.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 11
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CmdletAdapter

Anger cmdlet-nätverkskortet. De acceptabla värdena för den här parametern är: ODataAdapter och NetworkControllerAdapter.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ODataAdapter, NetworkControllerAdapter, ODataV4Adapter

Required: False
Position: 6
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CreateRequestMethod

Anger metod för begäran. De acceptabla värdena för den här parametern är: placering, POST och korrigering.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 4
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har åtkomst till OData-slutpunkten. Standardvärdet är den aktuella användaren. Om en fjärrdator kör Windows Vista eller en senare version av Windows-operativsystemet, uppmanas du att ange autentiseringsuppgifter för cmdleten.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – CustomData

Anger en hash-tabell med anpassade data.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 9
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

Anger att denna cmdlet skriver över en befintlig genererad modul med samma namn i en befintlig `Modules` mapp.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 8
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Sidhuvud

Anger webb begärans rubriker. Ange en hash-tabell eller-ord lista.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 12
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MetadataUri

Anger URI för slut punktens metadata.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OutputModule

Anger den sökväg och det Modulnamn som denna cmdlet ska spara den genererade modulen med proxy-kommandon i.

Denna cmdlet kopierar en binär modul, ett modul manifest och en format fil, om det är tillämpligt, till den angivna mappen. Om du bara anger namnet på modulen `Export-ODataEndpointProxy` sparar modulen i `$home\Documents\WindowsPowerShell\Modules` mappen. Om du anger en sökväg skapar cmdleten mappen modul i den sökvägen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceNameMapping

Anger en hash-tabellen som innehåller mappningar som gör att du kan anpassa de genererade cmdletarna. I den här hash-tabellen är resurs samlingens namn nyckeln. Önskad cmdlet Substantiv är värdet.

I tabellen hash är produkter till exempel `@{Products = 'Merchandise'}` resurs **Products** samlings namnet som fungerar som nyckel. **Produkter** är den resulterande cmdleten substantiv. De genererade cmdlet-namnen kanske inte överensstämmer med namngivnings rikt linjerna för Windows PowerShell-cmdlet. Du kan ändra resursens CDXLM-fil om du vill ändra cmdlet-namnen när denna cmdlet skapar modulen. Mer information finns i [rikt linjer för starkt uppmuntrande utveckling](/powershell/scripting/developer/cmdlet/strongly-encouraged-development-guidelines).

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 7
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UpdateRequestMethod

Anger metoden för att uppdatera begäran. De acceptabla värdena för den här parametern är: placering, POST och korrigering.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 5
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -URI

Anger slut punktens URI.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

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

## UTDATA

## ANTECKNINGAR

## RELATERADE LÄNKAR

[OData-bibliotek](/previous-versions/dotnet/wcf-data-services/hh525392(v=vs.103))

[Vad är OData-protokollet?](https://www.odata.org/)

[Invoke-RestMethod](../Microsoft.PowerShell.Utility/Invoke-RestMethod.md)
