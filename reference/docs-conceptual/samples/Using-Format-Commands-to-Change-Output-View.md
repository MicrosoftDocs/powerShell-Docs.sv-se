---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Använd formatkommandon för att ändra utdatavyn
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 35ccd2525d40ffd5e3f25a1abfa38904a109bde5
ms.sourcegitcommit: 396509cd0d415acc306b68758b6f833406e26bf5
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/21/2019
ms.locfileid: "58320429"
---
# <a name="using-format-commands-to-change-output-view"></a>Använd formatkommandon för att ändra utdatavyn

Windows PowerShell har en uppsättning cmdletar som gör det möjligt att styra vilka egenskaper som visas för vissa objekt. Namnen på alla cmdletar börjar med verbet **Format**. De kan du välja en eller flera egenskaper för att visa.

Den **Format** cmdlet: ar är **Format hela**, **Format-List**, **Format-Table**, och **Format-anpassad**. Vi kommer endast att beskriva den **Format hela**, **Format-List**, och **Format-Table** cmdletar i den här användarhandboken.

Varje format-cmdlet har standardegenskaper som ska användas om du inte anger specifika egenskaper som ska visas. Varje cmdlet använder även samma parameternamnet **egenskapen**, för att ange vilka egenskaper som du vill visa. Eftersom **Format hela** visar bara en enda egenskap, dess **egenskapen** parametern tar bara ett enda värde, men egenskapen parametrarna för **Format-List** och **Format-Table** accepterar en lista över egenskapsnamn.

Om du använder kommandot **Get-Process - namnet powershell** med två instanser av Windows PowerShell kör du får utdata som ser ut så här:

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

I resten av det här avsnittet förklarar vi hur du använder **Format** cmdletar för att ändra hur kommandots utdata visas.

### <a name="using-format-wide-for-single-item-output"></a>Med hjälp av Format hela för Single-Item utdata

Den **Format hela** cmdlet, som standard visas endast standardegenskapen för ett objekt. Informationen som är associerade med varje objekt visas i en enda kolumn:

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

Du kan också ange en icke-standard-egenskap:

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a>Kontrollera formatet företagsomfattande visning med kolumn

Med den `Format-Wide` cmdlet, du kan bara visa en enskild egenskap i taget.
Detta gör det användbart för att visa enkla listor som visar bara ett element per rad.
För att få en enkel lista kan du ange värdet för den **kolumnen** parameter 1 genom att skriva:

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 1
```

```output
Custom
Hex
List
Table
Wide
```

### <a name="using-format-list-for-a-list-view"></a>Med hjälp av Format-List för en listvy

Den **Format-List** cmdlet visar ett objekt i form av en lista med varje egenskap med etiketten och visas på en separat rad:

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

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Hämta detaljerad Information med hjälp av Format-List med jokertecken

Den **Format-List** cmdlet kan du använda ett jokertecken som värdet för dess **egenskapen** parametern. På så sätt kan du visa detaljerad information. Objekt omfattar ofta mer information än vad du behöver, vilket är anledningen till Windows PowerShell inte visar alla egenskapsvärden som standard. För att visa alla egenskaper för ett objekt, använda den **Format-List-egenskapen \&#42;** kommando. Följande kommando genererar över 60 rader med utdata för en enda process:

```powershell
Get-Process -Name powershell | Format-List -Property *
```

Även om den **Format-List** kommandot är användbart för att visa information om du vill att en översikt över utdata som innehåller många objekt, en enklare tabellvy är ofta mer användbart.

### <a name="using-format-table-for-tabular-output"></a>Med hjälp av Format-Table för Tabellutdata

Om du använder den **Format-Table** cmdlet med inga egenskapsnamn som angetts för att formatera utdata från den **Get-Process** kommandot får du exakt samma utdata som du gör utan att behöva genomföra några formatering. Anledningen är att processer vanligtvis visas i tabellformat, eftersom de flesta Windows PowerShell-objekt.

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a>Förbättra Format-Table utdata (AutoSize)

Även om en tabellvy är användbart för att visa mycket jämförbar information, kan det vara svårt att tolka om skärmen är för smal för data. Till exempel om du försöker visa processen sökväg, ID, namn och företag, får du trunkerade utdata för processökvägen och kolumnen företag:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

Om du anger den **AutoSize** parameter när du kör den **Format-Table** kommandot Windows PowerShell beräknas kolumnbredder baserat på de faktiska data som du kommer att visa. Detta gör det **sökväg** kolumnen läsbar, men kolumnen företag förblir trunkerat:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

Den **Format-Table** cmdlet kan fortfarande trunkera data, men det kommer bara göra det i slutet av skärmen. Andra egenskaper än den senaste som visas, ges så mycket storlek som de behöver för sin längsta dataelement kan inte visas korrekt. Du kan se att företagets namn är synligt men trunkeras sökvägen om du växlar mellan platserna för **sökväg** och **företagets** i den **egenskapen** värdelista:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

Den **Format-Table** kommandot förutsätter att det kommer allt närmare en egenskap som är i början av egenskapslistan ju viktigare det är. Så görs ett försök att visa egenskaperna för närmaste början helt. Om den **Format-Table** kommandot kan inte visas alla egenskaper kan det ta bort vissa kolumner som visningen och skicka någon varning. Du kan se det här beteendet om du gör **namn** egenskapen senaste i listan:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

ID-kolumnen förkortas så att den passar i listan i utdata ovan och kolumnrubrikerna staplade. Automatiskt ändra storlek på kolumnerna som gör inte alltid det du söker.

#### <a name="wrapping-format-table-output-in-columns-wrap"></a>Radbrytning Format-Table utdata i kolumnerna (radbyte)

Du kan tvinga långa **Format-Table** data du omsluter inom dess Visningskolumn med hjälp av den **omsluta** parametern. Med hjälp av den **omsluta** parametern enbart inte nödvändigtvis att utföra vad du förväntar dig, eftersom det använder standardinställningarna om du inte också anger **AutoSize**:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

En fördel med den **omsluta** parametern påverkar i sig är att det inte fördröjer bearbetar mycket. Om du gör en rekursiv fil lista över ett stort directory-system, det kan ta mycket lång tid och använder mycket minne innan den visas de första utdata-objekten om du använder **AutoSize**.

Om du inte är orolig över systembelastning har sedan **AutoSize** fungerar bra med de **omsluta** parametern. De inledande kolumnerna reduceras alltid så mycket bredd som de behöver för att visa objekten i en rad, precis som när du anger **AutoSize** utan den **omsluta** parametern. Den enda skillnaden är att den sista kolumnen hanteras om det behövs:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

Vissa kolumner kan inte visas om du anger de bredaste kolumnerna först, så är det säkrast att ange de minsta dataelementen först. I följande exempel vi ange mycket brett sökvägselementet först och även med radbrytning, vi fortfarande förlorar sista **namn** kolumn:

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

En annan användbar parametern för tabellutdata kontroll är **GroupBy**. Längre tabular listor kan i synnerhet vara svåra att jämföra. Den **GroupBy** parametern grupperar utdata baserat på ett egenskapsvärde. Vi kan exempelvis gruppera processer av företag för enklare kontroll, om du utesluter företagets värdet från egenskapen lista:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```