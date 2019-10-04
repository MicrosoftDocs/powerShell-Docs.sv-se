---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Använda autentiseringsuppgifter med DSC-resurser
ms.openlocfilehash: fea2e3cad8d081c17853e127203f1d40d98c5de2
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941966"
---
# <a name="use-credentials-with-dsc-resources"></a><span data-ttu-id="a1b70-103">Använda autentiseringsuppgifter med DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="a1b70-103">Use Credentials with DSC Resources</span></span>

> <span data-ttu-id="a1b70-104">Gäller för: Windows PowerShell 5,0, Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="a1b70-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="a1b70-105">Du kan köra en DSC-resurs under en angiven uppsättning autentiseringsuppgifter genom att använda den automatiska **PsDscRunAsCredential** -egenskapen i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a1b70-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="a1b70-106">Som standard kör DSC varje resurs som system konto.</span><span class="sxs-lookup"><span data-stu-id="a1b70-106">By default, DSC runs each resource as the system account.</span></span> <span data-ttu-id="a1b70-107">Det finns tillfällen när det är nödvändigt att köra som en användare, till exempel att installera MSI-paket i en speciell användar kontext, ange en användares register nycklar, komma åt en användares lokala katalog eller åtkomst till en nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="a1b70-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span> <span data-ttu-id="a1b70-108">**SeInteractiveLogonRight** krävs av mål datorn för alla konton som du anger som **PSDSCRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="a1b70-108">The **SeInteractiveLogonRight** is required, by the target machine, for any account you specify to **PSDSCRunAsCredential**.</span></span> <span data-ttu-id="a1b70-109">Mer information finns i [konto rättigheter konstanter](/windows/desktop/secauthz/account-rights-constants).</span><span class="sxs-lookup"><span data-stu-id="a1b70-109">For more information, see [Account Rights Constants](/windows/desktop/secauthz/account-rights-constants).</span></span>

<span data-ttu-id="a1b70-110">Varje DSC-resurs har en **PsDscRunAsCredential** -egenskap som kan anges till alla användarautentiseringsuppgifter (ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt).</span><span class="sxs-lookup"><span data-stu-id="a1b70-110">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span></span> <span data-ttu-id="a1b70-111">Autentiseringsuppgiften kan vara hårdkodad som värde för egenskapen i konfigurationen, eller så kan du ställa in värdet för att [Hämta autentiseringsuppgifter](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), vilket kommer att uppmana användaren att ange autentiseringsuppgifter när konfigurationen kompileras (för information om kompilering av konfigurationer). Se [konfigurationer](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="a1b70-111">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a1b70-112">I PowerShell 5,0 stöds inte användning av egenskapen **PsDscRunAsCredential** i konfigurationer som anropar sammansatta resurser.</span><span class="sxs-lookup"><span data-stu-id="a1b70-112">In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> <span data-ttu-id="a1b70-113">I PowerShell 5,1 stöds egenskapen **PsDscRunAsCredential** i konfigurationer som anropar sammansatta resurser.</span><span class="sxs-lookup"><span data-stu-id="a1b70-113">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span> <span data-ttu-id="a1b70-114">Egenskapen **PsDscRunAsCredential** är inte tillgänglig i PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="a1b70-114">The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="a1b70-115">I följande exempel används `Get-Credential` för att uppmana användaren att ange autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="a1b70-115">In the following example, `Get-Credential` is used to prompt the user for credentials.</span></span> <span data-ttu-id="a1b70-116">**Register** resursen används för att ändra register nyckeln som anger bakgrunds färgen för kommando tolks fönstret i Windows.</span><span class="sxs-lookup"><span data-stu-id="a1b70-116">The **Registry** resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
> <span data-ttu-id="a1b70-117">I det här exemplet förutsätts att du har ett giltigt certifikat på `C:\publicKeys\targetNode.cer` och att tumavtrycket för certifikatet är det värde som visas.</span><span class="sxs-lookup"><span data-stu-id="a1b70-117">This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span> <span data-ttu-id="a1b70-118">Information om hur du krypterar autentiseringsuppgifter i MOF-filer för DSC-konfiguration finns i [skydda MOF-filen](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="a1b70-118">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>
