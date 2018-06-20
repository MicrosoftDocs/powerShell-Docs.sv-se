---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Förstå PowerShell-pipelinen
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: c3f1d17432cf3a77c0f5ecae137a4233a28a19d7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951077"
---
# <a name="understanding-the-windows-powershell-pipeline"></a>Förstå PowerShell-pipelinen
Rörnät fungerar praktiskt taget överallt i Windows PowerShell. Även om du ser texten på skärmen, Windows PowerShell inte att skicka text mellan kommandon. Den kommer i stället objekt.

Det format som används för pipelines är liknande som används i andra så vid en första titt, kanske inte tydligt att Windows PowerShell innehåller något nytt. Till exempel om du använder den **ut värd** att framtvinga en varje sida visning av utdata från ett annat kommando, utdata söker precis som den normala texten som visas på skärmen, uppdelade sidor:

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

Out-Host-sidindelning kommandot är en användbar pipeline-elementet när du har långa utdata som du vill visa långsamt. Det är särskilt användbart om åtgärden är mycket processorintensiva. Eftersom bearbetning överförs till den inkommande värd cmdlet när den har en hel sida som är redo att visa cmdlets som föregår i pipelinen stoppa åtgärden tills nästa sida i utdata är tillgänglig. Du kan se dessa om du använder Aktivitetshanteraren för att övervaka CPU och minne används av Windows PowerShell.

Kör följande kommando: **Get-ChildItem C:\\Windows-Recurse**. Jämför processor- och minnesanvändning för det här kommandot: **Get-ChildItem C:\\Windows-Recurse | Routningsserver Host-växling**. Vad som visas på skärmen är text, men det beror på att det är nödvändigt för att representera objekt som text i konsolfönstret. Detta är bara en representation av vad är verkligen pågår i Windows PowerShell. Anta till exempel att cmdleten Get-plats. Om du anger **Get-plats** din aktuella plats är roten på enhet C, visas följande utdata:

```
PS> Get-Location

Path
----
C:\
```

Om Windows PowerShell pipeline text, utfärda ett kommando som **Get-plats | Värd för inkommande**, skulle skickas från **Get-plats** till **ut värd** en uppsättning tecken i den ordning de visas på skärmen. Med andra ord, om du ignorerar rubrikinformationen, **ut värd** kommer först att ta emot tecknet '**C'**, sedan tecknet '**:'**, sedan tecknet ' **\\'**. Den **ut värd** cmdlet kunde inte avgöra vilka vilket innebär att associera med tecken resultatet av den **Get-plats** cmdlet.

I stället för text för att kommandon i en pipeline kommunicera Windows PowerShell använder objekt. När gäller för en användare objekt paketet relaterad information i ett formulär som gör det enklare att manipulera informationen som en enhet och extrahera specifika objekt som du behöver.

Den **Get-plats** inte returnerar text som innehåller den aktuella sökvägen. Den returnerar ett paket med information som kallas en **PathInfo** objekt som innehåller den aktuella sökvägen tillsammans med annan information. Den **ut värd** cmdlet skickar sedan detta **PathInfo** objekt till skärmen och Windows PowerShell bestämmer vad information som ska visas och hur det ska visas baserat på dess formateringsregler.

I själva verket rubrikinformationen utdata genom att den **Get-plats** cmdlet läggs endast i slutet av processen, som en del av processen för att formatera data för visning på skärmen. Vad som visas på skärmen är en sammanfattning av information och inte en fullständig representation av utdata-objektet.

Med hänsyn till att det kan finnas mer information utdata från en Windows PowerShell kommando än vad vi se visas i konsolfönstret, hur kan du hämta icke-synliga element? Hur visar du extra data? Och om du vill visa data i ett format som skiljer sig en Windows PowerShell normalt använder?

Resten av det här kapitlet beskrivs hur du kan identifiera strukturen för specifika objekt i Windows PowerShell, välja specifika objekt och formatera dem för enklare visning och hur du skickar informationen till alternativa utdatafilerna som filer och skrivare.