---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Använda autentiseringsuppgifter med DSC-resurser
ms.openlocfilehash: af54c286ce744cd7db0b0e2d05087f60cdf1a33c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686854"
---
# <a name="use-credentials-with-dsc-resources"></a><span data-ttu-id="ec590-103">Använda autentiseringsuppgifter med DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="ec590-103">Use Credentials with DSC Resources</span></span>

> <span data-ttu-id="ec590-104">Gäller för: Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="ec590-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="ec590-105">Du kan köra en DSC-resurs under en angiven uppsättning autentiseringsuppgifter med hjälp av automatiskt **PsDscRunAsCredential** -egenskapen i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="ec590-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span>
<span data-ttu-id="ec590-106">Som standard körs DSC varje resurs som system-kontot.</span><span class="sxs-lookup"><span data-stu-id="ec590-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="ec590-107">Det finns tillfällen när körs som en användare är nödvändigt, till exempel installera MSI-paket i kontexten för en viss användare, ställa in en användares registernycklar, åtkomst till en användares specifika lokal katalog eller tillgång till ett nätverk delar.</span><span class="sxs-lookup"><span data-stu-id="ec590-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="ec590-108">Alla DSC-resurser har en **PsDscRunAsCredential** egenskapen som kan ställas in att alla användarens autentiseringsuppgifter (en [PSCredential](/dotnet/api/system.management.automation.pscredential) objekt).</span><span class="sxs-lookup"><span data-stu-id="ec590-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span></span>
<span data-ttu-id="ec590-109">Autentiseringsuppgifterna kan vara hårdkodade som värde för egenskapen i konfigurationen, eller du kan ange värdet [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), som kommer frågar användaren om autentiseringsuppgifter när konfigurationen kompileras (för information om Kompilera konfigurationer finns i [konfigurationer](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="ec590-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ec590-110">I PowerShell 5.0, med hjälp av den **PsDscRunAsCredential** -egenskapen i konfigurationer som anropar sammansatta resurser stöds inte.</span><span class="sxs-lookup"><span data-stu-id="ec590-110">In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span>
> <span data-ttu-id="ec590-111">I PowerShell 5.1 den **PsDscRunAsCredential** egenskapen stöds i konfigurationer som anropar sammansatta resurser.</span><span class="sxs-lookup"><span data-stu-id="ec590-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>
> <span data-ttu-id="ec590-112">Den **PsDscRunAsCredential** egenskapen är inte tillgänglig i PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="ec590-112">The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="ec590-113">I följande exempel `Get-Credential` används för att fråga användaren om autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="ec590-113">In the following example, `Get-Credential` is used to prompt the user for credentials.</span></span>
<span data-ttu-id="ec590-114">Den **registret** resursen används för att ändra den registernyckel som anger bakgrundsfärgen för Windows-Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="ec590-114">The **Registry** resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```

> [!NOTE]
> <span data-ttu-id="ec590-115">Det här exemplet förutsätter att du har ett giltigt certifikat i `C:\publicKeys\targetNode.cer`, och att tumavtrycket för certifikatet är värdet som visas.</span><span class="sxs-lookup"><span data-stu-id="ec590-115">This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
> <span data-ttu-id="ec590-116">Information om hur du krypterar autentiseringsuppgifterna i MOF-filer för DSC-konfiguration finns i [skydda MOF-filen](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="ec590-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>
