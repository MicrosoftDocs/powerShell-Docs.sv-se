---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
title: Kända problem i WMF 5.1
ms.openlocfilehash: 467a191f40d85bfca7c794915d6274a9a1b201e7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="e7343-103">Kända problem i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="e7343-103">Known Issues in WMF 5.1</span></span> #

> <span data-ttu-id="e7343-104">Obs: Den här informationen kan ändras.</span><span class="sxs-lookup"><span data-stu-id="e7343-104">Note: This information is subject to change.</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="e7343-105">Startar genvägen PowerShell som administratör</span><span class="sxs-lookup"><span data-stu-id="e7343-105">Starting PowerShell shortcut as Administrator</span></span>
<span data-ttu-id="e7343-106">Om du försöker starta PowerShell som administratör från genvägen när installeras WMF kan du få ett ”okänt fel”-meddelande.</span><span class="sxs-lookup"><span data-stu-id="e7343-106">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span>
<span data-ttu-id="e7343-107">Öppna en genväg som icke-administratör och genvägen nu fungerar även som administratör.</span><span class="sxs-lookup"><span data-stu-id="e7343-107">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="e7343-108">Lära</span><span class="sxs-lookup"><span data-stu-id="e7343-108">Pester</span></span>
<span data-ttu-id="e7343-109">Det finns två saker du bör vara medveten om när du använder Pester på Nano Server i den här versionen:</span><span class="sxs-lookup"><span data-stu-id="e7343-109">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

* <span data-ttu-id="e7343-110">Kör tester mot Pester själva kan resultera i några fel på grund av skillnader mellan fullständig CLR och CORE CLR.</span><span class="sxs-lookup"><span data-stu-id="e7343-110">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="e7343-111">I synnerhet är Validate-metoden inte tillgänglig i XmlDocument-typen.</span><span class="sxs-lookup"><span data-stu-id="e7343-111">In particular, the Validate method is not available on the XmlDocument type.</span></span> <span data-ttu-id="e7343-112">Sex tester som försöker verifiera schemat NUnit utdata loggar är känt att misslyckas.</span><span class="sxs-lookup"><span data-stu-id="e7343-112">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
* <span data-ttu-id="e7343-113">En kod täckning testet misslyckas för tillfället eftersom den *WindowsFeature* DSC-resursen finns inte i Nano Server.</span><span class="sxs-lookup"><span data-stu-id="e7343-113">One Code Coverage test fails currently because the *WindowsFeature* DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="e7343-114">Dessa fel är vanligtvis ofarlig och ignoreras.</span><span class="sxs-lookup"><span data-stu-id="e7343-114">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="e7343-115">Validering av Distributionsåtgärden</span><span class="sxs-lookup"><span data-stu-id="e7343-115">Operation Validation</span></span>

* <span data-ttu-id="e7343-116">Update-Help misslyckas för Microsoft.PowerShell.Operation.Validation modulen på grund av icke-fungerande hjälp URI</span><span class="sxs-lookup"><span data-stu-id="e7343-116">Update-Help fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="e7343-117">DSC efter avinstallera WMF</span><span class="sxs-lookup"><span data-stu-id="e7343-117">DSC after uninstall WMF</span></span>
* <span data-ttu-id="e7343-118">Avinstallera WMF tar inte bort DSC MOF dokument från konfigurationsmappen.</span><span class="sxs-lookup"><span data-stu-id="e7343-118">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="e7343-119">DSC fungerar inte korrekt om MOF-dokument innehåller nyare egenskaper som inte är tillgängliga på äldre system.</span><span class="sxs-lookup"><span data-stu-id="e7343-119">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="e7343-120">Kör följande skript i det här fallet från upphöjd PowerShell-konsolen för att rensa DSC-tillstånd.</span><span class="sxs-lookup"><span data-stu-id="e7343-120">In this case, run the following script from elevated PowerShell console to to clean up the DSC states.</span></span>
 ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="e7343-121">JEA virtuella konton</span><span class="sxs-lookup"><span data-stu-id="e7343-121">JEA Virtual Accounts</span></span>
<span data-ttu-id="e7343-122">JEA slutpunkter och sessionskonfigurationer som konfigurerats för att använda virtuella konton i WMF 5.0 konfigureras inte för att använda ett virtuellt konto när du har uppgraderat till WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="e7343-122">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span>
<span data-ttu-id="e7343-123">Det innebär att kommandon som körs i JEA sessioner kommer att köras under den anslutande användarens identitet i stället för ett tillfälligt administratörskonto potentiellt hindrar användaren från att köra kommandon som kräver utökade privilegier.</span><span class="sxs-lookup"><span data-stu-id="e7343-123">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span>
<span data-ttu-id="e7343-124">Om du vill återställa de virtuella kontona, måste du avregistrera och registrera alla sessionskonfigurationer som använder virtuella konton.</span><span class="sxs-lookup"><span data-stu-id="e7343-124">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```