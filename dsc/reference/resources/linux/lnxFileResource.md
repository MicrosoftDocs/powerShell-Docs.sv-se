---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxFile-resurs
ms.openlocfilehash: be5f098d2fe1c8b354c07e6a8f882b8fdf00e1db
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324801"
---
# <a name="dsc-for-linux-nxfile-resource"></a>DSC för Linux nxFile-resurs

**NxFile** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera filer och kataloger på en Linux-nod.

## <a name="syntax"></a>Syntax

```Syntax
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage | ignore } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>properties

|Egenskap |Beskrivning |
|---|---|
|DestinationPath |Anger den plats där du vill kontrol lera statusen för en fil eller katalog. |
|Sök |Anger sökvägen från vilken du vill kopiera filen eller mappens resurs. Sökvägen kan vara en lokal sökväg eller en `http/https/ftp` URL. Fjärranslutna `http/https/ftp` URL: er stöds bara när värdet för **Type** -egenskapen är **File**. |
|type |Anger om den resurs som konfigureras är en katalog eller en fil. Ange den här egenskapen som **katalog** för att ange att resursen är en katalog. Ange den som **fil** för att ange att resursen är en fil. Standardvärdet är **File**. |
|Innehåll |Anger innehållet i en fil, till exempel en viss sträng. |
|Kontrollsumma |Definierar den typ som ska användas för att avgöra om två filer är identiska. Om ingen **kontroll Summa** anges används bara fil-eller katalog namnet för jämförelse. Värdena är: **ctime**, **mtime**eller **MD5**. |
|Rekursivt |Anger om under kataloger ingår. Ange den här egenskapen `$true` som anger att du vill att under kataloger ska tas med. Standardvärdet är `$false`. Den här egenskapen är endast giltig när egenskapen **Type** har angetts till **Directory**. |
|Force |Vissa fil åtgärder (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel. Om du använder **Force** -egenskapen åsidosätts sådana fel. Standardvärdet är `$false`. |
|Länkar |Anger det önskade beteendet för symboliska länkar. Ange den här egenskapen som **ska följas för att följa** symboliska länkar och agera på länk målet. Kopiera till exempel filen i stället för länken. Ange den här egenskapen som ska **hanteras** för att agera på länken. Kopiera till exempel själva länken. Ange den här egenskapen som **Ignorera** om du vill ignorera symboliska länkar. |
|Grupp |Namnet på **gruppen** som har behörighet till filen eller katalogen. |
|Läge |Anger önskade behörigheter för resursen, i oktalt eller symbolisk notation. Till exempel **777** eller **rwxrwxrwx**. Om du använder symbolisk notation ska du inte ange det första tecknen som anger katalog eller fil. |
|Ägare |Namnet på gruppen som ska äga filen eller katalogen. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. |
|Kontrol |Avgör om du ska kontrol lera om filen finns. Ange att den här egenskapen **finns för att se till att** filen finns. Ange det som **frånvarande** för att se till att filen inte finns. Standardvärdet finns **.** |

## <a name="additional-information"></a>Ytterligare information

Linux och Windows använder olika rad brytnings tecken i textfiler som standard och detta kan orsaka oväntade resultat när du konfigurerar vissa filer på en Linux-dator med **nxFile**. Det finns flera sätt att hantera innehållet i en Linux-fil samtidigt som du undviker problem som orsakas av oväntade rad brytnings tecken:

1. Kopiera filen från en fjärran sluten källa (http, https eller FTP)

   Skapa en fil på Linux med det önskade innehållet och stega den på en webb-eller FTP-server som är tillgänglig för de noder som du konfigurerar. Definiera egenskapen **SourcePath** i **nxFile** -resursen med webb-eller FTP-adressen till filen.

   ```powershell
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

1. Läs filens innehåll i PowerShell-skriptet med [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) när du har angett att **$OFS** -egenskapen ska använda det rad brytnings tecken som används i Linux.

   ```powershell
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

1. Använd en PowerShell-funktion för att ersätta Windows rad brytningar med rad brytnings tecken i Linux.

   ```powershell
   Function LinuxString($inputStr){
      $outputStr = $inputStr.Replace("`r`n","`n")
      $outputStr += "`n"
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

I följande exempel ser du till att `/opt/mydir` katalogen finns och att en fil med angivet innehåll finns i katalogen.

```powershell
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
        Mode = "755"
        DependsOn = "[nxFile]DirectoryExample"
    }
}
```