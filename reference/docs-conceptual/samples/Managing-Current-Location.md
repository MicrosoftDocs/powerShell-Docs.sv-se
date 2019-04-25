---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Hantera aktuell plats
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: f5e0653b2c3bbc9d2526c7a1c2ff88a8a6641695
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086263"
---
# <a name="managing-current-location"></a>Hantera aktuell plats

När du navigerar i mappen System i Utforskaren, har du vanligtvis en specifik plats i fungerande - handlar bl.a, den aktuella öppna mappen. Objekt i den aktuella mappen kan ändras genom att klicka på dem enkelt. För kommandoradsverktyget gränssnitt, till exempel Cmd.exe, när du är i samma mapp som en viss fil, du kan komma åt den genom att ange ett relativt kort namn i stället för att behöva ange hela sökvägen till filen. Den aktuella katalogen kallas arbetskatalogen.

Windows PowerShell använder substantivet **plats** att referera till arbetskatalogen och och implementerar en familj av cmdletar för att granska och ändra din plats.

## <a name="getting-your-current-location-get-location"></a>Hämta din aktuella plats (Get-plats)

För att fastställa sökvägen till din aktuella katalogplats, ange den **Get-Location** kommando:

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Cmdleten Get-Location liknar den **pwd** i BASH-gränssnittet. Cmdleten Set-Location liknar den **cd** i Cmd.exe.

## <a name="setting-your-current-location-set-location"></a>Ange din aktuella plats (Set-plats)

Den **Get-Location** används med den **Set-Location** kommando. Den **Set-Location** kommandot kan du ange den aktuella katalogplatsen.

```powershell
Set-Location -Path C:\Windows
```

När du har angett kommandot ser du att du inte får någon direkt feedback om effekten av kommandot. De flesta Windows PowerShell-kommandon som utför en åtgärd att generera lite eller ingen utdata eftersom utdata inte är alltid praktiskt. Att verifiera att en lyckad katalogändring har inträffat när du anger den **Set-Location** kommandot, innehåller den **- PassThru** parameter när du anger den **Set-Location**kommando:

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

Den **- PassThru** parametern kan användas med många Set-kommandon i Windows PowerShell för att returnera information om resultatet i fall där det finns inga standardutdata.

Du kan ange sökvägar i förhållande till din aktuella plats på samma sätt som du skulle i de flesta UNIX- och Windows kommandot gränssnitt. I standard-notation för relativa sökvägar, en period (**.**) representerar din aktuella mapp och ett dubbelt period (**...** ) representerar den överordnade katalogen i din aktuella plats.

Exempel: Om du är i den **C:\\Windows** mapp, en period (**.**) representerar **C:\\Windows** och dubbel perioder (**...** ) representerar **C:**. Du kan ändra från din aktuella plats i roten på C:-enheten genom att skriva:

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

Samma teknik som fungerar på Windows PowerShell-enheter som inte är enheter, till exempel **HKLM:**. Du kan ange din plats och HKLM\\programvarunyckel i registret genom att skriva:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

Du kan sedan ändra katalogen till den överordnade katalogen som är roten av Windows PowerShell HKLM:-enheten genom att använda en relativ sökväg:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

Du kan ange Set-plats eller använda någon av de inbyggda Windows PowerShell-alias för Set-plats (cd, chdir, sl). Till exempel:

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>Spara och återkalla nyligen använda platser (Push- och Pop-plats)

När du ändrar platser, är det bra att hålla reda på var du har varit och för att kunna gå tillbaka till föregående plats. Den **Push-Location** cmdlet i Windows PowerShell skapar en ordnad historik (”stackar”) för katalogsökvägar där du har, och du kan gå tillbaka genom historiken för katalogsökvägar med hjälp av den kompletterande  **POP-platsen** cmdlet.

Till exempel startas Windows PowerShell normalt i användarens arbetskatalog.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Ordet *stack* har en särskild betydelse i många programmeringsspråk inställningar, inklusive .NET Framework. Precis som en fysisk stack med objekt är det sista objektet som du lägger till stacken det första objektet som du kan hämta från bufferten. Att lägga till ett objekt i en stack kallas colloquially ”Skicka” objektet till stacken. Hämta ett objekt från bufferten kallas colloquially ”händelser” objekt från bufferten.

Om du vill skicka den aktuella platsen till stacken och sedan flytta till mappen lokala inställningar, skriver du:

```powershell
Push-Location -Path "Local Settings"
```

Du kan push-inställningar för lokal plats till stacken och flytta till Temp-mappen genom att skriva:

```powershell
Push-Location -Path Temp
```

Du kan kontrollera att du har ändrat kataloger genom att ange den **Get-Location** kommando:

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

Du kan sedan öppna tillbaka till den senast använda katalogen genom att ange den **Pop-platsen** , och bekräfta ändringen genom att ange den **Get-Location** kommando:

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Precis som den **Set-Location** cmdlet, som du kan inkludera den **- PassThru** parameter när du anger den **Pop-platsen** cmdleten för att visa den katalog som du angav:

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

Du kan också använda cmdletarna plats med nätverksvägar. Om du har en server med namnet FS01 med en filresurs som heter offentlig, kan du ändra din plats genom att skriva

```powershell
Set-Location \\FS01\Public
```

eller

```powershell
Push-Location \\FS01\Public
```

Du kan använda den **Push-Location** och **Set-Location** kommandon för att ändra platsen till alla tillgängliga enhet. Till exempel om du har en lokal CD-ROM-enhet med enhetsbeteckningen D som innehåller en data-CD, du kan ändra platsen från CD-enheten genom att ange den **Set-Location D:** kommando.

Om enheten är tom, får du följande felmeddelande visas:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

När du använder ett kommandoradsgränssnitt, är det inte praktiskt att använda Utforskaren för att undersöka de fysiska enheterna. Dessutom innehåller Utforskaren inte alla enheter som Windows PowerShell. Windows PowerShell tillhandahåller en uppsättning kommandon för att hantera enheter med Windows PowerShell och vi ska prata om dessa nästa.
