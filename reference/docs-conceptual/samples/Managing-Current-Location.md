---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Hantera aktuell plats
ms.openlocfilehash: 42ab56759dec882d140f813c8614e578957722b3
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030198"
---
# <a name="managing-current-location"></a>Hantera aktuell plats

När du navigerar i mappfönster i Utforskaren har du vanligt vis en speciell arbets plats, nämligen den aktuella öppna mappen. Objekt i den aktuella mappen kan ändras enkelt genom att du klickar på dem. För kommando rads gränssnitt som cmd. exe, när du befinner dig i samma mapp som en viss fil, kan du komma åt den genom att ange ett relativt kort namn, i stället för att behöva ange hela sökvägen till filen. Den aktuella katalogen kallas arbets katalog.

Windows PowerShell använder **platsen** Substantiv för att referera till arbets katalogen och implementerar en serie cmdlets för att granska och ändra din plats.

## <a name="getting-your-current-location-get-location"></a>Hämta din aktuella plats (Get-location)

För att fastställa sökvägen till din nuvarande katalog plats, ange kommandot **Get-location** :

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Cmdleten Get-location liknar kommandot **PWD** i bash-gränssnittet. Cmdleten Set-location liknar **CD-** kommandot i cmd. exe.

## <a name="setting-your-current-location-set-location"></a>Ange din aktuella plats (Ange plats)

Kommandot **Get-location** används med kommandot **set-location** . Med kommandot **set-location** kan du ange din nuvarande katalog plats.

```powershell
Set-Location -Path C:\Windows
```

När du har angett kommandot ser du att du inte får någon direkt feedback om kommandots effekter. De flesta Windows PowerShell-kommandon som utför en åtgärd ger lite eller inga utdata eftersom utdata inte alltid är användbara. För att kontrol lera att en lyckad katalog ändring har inträffat när du anger kommandot **set-location** , inkluderar du parametern **-Passthru** när du anger kommandot **set-location** :

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

Parametern **-Passthru** kan användas med många Set-kommandon i Windows PowerShell för att returnera information om resultatet i fall där det inte finns några standardutdata.

Du kan ange sökvägar i förhållande till din aktuella plats på samma sätt som i de flesta UNIX-och Windows-kommandofiler. I standard notation för relativa sökvägar, en punkt (**.**) representerar den aktuella mappen och en dubbel period (**..**) representerar den överordnade katalogen för din aktuella plats.

Om du till exempel är i mappen **C:\\Windows** , en punkt (**.**) representerar **c:\\Windows** -och dubbla punkter (**..**) representerar **c:**. Du kan ändra från din aktuella plats till roten på enhet C: genom att skriva:

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

Samma teknik fungerar på Windows PowerShell-enheter som inte är fil system enheter, till exempel **HKLM:**. Du kan ange din plats till HKLM\\-program nyckeln i registret genom att skriva:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

Du kan sedan ändra katalog platsen till den överordnade katalogen, som är roten för Windows PowerShell HKLM: Drive, genom att använda en relativ sökväg:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

Du kan skriva set-location eller använda något av de inbyggda Windows PowerShell-aliasen för set-Location (CD, chdir, SL). Ett exempel:

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>Spara och återkalla de senaste platserna (push-location och pop-location)

När du ändrar platser är det bra att hålla reda på var du har varit och att du kan återgå till din tidigare plats. Cmdleten **push-location** i Windows PowerShell skapar en ordnad historik (en "stack") för katalog Sök vägar där du har varit, och du kan gå tillbaka genom historiken för katalog Sök vägar med hjälp av den kompletterande cmdleten för **popup-platsen** .

Windows PowerShell startar till exempel normalt i användarens Hem Katalog.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Word- *stacken* har en särskild betydelse i många programmerings inställningar, inklusive .NET Framework. Precis som en fysisk stack med objekt, är det sista objektet som du har placerat i stacken det första objektet som du kan dra av stacken. Att lägga till ett objekt i en stack är colloquially kallat "pusha" objektet till stacken. Att hämta ett objekt från stacken är colloquially känt som "underordnad" objektet från stacken.

Om du vill skicka den aktuella platsen till stacken och sedan gå till mappen Lokala inställningar skriver du:

```powershell
Push-Location -Path "Local Settings"
```

Du kan sedan skicka den lokala inställnings platsen till stacken och flytta den till Temp-mappen genom att skriva:

```powershell
Push-Location -Path Temp
```

Du kan kontrol lera att du har ändrat kataloger genom att ange kommandot **Get-location** :

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

Du kan sedan gå tillbaka till den senast besökta katalogen genom att ange kommandot **pop-location** och kontrol lera ändringen genom att ange kommandot **Get-location** :

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Precis som med cmdleten **set-location** kan du inkludera parametern **-Passthru** när du anger cmdleten för **popup-platsen** för att visa den katalog som du har angett:

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

Du kan också använda plats-cmdlet: ar med nätverks Sök vägar. Om du har en server med namnet FS01 med en resurs som heter offentlig kan du ändra din plats genom att skriva

```powershell
Set-Location \\FS01\Public
```

eller

```powershell
Push-Location \\FS01\Public
```

Du kan använda kommandona **push-location** och **set-location** för att ändra platsen till en tillgänglig enhet. Om du till exempel har en lokal CD-ROM-enhet med enhets beteckningen D som innehåller en data-CD kan du ändra platsen till CD-enheten genom att ange kommandot **set-location D:** .

Om enheten är tom visas följande fel meddelande:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

När du använder ett kommando rads gränssnitt är det inte lämpligt att använda Utforskaren för att undersöka tillgängliga fysiska enheter. Dessutom visar Utforskaren inte alla Windows PowerShell-enheter. Windows PowerShell innehåller en uppsättning kommandon för att ändra Windows PowerShell-enheter och vi pratar om dessa härnäst.
