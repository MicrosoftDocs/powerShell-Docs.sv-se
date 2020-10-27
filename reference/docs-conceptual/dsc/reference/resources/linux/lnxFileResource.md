---
ms.date: 07/17/2020
ms.topic: reference
title: DSC för Linux nxFile-resurs
description: DSC för Linux nxFile-resurs
ms.openlocfilehash: 6ec2d8201f3594879b781fe04e32a28cc87ba934
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644740"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="7ea53-103">DSC för Linux nxFile-resurs</span><span class="sxs-lookup"><span data-stu-id="7ea53-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="7ea53-104">**NxFile** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera filer och kataloger på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="7ea53-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="7ea53-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7ea53-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="7ea53-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="7ea53-106">Properties</span></span>

|<span data-ttu-id="7ea53-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7ea53-107">Property</span></span> |<span data-ttu-id="7ea53-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7ea53-108">Description</span></span> |
|---|---|
|<span data-ttu-id="7ea53-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="7ea53-109">DestinationPath</span></span> |<span data-ttu-id="7ea53-110">Anger den plats där du vill kontrol lera statusen för en fil eller katalog.</span><span class="sxs-lookup"><span data-stu-id="7ea53-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="7ea53-111">Sök</span><span class="sxs-lookup"><span data-stu-id="7ea53-111">SourcePath</span></span> |<span data-ttu-id="7ea53-112">Anger sökvägen från vilken du vill kopiera filen eller mappens resurs.</span><span class="sxs-lookup"><span data-stu-id="7ea53-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="7ea53-113">Sökvägen kan vara en lokal sökväg eller en `http/https/ftp` URL.</span><span class="sxs-lookup"><span data-stu-id="7ea53-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="7ea53-114">Fjärranslutna `http/https/ftp` URL: er stöds bara när värdet för **Type** -egenskapen är **File** .</span><span class="sxs-lookup"><span data-stu-id="7ea53-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is **file** .</span></span> |
|<span data-ttu-id="7ea53-115">Typ</span><span class="sxs-lookup"><span data-stu-id="7ea53-115">Type</span></span> |<span data-ttu-id="7ea53-116">Anger om den resurs som konfigureras är en katalog eller en fil.</span><span class="sxs-lookup"><span data-stu-id="7ea53-116">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="7ea53-117">Ange den här egenskapen som **katalog** för att ange att resursen är en katalog.</span><span class="sxs-lookup"><span data-stu-id="7ea53-117">Set this property to **directory** to indicate that the resource is a directory.</span></span> <span data-ttu-id="7ea53-118">Ange den som **fil** för att ange att resursen är en fil.</span><span class="sxs-lookup"><span data-stu-id="7ea53-118">Set it to **file** to indicate that the resource is a file.</span></span> <span data-ttu-id="7ea53-119">Standardvärdet är **File** .</span><span class="sxs-lookup"><span data-stu-id="7ea53-119">The default value is **file** .</span></span> |
|<span data-ttu-id="7ea53-120">Innehåll</span><span class="sxs-lookup"><span data-stu-id="7ea53-120">Contents</span></span> |<span data-ttu-id="7ea53-121">Anger innehållet i en fil, till exempel en viss sträng.</span><span class="sxs-lookup"><span data-stu-id="7ea53-121">Specifies the contents of a file, such as a particular string.</span></span> |
|<span data-ttu-id="7ea53-122">Kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="7ea53-122">Checksum</span></span> |<span data-ttu-id="7ea53-123">Definierar den typ som ska användas för att avgöra om två filer är identiska.</span><span class="sxs-lookup"><span data-stu-id="7ea53-123">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="7ea53-124">Om ingen **kontroll Summa** anges används bara fil-eller katalog namnet för jämförelse.</span><span class="sxs-lookup"><span data-stu-id="7ea53-124">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="7ea53-125">Värdena är: **ctime** , **mtime** eller **MD5** .</span><span class="sxs-lookup"><span data-stu-id="7ea53-125">Values are: **ctime** , **mtime** , or **md5** .</span></span> |
|<span data-ttu-id="7ea53-126">Rekursivt</span><span class="sxs-lookup"><span data-stu-id="7ea53-126">Recurse</span></span> |<span data-ttu-id="7ea53-127">Anger om under kataloger ingår.</span><span class="sxs-lookup"><span data-stu-id="7ea53-127">Indicates if subdirectories are included.</span></span> <span data-ttu-id="7ea53-128">Ange den här egenskapen som `$true` anger att du vill att under kataloger ska tas med.</span><span class="sxs-lookup"><span data-stu-id="7ea53-128">Set this property to `$true` to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="7ea53-129">Standardvärdet är `$false`.</span><span class="sxs-lookup"><span data-stu-id="7ea53-129">The default is `$false`.</span></span> <span data-ttu-id="7ea53-130">Den här egenskapen är endast giltig när egenskapen **Type** har angetts till **Directory** .</span><span class="sxs-lookup"><span data-stu-id="7ea53-130">This property is only valid when the **Type** property is set to **directory** .</span></span> |
|<span data-ttu-id="7ea53-131">Force</span><span class="sxs-lookup"><span data-stu-id="7ea53-131">Force</span></span> |<span data-ttu-id="7ea53-132">Vissa fil åtgärder (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="7ea53-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="7ea53-133">Om du använder **Force** -egenskapen åsidosätts sådana fel.</span><span class="sxs-lookup"><span data-stu-id="7ea53-133">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="7ea53-134">Standardvärdet är `$false`.</span><span class="sxs-lookup"><span data-stu-id="7ea53-134">The default value is `$false`.</span></span> |
|<span data-ttu-id="7ea53-135">Länkar</span><span class="sxs-lookup"><span data-stu-id="7ea53-135">Links</span></span> |<span data-ttu-id="7ea53-136">Anger det önskade beteendet för symboliska länkar.</span><span class="sxs-lookup"><span data-stu-id="7ea53-136">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="7ea53-137">Ange den här egenskapen som **ska följas för att följa** symboliska länkar och agera på länk målet.</span><span class="sxs-lookup"><span data-stu-id="7ea53-137">Set this property to **follow** to follow symbolic links and act on the links target.</span></span> <span data-ttu-id="7ea53-138">Kopiera till exempel filen i stället för länken.</span><span class="sxs-lookup"><span data-stu-id="7ea53-138">For example, copy the file instead of the link.</span></span> <span data-ttu-id="7ea53-139">Ange den här egenskapen som ska **hanteras** för att agera på länken.</span><span class="sxs-lookup"><span data-stu-id="7ea53-139">Set this property to **manage** to act on the link.</span></span> <span data-ttu-id="7ea53-140">Kopiera till exempel själva länken.</span><span class="sxs-lookup"><span data-stu-id="7ea53-140">For example, copy the link itself.</span></span> <span data-ttu-id="7ea53-141">Ange den här egenskapen som **Ignorera** om du vill ignorera symboliska länkar.</span><span class="sxs-lookup"><span data-stu-id="7ea53-141">Set this property to **ignore** to ignore symbolic links.</span></span> |
|<span data-ttu-id="7ea53-142">Group</span><span class="sxs-lookup"><span data-stu-id="7ea53-142">Group</span></span> |<span data-ttu-id="7ea53-143">Namnet på **gruppen** som har behörighet till filen eller katalogen.</span><span class="sxs-lookup"><span data-stu-id="7ea53-143">The name of the **Group** to have permissions to the file or directory.</span></span> |
|<span data-ttu-id="7ea53-144">Läge</span><span class="sxs-lookup"><span data-stu-id="7ea53-144">Mode</span></span> |<span data-ttu-id="7ea53-145">Anger önskade behörigheter för resursen, i oktalt eller symbolisk notation.</span><span class="sxs-lookup"><span data-stu-id="7ea53-145">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="7ea53-146">Till exempel **777** eller **rwxrwxrwx** .</span><span class="sxs-lookup"><span data-stu-id="7ea53-146">For example, **777** or **rwxrwxrwx** .</span></span> <span data-ttu-id="7ea53-147">Om du använder symbolisk notation ska du inte ange det första tecknen som anger katalog eller fil.</span><span class="sxs-lookup"><span data-stu-id="7ea53-147">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span> |
|<span data-ttu-id="7ea53-148">Ägare</span><span class="sxs-lookup"><span data-stu-id="7ea53-148">Owner</span></span> |<span data-ttu-id="7ea53-149">Namnet på gruppen som ska äga filen eller katalogen.</span><span class="sxs-lookup"><span data-stu-id="7ea53-149">The name of the group to own the file or directory.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7ea53-150">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="7ea53-150">Common properties</span></span>

|<span data-ttu-id="7ea53-151">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7ea53-151">Property</span></span> |<span data-ttu-id="7ea53-152">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7ea53-152">Description</span></span> |
|---|---|
|<span data-ttu-id="7ea53-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7ea53-153">DependsOn</span></span> |<span data-ttu-id="7ea53-154">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="7ea53-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7ea53-155">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="7ea53-155">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7ea53-156">Kontrol</span><span class="sxs-lookup"><span data-stu-id="7ea53-156">Ensure</span></span> |<span data-ttu-id="7ea53-157">Avgör om du ska kontrol lera om filen finns.</span><span class="sxs-lookup"><span data-stu-id="7ea53-157">Determines whether to check if the file exists.</span></span> <span data-ttu-id="7ea53-158">Ange att den här egenskapen **finns för att se till att** filen finns.</span><span class="sxs-lookup"><span data-stu-id="7ea53-158">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="7ea53-159">Ange det som **frånvarande** för att se till att filen inte finns.</span><span class="sxs-lookup"><span data-stu-id="7ea53-159">Set it to **Absent** to ensure the file does not exist.</span></span> <span data-ttu-id="7ea53-160">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="7ea53-160">The default value is **Present** .</span></span> |

## <a name="additional-information"></a><span data-ttu-id="7ea53-161">Ytterligare information</span><span class="sxs-lookup"><span data-stu-id="7ea53-161">Additional Information</span></span>

<span data-ttu-id="7ea53-162">Linux och Windows använder olika rad brytnings tecken i textfiler som standard och detta kan orsaka oväntade resultat när du konfigurerar vissa filer på en Linux-dator med **nxFile** .</span><span class="sxs-lookup"><span data-stu-id="7ea53-162">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with **nxFile** .</span></span> <span data-ttu-id="7ea53-163">Det finns flera sätt att hantera innehållet i en Linux-fil samtidigt som du undviker problem som orsakas av oväntade rad brytnings tecken:</span><span class="sxs-lookup"><span data-stu-id="7ea53-163">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

1. <span data-ttu-id="7ea53-164">Kopiera filen från en fjärran sluten källa (http, https eller FTP)</span><span class="sxs-lookup"><span data-stu-id="7ea53-164">Copy the file from a remote source (http, https, or ftp)</span></span>

   <span data-ttu-id="7ea53-165">Skapa en fil på Linux med det önskade innehållet och stega den på en webb-eller FTP-server som är tillgänglig för de noder som du konfigurerar.</span><span class="sxs-lookup"><span data-stu-id="7ea53-165">Create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="7ea53-166">Definiera egenskapen **SourcePath** i **nxFile** -resursen med webb-eller FTP-adressen till filen.</span><span class="sxs-lookup"><span data-stu-id="7ea53-166">Define the **SourcePath** property in the **nxFile** resource with the web or ftp URL to the file.</span></span>

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

1. <span data-ttu-id="7ea53-167">Läs filens innehåll i PowerShell-skriptet med [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) när du har angett att **$OFS** -egenskapen ska använda det rad brytnings tecken som används i Linux.</span><span class="sxs-lookup"><span data-stu-id="7ea53-167">Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the **$OFS** property to use the Linux line-break character.</span></span>

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

1. <span data-ttu-id="7ea53-168">Använd en PowerShell-funktion för att ersätta Windows rad brytningar med rad brytnings tecken i Linux.</span><span class="sxs-lookup"><span data-stu-id="7ea53-168">Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

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

## <a name="example"></a><span data-ttu-id="7ea53-169">Exempel</span><span class="sxs-lookup"><span data-stu-id="7ea53-169">Example</span></span>

<span data-ttu-id="7ea53-170">I följande exempel ser du till att katalogen `/opt/mydir` finns och att en fil med angivet innehåll finns i katalogen.</span><span class="sxs-lookup"><span data-stu-id="7ea53-170">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

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
