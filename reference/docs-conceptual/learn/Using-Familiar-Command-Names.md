---
ms.date: 08/27/2018
keywords: PowerShell, cmdlet
title: Använd bekanta kommandonamn
ms.openlocfilehash: 30b33bc8739975c1a40e51c04a3ee4e426c199e7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030891"
---
# <a name="using-familiar-command-names"></a>Använd bekanta kommandonamn

PowerShell stöder alias för att referera till kommandon med alternativa namn. Med aliasering kan användare i andra gränssnitt använda vanliga kommando namn som de redan känner till för liknande åtgärder i PowerShell.

Alias associerar ett nytt namn med ett annat kommando. PowerShell har till exempel en intern funktion med namnet `Clear-Host` som rensar utdatafönstret. Du kan ange antingen `cls` eller `clear` alias i en kommando tolk. PowerShell tolkar dessa alias och kör funktionen `Clear-Host`.

Den här funktionen hjälper användare att lära sig PowerShell. Först har de flesta **cmd. exe** -och UNIX-användare en stor repertoaren av kommandon som användarna redan känner till med namn. PowerShell-motsvarigheterna kanske inte genererar identiska resultat. Resultaten är dock tillräckligt nära att användarna kan arbeta utan att känna till PowerShell-kommando namnet. "Finger minne" är en annan stor källa för att lära sig ett nytt kommando gränssnitt. Om du har använt **cmd. exe** för år kan du ange `cls` kommandot för att rensa skärmen. Utan alias för `Clear-Host`får du ett fel meddelande och vet inte vad du ska göra för att rensa utdata.

I följande lista visas några av de vanliga **cmd. exe** -och UNIX-kommandon som du kan använda i PowerShell:

|||||
|-|-|-|-|
|lat|tillämpning|insättning|RM|
|cd|echo|flytta|rmdir|
|chdir|radera|POPD|Spar|
|Rensa|h|PS|sortera|
|CLS|Historik|PUSHD|tee|
|exemplar|döda|PWD|typ|
|Backsteg|LP|R|skriva|
|differensområden|LS|Outlook||

`Get-Alias`-cmdleten visar det verkliga namnet på det ursprungliga PowerShell-kommandot som är associerat med ett alias.

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a>Tolka Standardalias

De alias som vi beskrivit tidigare har utformats för namn-kompatibilitet med andra kommando gränssnitt.
De flesta alias som är inbyggda i PowerShell är utformade för det kortfattat. Kortare namn är enklare att skriva, men det är svårt att läsa om du inte vet vad de refererar till.

PowerShell-alias försöker kompromissa mellan klarhet och det kortfattat. PowerShell använder en standard uppsättning alias för vanliga Substantiv och verb.

Exempel förkortningar:

| Substantiv eller verb | Förkortning |
|--------------|--------------|
| Get          | g            |
| Ange          | s            |
| Artikel         | Jag            |
| Position     | L            |
| Kommando      | 210           |
| Alias        | Al           |

Dessa alias är begripliga när du känner till stenografiska namn.

| Cmdlet-namn    | Alias |
|----------------|-------|
| `Get-Item`     | eter    |
| `Set-Item`     | Si    |
| `Get-Location` | huvud    |
| `Set-Location` | SL    |
| `Get-Command`  | GCM   |
| `Get-Alias`    | gal   |

När du är bekant med PowerShell-alias är det enkelt att gissa att **sal** -aliaset refererar till `Set-Alias`.

## <a name="creating-new-aliases"></a>Skapa nya alias

Du kan skapa egna alias med hjälp av `Set-Alias`-cmdleten. Följande uttryck skapar till exempel standard-cmdlet-alias som tidigare diskuterats:

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Internt använder PowerShell liknande kommandon vid start, men dessa alias kan inte ändras.
Om du försöker köra ett av dessa kommandon får du ett fel som förklarar att aliaset inte kan ändras. Till exempel:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
