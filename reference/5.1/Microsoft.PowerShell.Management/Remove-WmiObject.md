---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WmiObject
ms.openlocfilehash: 287eb02e7de2f4182e0ecfd7f6b6a7cafb66969e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265473"
---
# Remove-WmiObject

## SAMMANFATTNING
Tar bort en instans av en befintlig Windows Management Instrumentation (WMI)-klass.

## SYNTAX

### klass (standard)

```
Remove-WmiObject [-Class] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### objekt

```
Remove-WmiObject -InputObject <ManagementObject> [-AsJob] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### path

```
Remove-WmiObject -Path <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### WQLQuery

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DocumentDB

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### lista

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING
Cmdlet: en **Remove-WmiObject** tar bort en instans av en befintlig Windows Management INSTRUMENTATION (WMI)-klass.

## EXEMPEL

### Exempel 1: Stäng alla instanser av en Win32-process

```
PS C:\> notepad
PS C:\> $np = Get-WmiObject -Query "select * from win32_process where name='notepad.exe'"
PS C:\> $np | Remove-WmiObject
```

I det här exemplet stängs alla instanser av Notepad.exe.

Det första kommandot startar en instans av Notepad.

Det andra kommandot använder cmdleten Get-WmiObject för att hämta instanserna av Win32_Process som motsvarar Notepad.exe och lagrar dem sedan i $np variabeln.

Det tredje kommandot skickar objektet i $np-variabeln till **Remove-WmiObject** , som tar bort alla instanser av Notepad.exe.

### Exempel 2: ta bort en mapp

```
PS C:\> $a = Get-WMIObject -Query "Select * From Win32_Directory Where Name ='C:\\Test'"
PS C:\> $a | Remove-WMIObject
```

Detta kommando tar bort mappen C:\Test.

Det första kommandot använder **Get-WMIObject** för att fråga efter mappen C:\Test och lagrar sedan objektet i variabeln $a.

Det andra kommandot rör $a-variabeln som **Remove-WMIObject** , som tar bort mappen.

## PARAMETRAR

### – AsJob
Anger att denna cmdlet körs som ett bakgrunds jobb.
Använd den här parametern för att köra kommandon som tar lång tid att slutföra.

Nya CIM-cmdletar, introducerade Windows PowerShell 3,0, utför samma uppgifter som WMI-cmdlets.
CIM-cmdlets följer WS-Management (WSMan)-standarder och med Common Information Model (CIM) standard, vilket gör att cmdletarna kan använda samma metoder för att hantera datorer som kör Windows-operativsystemet och de som kör andra operativ system.
Överväg att använda cmdleten Remove-CimInstance i stället för att använda **Remove-WmiObject** https://go.microsoft.com/fwlink/?LinkId=227964 .

När du använder parametern *AsJob* returnerar kommandot ett objekt som representerar bakgrunds jobbet och visar sedan kommando tolken.
Du kan fortsätta att arbeta i sessionen medan jobbet är klart.
Om **Remove-WmiObject** används mot en fjärrdator, skapas jobbet på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn.
Om du vill hantera jobbet använder du de cmdlet: ar som innehåller **jobbet** Substantiv ( **jobb** -cmdletarna).
Använd Receive-Job-cmdleten för att hämta jobb resultatet.

Om du vill använda den här parametern för fjärrdatorer måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation.
Starta Windows PowerShell med alternativet Kör som administratör.
Mer information finns i about_Remote_Requirements.

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
Anger den autentiseringsnivå som ska användas för WMI-anslutningen.
De acceptabla värdena för den här parametern är:

- -1: oförändrad.
- 0: standard.
- 1: ingen.
Ingen autentisering utförs.
- 2: Anslut.
Autentisering utförs endast när klienten upprättar en relation med programmet.
- 3: anropa.
Autentisering utförs endast i början av varje anrop när programmet tar emot begäran.
- 4: paket.
Autentisering utförs på alla data som tas emot från klienten.
- 5: PacketIntegrity.
Alla data som överförs mellan klienten och programmet autentiseras och verifieras.
- 6: PacketPrivacy.
Egenskaperna för de andra autentiseringsnivåer används och alla data krypteras.

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
Anger den auktoritet som ska användas för att autentisera WMI-anslutningen.
Du kan ange standard-NTLM eller Kerberos-autentisering.
Om du vill använda NTLM ställer du in inställningen auktoritet på ntlmdomain: \<DomainName\> , där \<DomainName\> identifierar ett giltigt NTLM-domännamn.
Ange Kerberos om du vill använda Kerberos: \<DomainName\> \\ \<ServerName\> .
Du kan inte inkludera auktoritets inställningen när du ansluter till den lokala datorn.

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
Anger namnet på en WMI-klass som denna cmdlet tar bort.

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
Anger namnet på den dator där cmdleten körs.
Standard är den lokala datorn.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera datorer.
Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller localhost.

Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.
Du kan använda parametern *computername* även om datorn inte är konfigurerad för att köra fjärrkommandon.

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
Anger ett användar konto som har behörighet att utföra den här åtgärden.
Standard är den aktuella användaren.

Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, till exempel ett som genereras av Get-Credential cmdlet.
Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.

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
Anger att denna cmdlet aktiverar alla behörigheter för den aktuella användaren innan det kommando som gör WMI-anropet.

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
Anger personifieringsnivån som ska användas.
De acceptabla värdena för den här parametern är:

- 0: standard.
Läser det lokala registret för standard personifieringsnivån, som vanligt vis anges till 3: personifiera.
- 1: Anonym.
Döljer anroparens autentiseringsuppgifter.
- 2: identifiera.
Tillåter att objekt frågar efter anroparens autentiseringsuppgifter.
- 3: personifiera.
Tillåter att objekt använder autentiseringsuppgifterna för anroparen.
- 4: delegera.
Tillåter objekt att tillåta att andra objekt använder autentiseringsuppgifterna för anroparen.

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
Anger ett **ManagementObject** -objekt som ska användas som indatamängd.
När den här parametern används ignoreras alla andra parametrar.

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
Anger det önskade språket för WMI-objekt.
Parametern *locale* anges som en matris i MS_ \<LCID\> formatet i den ordning som du föredrar.

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

### – Namnrymd
Anger namn området för WMI-lagringsplatsen där den refererade WMI-klassen finns när den används med *klass* parametern.

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
Anger WMI-objektets sökväg för en WMI-klass, eller anger sökvägen till WMI-objektet för en instans av en WMI-klass som ska tas bort.

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
Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.
Den här parametern används tillsammans med parametern *AsJob* .
Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.

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

### System. Management. ManagementObject
Du kan skicka vidare ett hanterings objekt till denna cmdlet.

## UTDATA

### Ingen, system. Management. Automation. RemotingJob
Den här cmdleten returnerar ett jobb objekt, om du anger parametern *AsJob* .
Annars genererar den inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-WmiObject](Get-WmiObject.md)

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Set-WmiInstance](Set-WmiInstance.md)
