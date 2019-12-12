---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Kända problem i WMF 5.1
ms.openlocfilehash: 8348f9d45dca32dcda2ef8baa75d586c8728d0a4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71145280"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="a86df-103">Kända problem i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="a86df-103">Known Issues in WMF 5.1</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="a86df-104">Startar PowerShell-genväg som administratör</span><span class="sxs-lookup"><span data-stu-id="a86df-104">Starting PowerShell shortcut as Administrator</span></span>

<span data-ttu-id="a86df-105">Vid installation av WMF, om du försöker starta PowerShell som administratör från genvägen, kan det hända att meddelandet "Ospecificerat fel" visas.</span><span class="sxs-lookup"><span data-stu-id="a86df-105">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span> <span data-ttu-id="a86df-106">Öppna genvägen igen som icke-administratör och genvägen fungerar nu även som administratör.</span><span class="sxs-lookup"><span data-stu-id="a86df-106">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="a86df-107">Pester</span><span class="sxs-lookup"><span data-stu-id="a86df-107">Pester</span></span>

<span data-ttu-id="a86df-108">I den här versionen finns det två problem som du bör känna till när du använder pester på Nano Server:</span><span class="sxs-lookup"><span data-stu-id="a86df-108">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

- <span data-ttu-id="a86df-109">Att köra tester mot pester kan leda till problem på grund av skillnader mellan fullständig CLR och CORE CLR.</span><span class="sxs-lookup"><span data-stu-id="a86df-109">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="a86df-110">I synnerhet är **validate** -metoden inte tillgänglig för typen **XMLDocument** .</span><span class="sxs-lookup"><span data-stu-id="a86df-110">In particular, the **Validate** method is not available on the **XmlDocument** type.</span></span> <span data-ttu-id="a86df-111">Sex tester som försöker validera schemat för NUnit-utgående loggar är kända för att Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="a86df-111">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
- <span data-ttu-id="a86df-112">Ett kod täcknings test Miss lyckas eftersom **WindowsFeature** DSC-resursen inte finns i Nano Server.</span><span class="sxs-lookup"><span data-stu-id="a86df-112">One code coverage test fails because the **WindowsFeature** DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="a86df-113">Dessa problem är dock i allmänhet ofarliga och kan ignoreras på ett säkert sätt.</span><span class="sxs-lookup"><span data-stu-id="a86df-113">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="a86df-114">Åtgärds validering</span><span class="sxs-lookup"><span data-stu-id="a86df-114">Operation Validation</span></span>

- <span data-ttu-id="a86df-115">`Update-Help` Miss lyckas för Microsoft. PowerShell. operation. Validation-modulen på grund av en icke fungerande hjälp-URI</span><span class="sxs-lookup"><span data-stu-id="a86df-115">`Update-Help` fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="a86df-116">DSC efter avinstallation av WMF</span><span class="sxs-lookup"><span data-stu-id="a86df-116">DSC after uninstall WMF</span></span>

- <span data-ttu-id="a86df-117">Om du avinstallerar WMF raderas inte DSC MOF-dokument från mappen konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a86df-117">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="a86df-118">DSC fungerar inte korrekt om MOF-dokumenten innehåller nyare egenskaper som inte är tillgängliga på äldre system.</span><span class="sxs-lookup"><span data-stu-id="a86df-118">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="a86df-119">I det här fallet kör du följande skript från upphöjd PowerShell-konsolen för att rensa DSC-tillstånd.</span><span class="sxs-lookup"><span data-stu-id="a86df-119">In this case, run the following script from elevated PowerShell console to clean up the DSC states.</span></span>

  ```powershell
  $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
    "$env:windir\system32\configuration\*.mof.checksum",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
  )
  $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="a86df-120">Virtuella JEA-konton</span><span class="sxs-lookup"><span data-stu-id="a86df-120">JEA Virtual Accounts</span></span>

<span data-ttu-id="a86df-121">JEA-slutpunkter och sessionsinställningar som kon figurer ATS för att använda virtuella konton i WMF 5,0 kommer inte att konfigureras att använda ett virtuellt konto efter uppgraderingen till WMF 5,1.</span><span class="sxs-lookup"><span data-stu-id="a86df-121">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span> <span data-ttu-id="a86df-122">Det innebär att kommandon som körs i JEA-sessioner körs under den anslutna användarens identitet i stället för ett tillfälligt administratörs konto, vilket kan hindra användaren från att köra kommandon som kräver förhöjd behörighet.</span><span class="sxs-lookup"><span data-stu-id="a86df-122">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span> <span data-ttu-id="a86df-123">Om du vill återställa de virtuella kontona måste du avregistrera och registrera om alla användarsessioner som använder virtuella konton.</span><span class="sxs-lookup"><span data-stu-id="a86df-123">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

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