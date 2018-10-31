---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxFile-resurs
ms.openlocfilehash: 80969ba2ea6247fcd616a301d951403a840c851d
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225717"
---
# <a name="dsc-for-linux-nxfile-resource"></a>DSC för Linux nxFile-resurs

Den **nxFile** resursen i PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera filer och kataloger på en Linux-nod.

## <a name="syntax"></a>Syntax

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Egenskaper

|  Egenskap |  Beskrivning |
|---|---|
| Målsökväg| Anger den plats där du vill kontrollera status för en fil eller katalog.|
| Källsökväg| Anger sökvägen som du vill kopiera filen eller mappen resursen från. Den här sökvägen kan vara en lokal sökväg eller en `http/https/ftp` URL: en. Remote `http/https/ftp` URL: er är bara när värdet för den **typ** egenskapen är filen.|
| Se till att| Anger om du vill kontrollera om filen finns. Ange egenskapen ”aktuella” för att se till att filen finns. Ange den till ”inte” för att se till att filen inte finns. Standardvärdet är ”tillgänglig”.|
| Typ| Anger om resursen som konfigureras är en katalog eller en fil. Ange egenskapen till ”directory” för att indikera att resursen är en katalog. Ange den till ”filen” för att indikera att resursen är en fil. Standardvärdet är ”fil”|
| Innehåll| Anger innehållet i en fil, till exempel en viss sträng.|
| Kontrollsumma| Definierar den typ som ska användas när du bestämmer om två filer är lika. Om **kontrollsumma** inte anges endast filen eller katalogen namnet används för jämförelse. Värden är: ”ctime”, ”mtime” eller ”md5”.|
| Recurse| Anger om underkataloger ingår. Den här egenskapen **$true** att indikera att du vill att underkataloger som ska tas med. Standardvärdet är **$false**. **Obs:** den här egenskapen är endast giltig när den **typ** är inställd på katalogen.|
| Force| Vissa åtgärder för sammansättningsfiler (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel. Med hjälp av den **kraft** egenskapen åsidosätter sådana fel. Standardvärdet är **$false**.|
| Länkar| Anger du önskat beteende för symboliska länkar. Ange den här egenskapen ”följer” för att följa symboliska länkar och agera på mål-länkar (till exempel. Kopiera filen i stället för länken). Ange den här egenskapen till ”hantera” för att agera på länken (till exempel. kopiera länken själva). Ange den här egenskapen till ”Ignorera” ignorerar symboliska länkar.|
| Grupp| Namnet på den **grupp** äga filen eller katalogen.|
| Läge| Anger de önskade behörigheterna för resursen i oktala eller symboliska notation. (till exempel 777 eller rwxrwxrwx). Om du använder symboliska notation, ingår det första tecknet som anger mapp eller fil.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Ytterligare information


Linux och Windows använder olika radbrytningstecken i textfiler som standard och detta kan orsaka oväntade resultat när du konfigurerar vissa filer på en Linux-dator med __nxFile__. Det finns flera sätt att hantera innehållet i en Linux-fil samtidigt som du undviker problem som orsakas av ett oväntat radbrytningstecken:

Steg 1: Kopiera filen från en fjärrkälla (http, https eller ftp): skapa en fil i Linux med önskade innehållet och mellanlagra dem på en webbplats eller FTP-server som är tillgängliga noder som du vill konfigurera. Definiera den __SourcePath__ -egenskapen i den __nxFile__ resurs med webb- eller ftp-URL till filen.

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"

}

}
```


Steg 2: Läsa filinnehållet i PowerShell-skript med [Get-innehåll](https://technet.microsoft.com/library/hh849787.aspx) när den __$OFS__ egenskapen att använda radbrytningstecken Linux.


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = "$Contents"
}

}
```


Steg 3: Använda en PowerShell-funktion för att ersätta Windows radbrytningar med Linux radbrytningstecken.

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = $Contents

}
}
```

## <a name="example"></a>Exempel

I följande exempel ser till att katalogen `/opt/mydir` finns, och att den här katalogen finns i en fil med innehåll har angetts.

```
Import-DSCResource -Module nx

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
}
}
```