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
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="e8913-103">DSC för Linux nxFile-resurs</span><span class="sxs-lookup"><span data-stu-id="e8913-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="e8913-104">Den **nxFile** resursen i PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera filer och kataloger på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="e8913-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8913-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e8913-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="e8913-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="e8913-106">Properties</span></span>

|  <span data-ttu-id="e8913-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="e8913-107">Property</span></span> |  <span data-ttu-id="e8913-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e8913-108">Description</span></span> |
|---|---|
| <span data-ttu-id="e8913-109">Målsökväg</span><span class="sxs-lookup"><span data-stu-id="e8913-109">DestinationPath</span></span>| <span data-ttu-id="e8913-110">Anger den plats där du vill kontrollera status för en fil eller katalog.</span><span class="sxs-lookup"><span data-stu-id="e8913-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="e8913-111">Källsökväg</span><span class="sxs-lookup"><span data-stu-id="e8913-111">SourcePath</span></span>| <span data-ttu-id="e8913-112">Anger sökvägen som du vill kopiera filen eller mappen resursen från.</span><span class="sxs-lookup"><span data-stu-id="e8913-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="e8913-113">Den här sökvägen kan vara en lokal sökväg eller en `http/https/ftp` URL: en.</span><span class="sxs-lookup"><span data-stu-id="e8913-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="e8913-114">Remote `http/https/ftp` URL: er är bara när värdet för den **typ** egenskapen är filen.</span><span class="sxs-lookup"><span data-stu-id="e8913-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>|
| <span data-ttu-id="e8913-115">Se till att</span><span class="sxs-lookup"><span data-stu-id="e8913-115">Ensure</span></span>| <span data-ttu-id="e8913-116">Anger om du vill kontrollera om filen finns.</span><span class="sxs-lookup"><span data-stu-id="e8913-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="e8913-117">Ange egenskapen ”aktuella” för att se till att filen finns.</span><span class="sxs-lookup"><span data-stu-id="e8913-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="e8913-118">Ange den till ”inte” för att se till att filen inte finns.</span><span class="sxs-lookup"><span data-stu-id="e8913-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="e8913-119">Standardvärdet är ”tillgänglig”.</span><span class="sxs-lookup"><span data-stu-id="e8913-119">The default value is "Present".</span></span>|
| <span data-ttu-id="e8913-120">Typ</span><span class="sxs-lookup"><span data-stu-id="e8913-120">Type</span></span>| <span data-ttu-id="e8913-121">Anger om resursen som konfigureras är en katalog eller en fil.</span><span class="sxs-lookup"><span data-stu-id="e8913-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="e8913-122">Ange egenskapen till ”directory” för att indikera att resursen är en katalog.</span><span class="sxs-lookup"><span data-stu-id="e8913-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="e8913-123">Ange den till ”filen” för att indikera att resursen är en fil.</span><span class="sxs-lookup"><span data-stu-id="e8913-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="e8913-124">Standardvärdet är ”fil”</span><span class="sxs-lookup"><span data-stu-id="e8913-124">The default value is "file"</span></span>|
| <span data-ttu-id="e8913-125">Innehåll</span><span class="sxs-lookup"><span data-stu-id="e8913-125">Contents</span></span>| <span data-ttu-id="e8913-126">Anger innehållet i en fil, till exempel en viss sträng.</span><span class="sxs-lookup"><span data-stu-id="e8913-126">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="e8913-127">Kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="e8913-127">Checksum</span></span>| <span data-ttu-id="e8913-128">Definierar den typ som ska användas när du bestämmer om två filer är lika.</span><span class="sxs-lookup"><span data-stu-id="e8913-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="e8913-129">Om **kontrollsumma** inte anges endast filen eller katalogen namnet används för jämförelse.</span><span class="sxs-lookup"><span data-stu-id="e8913-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="e8913-130">Värden är: ”ctime”, ”mtime” eller ”md5”.</span><span class="sxs-lookup"><span data-stu-id="e8913-130">Values are: "ctime", "mtime", or "md5".</span></span>|
| <span data-ttu-id="e8913-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="e8913-131">Recurse</span></span>| <span data-ttu-id="e8913-132">Anger om underkataloger ingår.</span><span class="sxs-lookup"><span data-stu-id="e8913-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="e8913-133">Den här egenskapen **$true** att indikera att du vill att underkataloger som ska tas med.</span><span class="sxs-lookup"><span data-stu-id="e8913-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="e8913-134">Standardvärdet är **$false**.</span><span class="sxs-lookup"><span data-stu-id="e8913-134">The default is **$false**.</span></span> <span data-ttu-id="e8913-135">**Obs:** den här egenskapen är endast giltig när den **typ** är inställd på katalogen.</span><span class="sxs-lookup"><span data-stu-id="e8913-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>|
| <span data-ttu-id="e8913-136">Force</span><span class="sxs-lookup"><span data-stu-id="e8913-136">Force</span></span>| <span data-ttu-id="e8913-137">Vissa åtgärder för sammansättningsfiler (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="e8913-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="e8913-138">Med hjälp av den **kraft** egenskapen åsidosätter sådana fel.</span><span class="sxs-lookup"><span data-stu-id="e8913-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="e8913-139">Standardvärdet är **$false**.</span><span class="sxs-lookup"><span data-stu-id="e8913-139">The default value is **$false**.</span></span>|
| <span data-ttu-id="e8913-140">Länkar</span><span class="sxs-lookup"><span data-stu-id="e8913-140">Links</span></span>| <span data-ttu-id="e8913-141">Anger du önskat beteende för symboliska länkar.</span><span class="sxs-lookup"><span data-stu-id="e8913-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="e8913-142">Ange den här egenskapen ”följer” för att följa symboliska länkar och agera på mål-länkar (till exempel.</span><span class="sxs-lookup"><span data-stu-id="e8913-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="e8913-143">Kopiera filen i stället för länken).</span><span class="sxs-lookup"><span data-stu-id="e8913-143">copy the file instead of the link).</span></span> <span data-ttu-id="e8913-144">Ange den här egenskapen till ”hantera” för att agera på länken (till exempel.</span><span class="sxs-lookup"><span data-stu-id="e8913-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="e8913-145">kopiera länken själva).</span><span class="sxs-lookup"><span data-stu-id="e8913-145">copy the link itself).</span></span> <span data-ttu-id="e8913-146">Ange den här egenskapen till ”Ignorera” ignorerar symboliska länkar.</span><span class="sxs-lookup"><span data-stu-id="e8913-146">Set this property to "ignore" to ignore symbolic links.</span></span>|
| <span data-ttu-id="e8913-147">Grupp</span><span class="sxs-lookup"><span data-stu-id="e8913-147">Group</span></span>| <span data-ttu-id="e8913-148">Namnet på den **grupp** äga filen eller katalogen.</span><span class="sxs-lookup"><span data-stu-id="e8913-148">The name of the **Group** to own the file or directory.</span></span>|
| <span data-ttu-id="e8913-149">Läge</span><span class="sxs-lookup"><span data-stu-id="e8913-149">Mode</span></span>| <span data-ttu-id="e8913-150">Anger de önskade behörigheterna för resursen i oktala eller symboliska notation.</span><span class="sxs-lookup"><span data-stu-id="e8913-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="e8913-151">(till exempel 777 eller rwxrwxrwx).</span><span class="sxs-lookup"><span data-stu-id="e8913-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="e8913-152">Om du använder symboliska notation, ingår det första tecknet som anger mapp eller fil.</span><span class="sxs-lookup"><span data-stu-id="e8913-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>|
| <span data-ttu-id="e8913-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e8913-153">DependsOn</span></span> | <span data-ttu-id="e8913-154">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="e8913-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e8913-155">Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e8913-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="e8913-156">Ytterligare information</span><span class="sxs-lookup"><span data-stu-id="e8913-156">Additional Information</span></span>


<span data-ttu-id="e8913-157">Linux och Windows använder olika radbrytningstecken i textfiler som standard och detta kan orsaka oväntade resultat när du konfigurerar vissa filer på en Linux-dator med __nxFile__.</span><span class="sxs-lookup"><span data-stu-id="e8913-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="e8913-158">Det finns flera sätt att hantera innehållet i en Linux-fil samtidigt som du undviker problem som orsakas av ett oväntat radbrytningstecken:</span><span class="sxs-lookup"><span data-stu-id="e8913-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="e8913-159">Steg 1: Kopiera filen från en fjärrkälla (http, https eller ftp): skapa en fil i Linux med önskade innehållet och mellanlagra dem på en webbplats eller FTP-server som är tillgängliga noder som du vill konfigurera.</span><span class="sxs-lookup"><span data-stu-id="e8913-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="e8913-160">Definiera den __SourcePath__ -egenskapen i den __nxFile__ resurs med webb- eller ftp-URL till filen.</span><span class="sxs-lookup"><span data-stu-id="e8913-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

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


<span data-ttu-id="e8913-161">Steg 2: Läsa filinnehållet i PowerShell-skript med [Get-innehåll](https://technet.microsoft.com/library/hh849787.aspx) när den __$OFS__ egenskapen att använda radbrytningstecken Linux.</span><span class="sxs-lookup"><span data-stu-id="e8913-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


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


<span data-ttu-id="e8913-162">Steg 3: Använda en PowerShell-funktion för att ersätta Windows radbrytningar med Linux radbrytningstecken.</span><span class="sxs-lookup"><span data-stu-id="e8913-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

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

## <a name="example"></a><span data-ttu-id="e8913-163">Exempel</span><span class="sxs-lookup"><span data-stu-id="e8913-163">Example</span></span>

<span data-ttu-id="e8913-164">I följande exempel ser till att katalogen `/opt/mydir` finns, och att den här katalogen finns i en fil med innehåll har angetts.</span><span class="sxs-lookup"><span data-stu-id="e8913-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

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