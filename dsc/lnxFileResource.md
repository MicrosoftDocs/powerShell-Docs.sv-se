---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "DSC för Linux nxFile resurs"
ms.openlocfilehash: 7ee8a37ee63a70b1c8c69dc79dfbc77c1f583234
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-for-linux-nxfile-resource"></a>DSC för Linux nxFile resurs

Den **nxFile** resurs i PowerShell önskad tillstånd Configuration (DSC) ger möjlighet till att hantera filer och kataloger på en Linux-nod.

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
| Målsökväg| Anger den plats där du vill kontrollera tillståndet för en fil eller katalog.| 
| Källsökväg| Anger sökvägen som du vill kopiera filen eller mappen resurs. Den här sökvägen kan vara en lokal sökväg eller en `http/https/ftp` URL. Remote `http/https/ftp` URL: er är endast när värdet för den **typen** egenskapen är filen.| 
| Se till att| Anger om du vill kontrollera om filen finns. Ange egenskapen ”aktuella” för att se till att filen finns. Ange den till ”saknas” för att se till att filen inte finns. Standardvärdet är ”saknas”.| 
| Typ| Anger om resursen som konfigureras är en katalog eller fil. Ange den här egenskapen till ”directory” för att indikera att resursen är en katalog. Ange att ”fil” för att indikera att resursen är en fil. Standardvärdet är ”fil”| 
| Innehåll| Anger innehållet i en fil, till exempel en viss sträng.| 
| Kontrollsumma| Definierar den typ som används när du fastställer om två filerna är samma. Om **kontrollsumma** anges endast filen eller katalogen namn som används för jämförelse. Värden är: ”ctime”, ”mtime” eller ”md5”.| 
| Recurse| Anger om underkataloger ingår. Den här egenskapen **$true** att ange att du vill underkataloger som ska inkluderas. Standardvärdet är **$false**. **Obs:** den här egenskapen är endast giltig när den **typen** egenskap är inställd på katalogen.| 
| Force| Vissa åtgärder (till exempel skriver över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel. Med hjälp av den **kraft** egenskapen åsidosätter sådana fel. Standardvärdet är **$false**.| 
| Länkar| Anger beteenden som önskas för symboliska länkar. Ange den här egenskapen till ”följa med” om du vill följa symboliska länkar och agera på målet länkar (till exempel. Kopiera filen i stället för länken). Ange den här egenskapen till ”hantera” för att fungera på länken (till exempel. Kopiera själva länken). Ange den här egenskapen till ”Ignorera” om du vill ignorera symboliska länkar.| 
| Grupp| Namnet på den **grupp** ska äga filen eller katalogen.| 
| Läge| Anger behörigheter för resursen i oktala eller symboliska notation. (till exempel 777 eller rwxrwxrwx). Om du använder symboliska notation, ange inte det första tecknet som anger katalog eller fil.| 
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** resursens configuration skriptblock som du vill köra först är **ResourceName** och dess typ är **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="additional-information"></a>Ytterligare information


Linux och Windows använder olika radbrytningstecken i textfiler som standard och detta kan orsaka oväntade resultat när du konfigurerar vissa filer på en Linux-dator med __nxFile__. Det finns flera sätt att hantera innehåll på en Linux-fil när undvika problem som orsakas av ett oväntat radbrytningstecken:

Steg 1: Kopiera filen från en fjärrkälla (http, FTP- eller https): skapa en fil på Linux med det önskade innehållet och Förbered den på en webbplats eller FTP-server som är tillgänglig noder som du vill konfigurera. Definiera den __SourcePath__ egenskap i den __nxFile__ resursen med webb- eller ftp-URL i filen.

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


Steg 2: Läsa innehållet i filen i PowerShell-skript med [Get-innehåll](https://technet.microsoft.com/library/hh849787.aspx) när du har angett den __$OFS__ egenskap som ska användas radbrytningstecken Linux.


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


Steg 3: Använda ett PowerShell-funktionen för att ersätta Windows radbrytningar med Linux radbrytningstecken.

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

I följande exempel säkerställer att katalogen `/opt/mydir` finns och att den här katalogen finns på en fil med innehåll har angetts.

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

