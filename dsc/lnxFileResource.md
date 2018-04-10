---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxFile resurs
ms.openlocfilehash: 41b5ebde299c47b38d7a6e7f71607332b24ca0e4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="01c77-103">DSC för Linux nxFile resurs</span><span class="sxs-lookup"><span data-stu-id="01c77-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="01c77-104">Den **nxFile** resurs i PowerShell önskad tillstånd Configuration (DSC) ger möjlighet till att hantera filer och kataloger på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="01c77-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="01c77-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="01c77-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="01c77-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="01c77-106">Properties</span></span>

|  <span data-ttu-id="01c77-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="01c77-107">Property</span></span> |  <span data-ttu-id="01c77-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="01c77-108">Description</span></span> |
|---|---|
| <span data-ttu-id="01c77-109">Målsökväg</span><span class="sxs-lookup"><span data-stu-id="01c77-109">DestinationPath</span></span>| <span data-ttu-id="01c77-110">Anger den plats där du vill kontrollera tillståndet för en fil eller katalog.</span><span class="sxs-lookup"><span data-stu-id="01c77-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="01c77-111">Källsökväg</span><span class="sxs-lookup"><span data-stu-id="01c77-111">SourcePath</span></span>| <span data-ttu-id="01c77-112">Anger sökvägen som du vill kopiera filen eller mappen resurs.</span><span class="sxs-lookup"><span data-stu-id="01c77-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="01c77-113">Den här sökvägen kan vara en lokal sökväg eller en `http/https/ftp` URL.</span><span class="sxs-lookup"><span data-stu-id="01c77-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="01c77-114">Remote `http/https/ftp` URL: er är endast när värdet för den **typen** egenskapen är filen.</span><span class="sxs-lookup"><span data-stu-id="01c77-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>|
| <span data-ttu-id="01c77-115">Se till att</span><span class="sxs-lookup"><span data-stu-id="01c77-115">Ensure</span></span>| <span data-ttu-id="01c77-116">Anger om du vill kontrollera om filen finns.</span><span class="sxs-lookup"><span data-stu-id="01c77-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="01c77-117">Ange egenskapen ”aktuella” för att se till att filen finns.</span><span class="sxs-lookup"><span data-stu-id="01c77-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="01c77-118">Ange den till ”saknas” för att se till att filen inte finns.</span><span class="sxs-lookup"><span data-stu-id="01c77-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="01c77-119">Standardvärdet är ”saknas”.</span><span class="sxs-lookup"><span data-stu-id="01c77-119">The default value is "Present".</span></span>|
| <span data-ttu-id="01c77-120">Typ</span><span class="sxs-lookup"><span data-stu-id="01c77-120">Type</span></span>| <span data-ttu-id="01c77-121">Anger om resursen som konfigureras är en katalog eller fil.</span><span class="sxs-lookup"><span data-stu-id="01c77-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="01c77-122">Ange den här egenskapen till ”directory” för att indikera att resursen är en katalog.</span><span class="sxs-lookup"><span data-stu-id="01c77-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="01c77-123">Ange att ”fil” för att indikera att resursen är en fil.</span><span class="sxs-lookup"><span data-stu-id="01c77-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="01c77-124">Standardvärdet är ”fil”</span><span class="sxs-lookup"><span data-stu-id="01c77-124">The default value is "file"</span></span>|
| <span data-ttu-id="01c77-125">Innehåll</span><span class="sxs-lookup"><span data-stu-id="01c77-125">Contents</span></span>| <span data-ttu-id="01c77-126">Anger innehållet i en fil, till exempel en viss sträng.</span><span class="sxs-lookup"><span data-stu-id="01c77-126">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="01c77-127">Kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="01c77-127">Checksum</span></span>| <span data-ttu-id="01c77-128">Definierar den typ som används när du fastställer om två filerna är samma.</span><span class="sxs-lookup"><span data-stu-id="01c77-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="01c77-129">Om **kontrollsumma** anges endast filen eller katalogen namn som används för jämförelse.</span><span class="sxs-lookup"><span data-stu-id="01c77-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="01c77-130">Värden är: ”ctime”, ”mtime” eller ”md5”.</span><span class="sxs-lookup"><span data-stu-id="01c77-130">Values are: "ctime", "mtime", or "md5".</span></span>|
| <span data-ttu-id="01c77-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="01c77-131">Recurse</span></span>| <span data-ttu-id="01c77-132">Anger om underkataloger ingår.</span><span class="sxs-lookup"><span data-stu-id="01c77-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="01c77-133">Den här egenskapen **$true** att ange att du vill underkataloger som ska inkluderas.</span><span class="sxs-lookup"><span data-stu-id="01c77-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="01c77-134">Standardvärdet är **$false**.</span><span class="sxs-lookup"><span data-stu-id="01c77-134">The default is **$false**.</span></span> <span data-ttu-id="01c77-135">**Obs:** den här egenskapen är endast giltig när den **typen** egenskap är inställd på katalogen.</span><span class="sxs-lookup"><span data-stu-id="01c77-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>|
| <span data-ttu-id="01c77-136">Force</span><span class="sxs-lookup"><span data-stu-id="01c77-136">Force</span></span>| <span data-ttu-id="01c77-137">Vissa åtgärder (till exempel skriver över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="01c77-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="01c77-138">Med hjälp av den **kraft** egenskapen åsidosätter sådana fel.</span><span class="sxs-lookup"><span data-stu-id="01c77-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="01c77-139">Standardvärdet är **$false**.</span><span class="sxs-lookup"><span data-stu-id="01c77-139">The default value is **$false**.</span></span>|
| <span data-ttu-id="01c77-140">Länkar</span><span class="sxs-lookup"><span data-stu-id="01c77-140">Links</span></span>| <span data-ttu-id="01c77-141">Anger beteenden som önskas för symboliska länkar.</span><span class="sxs-lookup"><span data-stu-id="01c77-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="01c77-142">Ange den här egenskapen till ”följa med” om du vill följa symboliska länkar och agera på målet länkar (till exempel.</span><span class="sxs-lookup"><span data-stu-id="01c77-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="01c77-143">Kopiera filen i stället för länken).</span><span class="sxs-lookup"><span data-stu-id="01c77-143">copy the file instead of the link).</span></span> <span data-ttu-id="01c77-144">Ange den här egenskapen till ”hantera” för att fungera på länken (till exempel.</span><span class="sxs-lookup"><span data-stu-id="01c77-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="01c77-145">Kopiera själva länken).</span><span class="sxs-lookup"><span data-stu-id="01c77-145">copy the link itself).</span></span> <span data-ttu-id="01c77-146">Ange den här egenskapen till ”Ignorera” om du vill ignorera symboliska länkar.</span><span class="sxs-lookup"><span data-stu-id="01c77-146">Set this property to "ignore" to ignore symbolic links.</span></span>|
| <span data-ttu-id="01c77-147">Grupp</span><span class="sxs-lookup"><span data-stu-id="01c77-147">Group</span></span>| <span data-ttu-id="01c77-148">Namnet på den **grupp** ska äga filen eller katalogen.</span><span class="sxs-lookup"><span data-stu-id="01c77-148">The name of the **Group** to own the file or directory.</span></span>|
| <span data-ttu-id="01c77-149">Läge</span><span class="sxs-lookup"><span data-stu-id="01c77-149">Mode</span></span>| <span data-ttu-id="01c77-150">Anger behörigheter för resursen i oktala eller symboliska notation.</span><span class="sxs-lookup"><span data-stu-id="01c77-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="01c77-151">(till exempel 777 eller rwxrwxrwx).</span><span class="sxs-lookup"><span data-stu-id="01c77-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="01c77-152">Om du använder symboliska notation, ange inte det första tecknet som anger katalog eller fil.</span><span class="sxs-lookup"><span data-stu-id="01c77-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>|
| <span data-ttu-id="01c77-153">dependsOn</span><span class="sxs-lookup"><span data-stu-id="01c77-153">DependsOn</span></span> | <span data-ttu-id="01c77-154">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="01c77-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="01c77-155">Till exempel om den **ID** resursens configuration skriptblock som du vill köra först är **ResourceName** och dess typ är **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="01c77-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="01c77-156">Ytterligare information</span><span class="sxs-lookup"><span data-stu-id="01c77-156">Additional Information</span></span>


<span data-ttu-id="01c77-157">Linux och Windows använder olika radbrytningstecken i textfiler som standard och detta kan orsaka oväntade resultat när du konfigurerar vissa filer på en Linux-dator med __nxFile__.</span><span class="sxs-lookup"><span data-stu-id="01c77-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="01c77-158">Det finns flera sätt att hantera innehåll på en Linux-fil när undvika problem som orsakas av ett oväntat radbrytningstecken:</span><span class="sxs-lookup"><span data-stu-id="01c77-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="01c77-159">Steg 1: Kopiera filen från en fjärrkälla (http, FTP- eller https): skapa en fil på Linux med det önskade innehållet och Förbered den på en webbplats eller FTP-server som är tillgänglig noder som du vill konfigurera.</span><span class="sxs-lookup"><span data-stu-id="01c77-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="01c77-160">Definiera den __SourcePath__ egenskap i den __nxFile__ resursen med webb- eller ftp-URL i filen.</span><span class="sxs-lookup"><span data-stu-id="01c77-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

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


<span data-ttu-id="01c77-161">Steg 2: Läsa innehållet i filen i PowerShell-skript med [Get-innehåll](https://technet.microsoft.com/library/hh849787.aspx) när du har angett den __$OFS__ egenskap som ska användas radbrytningstecken Linux.</span><span class="sxs-lookup"><span data-stu-id="01c77-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


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


<span data-ttu-id="01c77-162">Steg 3: Använda ett PowerShell-funktionen för att ersätta Windows radbrytningar med Linux radbrytningstecken.</span><span class="sxs-lookup"><span data-stu-id="01c77-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

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

## <a name="example"></a><span data-ttu-id="01c77-163">Exempel</span><span class="sxs-lookup"><span data-stu-id="01c77-163">Example</span></span>

<span data-ttu-id="01c77-164">I följande exempel säkerställer att katalogen `/opt/mydir` finns och att den här katalogen finns på en fil med innehåll har angetts.</span><span class="sxs-lookup"><span data-stu-id="01c77-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

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