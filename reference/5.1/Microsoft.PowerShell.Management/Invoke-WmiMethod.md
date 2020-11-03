---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-wmimethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WmiMethod
ms.openlocfilehash: e9743488e86429e5cc3252162e51268a7978b79d
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/09/2020
ms.locfileid: "93268029"
---
# Invoke-WmiMethod

## SAMMANFATTNING
Anropar WMI-metoder.

## SYNTAX

### klass (standard)

```
Invoke-WmiMethod [-Class] <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### objekt

```
Invoke-WmiMethod -InputObject <ManagementObject> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### path

```
Invoke-WmiMethod -Path <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### WQLQuery

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DocumentDB

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### lista

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Invoke-WmiMethod`Cmdleten anropar metoder för Windows Management Instrumentation (WMI)-objekt.

Nya Common Information Model CIM-cmdletar, som introducerades i Windows PowerShell 3,0, utför samma uppgifter som WMI-cmdlets. CIM-cmdlets följer WS-Management (WSMan)-standarder och med CIM-standarden, som gör att cmdlets kan använda samma metoder för att hantera Windows-datorer och de som kör andra operativ system. Använd `Invoke-WmiMethod` [Invoke-CimMethod](../cimcmdlets/invoke-cimmethod.md)i stället för att använda.

## EXEMPEL

### Exempel 1: Ange den nödvändiga ordningen för WMI-objekt

```powershell
([wmiclass]'Win32_Volume').GetMethodParameters('Format')
```

```Output
__GENUS           : 2
__CLASS           : __PARAMETERS
__SUPERCLASS      :
__DYNASTY         : __PARAMETERS
__RELPATH         :
__PROPERTY_COUNT  : 6
__DERIVATION      : {}
__SERVER          :
__NAMESPACE       :
__PATH            :
ClusterSize       : 0
EnableCompression : False
FileSystem        : NTFS
Label             :
QuickFormat       : False
Version           : 0
PSComputerName    :
```

Det här kommandot visar den ordning som krävs för objekten. Att anropa WMI i PowerShell 3,0 skiljer sig från alternativa metoder och kräver att objekt värden anges i en speciell ordning.

### Exempel 2: starta en instans av ett program

```powershell
([Wmiclass]'Win32_Process').GetMethodParameters('Create')
```

```Output
__GENUS                   : 2
__CLASS                   : __PARAMETERS
__SUPERCLASS              :
__DYNASTY                 : __PARAMETERS
__RELPATH                 :
__PROPERTY_COUNT          : 3
__DERIVATION              : {}
__SERVER                  :
__NAMESPACE               :
__PATH                    :
CommandLine               :
CurrentDirectory          :
ProcessStartupInformation :
PSComputerName            :
```

```powershell
Invoke-WmiMethod -Path win32_process -Name create -ArgumentList notepad.exe
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 2
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ProcessId        : 11312
ReturnValue      : 0
PSComputerName   :
```

Det här kommandot startar en instans av anteckningar genom `Create` att anropa metoden i **Win32_Process** -klassen.

Egenskapen **returnValue** fylls med en 0 och **ProcessID** -egenskapen fylls med ett heltal (nästa process-ID-nummer) om kommandot har slutförts.

### Exempel 3: Byt namn på en fil

```powershell
Invoke-WmiMethod -Path "CIM_DataFile.Name='C:\scripts\test.txt'" -Name Rename -ArgumentList "C:\scripts\test_bu.txt"
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ReturnValue      : 0
```

Det här kommandot byter namn på en fil. Parametern **Path** används för att referera till en instans av klassen **cim_datafile** . Sedan tillämpar den metoden Rename på den specifika instansen.

Egenskapen **returnValue** fylls med en 0 om kommandot har slutförts.

### Exempel 4: skicka en matris med värden med hjälp av `-ArgumentList`

Ett exempel som använder en matris med objekt `$binSD` följt av ett `$null` värde.

```powershell
$acl = get-acl test.txt
$binSD = $acl.GetSecurityDescriptorBinaryForm()
Invoke-WmiMethod -class Win32_SecurityDescriptorHelper -Name BinarySDToSDDL -ArgumentList $binSD, $null
```

## PARAMETRAR

### – Argument List

Anger de parametrar som ska skickas till den anropade metoden. Värdet för den här parametern måste vara en matris med objekt, och de måste visas i den ordning som den anropade metoden kräver. `Invoke-CimCommand`Cmdleten har inte de här begränsningarna.

Om du vill fastställa i vilken ordning dessa objekt ska visas kör du `GetMethodParameters()` metoden i WMI-klassen, som visas i exempel 1, nära slutet av det här avsnittet.

> [!IMPORTANT]
> Om det första värdet är en matris som innehåller mer än ett element, krävs ett andra värde för $null. Annars genererar kommandot ett fel, till exempel "det går inte att omvandla objekt av typen system. byte" till typen "system. array". ". Se exempel 4 ovan.

```yaml
Type: System.Object[]
Parameter Sets: class, object, path
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – AsJob

Anger att denna cmdlet kör kommandot som ett bakgrunds jobb. Använd den här parametern för att köra kommandon som tar lång tid att slutföra.

När du använder parametern **AsJob** returnerar kommandot ett objekt som representerar bakgrunds jobbet och visar sedan kommando tolken. Du kan fortsätta att arbeta i sessionen medan jobbet är klart. Om `Invoke-WmiMethod` används mot en fjärrdator skapas jobbet på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn. Om du vill hantera jobbet använder du de cmdlet: ar som innehåller jobbet Substantiv (jobb-cmdletarna). Använd Receive-Job-cmdleten för att hämta jobb resultatet.

Om du vill använda den här parametern med fjärrdatorer måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation. Dessutom måste du starta Windows PowerShell med alternativet Kör som administratör i Windows Vista och senare versioner av Windows. Mer information finns i about_Remote_Requirements.

Mer information om bakgrunds jobb i Windows PowerShell finns i about_Jobs och about_Remote_Jobs.

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

### -Autentisering

Anger den autentiseringsnivå som ska användas med WMI-anslutningen. De acceptabla värdena för den här parametern är:

- -1: oförändrad
- 0: standard
- 1: ingen (ingen autentisering utförs)
- 2: Anslut (autentisering utförs endast när klienten upprättar en relation med programmet.)
- 3: anrop (autentisering utförs endast i början av varje anrop när programmet tar emot begäran.)
- 4: paket (autentisering utförs på alla data som tas emot från klienten).
- 5: PacketIntegrity (alla data som överförs mellan klienten och programmet autentiseras och verifieras.)
- 6: PacketPrivacy (egenskaperna för de andra autentiseringsnivåer används och alla data krypteras.)

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authority

Anger den auktoritet som ska användas för att autentisera WMI-anslutningen. Du kan ange standard för Windows NT LAN Manager (NTLM) eller Kerberos-autentisering. Om du vill använda NTLM ställer du in inställningen auktoritet på ntlmdomain: \<DomainName\> , där \<DomainName\> identifierar ett giltigt NTLM-domännamn. Ange Kerberos om du vill använda Kerberos: \<DomainName\ServerName\> . Du kan inte inkludera auktoritets inställningen när du ansluter till den lokala datorn.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Klass

Anger den WMI-klass som innehåller en statisk metod som ska anropas.

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Anger, som en sträng mat ris, de datorer som denna cmdlet kör kommandot på. Standard är den lokala datorn.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera datorer. Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller localhost.

Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation. Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Standard är den aktuella användaren. Ange ett användar namn, till exempel `User01` , `Domain01\User01` eller `User@Contoso.com` . Eller ange ett **PSCredential** -objekt, till exempel ett objekt som returneras av Get-Credential-cmdleten. När du anger ett användar namn uppmanas du att ange ett lösen ord.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableAllPrivileges

Anger att denna cmdlet aktiverar alla behörigheter för den aktuella användaren innan kommandot gör WMI-anropet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Personifiering

Anger personifieringsnivån som ska användas. De acceptabla värdena för den här parametern är:

- 0: standard (läser det lokala registret för standard personifieringsnivån, som vanligt vis anges till "3: personifiera".)
- 1: Anonym (döljer anroparens autentiseringsuppgifter.)
- 2: identifiera (tillåter objekt att fråga om autentiseringsuppgifterna för anroparen.)
- 3: personifiera (tillåter att objekt använder autentiseringsuppgifterna för anroparen.)
- 4: delegera (tillåter att objekt tillåter andra objekt att använda autentiseringsuppgifterna för anroparen.)

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger ett **ManagementObject** -objekt som ska användas som indatamängd. När den här parametern används ignoreras alla andra parametrar förutom parametrarna **flagga** och **argument** .

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Locale

Anger det önskade språket för WMI-objekt. Ange värdet för parametern **locale** som en matris i `MS_<LCID>` formatet i önskad ordning.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger namnet på den metod som ska anropas. Den här parametern är obligatorisk och får inte vara null eller tom.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Namnrymd

När den används med **klass** parametern anger den här parametern namn området för WMI-lagringsplatsen där den refererade WMI-klassen eller-objektet finns.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger WMI-objektets sökväg för en WMI-klass eller anger sökvägen till WMI-objektet för en instans av en WMI-klass. Den klass eller instans som du anger måste innehålla metoden som anges i parametern **Name** .

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Anger ett begränsnings värde för antalet WMI-åtgärder som kan köras samtidigt.
Den här parametern används tillsammans med parametern **AsJob** . Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

### Inget

Denna cmdlet accepterar inte några indatatyper.

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-WSManInstance](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[Invoke-WSManAction](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[New-WSManInstance](../Microsoft.WsMan.Management/New-WSManInstance.md)

[Remove-WSManInstance](../Microsoft.WsMan.Management/Remove-WSManInstance.md)

[Get-WmiObject](Get-WmiObject.md)

[Remove-WmiObject](Remove-WmiObject.md)

[Set-WmiInstance](Set-WmiInstance.md)
