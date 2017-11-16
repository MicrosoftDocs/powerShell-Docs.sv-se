---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Hantera aktuella plats
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: cbdebb84b3191e3bd549a1cf344cbeefaa91a23c
ms.sourcegitcommit: c5251755c4442487f99ff74fadf7e37bbf039089
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/18/2017
---
# <a name="managing-current-location"></a>Hantera aktuella plats
När du navigerar i mappen System i Utforskaren, har vanligtvis en specifik plats i fungerande - nämligen den aktuella öppna mappen. Objekt i den aktuella mappen kan ändras genom att klicka på dem enkelt. För kommandoradsverktyget gränssnitt, till exempel Cmd.exe, när du är i samma mapp som en viss fil, kan du öppna den genom att ange ett relativt kort namn i stället för att behöva ange hela sökvägen till filen. Den aktuella katalogen kallas arbetskatalogen.

Windows PowerShell använder substantivet **plats** att referera till arbetskatalogen, och implementerar en familj av cmdletar för att granska och ändra din plats.

### <a name="getting-your-current-location-get-location"></a>Hämta din aktuella plats (Get-plats)
För att fastställa sökvägen för din aktuella katalogplats, ange den **Get-plats** kommando:

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Get-plats-cmdlet liknar den **pwd** i BASH-gränssnitt. Cmdlet Set-Location liknar den **cd** i Cmd.exe.

### <a name="setting-your-current-location-set-location"></a>Ange din aktuella plats (Set-plats)
Den **Get-plats** kommandot används med den **Set-Location** kommando. Den **Set-Location** kommandot kan du ange den aktuella directory-platsen.

```
PS> Set-Location -Path C:\Windows
```

När du har angett kommandot ser du att du inte har fått någon direkt feedback om effekten av kommandot. De flesta Windows PowerShell-kommandon som utför en åtgärd resultat lite eller ingen eftersom utdata inte är alltid praktiskt. Att verifiera att en lyckad katalogändring uppstod när du anger den **Set-Location** kommandot, innehåller den **- PassThru** parameter när du anger den **Set-Location**kommando:

```
PS> Set-Location -Path C:\Windows -PassThru
Path
----
C:\WINDOWS
```

Den **- PassThru** parameter som kan användas med många uppsättning kommandon i Windows PowerShell för att returnera information om resultatet i fall där det finns inga standardutdata.

Du kan ange sökvägar i förhållande till din aktuella plats på samma sätt som du skulle i de flesta UNIX- och Windows kommandot gränssnitt. I standard notation för relativa sökvägar, en period (**.**) representerar den aktuella mappen och en dubbelt period (**...** ) representerar den överordnade katalogen i din aktuella plats.

Om du befinner dig i till exempel den **C:\\Windows** mapp, en period (**.**) representerar **C:\\Windows** och punkter (**...** ) representerar **C:**. Du kan ändra från den aktuella platsen till roten på enhet C: genom att skriva:

```powershell
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

Samma teknik som fungerar på Windows PowerShell-enheter som inte enheter, exempelvis **HKLM:**. Du kan ange plats och HKLM\\programvarunyckel i registret genom att skriva:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

Du kan sedan ändra katalogen till den överordnade katalogen som är roten till Windows PowerShell HKLM:-enheten med hjälp av en relativ sökväg:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

Du kan skriva Set-Location eller använda någon av de inbyggda Windows PowerShell-alias för Set-Location (cd, chdir, sl). Till exempel:

```
cd -Path C:\Windows
```

```
chdir -Path .. -PassThru
```

```
sl -Path HKLM:\SOFTWARE -PassThru
```

### <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>Spara och återkalla senaste platser (Push- och Pop-plats)
När du ändrar platser, är det bra att hålla reda på var du har varit och för att kunna återgå till föregående plats. Den **Push-plats** cmdlet i Windows PowerShell skapar en ordnad historik (en ”stack”) för katalogsökvägar där du har, och du kan gå tillbaka historiken för directory-sökvägar med hjälp av den kompletterande  **POP-plats** cmdlet.

Till exempel startas Windows PowerShell normalt i användarens hemkatalog.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Ordet *stack* har en särskild innebörd i många programmeringsspråk inställningar, inklusive .NET Framework. Det sista objektet som du lägger till stacken är det första objektet som du kan inaktivera stacken som en fysisk stack objekt. Lägga till ett objekt i en stack kallas colloquially ”push-installation” objektet till stacken. Dra ett objekt från bufferten kallas colloquially ”poppar” objektet från stacken.

För att push-den aktuella platsen till stacken och gå sedan till mappen lokala inställningar, skriver du:

```
PS> Push-Location -Path "Local Settings"
```

Du kan sedan push lokala inställningar plats i bufferten och och gå till Temp-mappen genom att skriva:

```
PS> Push-Location -Path Temp
```

Du kan kontrollera att du har ändrat kataloger genom att ange den **Get-plats** kommando:

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

Du kan sedan öppna tillbaka till den senast besökta katalogen genom att ange den **Pop plats** och kontrollera ändringen genom att ange den **Get-plats** kommando:

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Precis som med den **Set-Location** cmdlet, som du kan inkludera den **- PassThru** parameter när du anger den **Pop plats** för att visa den katalog som du angav:

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

Du kan också använda cmdlet: ar för plats med nätverkssökvägar. Om du har en server med namnet FS01 med en resurs med namnet Public, kan du ändra din plats genom att skriva

```
Set-Location \\FS01\Public
```

eller

```
Push-Location \\FS01\Public
```

Du kan använda den **Push-plats** och **Set-Location** kommandon för att ändra platsen till en tillgänglig enhet. Till exempel om du har en lokal CD-ROM-enhet med enhetsbeteckningen D som innehåller en CD, du kan ändra platsen från CD-enheten genom att ange den **Set-Location D:** kommando.

Om enheten är tom, får du följande felmeddelande:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

När du använder ett kommandoradsgränssnitt, är det inte praktiskt att använda Utforskaren för att undersöka tillgängliga fysiska enheter. Dessutom innehåller Utforskaren inte alla enheter som Windows PowerShell. Windows PowerShell innehåller en uppsättning kommandon för att hantera enheter med Windows PowerShell och vi pratar om dessa nästa.

