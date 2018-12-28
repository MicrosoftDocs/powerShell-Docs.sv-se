---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Använd autentiseringsuppgifter med DSC-resurser
ms.openlocfilehash: af54c286ce744cd7db0b0e2d05087f60cdf1a33c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405207"
---
# <a name="use-credentials-with-dsc-resources"></a>Använd autentiseringsuppgifter med DSC-resurser

> Gäller för: Windows PowerShell 5.0, Windows PowerShell 5.1

Du kan köra en DSC-resurs under en angiven uppsättning autentiseringsuppgifter med hjälp av automatiskt **PsDscRunAsCredential** -egenskapen i konfigurationen.
Som standard körs DSC varje resurs som system-kontot.
Det finns tillfällen när körs som en användare är nödvändigt, till exempel installera MSI-paket i kontexten för en viss användare, ställa in en användares registernycklar, åtkomst till en användares specifika lokal katalog eller tillgång till ett nätverk delar.

Alla DSC-resurser har en **PsDscRunAsCredential** egenskapen som kan ställas in att alla användarens autentiseringsuppgifter (en [PSCredential](/dotnet/api/system.management.automation.pscredential) objekt).
Autentiseringsuppgifterna kan vara hårdkodade som värde för egenskapen i konfigurationen, eller du kan ange värdet [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), som kommer frågar användaren om autentiseringsuppgifter när konfigurationen kompileras (för information om Kompilera konfigurationer finns i [konfigurationer](configurations.md).

> [!NOTE]
> I PowerShell 5.0, med hjälp av den **PsDscRunAsCredential** -egenskapen i konfigurationer som anropar sammansatta resurser stöds inte.
> I PowerShell 5.1 den **PsDscRunAsCredential** egenskapen stöds i konfigurationer som anropar sammansatta resurser.
> Den **PsDscRunAsCredential** egenskapen är inte tillgänglig i PowerShell 4.0.

I följande exempel `Get-Credential` används för att fråga användaren om autentiseringsuppgifter.
Den **registret** resursen används för att ändra den registernyckel som anger bakgrundsfärgen för Windows-Kommandotolken.

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
> Det här exemplet förutsätter att du har ett giltigt certifikat i `C:\publicKeys\targetNode.cer`, och att tumavtrycket för certifikatet är värdet som visas.
> Information om hur du krypterar autentiseringsuppgifterna i MOF-filer för DSC-konfiguration finns i [skydda MOF-filen](../pull-server/secureMOF.md).
