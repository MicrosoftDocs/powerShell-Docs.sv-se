---
ms.date: 08/27/2018
keywords: PowerShell cmdlet
title: Använd bekanta kommandonamn
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: 08402aa5b959711c150fff89aa6747b6b43f8aa8
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134091"
---
# <a name="using-familiar-command-names"></a>Använd bekanta kommandonamn

PowerShell stöder alias att referera till kommandon med alternativa namn. Alias kan användare med upplevelsen i andra gränssnitt för att använda vanliga kommandonamn som de redan känner för liknande åtgärder i PowerShell.

Alias associerar ett nytt namn med ett annat kommando. Till exempel PowerShell har en intern funktion med namnet `Clear-Host` som rensar utdatafönstret. Du kan ange antingen den `cls` eller `clear` alias i Kommandotolken. PowerShell tolkar dessa alias och kör den `Clear-Host` funktion.

Den här funktionen hjälper användare att lära dig PowerShell. Första, de flesta Cmd.exe- och Unix-användare har en stor kan representeras av kommandon som användarna redan känner till namnet. PowerShell-motsvarigheter kanske inte ger samma resultat. Resultatet är dock Stäng tillräckligt som användare kan fungerar utan att känna till namnet för PowerShell-kommando. ”Finger minne” är en annan större orsaken frustrationen när learning en ny kommandotolk. Om du har använt Cmd.exe i flera år, du kan skriva reflexively den `cls` kommando för att rensa skärmen. Utan alias för `Clear-Host`, du får ett felmeddelande och inte vet vad du gör för att ta bort utdata.

I följande lista visas några vanliga kommandon som Cmd.exe och Unix som du kan använda i PowerShell:

|||||
|-|-|-|-|
|cat|dir|Montera|RM|
|CD|echo|Flytta|rmdir|
|chdir|Radera|popd|strömsparläge|
|Rensa|H|PS|Sortera|
|CLS|Historik|pushd|Tee|
|Kopiera|Avsluta|pwd|typ|
|del|LP|r|skriva|
|diff|Ls|ren||

Den `Get-Alias` cmdlet visar det verkliga namnet på den interna PowerShell-kommando som är associerade med ett alias.

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a>Tolka standard alias

Alias vi beskrivs tidigare utformades för namn-kompatibilitet med andra kommandogränssnitt.
De flesta alias som är inbyggda i PowerShell är utformade för kortfattat. Kortare namn är lättare att typ, men är svåra att läsa om du inte vet vad de refererar till.

PowerShell-alias försöker angripa mellan tydlighet och kortfattat. PowerShell använder en standarduppsättning med alias för vanliga substantiv och verb.

Exempel förkortningar:

| Substantiv eller Verb | Förkortning |
|--------------|--------------|
| Get          | G            |
| Ange          | S            |
| Objekt         | Jag            |
| Position     | L            |
| Kommando      | cm           |
| Alias        | AL           |

Dessa alias är att förstå när du vet vilka snabbformat.

| Cmdlet-namn    | Alias |
|----------------|-------|
| `Get-Item `    | GI    |
| `Set-Item`     | Si    |
| `Get-Location` | GL    |
| `Set-Location` | Sl    |
| `Get-Command`  | GCM   |
| `Get-Alias`    | GAL   |

När du är bekant med PowerShell-alias är det enkelt att gissa som den **sal** alias refererar till `Set-Alias`.

## <a name="creating-new-aliases"></a>Skapa nytt alias

Du kan skapa egna alias med hjälp av den `Set-Alias` cmdlet. Till exempel skapa följande instruktioner standard cmdlet-alias som beskrivits tidigare:

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Internt PowerShell använder liknande kommandon under starten, men dessa alias är inte kan ändras.
Om du försöker köra något av följande kommandon, får du ett felmeddelande om att aliaset som inte kan ändras. Till exempel:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```