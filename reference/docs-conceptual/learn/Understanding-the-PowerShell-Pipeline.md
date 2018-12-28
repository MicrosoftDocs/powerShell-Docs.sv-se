---
ms.date: 08/23/2018
keywords: PowerShell cmdlet
title: Förstå PowerShell-förlopp
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: fc7c7f57bdce458185a0f5bdb8bc1fbbd81d0d61
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404738"
---
# <a name="understanding-pipelines"></a>Förstå pipelines

Pipelines fungerar som en serie med anslutna pipe-segment. Artiklar som flyttas längsmed pipelinen släpper igenom varje segment. Om du vill skapa en pipeline i PowerShell som du ansluter kommandon tillsammans med operatorn ”|”. Utdata för varje kommando används som indata till nästa kommando.

Notation används för pipelines liknar beteckningen används i andra gränssnitt. Vid en första titt kanske det inte tydligt hur skiljer sig pipelines i PowerShell. Även om du ser text på skärmen, kommer objekt inte text mellan kommandon i PowerShell.

## <a name="the-powershell-pipeline"></a>PowerShell-pipelinen

Pipeliner är utan tvekan den mest värdefulla begrepp som används i kommandoradsverktyget gränssnitt. När detta används korrekt kan minska arbetet med att använda komplexa kommandon pipelines och gör det lättare att se arbetsflödet för kommandon. Varje kommando i en pipeline (kallas en pipeline-elementet) skickar sina utdata till nästa kommando i pipeline-post. Kommandon har inte kan hantera mer än ett objekt i taget. Resultatet är lägre resursförbrukning och möjligheten att börja hämta utdata direkt.

Exempel: Om du använder den `Out-Host` cmdlet för att framtvinga en sida för sida visning av utdata från ett annat kommando, de utdata ser ut precis som den normala texten som visas på skärmen som delats upp i sidor:

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

Växling också minskar CPU-belastningen eftersom bearbetning överförs till den `Out-Host` cmdlet när den har en hel sida som är redo att visa. De cmdletar som redan har infogats i pipelinen Pausa körning tills nästa sida i utdata är tillgänglig.

Du kan se skillnaden Windows Aktivitetshanteraren för att övervaka CPU och minne som används av PowerShell. Kör följande kommando: `Get-ChildItem C:\Windows -Recurse`. Jämför användningen av processor och minne det här kommandot: `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`.

## <a name="objects-in-the-pipeline"></a>Objekt i pipelinen

När du kör en cmdlet i PowerShell, se textutdata eftersom det är nödvändigt att representera objekt som text i ett konsolfönster. Text-utdata visas inte alla egenskaper i objektet som utdata.

Anta exempelvis att den `Get-Location` cmdlet. Om du kör `Get-Location` din aktuella plats är roten på C-enheten, finns i följande utdata:

```
PS> Get-Location

Path
----
C:\
```

Textutdata är en sammanfattning av informationen, inte en fullständig återgivning av objektet som returnerades av `Get-Location`. Rubriken i utdata har lagts till via processen som formaterar data för visning på skärmen.

När du skicka utdata till den `Get-Member` cmdlet du få information om objektet som returnerades av `Get-Location`.

```powershell
PS> Get-Location | Get-Member
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

`Get-Location` Returnerar en **PathInfo** objekt som innehåller den aktuella sökvägen och annan information.
