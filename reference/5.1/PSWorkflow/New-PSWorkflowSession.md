---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflow
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowSession
ms.openlocfilehash: 995dd8a6df3ac8ebd7a204d2aefef3fa6aa71e14
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264602"
---
# New-PSWorkflowSession

## SAMMANFATTNING
Skapar en arbets flödes session.

## SYNTAX

```
New-PSWorkflowSession [[-ComputerName] <String[]>] [-Credential <Object>] [-Name <String[]>] [-Port <Int32>]
 [-UseSSL] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-EnableNetworkAccess]
 [<CommonParameters>]
```

## BESKRIVNING

`New-PSWorkflowSession`Cmdlet: en skapar en **PSSession** (User-Managed session) som är särskilt utformad för att köra Windows PowerShell-arbetsflöden. Konfigurationen för Microsoft. PowerShell. Workflow-sessionen används, som innehåller skript, typ och formatering av filer och alternativ som krävs för arbets flöden.

Du kan använda `New-PSWorkflowSession` eller dess alias `nwsn` .

Du kan också lägga till gemensamma parametrar för arbets flöden i det här kommandot. Mer information om gemensamma parametrar för arbets flöden finns i [about_WorkflowCommonParameters](./about/about_WorkflowCommonParameters.md)

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: skapa en arbets flödes session på en fjärran sluten dator

I det här exemplet skapas en **WorkflowTests** -session på ServerNode01-fjärrdatorn.

```powershell
$params = @{
    ComputerName = "ServerNode01"
    Name = "WorkflowTests"
    SessionOption = (New-PSSessionOption -OutputBufferingMode Drop)
}
New-PSWorkflowSession @params
```

Värdet för parametern **SessionOption** är ett `New-PSSessionOption` kommando som ställer in buffrings läget för utdata i sessionen för att **släppa**.

### Exempel 2: skapa arbets flödes sessioner på flera fjärrdatorer

I det här exemplet skapas arbets flödes sessioner på ServerNode01-och Server12-datorerna. Kommandot använder parametern **Credential** för att köras med behörigheterna för domän administratören.

```powershell
"ServerNode01", "Server12" |
    New-PSWorkflowSession -Name WorkflowSession -Credential Domain01\Admin01 -ThrottleLimit 150
```

Kommandot använder parametern **ThrottleLimit** för att öka begränsningen per kommando till 150.
Värdet prioriteras över standard begränsningen på 100 som anges i konfigurationen för **Microsoft. PowerShell. Workflow** -sessionen.

## PARAMETRAR

### -ApplicationName

Anger program namns segmentet för anslutnings-URI: n.

Standardvärdet är värdet för Preference- `$PSSessionApplicationName` variabeln på den lokala datorn. Om den här preferens variabeln inte definieras är standardvärdet WSMAN. Det här värdet är lämpligt för de flesta användnings områden. Mer information finns i [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

WinRM-tjänsten använder program namnet för att välja en lyssnare som ska betjäna anslutningsbegäran.
Värdet för den här parametern ska matcha värdet på egenskapen **URLPrefix** för en lyssnare på fjärrdatorn.

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

### -Autentisering

Anger den mekanism som används för att autentisera användarautentiseringsuppgifter.
De acceptabla värdena för den här parametern är:

- Default
- Basic
- CredSSP
- Sammandrag
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

Standardvärdet är default.

CredSSP-autentisering är endast tillgängligt i Windows Vista, Windows Server 2008 och senare versioner av Windows operativ system.

Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

> [!CAUTION]
> Autentisering av Credential Security Service Provider (CredSSP), där användarautentiseringsuppgifterna skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs. Den här mekanismen ökar säkerhets risken för Fjärråtgärden. Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden. Ange certifikatets tumavtryck.

Certifikat används i klient certifikat-baserad autentisering. De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.

Om du vill hämta ett tumavtryck för certifikatet använder du `Get-Item` cmdleten eller `Get-ChildItem` cmdleten i Windows PowerShell-certifikatet: enhet.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Skapar en permanent anslutning ( **PSSession** ) till den angivna datorn. Om du anger flera dator namn skapar Windows PowerShell flera **PSSessions** , en för varje dator. Standard är den lokala datorn.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera fjärrdatorer. Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.). När datorn finns i en annan domän än användaren, krävs det fullständigt kvalificerade domän namnet. Du kan också skicka ett dator namn inom citat tecken till `New-PSWorkflowSession` .

Om du vill använda en IP-adress i värdet för parametern **computername** måste kommandot innehålla parametern **Credential** . Dessutom måste datorn konfigureras för HTTPS-transport eller fjärrdatorns IP-adress måste ingå i listan WinRM TrustedHosts på den lokala datorn. Instruktioner för att lägga till ett dator namn i listan TrustedHosts finns i avsnittet om hur du lägger till en dator i listan över betrodda värdar i [about_Remote_Troubleshooting](../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Standard är den aktuella användaren. Ange ett användar namn, till exempel user01, Domain01\User01 eller User@Domain.com , eller ange ett **PSCredential** -objekt, till exempel ett som returneras av `Get-Credential` cmdleten.

När du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

Anger att denna cmdlet lägger till en interaktiv säkerhetstoken till loopback-sessioner. Med den interaktiva token kan du köra kommandon i loopback-sessionen som hämtar data från andra datorer. Du kan till exempel köra ett kommando i sessionen som kopierar XML-filer från en fjärrdator till den lokala datorn.

En loopback-session är en **PSSession** som kommer från och slutar på samma dator. Om du vill skapa en loopback-session ska du inte ange parametern **computername** eller ange värdet för punkt, localhost eller namnet på den lokala datorn.

Som standard skapas loopback-sessioner som har en nätverks-token som kanske inte ger behörighet att autentisera till fjärrdatorer.

Parametern **EnableNetworkAccess** är endast effektiv i loopback-sessioner. Om du anger parametern **EnableNetworkAccess** när du skapar en session på en fjärrdator, lyckas kommandot, men parametern ignoreras.

Du kan också tillåta fjärråtkomst i en loopback-session med hjälp av **CredSSP** -värdet för parametern **Authentication** , som delegerar autentiseringsuppgifterna för sessionen till andra datorer.

För att skydda datorn från skadlig åtkomst, frånkopplade loopback-sessioner som har interaktiva tokens, kan de som skapats med hjälp av parametern **EnableNetworkAccess** bara återanslutas från den dator där sessionen skapades. Frånkopplade sessioner som använder CredSSP-autentisering kan återanslutas från andra datorer. Mer information finns i `Disconnect-PSSession` cmdleten.

Den här parametern introducerades i Windows PowerShell 3,0.

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

### -Name

Anger ett eget namn för arbets flödes sessionen. Du kan använda namnet med andra cmdletar, till exempel `Get-PSSession` och `Enter-PSSession` . Namnet måste inte vara unikt för datorn eller den aktuella sessionen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Session#
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Anger nätverks porten på den fjärrdator som används för den här anslutningen. Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder. Standard portarna är 5985 (WinRM-port för HTTP) och 5986 (WinRM-port för HTTPS).

Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten. Använd följande kommandon för att konfigurera lyssnaren:

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

Använd inte **port** parametern om du inte behöver. Port inställningen i kommandot gäller för alla datorer eller sessioner där kommandot körs. En alternativ port inställning kan hindra kommandot från att köras på alla datorer.

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

### -SessionOption

Anger avancerade alternativ för sessionen. Ange ett **SessionOption** -objekt, till exempel ett som du skapar med hjälp av `New-PSSessionOption` cmdleten.

Standardvärdena för alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts. Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.

Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i `$PSSessionOption` variabeln Preference och i konfigurationen för sessionen. De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen. För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).

En beskrivning av sessions alternativen, inklusive standardvärdena, finns i `New-PSSessionOption` .
Information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.
Om du utelämnar den här parametern eller anger värdet 0 (noll) används standardvärdet för konfigurationen av **Microsoft. PowerShellWorkflow** -sessionen, 100.

Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Anger att denna cmdlet använder Secure Sockets Layer-protokollet (SSL) för att upprätta en anslutning till fjärrdatorn. Som standard används inte SSL.

WS-Management krypterar allt Windows PowerShell-innehåll som överförs via nätverket. Parametern **UseSSL** är ett ytterligare skydd som skickar data via en HTTPS-anslutning i stället för en HTTP-anslutning.

Om du anger den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. körnings utrymmen. PSSession [], system. String

Du kan skicka vidare en session eller ett dator namn till denna cmdlet.

## UTDATA

### System. Management. Automation. körnings utrymmen. PSSession

## ANTECKNINGAR

Ett `New-PSWorkflowSession` kommando motsvarar följande kommando:

`New-PSSession -ConfigurationName Microsoft.PowerShell.Workflow`

## RELATERADE LÄNKAR

[Koppla från-PSSession](../Microsoft.PowerShell.Core/Disconnect-PSSession.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-PSTransportOption](../Microsoft.PowerShell.Core/New-PSTransportOption.md)

[Registrera – PSSessionConfiguration](../Microsoft.PowerShell.Core/Register-PSSessionConfiguration.md)

[about_PSSessions](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)

[about_Workflows](../PSWorkflow/About/about_Workflows.md)

[about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)
