---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: 26c4f8c8dcc1fbd56e29f55a6a8c2e6aa37a2842
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "93273428"
---
# Get-Credential

## SAMMANFATTNING
Hämtar ett Credential-objekt baserat på ett användar namn och lösen ord.

## SYNTAX

### CredentialSet (standard)

```
Get-Credential [-Credential] <PSCredential> [<CommonParameters>]
```

### MessageSet

```
Get-Credential -Message <String> [[-UserName] <String>] [<CommonParameters>]
```

## BESKRIVNING

`Get-Credential`Cmdleten skapar ett Credential-objekt för ett angivet användar namn och lösen ord. Du kan använda Credential-objektet i säkerhets åtgärder.

Från och med PowerShell 3,0 kan du använda **meddelande** parametern för att ange ett anpassat meddelande i dialog rutan där användaren uppmanas att ange namn och lösen ord.

`Get-Credential`Cmdleten uppmanas användaren att ange ett lösen ord eller ett användar namn och lösen ord. Som standard visas en dialog ruta för autentisering där användaren uppmanas att bekräfta. I vissa värd program, t. ex. PowerShell-konsolen, kan du dock bli ombedd att ange användaren på kommando raden genom att ändra en register post. Mer information om den här register posten finns i anteckningar och exempel.

## EXEMPEL

### Exempel 1

```powershell
$c = Get-Credential
```

Det här kommandot hämtar ett Credential-objekt och sparar det i `$c` variabeln.

När du anger kommandot visas en dialog ruta som efterfrågar ett användar namn och lösen ord. När du anger den begärda informationen skapar cmdleten ett **PSCredential** -objekt som representerar användarens autentiseringsuppgifter och sparar det i `$c` variabeln.

Du kan använda objektet som indata för cmdletar som begär användarautentisering, till exempel de med en **Credential** -parameter. Vissa leverantörer som installeras med PowerShell stöder dock inte parametern för **autentiseringsuppgifter** .

### Exempel 2

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

Dessa kommandon använder ett Credential-objekt som `Get-Credential` cmdleten returnerar för att autentisera en användare på en fjärrdator så att de kan använda Windows Management Instrumentation (WMI) för att hantera datorn.

Det första kommandot hämtar ett Credential-objekt och sparar det i `$c` variabeln. Det andra kommandot använder Credential-objektet i ett `Get-CimInstance` kommando. Det här kommandot hämtar information om disk enheterna på den Server01 datorn.

### Exempel 3

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

Det här kommandot visar hur du lägger till ett `Get-Credential` kommando i ett  `Get-CimInstance` kommando.

Det här kommandot använder `Get-CimInstance` cmdleten för att hämta information om BIOS på Server01-datorn. Den använder parametern **Credential** för att autentisera användaren, Domain01\User01 och ett `Get-Credential` kommando som värde för parametern **Credential** .

### Exempel 4

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

I det här exemplet skapas en autentiseringsuppgift som innehåller ett användar namn utan ett domän namn.

Det första kommandot hämtar en autentiseringsuppgift med användar namnet user01 och lagrar det i `$c` variabeln.
Det andra kommandot visar värdet för egenskapen **username** för objektet som resulterande autentiseringsuppgifter.

### Exempel 5

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

Det här kommandot använder **PromptForCredential** -metoden för att uppmana användaren att ange användar namn och lösen ord. Kommandot sparar de resulterande autentiseringsuppgifterna i `$Credential` variabeln.

Metoden **PromptForCredential** är ett alternativ till att använda `Get-Credential` cmdleten. När du använder **PromptForCredential** kan du ange rubriken, meddelandena och användar namnet som visas i meddelande rutan.

Mer information finns i dokumentationen för [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) i SDK.

### Exempel 6

```powershell
Set-ItemProperty "HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds" -Name ConsolePrompting -Value $true
```

Det här exemplet visar hur du ändrar registret så att användaren uppmanas på kommando raden, i stället för att använda en dialog ruta.

Kommandot skapar register posten **ConsolePrompting** och anger värdet true. Starta PowerShell med alternativet "kör som administratör" för att köra det här kommandot.

Om du vill använda en dialog ruta för att ställa frågan ställer du in värdet för ConsolePrompting på falskt ($false) eller använder `Remove-ItemProperty` cmdleten för att ta bort den.

Register posten ConsolePrompting fungerar i vissa värd program, till exempel PowerShell-konsolen. Det kanske inte fungerar i alla värd program.

### Exempel 7

Det här exemplet visar hur du skapar ett Credential-objekt som är identiskt med det objekt som `Get-Credential` returneras utan att användaren tillkommer. Den här metoden kräver ett lösen ord för oformaterad text, vilket kan strida mot säkerhets standarder i vissa företag.

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

Det första kommandot sparar användar konto namnet i `$User` parametern. Värdet måste ha formatet "domän \ användare" eller "ComputerName\User".

Det andra kommandot använder `ConvertTo-SecureString` cmdleten för att skapa en säker sträng från ett lösen ord med oformaterad text. Kommandot använder parametern **Disklar** text för att ange att strängen är oformaterad text och **Force** -parametern för att bekräfta att du förstår riskerna med att använda oformaterad text.

Det tredje kommandot använder `New-Object` cmdleten för att skapa ett **PSCredential** -objekt från värdena i `$User` `$PWord` variablerna och.

### Exempel 8

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

Det här kommandot använder cmdlet: en **meddelande** och **användar namn** `Get-Credential` . Det här kommando formatet är utformat för delade skript och funktioner. I det här fallet visar meddelandet användaren varför autentiseringsuppgifter krävs och ger dem förtroende för att begäran är giltig.

### Exempel 9

```powershell
Invoke-Command -ComputerName Server01 {Get-Credential Domain01\User02}
```

```Output
PowerShell Credential Request : PowerShell Credential Request
Warning: This credential is being requested by a script or application on the SERVER01 remote computer. Enter your credentials only if you
 trust the remote computer and the application or script requesting it.

Enter your credentials.
Password for user Domain01\User02: ***************

PSComputerName     : Server01
RunspaceId         : 422bdf52-9886-4ada-ab2f-130497c6777f
PSShowComputerName : True
UserName           : Domain01\User01
Password           : System.Security.SecureString
```

Det här kommandot hämtar autentiseringsuppgifter från fjärrdatorn Server01. Kommandot använder `Invoke-Command` cmdleten för att köra ett `Get-Credential` kommando på fjärrdatorn. Utdata visar det fjärranslutna säkerhets meddelande som `Get-Credential` ingår i verifierings frågan.

## PARAMETRAR

### -Credential

Anger ett användar namn för autentiseringsuppgiften, till exempel **user01** eller **Domain01\User01**. Parameter namnet, `-Credential` , är valfritt.

När du skickar kommandot och anger ett användar namn uppmanas du att ange ett lösen ord. Om du utelämnar den här parametern uppmanas du att ange ett användar namn och lösen ord.

Från och med PowerShell 3,0, om du anger ett användar namn utan en domän, `Get-Credential` infogar inte längre ett omvänt snedstreck före namnet.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Meddelande

Anger ett meddelande som visas i autentiserings-prompten. Den här parametern är avsedd att användas i en funktion eller ett skript. Du kan använda meddelandet för att förklara för användaren varför du begär autentiseringsuppgifter och hur de ska användas.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserName

Anger ett användar namn. Autentiserings-prompten begär ett lösen ord för användar namnet. Som standard är användar namnet tomt och autentiserings-prompten begär både ett användar namn och ett lösen ord.

När frågan om autentisering visas i en dialog ruta kan användaren redigera det angivna användar namnet.
Användaren kan dock inte ändra användar namnet när prompten visas på kommando raden. När du använder den här parametern i en delad funktion eller ett skript, bör du ta hänsyn till alla möjliga presentationer.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: 1
Default value: None (blank)
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Management. Automation. PSCredential

`Get-Credential` Returnerar ett Credential-objekt.

## ANTECKNINGAR

Du kan använda **PSCredential** -objektet som `Get-Credential` skapar i-cmdletar som begär användarautentisering, till exempel de med en **Credential** -parameter.

Som standard visas verifierings frågan i en dialog ruta. Om du vill visa verifierings frågan på kommando raden lägger du till register posten **ConsolePrompting** ( `HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\ConsolePrompting` ) och anger värdet till **Sant**.
Om register posten **ConsolePrompting** inte finns eller om värdet är false visas autentiseringen i en dialog ruta. Anvisningar finns i exemplen.

Register posten **ConsolePrompting** fungerar i PowerShell-konsolen, men fungerar inte i alla värd program.

Den har till exempel ingen inverkan i PowerShell-miljön (Integrated Scripting Environment). Information om effekterna av register posten **ConsolePrompting** finns i hjälp avsnitten för värd programmet.

Parametern **Credential** stöds inte av alla providers som är installerade med PowerShell.
Från och med PowerShell 3,0 stöds det på utvalda cmdlets, till exempel `Get-Content` `New-PSDrive` cmdletarna och.

## RELATERADE LÄNKAR

[PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
