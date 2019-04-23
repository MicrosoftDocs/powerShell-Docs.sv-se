---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Hantera Windows PowerShell-enheter
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: 9ac5136fb28b450ea6397cab2f36082c50f22e1f
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984280"
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="91089-103">Hantera Windows PowerShell-enheter</span><span class="sxs-lookup"><span data-stu-id="91089-103">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="91089-104">En *Windows PowerShell-enhet* är en lagringsplats för data som du har åtkomst till som en filsystemets enhet på Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91089-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="91089-105">Windows PowerShell-providers skapa vissa enheter för dig, som filsystemet enheter (inklusive C: och D:), registret enheter (HKCU: och HKLM:), och den certifikat-enheten (Cert:), och du kan skapa egna Windows PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="91089-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="91089-106">Dessa enheter är mycket användbara, men de är tillgängliga i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91089-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="91089-107">Du kan inte komma åt dem från andra Windows-verktyg, till exempel Utforskaren eller Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="91089-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="91089-108">Windows PowerShell använder substantiv, **PSDrive**, för kommandona som fungerar med Windows PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="91089-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="91089-109">En lista med Windows PowerShell-enheter i Windows PowerShell-sessionen, använda den **Get-PSDrive** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91089-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

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

<span data-ttu-id="91089-110">Även om enheterna i visningen variera med enheter på datorn, på listan ser ut ungefär som utdata från den **Get-PSDrive** kommandot ovan.</span><span class="sxs-lookup"><span data-stu-id="91089-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="91089-111">Enheter är en delmängd av Windows PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="91089-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="91089-112">Du kan identifiera filen systemenheter av filsystem posten i kolumnen providern.</span><span class="sxs-lookup"><span data-stu-id="91089-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="91089-113">(Filen systemenheter i Windows PowerShell stöds av filsystem för Windows PowerShell-providern.)</span><span class="sxs-lookup"><span data-stu-id="91089-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="91089-114">Se syntaxen för den **Get-PSDrive** cmdlet, ange ett **Get-Command** med den **Syntax** parameter:</span><span class="sxs-lookup"><span data-stu-id="91089-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="91089-115">Den **PSProvider** parametern kan du visa endast i Windows PowerShell-enheter som stöds av en viss provider.</span><span class="sxs-lookup"><span data-stu-id="91089-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="91089-116">För att visa endast de Windows PowerShell-enheter som stöds av filsystem för Windows PowerShell-providern, exempelvis en **Get-PSDrive** med den **PSProvider** parametern och  **Filsystem** värde:</span><span class="sxs-lookup"><span data-stu-id="91089-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="91089-117">Du kan visa de Windows PowerShell-enheter som representerar registreringsdatafilerna den **PSProvider** att visa endast i Windows PowerShell-enheter som stöds av registerprovidern för Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="91089-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="91089-118">Du kan också använda standard-plats-cmdlets med Windows PowerShell-enheter:</span><span class="sxs-lookup"><span data-stu-id="91089-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="91089-119">Att lägga till nya Windows PowerShell-enheter (ny PSDrive)</span><span class="sxs-lookup"><span data-stu-id="91089-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="91089-120">Du kan lägga till egna Windows PowerShell-enheter med hjälp av den **New PSDrive** kommando.</span><span class="sxs-lookup"><span data-stu-id="91089-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="91089-121">Som hämtar syntaxen för den **New-PSDrive** kommandot, ange den **Get-Command** med den **Syntax** parameter:</span><span class="sxs-lookup"><span data-stu-id="91089-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="91089-122">Om du vill skapa en ny Windows PowerShell-enhet, måste du ange tre parametrar:</span><span class="sxs-lookup"><span data-stu-id="91089-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="91089-123">Ett namn för enheten (du kan använda valfritt giltigt namn för Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="91089-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="91089-124">PSProvider (Använd ”filsystem” i sökvägar för system och ”registret” för registret platser)</span><span class="sxs-lookup"><span data-stu-id="91089-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="91089-125">Roten, det vill säga sökväg till roten i den nya enheten</span><span class="sxs-lookup"><span data-stu-id="91089-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="91089-126">Du kan till exempel skapa en enhet med namnet ”Office” som är mappad till den mapp som innehåller Microsoft Office-program på datorn, till exempel **C:\\programfiler\\Microsoft Office\\OFFICE11**.</span><span class="sxs-lookup"><span data-stu-id="91089-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="91089-127">För att skapa enheten, skriver du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="91089-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="91089-128">I allmänhet är sökvägar inte skiftlägeskänsliga.</span><span class="sxs-lookup"><span data-stu-id="91089-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="91089-129">Du refererar till den nya Windows PowerShell-enheten som du gör att alla enheter i Windows PowerShell - efter dess namn följt av ett kolon (**:**).</span><span class="sxs-lookup"><span data-stu-id="91089-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="91089-130">En Windows PowerShell-enhet kan göra många av de uppgifter som är mycket enklare.</span><span class="sxs-lookup"><span data-stu-id="91089-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="91089-131">Till exempel ha några av de viktigaste nycklarna i Windows-registret extremt långa sökvägar, vilket gör dem krånglig att åtkomst och svårt att komma ihåg.</span><span class="sxs-lookup"><span data-stu-id="91089-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="91089-132">Viktig konfigurationsinformation finns **HKEY_LOCAL_MACHINE\\programvara\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="91089-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="91089-133">Om du vill visa och ändra objekt i registernyckeln CurrentVersion, kan du skapa en Windows PowerShell-enhet är rotad i nyckeln genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="91089-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="91089-134">Du kan ändra platsen till den **cvkey:** enhet precis som alla andra enheter:''</span><span class="sxs-lookup"><span data-stu-id="91089-134">You can then change location to the **cvkey:** drive as you would any other drive:\`\`</span></span>

`PS> cd cvkey:`

<span data-ttu-id="91089-135">eller:</span><span class="sxs-lookup"><span data-stu-id="91089-135">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="91089-136">Cmdleten New-PsDrive lägger till den nya enheten endast till den aktuella Windows PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="91089-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="91089-137">Om du stänger Windows PowerShell-fönstret, går den nya enheten förlorad.</span><span class="sxs-lookup"><span data-stu-id="91089-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="91089-138">Använda cmdleten Export-konsolen för att exportera den aktuella Windows PowerShell-sessionen för att spara en Windows PowerShell-enhet, och sedan använda PowerShell.exe **PSConsoleFile** parameter för att importera den.</span><span class="sxs-lookup"><span data-stu-id="91089-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="91089-139">Eller Lägg till den nya enheten i din profil för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91089-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="91089-140">Tar bort Windows PowerShell-enheter (Remove-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="91089-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="91089-141">Du kan ta bort enheter från Windows PowerShell med hjälp av den **Remove-PSDrive** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91089-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="91089-142">Den **Remove-PSDrive** cmdlet är lätt att använda; om du vill ta bort en specifik Windows PowerShell-enhet måste du bara ange enhetsnamnet för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91089-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="91089-143">Exempel: Om du har lagt till den **Office:** Windows PowerShell-enhet, enligt den **New PSDrive** avsnittet, kan du radera den genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="91089-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="91089-144">Att ta bort den **cvkey:** Windows PowerShell enhet, även visas i den **New PSDrive** avsnittet använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="91089-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="91089-145">Det är enkelt att ta bort en Windows PowerShell-enhet, men du kan inte ta bort den när du arbetar med enheten.</span><span class="sxs-lookup"><span data-stu-id="91089-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="91089-146">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="91089-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="91089-147">Att lägga till och ta bort enheter utanför Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="91089-147">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="91089-148">Windows PowerShell identifierar enheter som läggs till eller tas bort i Windows, inklusive nätverksenheter som är mappade, USB-enheter som är anslutna och enheter som har tagits bort genom att använda antingen den **nätverksanv** kommando eller  **WScript.NetworkMapNetworkDrive** och **RemoveNetworkDrive** metoder från ett skript för Windows Script Host (WSH).</span><span class="sxs-lookup"><span data-stu-id="91089-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>