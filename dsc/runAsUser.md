---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Köra DSC med autentiseringsuppgifterna för användaren
ms.openlocfilehash: 37e6ff64c9c6d3960653d417e22a6c93c653230c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="running-dsc-with-user-credentials"></a>Köra DSC med autentiseringsuppgifterna för användaren

> Gäller för: Windows PowerShell 5.0, 5.1 för Windows PowerShell

Du kan köra en DSC-resurs under en angiven uppsättning autentiseringsuppgifter med hjälp av automatiskt **PsDscRunAsCredential** egenskap i konfigurationen.
Som standard körs DSC varje resurs som system-kontot.
Det finns tillfällen när körs som en användare är nödvändigt, till exempel installera MSI-paket i en specifik användarkontext, ställa in en användares registernycklar, åtkomst till en användarens specifika lokala katalog eller tillgång till ett nätverk delar.

Varje DSC-resursen har en **PsDscRunAsCredential** egenskap som kan anges till alla autentiseringsuppgifter (en [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx) objekt).
Autentiseringsuppgifter kan vara hårdkodad som värde för egenskapen i konfigurationen eller du kan ange värdet [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), som kommer uppmana användaren att ange autentiseringsuppgifter när konfigurationen kompileras (för information om Kompilera konfigurationer finns [konfigurationer](configurations.md).

>**Obs:** i PowerShell 5.0, med hjälp av den **PsDscRunAsCredential** egenskap i konfigurationer som anropar sammansatta resurser stöds inte.
>I PowerShell 5.1 den **PsDscRunAsCredential** egenskapen stöds i konfigurationer som anropar sammansatta resurser.

>**Obs:** den **PsDscRunAsCredential** egenskapen är inte tillgänglig i PowerShell 4.0.

I följande exempel **Get-Credential** används för att uppmana användaren att ange autentiseringsuppgifter.
Den [registret](registryResource.md) resursen används för att ändra den registernyckel som anger bakgrundsfärgen för Windows-kommandotolksfönster.

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
>**Obs:** det här exemplet förutsätter att du har ett giltigt certifikat i `C:\publicKeys\targetNode.cer`, och att tumavtrycket för certifikatet är värdet som visas.
>Information om hur du krypterar autentiseringsuppgifter i MOF-filer för DSC-konfigurationen finns [skydda MOF-filen](secureMOF.md).