---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Kör DSC med autentiseringsuppgifterna för användaren"
ms.openlocfilehash: f15b2e4bfb888e2f3646a33cc0191e33a7ebb8ab
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="running-dsc-with-user-credentials"></a><span data-ttu-id="6472f-103">Kör DSC med autentiseringsuppgifterna för användaren</span><span class="sxs-lookup"><span data-stu-id="6472f-103">Running DSC with user credentials</span></span> 

> <span data-ttu-id="6472f-104">Gäller för: Windows PowerShell 5.0, 5.1 för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6472f-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="6472f-105">Du kan köra en DSC-resurs under en angiven uppsättning autentiseringsuppgifter med hjälp av automatiskt **PsDscRunAsCredential** egenskap i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6472f-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="6472f-106">Som standard körs DSC varje resurs som system-kontot.</span><span class="sxs-lookup"><span data-stu-id="6472f-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="6472f-107">Det finns tillfällen när körs som en användare är nödvändigt, till exempel installera MSI-paket i en specifik användarkontext, ställa in en användares registernycklar, åtkomst till en användarens specifika lokala katalog eller tillgång till ett nätverk delar.</span><span class="sxs-lookup"><span data-stu-id="6472f-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="6472f-108">Varje DSC-resursen har en **PsDscRunAsCredential** egenskap som kan anges till alla autentiseringsuppgifter (en [PSCredential](https://msdn.microsoft.com/en-us/library/ms572524(v=VS.85).aspx) objekt).</span><span class="sxs-lookup"><span data-stu-id="6472f-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](https://msdn.microsoft.com/en-us/library/ms572524(v=VS.85).aspx) object).</span></span>
<span data-ttu-id="6472f-109">Autentiseringsuppgifter kan vara hårdkodad som värde för egenskapen i konfigurationen eller du kan ange värdet [Get-Credential](https://technet.microsoft.com/en-us/library/hh849815.aspx), som kommer uppmana användaren att ange autentiseringsuppgifter när konfigurationen kompileras (för information om Kompilera konfigurationer finns [konfigurationer](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="6472f-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](https://technet.microsoft.com/en-us/library/hh849815.aspx), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

><span data-ttu-id="6472f-110">**Obs:** i PowerShell 5.0, med hjälp av den **PsDscRunAsCredential** egenskap i konfigurationer som anropar sammansatta resurser stöds inte.</span><span class="sxs-lookup"><span data-stu-id="6472f-110">**Note:** In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> 
><span data-ttu-id="6472f-111">I PowerShell 5.1 den **PsDscRunAsCredential** egenskapen stöds i konfigurationer som anropar sammansatta resurser.</span><span class="sxs-lookup"><span data-stu-id="6472f-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>

><span data-ttu-id="6472f-112">**Obs:** den **PsDscRunAsCredential** egenskapen är inte tillgänglig i PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="6472f-112">**Note:** The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="6472f-113">I följande exempel **Get-Credential** används för att uppmana användaren att ange autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="6472f-113">In the following example, **Get-Credential** is used to prompt the user for credentials.</span></span> <span data-ttu-id="6472f-114">Den [registret](registryResource.md) resursen används för att ändra den registernyckel som anger bakgrundsfärgen för Windows-kommandotolksfönster.</span><span class="sxs-lookup"><span data-stu-id="6472f-114">The [Registry](registryResource.md) resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
><span data-ttu-id="6472f-115">**Obs:** det här exemplet förutsätter att du har ett giltigt certifikat i `C:\publicKeys\targetNode.cer`, och att tumavtrycket för certifikatet är värdet som visas.</span><span class="sxs-lookup"><span data-stu-id="6472f-115">**Note:** This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
><span data-ttu-id="6472f-116">Information om hur du krypterar autentiseringsuppgifter i MOF-filer för DSC-konfigurationen finns [skydda MOF-filen](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="6472f-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](secureMOF.md).</span></span>

