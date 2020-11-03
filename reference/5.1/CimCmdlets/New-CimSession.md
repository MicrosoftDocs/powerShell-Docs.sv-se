---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSession
ms.openlocfilehash: 04d0b272995538e88fff2725eb8806c66d217460
ms.sourcegitcommit: 9a53e53e7a3ef9ac0a212c61005efff9e9902452
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/18/2020
ms.locfileid: "93269246"
---
# New-CimSession

## SAMMANFATTNING

Skapar en CIM-session.

## SYNTAX

### CredentialParameterSet (standard)

```
New-CimSession [-Authentication <PasswordAuthenticationMechanism>] [[-Credential] <PSCredential>]
 [[-ComputerName] <String[]>] [-Name <String>] [-OperationTimeoutSec <UInt32>] [-SkipTestConnection]
 [-Port <UInt32>] [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

### CertificatePrameterSet

```
New-CimSession [-CertificateThumbprint <String>] [[-ComputerName] <String[]>] [-Name <String>]
 [-OperationTimeoutSec <UInt32>] [-SkipTestConnection] [-Port <UInt32>]
 [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

## BESKRIVNING

`New-CimSession`Cmdleten skapar en CIM-session. En CIM-session är ett objekt på klient sidan som representerar en anslutning till en lokal dator eller en fjärran sluten dator. CIM-sessionen innehåller information om anslutningen, till exempel **computername** , det använda protokollet eller olika identifierare.

Denna cmdlet returnerar ett CIM-sessionsobjekt som kan användas av alla andra CIM-cmdletar.

## EXEMPEL

### Exempel 1: skapa en CIM-session med standard alternativ

I det här exemplet skapas en lokal CIM-session med standard alternativ. Om **computername** inte anges `New-CimSession` skapar en DCOM-session till den lokala datorn.

```powershell
New-CimSession
```

### Exempel 2: skapa en CIM-session till en angiven dator

I det här exemplet skapas en CIM-session till den dator som anges av **computername**.
Som standard `New-CimSession` skapar en WSMan-session när **computername** anges.

```powershell
New-CimSession -ComputerName Server01
```

### Exempel 3: skapa en CIM-session till flera datorer

I det här exemplet skapas en CIM-session för varje dator som anges av **computername** i den kommaavgränsade listan.

```powershell
New-CimSession -ComputerName Server01,Server02,Server03
```

### Exempel 4: skapa en CIM-session med ett eget namn

I det här exemplet skapas en fjärrinstans av CIM till varje dator som anges av **computername** , i den kommaavgränsade listan, och tilldelar de nya sessionerna ett eget namn genom att ange **namn**.

```powershell
New-CimSession -ComputerName Server01,Server02 -Name FileServers
Get-CimSession -Name File*
```

Du kan använda det egna namnet på en CIM-session för att referera till sessionen i andra CIM-cmdletar, till exempel [Get-CimSession](Get-CimSession.md).

### Exempel 5: skapa en CIM-session till en dator med hjälp av ett PSCredential-objekt

I det här exemplet skapas en CIM-session till den dator som anges av **computername** , med hjälp av **PSCredential** -objektet som anges av **Credential** och autentiseringstypen som anges av **autentisering**.

```powershell
New-CimSession -ComputerName Server01 -Credential $cred -Authentication Negotiate
```

Du kan skapa ett **PSCredential** -objekt med hjälp av [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdleten.

### Exempel 6: skapa en CIM-session till en dator med en angiven port

I det här exemplet skapas en CIM-session till den dator som anges av **computername** med TCP-porten som anges av **port**.

```powershell
New-CimSession -ComputerName Server01 -Port 1234
```

### Exempel 7: skapa en CIM-session med DCOM

I det här exemplet skapas en CIM-session med hjälp av DCOM-protokollet (Distributed COM) i stället för WSMan.

```powershell
$SessionOption = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server1 -SessionOption $SessionOption
```

## PARAMETRAR

### -Autentisering

Anger autentiseringstypen som används för användarens autentiseringsuppgifter. De acceptabla värdena för den här parametern är:

- Default
- Sammandrag
- Negotiate
- Basic
- Kerberos
- NtlmDomain
- CredSsp

Du kan inte använda autentiseringstypen **NtlmDomain** för anslutning till den lokala datorn. **CredSSP** -autentisering är endast tillgängligt i Windows Vista, windows Server 2008 och senare versioner av Windows.

> [!CAUTION]
> Autentisering av Credential Security Service Provider (CredSSP) är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs. Den här mekanismen ökar säkerhets risken för Fjärråtgärden. Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: CredentialParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CertificateThumbprint

Anger det digitala offentliga nyckel certifikatet (X. 509) för ett användar konto som har behörighet att utföra den här åtgärden. Ange certifikatets tumavtryck.

Certifikat används i klient certifikat-baserad autentisering. De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.

Använd [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) cmdletarna eller i PowerShell-certifikat leverantören för att hämta ett tumavtryck för certifikatet.

Mer information finns i [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).

```yaml
Type: System.String
Parameter Sets: CertificatePrameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ComputerName

Anger namnet på den dator som CIM-sessionen ska skapas till. Ange antingen ett enda dator namn eller flera dator namn avgränsade med kommatecken.

Om **computername** inte anges skapas en CIM-session till den lokala datorn. Du kan ange värdet för dator namn i något av följande format:

- Ett eller flera NetBIOS-namn
- En eller flera IP-adresser
- Ett eller flera fullständigt kvalificerade domän namn.

Om datorn finns i en annan domän än användaren, måste du ange det fullständigt kvalificerade domän namnet.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Om **autentiseringsuppgifter** inte anges används det aktuella användar kontot.

Ange värdet för **autentiseringsuppgift** med något av följande format:

- Ett användar namn: "user01"
- Ett domän namn och ett användar namn: "Domain01\User01"
- En User Principal Name: " User@Domain.com "
- Ett PSCredential-objekt, till exempel ett som returneras av [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdleten.

När du anger ett användar namn uppmanas du att ange ett lösen ord.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialParameterSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger ett eget namn för CIM-sessionen.

Du kan använda namnet för att referera till CIM-sessionen när du använder andra cmdlets, till exempel [`Get-CimSession`](Get-CimSession.md) cmdleten.
Namnet måste inte vara unikt för datorn eller den aktuella sessionen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

Varaktighet för vilken cmdleten väntar på ett svar från servern.

Som standard är värdet för den här parametern 0, vilket innebär att cmdleten använder standardvärdet för timeout för servern.

Om **OperationTimeoutSec** -parametern har angetts till ett värde som är lägre än det stabila anslutnings försöket på 3 minuter, går det inte att återställa nätverks fel som sist mer än värdet för parametern **OperationTimeoutSec** , eftersom åtgärden på servern överskrider innan klienten kan återansluta.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

Anger nätverks porten på den fjärrdator som används för den här anslutningen.
Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder.
Standard portarna är 5985 (WinRM-porten för HTTP) och 5986 (WinRM-porten för HTTPS).

Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten.
Använd följande kommandon för att konfigurera lyssnaren:

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number>"}`

Använd inte **port** parametern om du inte behöver. Port inställningen i kommandot gäller för alla datorer eller sessioner där kommandot körs. En alternativ port inställning kan hindra kommandot från att köras på alla datorer.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SessionOption

Anger avancerade alternativ för den nya CIM-sessionen. Ange namnet på ett **CimSessionOption** -objekt som skapats med [`New-CimSessionOption`](New-CimSessionOption.md) cmdleten.

```yaml
Type: Microsoft.Management.Infrastructure.Options.CimSessionOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipTestConnection

Som standard `New-CimSession` upprättar cmdleten en anslutning med en fjärrWS-Management slut punkt av två skäl: för att kontrol lera att fjärrservern lyssnar på det port nummer som anges med parametern **port** och för att verifiera de angivna autentiseringsuppgifterna för kontot. Verifieringen utförs med hjälp av en standard WS-Identitys åtgärd. Du kan lägga till växeln **SkipTestConnection** om fjär WS-Management slut punkten inte kan använda WS-Identify eller om du vill minska data överförings tiden.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### Inget

Denna cmdlet accepterar inga indata.

## UTDATA

### Microsoft. Management. Infrastructure. CimSession

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-ChildItem](../Microsoft.Powershell.Management/Get-ChildItem.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Hämta objekt](../Microsoft.Powershell.Management/Get-Item.md)

[Get-CimSession](Get-CimSession.md)

[Remove-CimSession](Remove-CimSession.md)

[New-CimSessionOption](New-CimSessionOption.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)
