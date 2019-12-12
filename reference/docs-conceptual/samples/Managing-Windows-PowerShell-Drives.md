---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Hantera Windows PowerShell-enheter
ms.openlocfilehash: 5d1aba459caeaab2542e17e74534da6713b0faa9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "70215520"
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="ab61b-103">Hantera Windows PowerShell-enheter</span><span class="sxs-lookup"><span data-stu-id="ab61b-103">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="ab61b-104">En *Windows PowerShell-enhet* är en data lager plats som du kan komma åt som en fil system enhet i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab61b-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="ab61b-105">Windows PowerShell-providern skapar några enheter åt dig, till exempel fil system enheter (inklusive C: och D:), register enheterna (HKCU: och HKLM:) och certifikat enheten (cert:) och du kan skapa egna Windows PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="ab61b-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="ab61b-106">De här enheterna är mycket användbara, men de är bara tillgängliga i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab61b-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="ab61b-107">Du kan inte komma åt dem genom att använda andra Windows-verktyg, till exempel Utforskaren eller cmd. exe.</span><span class="sxs-lookup"><span data-stu-id="ab61b-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="ab61b-108">Windows PowerShell använder substantiv, **PSDrive**, för kommandon som fungerar med Windows PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="ab61b-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="ab61b-109">Om du vill ha en lista över Windows PowerShell-enheter i Windows PowerShell-sessionen använder du cmdleten **Get-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="ab61b-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

<span data-ttu-id="ab61b-110">Även om enheterna i visningen varierar med enheterna i systemet, kommer listan att se ut ungefär som utdata från kommandot **Get-PSDrive** som visas ovan.</span><span class="sxs-lookup"><span data-stu-id="ab61b-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="ab61b-111">Fil Systems enheter är en delmängd av Windows PowerShell-enheterna.</span><span class="sxs-lookup"><span data-stu-id="ab61b-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="ab61b-112">Du kan identifiera fil system enheterna med posten FileSystem i kolumnen Provider.</span><span class="sxs-lookup"><span data-stu-id="ab61b-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="ab61b-113">(Fil system enheter i Windows PowerShell stöds av Windows PowerShell-providern.)</span><span class="sxs-lookup"><span data-stu-id="ab61b-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="ab61b-114">Om du vill se syntaxen för **Get-PSDrive** -cmdleten skriver du ett **get-kommando-** kommando med parametern **syntax** :</span><span class="sxs-lookup"><span data-stu-id="ab61b-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="ab61b-115">Med parametern **PSProvider** kan du bara visa de Windows PowerShell-enheter som stöds av en viss Provider.</span><span class="sxs-lookup"><span data-stu-id="ab61b-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="ab61b-116">Om du till exempel bara vill visa de Windows PowerShell-enheter som stöds av Windows PowerShell-filprovidern, skriver du in kommandot **Get-PSDrive** med parametern **PSProvider** och värdet **filesystem** :</span><span class="sxs-lookup"><span data-stu-id="ab61b-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="ab61b-117">Om du vill visa de Windows PowerShell-enheter som representerar registreringsdatafiler använder du parametern **PSProvider** för att endast visa de Windows PowerShell-enheter som stöds av Windows PowerShell-registernyckeln:</span><span class="sxs-lookup"><span data-stu-id="ab61b-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="ab61b-118">Du kan också använda standard plats-cmdlet: ar med Windows PowerShell-enheter:</span><span class="sxs-lookup"><span data-stu-id="ab61b-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="ab61b-119">Lägga till nya Windows PowerShell-enheter (New-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="ab61b-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="ab61b-120">Du kan lägga till egna Windows PowerShell-enheter med kommandot **New-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="ab61b-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="ab61b-121">Hämta syntaxen för kommandot **New-PSDrive** genom att ange kommandot **Get-kommandot** med parametern **syntax** :</span><span class="sxs-lookup"><span data-stu-id="ab61b-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="ab61b-122">Om du vill skapa en ny Windows PowerShell-enhet måste du ange tre parametrar:</span><span class="sxs-lookup"><span data-stu-id="ab61b-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="ab61b-123">Ett namn på enheten (du kan använda alla giltiga Windows PowerShell-namn)</span><span class="sxs-lookup"><span data-stu-id="ab61b-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="ab61b-124">PSProvider (Använd "FileSystem" för fil system platser och "Registry" för register platser)</span><span class="sxs-lookup"><span data-stu-id="ab61b-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="ab61b-125">Roten, det vill säga sökvägen till roten för den nya enheten</span><span class="sxs-lookup"><span data-stu-id="ab61b-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="ab61b-126">Du kan till exempel skapa en enhet med namnet "Office" som är mappad till den mapp som innehåller Microsoft Office-program på datorn, till exempel **C:\\programfiler\\Microsoft Office\\Office11**.</span><span class="sxs-lookup"><span data-stu-id="ab61b-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="ab61b-127">Skriv följande kommando för att skapa enheten:</span><span class="sxs-lookup"><span data-stu-id="ab61b-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="ab61b-128">I allmänhet är sökvägar inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="ab61b-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="ab61b-129">Du kan referera till den nya Windows PowerShell-enheten på samma sätt som du gör med Windows PowerShell-enheter – efter dess namn följt av ett kolon ( **:** ).</span><span class="sxs-lookup"><span data-stu-id="ab61b-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="ab61b-130">En Windows PowerShell-enhet kan göra många aktiviteter mycket enklare.</span><span class="sxs-lookup"><span data-stu-id="ab61b-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="ab61b-131">Några av de viktigaste nycklarna i Windows-registret har till exempel extremt långa sökvägar, vilket gör det svårt att komma åt och svårt att komma ihåg.</span><span class="sxs-lookup"><span data-stu-id="ab61b-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="ab61b-132">Viktig konfigurations information finns i **HKEY_LOCAL_MACHINE\\program vara\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="ab61b-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="ab61b-133">Om du vill visa och ändra objekt i register nyckeln CurrentVersion, kan du skapa en Windows PowerShell-enhet som är rotad i nyckeln genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="ab61b-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="ab61b-134">Du kan sedan ändra plats till **cvkey:** enheten på samma sätt som med andra enheter:</span><span class="sxs-lookup"><span data-stu-id="ab61b-134">You can then change location to the **cvkey:** drive as you would any other drive:</span></span>

```
PS> cd cvkey:
```

<span data-ttu-id="ab61b-135">eller:</span><span class="sxs-lookup"><span data-stu-id="ab61b-135">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="ab61b-136">Cmdlet: en New-PsDrive lägger bara till den nya enheten till den aktuella Windows PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ab61b-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="ab61b-137">Om du stänger Windows PowerShell-fönstret går den nya enheten förlorad.</span><span class="sxs-lookup"><span data-stu-id="ab61b-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="ab61b-138">Om du vill spara en Windows PowerShell-enhet använder du cmdleten export-Console för att exportera den aktuella Windows PowerShell-sessionen och använder sedan PowerShell. exe **PSConsoleFile** -parametern för att importera den.</span><span class="sxs-lookup"><span data-stu-id="ab61b-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="ab61b-139">Eller Lägg till den nya enheten i Windows PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="ab61b-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="ab61b-140">Ta bort Windows PowerShell-enheter (Remove-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="ab61b-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="ab61b-141">Du kan ta bort enheter från Windows PowerShell med cmdleten **Remove-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="ab61b-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="ab61b-142">Cmdlet: en **Remove-PSDrive** är enkel att använda. Om du vill ta bort en Windows PowerShell-enhet anger du bara namnet på Windows PowerShell-enheten.</span><span class="sxs-lookup"><span data-stu-id="ab61b-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="ab61b-143">Om du till exempel har lagt till **Office:** Windows PowerShell-enheten, som du ser i avsnittet **New-PSDrive** , kan du ta bort den genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="ab61b-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="ab61b-144">För att ta bort **cvkey:** Windows PowerShell-enheten, som också visas i avsnittet **New-PSDrive** , använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="ab61b-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="ab61b-145">Det är enkelt att ta bort en Windows PowerShell-enhet, men du kan inte ta bort den när du befinner dig i enheten.</span><span class="sxs-lookup"><span data-stu-id="ab61b-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="ab61b-146">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="ab61b-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="ab61b-147">Lägga till och ta bort enheter utanför Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab61b-147">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="ab61b-148">Windows PowerShell identifierar fil Systems enheter som läggs till eller tas bort i Windows, inklusive nätverks enheter som är mappade, USB-enheter som är anslutna och enheter som tas bort med hjälp av kommandot **net use** eller metoden **wscript. NetworkMapNetworkDrive** och **RemoveNetworkDrive** från ett Windows Script Host-skript (WSH).</span><span class="sxs-lookup"><span data-stu-id="ab61b-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>
