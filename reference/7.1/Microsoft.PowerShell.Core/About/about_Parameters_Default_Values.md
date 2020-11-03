---
description: Beskriver hur du ställer in anpassade standardvärden för cmdlet-parametrar och avancerade funktioner.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 5/31/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters_default_values?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters_Default_Values
ms.openlocfilehash: c16af49308df26fc51f57c9bd176ad2fd5537e2c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271293"
---
# <a name="about-parameters-default-values"></a>Om standardvärden för parametrar

## <a name="short-description"></a>Kort beskrivning

Beskriver hur du ställer in anpassade standardvärden för cmdlet-parametrar och avancerade funktioner.

## <a name="long-description"></a>Lång beskrivning

Med `$PSDefaultParameterValues` variabeln Preference kan du ange anpassade standardvärden för valfri cmdlet eller avancerad funktion. Cmdletar och avancerade funktioner använder det anpassade standardvärdet om du inte anger något annat värde i kommandot.

Författare av cmdletar och avancerade funktioner ställer in standardvärden för sina parametrar. Vanliga standardvärden är vanligt vis användbara, men de är kanske inte lämpliga för alla miljöer.

Den här funktionen är särskilt användbar när du måste ange samma alternativa parameter värde nästan varje gång du använder kommandot eller när ett visst parameter värde är svårt att komma ihåg, till exempel ett e-postservernamn eller projekt-GUID.

Om det önskade standardvärdet varierar förutsägbart kan du ange ett skript block som innehåller olika standardvärden för en parameter under olika förhållanden.

`$PSDefaultParameterValues` introducerades i PowerShell 3,0.

## <a name="syntax"></a>Syntax

`$PSDefaultParameterValues`Variabeln är en hash-tabell som verifierar formatet för nycklar som objekt typ av **system. Management. Automation. DefaultParameterDictionary**. Hash-tabellen innehåller **nyckel/värde-** par. En **nyckel** har formatet `CmdletName:ParameterName` . Ett **värde** är **DefaultValue** eller **script block** som tilldelats nyckeln.

Syntaxen för `$PSDefaultParameterValues` Preference-variabeln är följande:

```
$PSDefaultParameterValues=@{"CmdletName:ParameterName"="DefaultValue"}

$PSDefaultParameterValues=@{ "CmdletName:ParameterName"={{ScriptBlock}} }

$PSDefaultParameterValues["Disabled"]=$True | $False
```

Jokertecken tillåts i värdena **CmdletName** och **ParameterName** .

Om du vill ange, ändra, lägga till eller ta bort ett speciellt **nyckel/värde** -par från `$PSDefaultParameterValues` använder du metoderna för att redigera en standard-hash-tabell. Till exempel metoderna **Add** och **Remove** . Dessa metoder skriver inte över andra värden i hash-tabellen.

Det finns en annan syntax som inte skriver över en befintlig `$PSDefaultParameterValues` hash-tabell. Om du vill lägga till eller ändra ett speciellt **nyckel/värde** -par använder du följande syntax:

```
$PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

**CmdletName** måste vara namnet på en cmdlet eller namnet på en avancerad funktion som använder attributet **CmdletBinding** . Du kan inte använda `$PSDefaultParameterValues` för att ange standardvärden för skript eller enkla funktioner.

**DefaultValue** kan vara ett objekt eller ett skript block. Om värdet är ett-skript block utvärderar PowerShell skript blocket och använder resultatet som parameter värde. När den angivna parametern accepterar ett skript Blocks värde, omger du skript block svärdet i en andra uppsättning klammerparenteser, till exempel:

```powershell
$PSDefaultParameterValues=@{ "Invoke-Command:ScriptBlock"={{Get-Process}} }
```

Mer information finns i följande dokument:

- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Script_Blocks](about_Script_Blocks.md)
- [about_Preference_Variables](about_Preference_Variables.md)

## <a name="examples"></a>Exempel

### <a name="how-to-set-psdefaultparametervalues"></a>Så här ställer du in \$ PSDefaultParameterValues

`$PSDefaultParameterValues` är en inställnings variabel, så den finns bara i den session där den har angetts. Det har inget standardvärde.

Ange `$PSDefaultParameterValues` genom att skriva variabelns namn och ett eller flera **nyckel/värde-** par. Om du kör ett annat `$PSDefaultParameterValues` kommando skriver det över den befintliga hash-tabellen.

Exempel på hur du ändrar **nyckel/värde-** par utan att skriva över befintliga värden för hash-tabeller finns i [så här lägger du till värden i \$ PSDefaultParameterValues](#how-to-add-values-to-psdefaultparametervalues) eller [hur du ändrar värden i \$ PSDefaultParameterValues](#how-to-change-values-in-psdefaultparametervalues).

Om du vill spara `$PSDefaultParameterValues` för framtida sessioner lägger du till ett `$PSDefaultParameterValues` kommando i din PowerShell-profil. Mer information finns i [about_Profiles](about_Profiles.md).

#### <a name="set-a-custom-default-value"></a>Ange ett anpassat standardvärde

**Nyckel/värde-** paret ställer in `Send-MailMessage:SmtpServer` nyckeln till ett anpassat standardvärde för **Server123**.

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
}
```

#### <a name="set-default-values-for-multiple-parameters"></a>Ange standardvärden för flera parametrar

Om du vill ange standardvärden för flera parametrar, separera varje **nyckel/värde** -par med ett semikolon ( `;` ). `Send-MailMessage:SmtpServer`Nycklarna och `Get-WinEvent:LogName` är inställda på anpassade standardvärden.

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123";
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
}
```

#### <a name="use-wildcards-and-switch-parameters"></a>Använda jokertecken och växla parametrar

Cmdlet och parameter namn får innehålla jokertecken. Använd `$True` och `$False` för att ange värden för växel parametrar, till exempel **verbose**. Den gemensamma parameterns **utförliga** parameter har angetts till `$True` för alla kommandon.

```powershell
$PSDefaultParameterValues = @{"*:Verbose"=$True}
```

#### <a name="use-an-array-for-the-default-value"></a>Använd en matris för standardvärdet

Om en parameter kan acceptera flera värden, en matris, kan du ange flera värden som standardvärden. Standardvärdet för `Invoke-Command:ComputerName` nyckeln anges till ett mat ris värde för **Server01** och **Server02**.

```powershell
$PSDefaultParameterValues = @{
  "Invoke-Command:ComputerName"="Server01","Server02"
}
```

#### <a name="use-a-script-block"></a>Använd ett skript block

Du kan använda ett-skript block för att ange olika standardvärden för en parameter under olika villkor. PowerShell utvärderar skript blocket och använder resultatet som standard parameter värde.

De `Format-Table:AutoSize` nyckel uppsättningar som byter parameter till värdet **Sant**. `If`Instruktionen innehåller ett villkor som `$host.Name` måste vara PowerShell-konsolen, **ConsoleHost**.

```powershell
$PSDefaultParameterValues=@{
  "Format-Table:AutoSize"={if ($host.Name -eq "ConsoleHost"){$True}}
}
```

Om en parameter accepterar ett skript Blocks värde, omger du skript blocket med en extra uppsättning klammerparenteser. När PowerShell utvärderar det yttre skript blocket är resultatet det inre skript blocket och det anges som standard parameter värde.

`Invoke-Command:ScriptBlock`Nyckeln har angetts till ett standardvärde för **system händelse loggen** eftersom skript blocket omges av en andra uppsättning klammerparenteser. Resultatet av skript blocket skickas till `Invoke-Command` cmdlet: en.

```powershell
$PSDefaultParameterValues=@{
  "Invoke-Command:ScriptBlock"={{Get-EventLog -Log System}}
}
```

### <a name="how-to-get-psdefaultparametervalues"></a>Så här hämtar du \$ PSDefaultParameterValues

Hash-tabellens värden visas genom att `$PSDefaultParameterValues` du anger i PowerShell-prompten.

En `$PSDefaultParameterValues` hash-tabell har angetts med tre **nyckel/värde-** par.
Den här hash-tabellen används i följande exempel som beskriver hur du lägger till, ändrar och tar bort värden från `$PSDefaultParameterValues` .

```
PS> $PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
  "Get-*:Verbose"=$True
}

PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

Använd följande syntax för att hämta värdet för en speciell `CmdletName:ParameterName` nyckel:

```
$PSDefaultParameterValues["CmdletName:ParameterName"]
```

Till exempel för att hämta värdet för `Send-MailMessage:SmtpServer` nyckeln.

```
PS> $PSDefaultParameterValues["Send-MailMessage:SmtpServer"]
Server123
```

### <a name="how-to-add-values-to-psdefaultparametervalues"></a>Så här lägger du till värden i \$ PSDefaultParameterValues

`$PSDefaultParameterValues`Använd metoden **Add** för att lägga till ett värde i. Om du lägger till ett värde påverkas inte hash-tabellens befintliga värden.

Använd kommatecken ( `,` ) för att avgränsa **nyckeln** från **värdet**. Följande syntax visar hur du använder metoden **Add** för `$PSDefaultParameterValues` .

```
PS> $PSDefaultParameterValues.Add("CmdletName:ParameterName", "DefaultValue")
```

Hash-tabellen som skapades i föregående exempel uppdateras med ett nytt **nyckel/värde-** par. Metoden **Add** ställer in `Get-Process:Name` nyckeln till **PowerShell** -värdet.

```powershell
$PSDefaultParameterValues.Add("Get-Process:Name", "PowerShell")
```

Följande syntax uppnår samma resultat.

```powershell
$PSDefaultParameterValues["Get-Process:Name"]="PowerShell"
```

`$PSDefaultParameterValues`Den uppdaterade hash-tabellen visas i variabeln. `Get-Process:Name`Nyckeln har lagts till.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-Process:Name               PowerShell
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-remove-values-from-psdefaultparametervalues"></a>Ta bort värden från \$ PSDefaultParameterValues

Ta bort ett värde från `$PSDefaultParameterValues` genom att använda **Remove** -metoden för hash-tabeller. Om du tar bort ett värde påverkas inte hash-tabellens befintliga värden.

Följande syntax visar hur du använder **Remove** -metoden i `$PSDefaultParameterValues` .

```
PS> $PSDefaultParameterValues.Remove("CmdletName:ParameterName")
```

I det här exemplet uppdateras hash-tabellen som skapades i föregående exempel för att ta bort ett **nyckel/värde-** par. Metoden **Remove** tar bort `Get-Process:Name` nyckeln.

```powershell
$PSDefaultParameterValues.Remove("Get-Process:Name")
```

`$PSDefaultParameterValues`Den uppdaterade hash-tabellen visas i variabeln. `Get-Process:Name`Nyckeln har tagits bort.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-change-values-in-psdefaultparametervalues"></a>Ändra värden i \$ PSDefaultParameterValues

Ändringar av ett speciellt värde påverkar inte befintliga värden för hash-tabeller. Om du vill ändra ett särskilt **nyckel/värde** -par i `$PSDefaultParameterValues` använder du följande syntax:

```
PS> $PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

I det här exemplet uppdateras hash-tabellen som skapades i föregående exempel för att ändra ett **nyckel/värde-** par. Följande kommando ändrar `Send-MailMessage:SmtpServer` nyckeln till ett nytt värde för **ServerXYZ**.

```powershell
$PSDefaultParameterValues["Send-MailMessage:SmtpServer"]="ServerXYZ"
```

`$PSDefaultParameterValues`Den uppdaterade hash-tabellen visas i variabeln. `Send-MailMessage:SmtpServer`Nyckeln ändrades till ett nytt värde.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

### <a name="how-to-disable-and-re-enable-psdefaultparametervalues"></a>Inaktivera och återaktivera \$ PSDefaultParameterValues

Du kan tillfälligt inaktivera och sedan återaktivera `$PSDefaultParameterValues` .
`$PSDefaultParameterValues`Att inaktivera är användbart om du kör skript som behöver olika standard parameter värden.

Om du vill inaktivera `$PSDefaultParameterValues` lägger du till en nyckel med `Disabled` värdet **Sant**. Värdena i `$PSDefaultParameterValues` bevaras, men är inte effektiva.

```
PS> $PSDefaultParameterValues.Add("Disabled", $True)
```

Följande syntax uppnår samma resultat.

```
PS> $PSDefaultParameterValues["Disabled"]=$True
```

`$PSDefaultParameterValues`Variabeln visar den uppdaterade hash-tabellen med värdet för `Disabled` nyckeln.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       True
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

`$PSDefaultParameterValues`Ta bort den **inaktiverade** nyckeln eller ändra värdet för den **inaktiverade** nyckeln till om du vill aktivera det igen `$False` . Det tidigare värdet för `$PSDefaultParameterValues` börjar gälla igen.

```
PS> $PSDefaultParameterValues.Remove("Disabled")
```

Följande syntax uppnår samma resultat.

```
PS> $PSDefaultParameterValues["Disabled"]=$False
```

`$PSDefaultParameterValues`Den uppdaterade hash-tabellen visas i variabeln. När metoden **Remove** används `Disabled` tas nyckeln bort från utdata.
Om den alternativa syntaxen användes för att aktivera igen `$PSDefaultParameterValues` `Disabled` visas nyckeln som **falsk**.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       False
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

## <a name="see-also"></a>Se även

[about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Script_Blocks](about_Script_Blocks.md)

