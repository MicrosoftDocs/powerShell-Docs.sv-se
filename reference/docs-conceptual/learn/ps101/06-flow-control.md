---
title: Flödeskontroll
description: PowerShell innehåller metoder för att skapa slingor, fatta beslut och logiskt styra flödet av kod i skript.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 4f0d7b7f5f3c12bb9475af5aed42b2d32cfbc14d
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84436311"
---
# <a name="chapter-6---flow-control"></a>Kapitel 6 – flödes kontroll

## <a name="scripting"></a>Använda skript

När du går från att skriva PowerShell en-liners för att skriva skript så låter det mycket mer komplicerat än det verkligen är. Ett skript är inget annat än samma eller liknande kommandon som du skulle kunna köra interaktivt i PowerShell-konsolen, förutom att de har sparats som en `.PS1` fil. Det finns vissa skript konstruktioner som du kan använda som en `foreach` loop i stället för `ForEach-Object` cmdleten. För nybörjare kan skillnaderna vara förvirrande särskilt när du anser att det `foreach` är både en skript konstruktion och ett alias för `ForEach-Object` cmdleten.

## <a name="looping"></a>Loopar

En av fördelarna med PowerShell är att när du har gått igenom hur du gör något för ett objekt är det nästan lika enkelt att göra samma uppgift för hundratals objekt. Upprepa bara objekten med någon av de många olika typerna av slingor i PowerShell.

### <a name="foreach-object"></a>-Objekt

`ForEach-Object`är en cmdlet för att söka igenom objekt i en pipeline, till exempel med PowerShell en-liners. `ForEach-Object`strömmar objekten via pipelinen.

Även om parametern **module** i `Get-Command` accepterar flera värden som är strängar, accepterar den bara dem via pipeline-inmatade efter egenskaps namn eller via parameter inmatade. I följande scenario måste du använda cmdleten om jag vill skicka två strängar efter värde till `Get-Command` för användning med parametern **module** `ForEach-Object` .

```powershell
'ActiveDirectory', 'SQLServer' |
   ForEach-Object {Get-Command -Module $_} |
     Group-Object -Property ModuleName -NoElement |
         Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  147 ActiveDirectory
   82 SqlServer
```

I föregående exempel `$_` är det aktuella objektet. Från och med PowerShell version 3,0 `$PSItem` kan användas i stället för `$_` . Men jag tycker att de flesta erfarna PowerShell-användare föredrar att använda `$_` eftersom det är bakåtkompatibelt och mindre för att skriva.

När du använder `foreach` nyckelordet måste du lagra alla objekt i minnet innan du går igenom dem, vilket kan vara svårt om du inte vet hur många objekt du arbetar med.

```powershell
$ComputerName = 'DC01', 'WEB01'
foreach ($Computer in $ComputerName) {
  Get-ADComputer -Identity $Computer
}
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

Många gånger en loop, till exempel `foreach` eller `ForEach-Object` är nödvändig. Annars visas ett fel meddelande.

```powershell
Get-ADComputer -Identity 'DC01', 'WEB01'
```

```Output
Get-ADComputer : Cannot convert 'System.Object[]' to the type
'Microsoft.ActiveDirectory.Management.ADComputer' required by parameter 'Identity'.
Specified method is not supported.
At line:1 char:26
+ Get-ADComputer -Identity 'DC01', 'WEB01'
+                          ```````````````
    + CategoryInfo          : InvalidArgument: (:) [Get-ADComputer], ParameterBindingExc
   eption
    + FullyQualifiedErrorId : CannotConvertArgument,Microsoft.ActiveDirectory.Management
   .Commands.GetADComputer
```

Andra gånger kan du få samma resultat samtidigt som du eliminerar slingan helt. Läs cmdlet-hjälpen för att förstå dina alternativ.

```powershell
'DC01', 'WEB01' | Get-ADComputer
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

Som du kan se i föregående exempel accepterar **identitets** parametern för `Get-ADComputer` bara ett enda värde när den tillhandahålls via parameter indata, men den tillåter flera objekt när indatan tillhandahålls via pipeline-indata.

### <a name="for"></a>För

En `for` loop upprepas när ett angivet villkor är sant. `for`Loopen är inte något som jag använder ofta, men den använder sig av den.

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
}
```

```Output
Sleeping for 1 seconds
Sleeping for 2 seconds
Sleeping for 3 seconds
Sleeping for 4 seconds
```

I föregående exempel itererar loopen fyra gånger genom att börja med siffran ett och fortsätta så länge som räknarvärdet `$i` är mindre än 5. Den försätts i vilo läge i totalt 10 sekunder.

### <a name="do"></a>Gör följande

Det finns två olika `do` slingor i PowerShell. `Do Until`körs när det angivna villkoret är falskt.

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  }
  elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
until ($guess -eq $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
```

Föregående exempel är ett tal spel som fortsätter tills värdet du antar motsvarar samma siffra som `Get-Random` cmdleten genererade.

`Do While`är bara tvärtom. Den körs så länge det angivna villkoret utvärderas till sant.

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  } elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
while ($guess -ne $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
Too low!
What's your guess?: 4
```

Samma resultat uppnås med en `Do While` slinga genom att du återställer test villkoret till inte lika med.

`Do`loopar körs alltid minst en gång eftersom villkoret utvärderas i slutet av slingan.

### <a name="while"></a>Tiden

På samma sätt som `Do While` slingan `While` körs loopen så länge det angivna villkoret är sant. Skillnaden är dock att en `While` slinga utvärderar villkoret överst i slingan innan koden körs. Så den körs inte om villkoret utvärderas till false.

```powershell
$date = Get-Date -Date 'November 22'
while ($date.DayOfWeek -ne 'Thursday') {
  $date = $date.AddDays(1)
}
Write-Output $date
```

```Output
Thursday, November 23, 2017 12:00:00 AM
```

Det föregående exemplet beräknar vilken dag som tacksägelse dag är på USA. Den är alltid den fjärde torsdagen november. Loopen börjar med 22-dagen i november och lägger till en dag medan vecko dagen inte är lika med torsdag. Om 22 är en torsdag körs inte loopen alls.

## <a name="break-continue-and-return"></a>Bryt, Fortsätt och returnera

`Break`är utformad för att bryta ut ur en slinga. Den används också ofta med `switch` instruktionen.

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
  break
}
```

```Output
Sleeping for 1 seconds
```

`break`Instruktionen som visas i föregående exempel gör att slingan avslutas vid den första iterationen.

Continue är utformat för att hoppa till nästa iteration av en slinga.

```powershell
while ($i -lt 5) {
  $i += 1
  if ($i -eq 3) {
    continue
  }
  Write-Output $i
}
```

```Output
1
2
4
5
```

I föregående exempel kommer siffrorna 1, 2, 4 och 5 att matas ut. Den hoppar över nummer 3 och fortsätter med nästa iteration av slingan. Det fungerar ungefär som `break` `continue` i loopen förutom för den aktuella iterationen. Körningen fortsätter med nästa iteration i stället för att bryta ut ur loopen och stoppa.

Return är utformad för att avsluta det befintliga omfånget.

```powershell
$number = 1..10
foreach ($n in $number) {
  if ($n -ge 4) {
    Return $n
  }
}
```

```Output
4
```

Observera att i föregående exempel returnerar utdata det första resultatet och finns kvar i slingan. En mer grundlig förklaring av resultat instruktionen finns i en av mina blogg artiklar: ["PowerShell Return Keyword"][].

## <a name="summary"></a>Sammanfattning

I det här kapitlet har du lärt dig om de olika typerna av slingor som finns i PowerShell.

## <a name="review"></a>Granska

1. Vad är skillnaden i `ForEach-Object` cmdleten och den uppbyggda skript konstruktionen?
1. Vad är den främsta fördelen med att använda en while-loop i stället för att göra det eller göra tills loop.
1. Hur skiljer sig Break-och Continue-satserna?

## <a name="recommended-reading"></a>Rekommenderad läsning

- [-Objekt][]
- [about_ForEach][]
- [about_For][]
- [about_Do][]
- [about_While][]
- [about_Break][]
- [about_Continue][]
- [about_Return][]

<!-- link references -->
[-Objekt]: /powershell/module/microsoft.powershell.core/foreach-object
[about_ForEach]: /powershell/module/microsoft.powershell.core/about/about_foreach
[about_For]: /powershell/module/microsoft.powershell.core/about/about_for
[about_Do]: /powershell/module/microsoft.powershell.core/about/about_do
[about_While]: /powershell/module/microsoft.powershell.core/about/about_while
[about_Break]: /powershell/module/microsoft.powershell.core/about/about_break
[about_Continue]: /powershell/module/microsoft.powershell.core/about/about_continue
[about_Return]: /powershell/module/microsoft.powershell.core/about/about_return
["Nyckelordet" PowerShell Return "]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
