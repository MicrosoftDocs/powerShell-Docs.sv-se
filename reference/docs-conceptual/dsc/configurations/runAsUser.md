---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Använda autentiseringsuppgifter med DSC-resurser
ms.openlocfilehash: fea2e3cad8d081c17853e127203f1d40d98c5de2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941966"
---
# <a name="use-credentials-with-dsc-resources"></a>Använda autentiseringsuppgifter med DSC-resurser

> Gäller för: Windows PowerShell 5,0, Windows PowerShell 5,1

Du kan köra en DSC-resurs under en angiven uppsättning autentiseringsuppgifter genom att använda den automatiska **PsDscRunAsCredential** -egenskapen i konfigurationen. Som standard kör DSC varje resurs som system konto. Det finns tillfällen när det är nödvändigt att köra som en användare, till exempel att installera MSI-paket i en speciell användar kontext, ange en användares register nycklar, komma åt en användares lokala katalog eller åtkomst till en nätverks resurs. **SeInteractiveLogonRight** krävs av mål datorn för alla konton som du anger som **PSDSCRunAsCredential**. Mer information finns i [konto rättigheter konstanter](/windows/desktop/secauthz/account-rights-constants).

Varje DSC-resurs har en **PsDscRunAsCredential** -egenskap som kan anges till alla användarautentiseringsuppgifter (ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt). Autentiseringsuppgiften kan vara hårdkodad som värde för egenskapen i konfigurationen eller så kan du ställa in värdet för att [Hämta Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), vilket kommer att uppmana användaren att ange autentiseringsuppgifter när konfigurationen kompileras (information om hur du kompilerar konfigurationer finns i [konfigurationer](configurations.md).

> [!NOTE]
> I PowerShell 5,0 stöds inte användning av egenskapen **PsDscRunAsCredential** i konfigurationer som anropar sammansatta resurser. I PowerShell 5,1 stöds egenskapen **PsDscRunAsCredential** i konfigurationer som anropar sammansatta resurser. Egenskapen **PsDscRunAsCredential** är inte tillgänglig i PowerShell 4,0.

I följande exempel `Get-Credential` används för att uppmana användaren att ange autentiseringsuppgifter. **Register** resursen används för att ändra register nyckeln som anger bakgrunds färgen för kommando tolks fönstret i Windows.

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
> I det här exemplet förutsätts att du har ett `C:\publicKeys\targetNode.cer`giltigt certifikat vid och att tumavtrycket för certifikatet är det värde som visas. Information om hur du krypterar autentiseringsuppgifter i MOF-filer för DSC-konfiguration finns i [skydda MOF-filen](../pull-server/secureMOF.md).
