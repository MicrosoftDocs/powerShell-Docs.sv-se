---
ms.date: 08/27/2018
keywords: PowerShell cmdlet
title: Använd bekanta kommandonamn
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: b61d647d882d4b2f7ea423a48319e3c104ce96c7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058003"
---
# <a name="using-familiar-command-names"></a>Använd bekanta kommandonamn

PowerShell stöder alias att referera till kommandon med alternativa namn. Alias kan användare med upplevelsen i andra gränssnitt för att använda vanliga kommandonamn som de redan känner för liknande åtgärder i PowerShell.

Alias associerar ett nytt namn med ett annat kommando. Till exempel PowerShell har en intern funktion med namnet `Clear-Host` som rensar utdatafönstret. Du kan ange antingen den `cls` eller `clear` alias i Kommandotolken. PowerShell tolkar dessa alias och kör den `Clear-Host` funktion.

Den här funktionen hjälper användare att lära dig PowerShell. Första, de flesta **cmd.exe** och Unix-användare har en stor kan representeras av kommandon som användarna redan känner till namnet. PowerShell-motsvarigheter kanske inte ger samma resultat. Resultatet är dock Stäng tillräckligt som användare kan fungerar utan att känna till namnet för PowerShell-kommando. ”Finger minne” är en annan större orsaken frustrationen när learning en ny kommandotolk. Om du har använt **cmd.exe** i flera år, kan du reflexively skriver den `cls` kommando för att rensa skärmen. Utan alias för `Clear-Host`, du får ett felmeddelande och inte vet vad du gör för att ta bort utdata.

I följande lista visas några vanliga **cmd.exe** och Unix-kommandon som du kan använda i PowerShell:

|||||
|-|-|-|-|
|cat|dir|Montera|rm|
|cd|echo|Flytta|rmdir|
|chdir|Radera|popd|Strömsparläge|
|Rensa|h|ps|Sortera|
|CLS|Historik|pushd|Tee|
|Kopiera|Avsluta|pwd|typ|
|del|LP|R|Skriva|
|diff|ls|ren||

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

Alias vi beskrivits utformades för namn-kompatibilitet med andra kommandogränssnitt.
De flesta alias som är inbyggda i PowerShell är utformade för kortfattat. Kortare namn är lättare att typ, men är svåra att läsa om du inte vet vad de refererar till.

PowerShell-alias försöker angripa mellan tydlighet och kortfattat. PowerShell använder en standarduppsättning med alias för vanliga substantiv och verb.

Exempel förkortningar:

| Substantiv eller Verb | Förkortning |
|--------------|--------------|
| Get          | g            |
| Ange          | S            |
| Artikel         | Jag            |
| Position     | L            |
| Kommando      | cm           |
| Alias        | AL           |

Dessa alias är att förstå när du vet vilka snabbformat.

| Cmdlet-namn    | Alias |
|----------------|-------|
| `Get-Item`     | gi    |
| `Set-Item`     | si    |
| `Get-Location` | gl    |
| `Set-Location` | sl    |
| `Get-Command`  | gcm   |
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
