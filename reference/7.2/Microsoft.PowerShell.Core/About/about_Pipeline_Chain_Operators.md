---
description: Beskriver länkning av pipelines med `&&` `||` operatorerna och i PowerShell.
Locale: en-US
ms.date: 09/30/2019
schema: 2.0.0
title: about_Pipeline_Chain_Operators
ms.openlocfilehash: ece84ec061126401e53bf58112cd79a07a816e8d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710986"
---
# <a name="about-pipeline-chain-operators"></a>Om operatorer för pipeline-kedjan

## <a name="short-description"></a>Kort beskrivning

Beskriver länkning av pipelines med `&&` `||` operatorerna och i PowerShell.

## <a name="long-description"></a>Lång beskrivning

Från och med PowerShell 7 implementerar PowerShell `&&` `||` operatorerna och för att villkorligt kedja pipelines. Dessa operatörer är kända i PowerShell som *operatorer för pipeline-kedjan* och liknar dem [och-eller-listor](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) i POSIX-gränssnitt som bash, zsh och sh, samt [villkorsstyrda bearbetnings symboler](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) i Windows Command Shell (cmd.exe).

`&&`Operatören kör den högra pipelinen om den vänstra pipelinen lyckades. I motsatt `||` Kör operatören den högra pipelinen om den vänstra pipelinen misslyckades.

Dessa operatörer använder `$?` `$LASTEXITCODE` variablerna och för att avgöra om en pipeline misslyckades. På så sätt kan du använda dem med inbyggda kommandon och inte bara med cmdlets eller functions. Exempel:

```powershell
# Create an SSH key pair - if successful copy the public key to clipboard
ssh-keygen -t rsa -b 2048 && Get-Content -Raw ~\.ssh\id_rsa.pub | clip
```

### <a name="examples"></a>Exempel

#### <a name="two-successful-commands"></a>Två lyckade kommandon

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

#### <a name="first-command-fails-causing-second-not-to-be-executed"></a>Det första kommandot Miss lyckas, vilket orsakar att den andra inte körs

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

#### <a name="first-command-succeeds-so-the-second-command-is-not-executed"></a>Det första kommandot slutförs, så det andra kommandot körs inte

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

#### <a name="first-command-fails-so-the-second-command-is-executed"></a>Det första kommandot Miss lyckas, så det andra kommandot körs

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error: Bad
Second
```

Pipelinen lyckades definieras av värdet för `$?` variabeln, som PowerShell anger automatiskt efter att en pipeline har körts baserat på dess körnings status.
Det innebär att operatörer i pipeline-kedjan har följande likvärdighet:

```powershell
Test-Command '1' && Test-Command '2'
```

fungerar på samma sätt som

```powershell
Test-Command '1'; if ($?) { Test-Command '2' }
```

och

```powershell
Test-Command '1' || Test-Command '2'
```

fungerar på samma sätt som

```powershell
Test-Command '1'; if (-not $?) { Test-Command '2' }
```

### <a name="assignment-from-pipeline-chains"></a>Tilldelning från pipeline-kedjor

Genom att tilldela en variabel från en pipeline-kedja tas sammanfogningen av alla pipeliner i kedjan:

```powershell
$result = Write-Output '1' && Write-Output '2'
$result
```

```Output
1
2
```

Om ett skript avslutas fel uppstår under tilldelningen från en pipeline-kedja, lyckas inte tilldelningen:

```powershell
try
{
    $result = Write-Output 'Value' && $(throw 'Bad')
}
catch
{
    # Do nothing, just squash the error
}

"Result: $result"
```

```Output
Result:
```

### <a name="operator-syntax-and-precedence"></a>Operator-syntax och prioritet

Till skillnad från andra operatörer `&&` och `||` drift på pipelines i stället för uttryck som `+` eller `-and` , till exempel.

`&&` och `||` har lägre prioritet än rörledning ( `|` ) eller omdirigering ( `>` ), men en högre prioritet än jobb operatörer ( `&` ), tilldelning ( `=` ) eller semikolon ( `;` ). Det innebär att pipeliner i en pipeline-kedja kan omdirigeras individuellt och att hela pipelinen kan vara bakgrunds, tilldelas variabler eller åtskiljas som instruktioner.

Om du vill använda en syntax med lägre prioritet i en pipeline-kedja kan du överväga att använda parenteser `(...)` .
Om du vill bädda in en instruktion i en pipeline-kedja kan du på samma sätt använda ett under uttryck `$(...)` .
Detta kan vara användbart för att kombinera inbyggda kommandon med kontroll flöde:

```powershell
foreach ($file in 'file1','file2','file3')
{
    # When find succeeds, the loop breaks
    find $file && Write-Output "Found $file" && $(break)
}
```

```Output
find: file1: No such file or directory
file2
Found file2
```

Från och med PowerShell 7 har beteendet för dessa syntax ändrats så att `$?` ställs in som förväntat när ett kommando lyckas eller Miss lyckas inom parenteser eller under uttryck.

Precis som de flesta andra operatorer i PowerShell, `&&` och `||` är också *kvar att associera*, vilket innebär att de är grupperade från vänster. Exempel:

```powershell
Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist" && Get-Content -Raw ./file.txt
```

kommer att grupperas som:

```
[Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist"] && Get-Content -Raw ./file.txt
```

motsvarar:

```powershell
Get-ChildItem -Path ./file.txt

if (-not $?) { Write-Error "file.txt does not exist" }

if ($?) { Get-Content -Raw ./file.txt }
```

### <a name="error-interaction"></a>Fel interaktion

Pipelines kedje operatorer absorberar inte fel. När en instruktion i en pipeline-kedja genererar ett skript-avslutande fel, avslutas pipelin kedjan.

Exempel:

```powershell
$(throw 'Bad') || Write-Output '2'
```

```Output
Exception: Bad
```

Även om felet fångas, avslutas pipelinen fortfarande:

```powershell
try
{
    $(throw 'Bad') || Write-Output '2'
}
catch
{
    Write-Output "Caught: $_"
}
Write-Output 'Done'
```

```Output
Caught: Bad
Done
```

Om ett fel inte är avslutat eller bara avslutar en pipeline, fortsätter pipelinen att uppfylla värdet för `$?` :

```powershell
function Test-NonTerminatingError
{
    [CmdletBinding()]
    param()

    $exception = [System.Exception]::new('BAD')
    $errorId = 'BAD'
    $errorCategory = 'NotSpecified'

    $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

    $PSCmdlet.WriteError($errorRecord)
}

Test-NonTerminatingError || Write-Output 'Second'
```

```Output
Test-NonTerminatingError: BAD
Second
```

### <a name="chaining-pipelines-rather-than-commands"></a>Länka pipeliner i stället för kommandon

Operatorer för pipeline-kedjan, efter namn, kan användas för att kedje pipelines, i stället för bara kommandon. Detta matchar beteendet för andra gränssnitt, men kan göra det *svårare att* fastställa:

```powershell
function Test-NotTwo
{
    [CmdletBinding()]
    param(
      [Parameter(ValueFromPipeline)]
      $Input
    )

    process
    {
        if ($Input -ne 2)
        {
            return $Input
        }

        $exception = [System.Exception]::new('Input is 2')
        $errorId = 'InputTwo'
        $errorCategory = 'InvalidData'

        $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

        $PSCmdlet.WriteError($errorRecord)
    }
}

1,2,3 | Test-NotTwo && Write-Output 'All done!'
```

```Output
1
Test-NotTwo : Input is 2
3
```

Observera att `Write-Output 'All done!'` inte körs eftersom det anses vara fel `Test-NotTwo` när du har genererat ett icke-avslutande fel.

## <a name="see-also"></a>Se även

- [about_Operators](about_Operators.md)
- [about_Automatic_Variables](about_Automatic_Variables.md)
- [about_pipelines](about_pipelines.md)

