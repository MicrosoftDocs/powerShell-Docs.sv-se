---
ms.date: 08/23/2018
keywords: PowerShell, cmdlet
title: Förstå PowerShell-pipeliner
ms.openlocfilehash: 3033a4fe1a704fbbfa76e6d38662c8b22c3dbd9b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030388"
---
# <a name="understanding-pipelines"></a>Förstå pipelines

Pipelines fungerar som en serie anslutna segment av en pipe. Objekt som flyttas utmed pipelinen passerar varje segment. Om du vill skapa en pipeline i PowerShell ansluter du kommandon tillsammans med pipe-operatorn "|". Utdata från varje kommando används som indata till nästa kommando.

Den notation som används för pipelines liknar den notation som används i andra gränssnitt. I första hand kan det vara inte uppenbart hur pipelines skiljer sig i PowerShell. Även om du ser text på skärmen, PowerShell pipe-objekt, inte text, mellan kommandon.

## <a name="the-powershell-pipeline"></a>PowerShell-pipeline

Pipelines är utan tvekan det mest värdefulla konceptet som används i kommando rads gränssnitt. När pipelinen används korrekt minskar pipelinen arbetet med att använda komplexa kommandon och gör det lättare att se arbets flödet för kommandona. Varje kommando i en pipeline (kallas ett pipeline-element) skickar utdata till nästa-kommando i pipelinen, item-by-Item. Kommandon behöver inte hantera mer än ett objekt i taget. Resultatet är minskad resursförbrukning och möjligheten att börja få utdata direkt.

Om du till exempel använder `Out-Host` cmdleten för att tvinga fram visning av utdata från ett annat kommando, ser utdata ut precis som den normala texten som visas på skärmen, och delas upp i sidor:

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

Växlingen minskar också processor användningen eftersom bearbetningen överförs till `Out-Host` cmdleten när en hel sida är klar att visas. Cmdletarna som föregår den i pipelinen pausar körningen tills nästa sida med utdata är tillgänglig.

Du kan se hur rörledning påverkar processor-och minnes användning i aktivitets hanteraren genom att jämföra följande kommandon:

- `Get-ChildItem C:\Windows -Recurse`
- `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`

> [!NOTE]
> **Växlings** parametern stöds inte av alla PowerShell-värdar. När du till exempel försöker använda **växlings** parametern i PowerShell ISE visas följande fel:
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a>Objekt i pipelinen

När du kör en cmdlet i PowerShell visas text utdata eftersom det är nödvändigt att representera objekt som text i ett konsol fönster. Text utmatningen kanske inte visar alla egenskaper för objektet som ska skrivas ut.

Överväg till exempel `Get-Location` cmdleten. Om du kör `Get-Location` medan din aktuella plats är roten på C-enheten visas följande utdata:

```
PS> Get-Location

Path
----
C:\
```

Text utmatningen är en sammanfattning av informationen, inte en fullständig representation av det objekt som `Get-Location`returnerades av. Rubriken i utdata läggs till av processen som formaterar data för skärm visning.

När du skickar utdata till `Get-Member` cmdleten får du information om det objekt som returnerades `Get-Location`av.

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location`Returnerar ett **PathInfo** -objekt som innehåller den aktuella sökvägen och annan information.
