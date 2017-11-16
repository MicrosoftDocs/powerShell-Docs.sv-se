---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Med formatet kommandon för att ändra utdata vy"
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 0163fcb21d586fc98902d9bdcfab6fe4eb97c225
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="using-format-commands-to-change-output-view"></a>Med formatet kommandon för att ändra utdata vy
Windows PowerShell har en uppsättning cmdlets som låter dig styra vilka egenskaper som visas för vissa objekt. Namnen på cmdletarna som börjar med verbet **Format**. De kan du välja en eller flera egenskaper som ska visas.

Den **Format** cmdlets är **Format hela**, **Format-List**, **Format-Table**, och **Format-anpassad**. Vi kommer bara beskriver den **Format hela**, **Format-List**, och **Format-Table** cmdlets i den här handboken.

Varje format-cmdlet har standardegenskaper som ska användas om du inte anger specifika egenskaper som ska visas. Varje cmdlet använder även samma parameternamn, **egenskapen**, för att ange vilka egenskaper som du vill visa. Eftersom **Format hela** visar bara en enskild egenskap dess **egenskapen** parametern tar bara ett värde, men egenskapen parametrarna för **Format-List** och **Format-Table** tar emot en lista med egenskapsnamn.

Om du använder kommandot **Get-Process - namnet powershell** med två instanser av Windows PowerShell kör du hämta utdata som ser ut så här:

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

I resten av det här avsnittet förklarar vi hur du använder **Format** -cmdletar för att ändra hur utdata från kommandot visas.

### <a name="using-format-wide-for-single-item-output"></a>Med formatet hela för Single-utdata
Den **Format hela** cmdlet, visas som standard endast standardegenskapen för ett objekt. Information som associeras med varje objekt visas i en enda kolumn:

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

Du kan också ange en standardegenskap:

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a>Kontrollera formatet hela bildskärm med kolumnen
Med den **Format hela** cmdlet, du kan bara visa en enskild egenskap i taget. Detta gör att det är användbart om du vill visa enkla listor som visar endast ett element per rad. För att få en enkel lista, ange värdet för den **kolumnen** parameter 1 genom att skriva:

```
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a>Använda Format-List för en listvy
Den **Format-List** cmdlet visar ett objekt i form av en lista med varje egenskap med namnet och visas på en separat rad:

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

Du kan ange alla egenskaper som du vill:

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Hämta detaljerad Information genom att använda Format-List med jokertecken
Den **Format-List** cmdlet kan du använda ett jokertecken som värde för dess **egenskapen** parameter. På så sätt kan du visa detaljerad information. Ofta objekt kan vara mer än vad du behöver, vilket är anledningen till Windows PowerShell inte visar alla egenskapsvärden som standard. Använd för att visa alla egenskaper för ett objekt i **Format-List-egenskapen \&#42;** kommando. Följande kommando skapar över 60 raderna i utdata för en enda process:

```
Get-Process -Name powershell | Format-List -Property *
```

Även om den **Format-List** kommandot är användbara för att visa information om du vill att en översikt över utdata som innehåller många objekt, en enklare tabellvy är ofta mer användbar.

### <a name="using-format-table-for-tabular-output"></a>Med hjälp av Format-Table för Tabular utdata
Om du använder den **Format-Table** med ingen egenskapsnamn som angetts för att formatera utdata från den **Get-Process** kommandot, du får exakt samma utdata som du gör utan att utföra någon formatering. Anledningen är att processer visas vanligtvis i tabellformat, eftersom de flesta Windows PowerShell-objekt.

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a>Förbättra Format-Table utdata (AutoSize)
Även om en tabellvy är användbart om du vill visa en stor mängd jämförbar information, kan det vara svårt att tolka om visningen är för restriktiva för data. Till exempel om du försöker visa processen sökväg, ID, namn och företag kan hämta du trunkerat utdata för sökvägen till processen och kolumnen företag:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

Om du anger den **AutoSize** parameter när du kör den **Format-Table** kommandot Windows PowerShell beräknar kolumnbredder baserat på de data du vill visa. Detta gör det **sökväg** kolumnen läsbar, men kolumnen företag förblir trunkerat:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

Den **Format-Table** cmdlet kan fortfarande trunkera data, men det kommer bara göra det i slutet av skärmen. Andra egenskaper än den sista som visas, ges så mycket storlek som de behöver för sin längsta dataelementet ska visas korrekt. Du kan se att företagets namn är synligt men trunkeras sökvägen om du byter platserna för **sökväg** och **företagets** i den **egenskapen** värdelistan:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

Den **Format-Table** kommandot förutsätter att det kommer allt närmare en egenskap som är i början av egenskapslistan, desto mer viktigt det är. Så försöker visa egenskaper närmsta början helt. Om den **Format-Table** kommandot kan inte visas alla egenskaper som kan den ta bort vissa kolumner som visas och ange en varning. Du kan se det här beteendet om du gör **namn** senaste egenskap i listan:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

ID-kolumnen trunkeras så att den passar in i listan i resultatet ovan och kolumnrubrikerna staplade. Ändra storlek på kolumnerna automatiskt utför alltid inte vad du vill.

#### <a name="wrapping-format-table-output-in-columns-wrap"></a>Byta Format-Table utdata i kolumner (Radbryt)
Du kan tvinga långa **Format-Table** data att omsluta i kolumnen visa med hjälp av den **omsluter** parameter. Med hjälp av den **omsluter** parametern enbart inte nödvändigtvis att utföra vad du förväntar dig, eftersom den använder standardinställningarna om du inte också anger **AutoSize**:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

En fördel med den **omsluter** parametern ensamt är att den inte fördröjer bearbetning mycket. Om du gör en lista över rekursiv fil för ett stort directory-system, det kan ta mycket lång tid och använda mycket minne innan de första utdata-objekt om du använder **AutoSize**.

Om du inte tänker på systembelastning sedan **AutoSize** fungerar bra med den **omsluter** parameter. De första kolumnerna är alltid tilldelats så mycket bredd som de behöver för att visa objekt på en rad, precis som när du anger **AutoSize** utan den **omsluter** parameter. Den enda skillnaden är att den sista kolumnen kommer att omslutas om det behövs:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

Vissa kolumner kanske inte visas om du anger de bredaste kolumnerna först, så det är säkrast att ange de minsta dataelement först. I följande exempel tar vi ange mycket brett sökvägselement först och även med radbrytningar, vi fortfarande förlorar slutliga **namn** kolumn:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a>Ordna Tabellutdata (-GroupBy)
En annan användbar parametern för tabular utdata-kontroll är **GroupBy**. Längre tabular listor kan i synnerhet vara svåra att jämföra. Den **GroupBy** parametern grupper utdata baserat på ett värde för egenskapen. Vi kan till exempel gruppera processer av företag för enklare kontroll utelämna företagets värdet från egenskapen lista:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```

