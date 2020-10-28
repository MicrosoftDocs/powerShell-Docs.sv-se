---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Konfigurera en virtuell dator vid första uppstart med hjälp av DSC
description: Den här artikeln explans hur du konfigurerar en virtuell dator vid första uppstarten med DSC
ms.openlocfilehash: 9fa8c4a21486aaef87e1c0a3097e5983a378d98d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656195"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>Konfigurera en virtuell dator vid första uppstart med hjälp av DSC

> [!IMPORTANT]
> Gäller för: Windows PowerShell 5,0

## <a name="requirements"></a>Krav

> [!NOTE]
> Register nyckeln **dscautomationhostenabled registernyckel** som beskrivs i det här avsnittet är inte tillgänglig i PowerShell 4,0. Information om hur du konfigurerar nya virtuella datorer vid första uppstart i PowerShell 4,0 finns i [vill konfigurera dina datorer automatiskt med DSC vid första uppstarten?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

Om du vill köra de här exemplen behöver du:

- En startbar virtuell hård disk att arbeta med. Du kan ladda ned en ISO-fil med en utvärderings version av Windows Server 2016 på [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016).
  Du hittar instruktioner om hur du skapar en virtuell hård disk från en ISO-avbildning vid [skapande av startbara virtuella hård diskar](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).
- En värddator som har Hyper-V aktiverat. Mer information finns i [Översikt över Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).

  Genom att använda DSC kan du automatisera program varu installation och konfiguration för en dator vid första uppstarten. Du gör detta genom att antingen mata in ett MOF-dokument eller en metaconfiguration till startbara media (till exempel en virtuell hård disk) så att de körs under den första start processen. Det här beteendet anges i register nyckeln register [nyckeln dscautomationhostenabled registernyckel](DSCAutomationHostEnabled.md) under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` .
  Som standard är värdet för den här nyckeln 2, vilket tillåter DSC att köras vid start.

  Om du inte vill att DSC ska köras vid start anger du värdet för register nyckeln [dscautomationhostenabled registernyckel register nyckel](DSCAutomationHostEnabled.md) till 0.

- Mata in ett konfigurations-MOF-dokument till en virtuell hård disk
- Mata in en DSC-metaconfiguration i en virtuell hård disk
- Inaktivera DSC vid start tid

> [!NOTE]
> Du kan mata in både `Pending.mof` och `MetaConfig.mof` i en dator på samma tidpunkt.
> Om båda filerna finns är inställningarna som anges i `MetaConfig.mof` prioritera.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Mata in ett konfigurations-MOF-dokument till en virtuell hård disk

För att införa en konfiguration vid första uppstarten kan du mata in ett kompilerat MOF-dokument i den virtuella hård disken som dess `Pending.mof` fil. Om register nyckeln **dscautomationhostenabled registernyckel** har angetts till 2 (standardvärdet) kommer DSC att tillämpa den konfiguration som definierats av `Pending.mof` när datorn startas för första gången.

I det här exemplet kommer vi att använda följande konfiguration, som kommer att installera IIS på den nya datorn:

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>Så här infogar du MOF-dokumentet för konfiguration på den virtuella hård disken

1. Montera den virtuella hård disken som du vill använda för att mata in konfigurationen genom att anropa cmdleten [Mount-VHD](/powershell/module/hyper-v/mount-vhd) . Exempel:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. På en dator som kör PowerShell 5,0 eller senare sparar du konfigurationen ovan ( **SampleIISInstall** ) som en PowerShell-skript fil (. ps1).

1. I en PowerShell-konsol navigerar du till mappen där du sparade. ps1-filen.

1. Kör följande PowerShell-kommandon för att kompilera MOF-dokumentet (information om hur du kompilerar DSC-konfigurationer finns i [DSC-konfigurationer](../configurations/configurations.md):

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

1. Då skapas en `localhost.mof` fil i en ny mapp med namnet `SampleIISInstall` . Byt namn på och flytta filen till rätt plats på den virtuella hård disken med `Pending.mof` hjälp av cmdleten [Move-item](/powershell/module/microsoft.powershell.management/move-item) . Exempel:

   ```powershell
   Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

1. Demontera den virtuella hård disken genom att anropa cmdleten [demontera-VHD](/powershell/module/hyper-v/dismount-vhd) .
   Exempel:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. Skapa en virtuell dator med hjälp av den virtuella hård disk där du har installerat DSC MOF-dokumentet.

Efter den första starten och operativ system installationen installeras IIS. Du kan kontrol lera detta genom att anropa cmdleten [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) .

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Mata in en DSC-metaconfiguration i en virtuell hård disk

Du kan också konfigurera en dator för att hämta en konfiguration vid första uppstarten genom att mata in en metaconfiguration (mer information finns i [Konfigurera den lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) i den virtuella hård disken som dess `MetaConfig.mof` fil. Om register nyckeln **dscautomationhostenabled registernyckel** har angetts till 2 (standardvärdet) kommer DSC att tillämpa metaconfiguration som definieras av `MetaConfig.mof` till LCM när datorn startas för första gången. Om metaconfiguration anger att LCM ska hämta konfigurationer från en pull-server kommer datorn att försöka hämta en konfiguration från den hämtnings servern vid första uppstarten. Information om hur du konfigurerar en DSC-pull-server finns i [Konfigurera en DSC-webb hämtnings Server](../pull-server/pullServer.md).

I det här exemplet kommer vi att använda både konfigurationen som beskrivs i föregående avsnitt ( **SampleIISInstall** ) och följande metaconfiguration:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>För att mata in MOF-dokumentet metaconfiguration på den virtuella hård disken

1. Montera den virtuella hård disken där du vill mata in metaconfiguration genom att anropa cmdleten [Mount-VHD](/powershell/module/hyper-v/mount-vhd) . Exempel:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. [Konfigurera en DSC-webb hämtnings Server](../pull-server/pullServer.md)och spara **SampleIISInstall** -konfigurationen till lämplig mapp.

1. På en dator som kör PowerShell 5,0 eller senare sparar du ovanstående metaconfiguration ( **PullClientBootstrap** ) som en PowerShell-skript fil (. ps1).

1. I en PowerShell-konsol navigerar du till mappen där du sparade. ps1-filen.

1. Kör följande PowerShell-kommandon för att kompilera MOF-dokumentet för metaconfiguration (information om hur du kompilerar DSC-konfigurationer finns i [DSC-konfigurationer](../configurations/configurations.md):

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

1. Då skapas en `localhost.meta.mof` fil i en ny mapp med namnet `PullClientBootstrap` . Byt namn på och flytta filen till rätt plats på den virtuella hård disken med `MetaConfig.mof` hjälp av cmdleten [Move-item](/powershell/module/microsoft.powershell.management/move-item) .

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

1. Demontera den virtuella hård disken genom att anropa cmdleten [demontera-VHD](/powershell/module/hyper-v/dismount-vhd) .
   Exempel:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. Skapa en virtuell dator med hjälp av den virtuella hård disk där du har installerat DSC MOF-dokumentet.

Efter den första starten och operativ system installationen kommer DSC att hämta konfigurationen från hämtnings servern och IIS installeras. Du kan kontrol lera detta genom att anropa cmdleten [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) .

## <a name="disable-dsc-at-boot-time"></a>Inaktivera DSC vid start tid

Som standard är värdet för `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled`
nyckeln har angetts till 2, vilket gör att en DSC-konfiguration kan köras om datorn är i vänte läge eller nuvarande tillstånd. Om du inte vill att en konfiguration ska köras vid första uppstarten måste du ange värdet för den här nyckeln till 0:

1. Montera den virtuella hård disken genom att anropa cmdleten [Mount-VHD](/powershell/module/hyper-v/mount-vhd) . Exempel:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. Läs in register `HKLM\Software` under nyckeln från den virtuella hård disken genom att anropa `reg load` .

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

1. Navigera till `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` med hjälp av PowerShell-huvudprovidern.

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

1. Ändra värdet `DSCAutomationHostEnabled` till 0.

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. Ta bort registret genom att köra följande kommandon:

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a>Se även

[DSC-konfigurationer](../configurations/configurations.md)

[DSCAutomationHostEnabled-registernyckel](DSCAutomationHostEnabled.md)

[Konfigurera den lokala konfigurationshanteraren (LCM)](../managing-nodes/metaConfig.md)

[Konfigurera en DSC-webb hämtnings Server](../pull-server/pullServer.md)
