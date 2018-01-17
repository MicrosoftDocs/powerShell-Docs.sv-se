---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Ange beroenden mellan noder
ms.openlocfilehash: f4411161d819d96803f57600646409d5bfe827b9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="specifying-cross-node-dependencies"></a>Ange beroenden mellan noder

> Gäller för: Windows PowerShell 5.0

DSC innehåller särskilda resurser **WaitForAll**, **WaitForAny**, och **WaitForSome** som kan användas i konfigurationerna för att ange beroenden på konfigurationer på andra noder. Beteendet för dessa resurser är följande:

* **WaitForAll**: lyckas om den angivna resursen är i tillståndet önskade på alla målnoder som definierats i den **nodnamn** egenskapen.
* **WaitForAny**: lyckas om den angivna resursen är i tillståndet önskade på minst en av målnoder som definierats i den **nodnamn** egenskapen.
* **WaitForSome**: Anger en **NodeCount** egenskapen förutom en **nodnamn** egenskapen. Resursen lyckas om resursen är i ett minsta antal noder önskade tillstånd (anges av **NodeCount**) definieras av den **nodnamn** egenskapen. 

## <a name="using-waitforxxxx-resources"></a>Använda WaitForXXXX resurser

Att använda den **WaitForXXXX** resurser, som du skapar en resurs block på den resurstyp som anger DSC-resurs och noderna vänta. Du sedan använda den **DependsOn** egenskap i någon annan resurs blockerar i konfigurationen för de villkor som anges i den **WaitForXXXX** noden ska lyckas.

Till exempel i följande konfiguration målnoden väntar på den **xADDomain** resurs till slut på den **MyDC** nod med maximalt antal 30 återförsök, med 15 sekunder intervall, innan den målnoden kan ansluta till domänen.

```powershell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present' 
            Name = 'AD-Domain-Services' 
        }

        xADDomain NewDomain 
        { 
            DomainName = 'Contoso.com'            
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }

    }

    Node myDomainJoinedServer
    {

        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

>**Obs:** som standard WaitForXXX resurser försök en gång och sedan inte. Även om det inte krävs, vill du förmodligen ange återförsöksintervall och count.

## <a name="see-also"></a>Se även
* [DSC-konfigurationer](configurations.md)
* [DSC-resurser](resources.md)
* [Konfigurera den lokala Configuration Manager](metaConfig.md)

