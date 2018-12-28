---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Konfigurera en virtuell dator vid första uppstart med hjälp av DSC
ms.openlocfilehash: 7b9ebc6c818aa39365759945667426c8976997e5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405272"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>Konfigurera en virtuell dator vid första uppstart med hjälp av DSC

> [!IMPORTANT]
> Gäller för: Windows PowerShell 5.0

## <a name="requirements"></a>Krav

> [!NOTE]
> Den **DSCAutomationHostEnabled** registernyckel som beskrivs i det här avsnittet är inte tillgänglig i PowerShell 4.0.
> Information om hur du konfigurerar nya virtuella datorer vid första uppstart i PowerShell 4.0 finns i [vill du automatiskt konfigurera dina datorer med hjälp av DSC vid första uppstart?] > ()https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

För att köra exemplen, behöver du:

- En startbar virtuell Hårddisk att arbeta med. Du kan hämta en ISO med ett utvärderingsexemplar av Windows Server 2016 på [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016). Du hittar anvisningar om hur du skapar en virtuell Hårddisk från en ISO-avbildning på [skapa startbara virtuella hårddiskar](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).
- En värddator som har Hyper-V aktiverat. Mer information finns i [översikt över Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).

  Du kan automatisera installationen och konfigurationen för en dator vid första uppstart med hjälp av DSC.
  Du kan göra detta genom att antingen infogar ett konfiguration MOF-dokument eller en metaconfiguration i startbara media (till exempel en virtuell Hårddisk) så att de körs under den ursprungliga startprocessen.
  Det här beteendet anges av den [DSCAutomationHostEnabled-registernyckel](DSCAutomationHostEnabled.md) registernyckel under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`.
  Som standard är värdet för den här nyckeln 2, vilket gör att DSC ska köras när datorn startas.

  Om du inte vill att DSC ska köras när datorn startas, ange värdet för den [DSCAutomationHostEnabled-registernyckel](DSCAutomationHostEnabled.md) registernyckeln på 0.

- Mata in en konfiguration MOF-dokument i en virtuell Hårddisk
- Mata in en DSC-metaconfiguration i en virtuell Hårddisk
- Inaktivera DSC när datorn startas

> [!NOTE]
> Du kan mata in båda `Pending.mof` och `MetaConfig.mof` till en dator samtidigt.
> Om båda filerna finns inställningarna som anges i `MetaConfig.mof` företräde.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Mata in en konfiguration MOF-dokument i en virtuell Hårddisk

För att införa en konfiguration vid första uppstart, kan du mata in en kompilerad konfiguration MOF-dokument i den virtuella Hårddisken som dess `Pending.mof` fil.
Om den **DSCAutomationHostEnabled** registernyckeln har angetts till 2 (standardvärde), DSC gäller konfigurationen av `Pending.mof` när datorn startas för första gången.

I det här exemplet ska vi använda följande konfiguration, som installerar IIS på den nya datorn:

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>Att mata in konfiguration MOF-dokument på den virtuella Hårddisken

1. Montera den virtuella Hårddisken som du vill att mata in konfigurationen genom att anropa den [Montera VHD](/powershell/module/hyper-v/mount-vhd) cmdlet. Till exempel:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. På en dator med PowerShell 5.0 eller senare, spara konfigurationen ovan (**SampleIISInstall**) som en PowerShell-skriptfil (.ps1).

3. Navigera till mappen där du sparade .ps1-fil i en PowerShell-konsol.

4. Kör följande PowerShell-kommandon för att kompilera MOF-dokument (information om kompilering av DSC-konfigurationer finns i [DSC-konfigurationer](../configurations/configurations.md):

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. Detta skapar en `localhost.mof` fil i en ny mapp med namnet `SampleIISInstall`.
   Byt namn på och flytta filen till rätt plats på den virtuella Hårddisken som `Pending.mof` med hjälp av den [flytta objekt](/powershell/module/microsoft.powershell.management/move-item) cmdlet. Till exempel:

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. Demontera den virtuella Hårddisken genom att anropa den [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet. Till exempel:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. Skapa en virtuell dator med hjälp av den virtuella Hårddisken där du installerade DSC MOF-dokument.

När du första uppstart och installationen av operativsystemet, kommer IIS att installeras.
Du kan kontrollera detta genom att anropa den [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Mata in en DSC-metaconfiguration i en virtuell Hårddisk

Du kan också konfigurera en dator för att hämta en konfiguration vid första uppstart genom att placera en metaconfiguration (se [konfigurerar den lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) till den virtuella Hårddisken som dess `MetaConfig.mof` fil.
Om den **DSCAutomationHostEnabled** registernyckeln har angetts till 2 (standardvärde), DSC ska gälla metaconfiguration som definieras av `MetaConfig.mof` till LCM när datorn startas för första gången.
Om metaconfiguration anger att LCM ska hämta konfigurationer från en pull-server, försöker datorn hämta en konfiguration från den pull-servern vid första uppstart.
Information om hur du konfigurerar en DSC-hämtningsserver finns i [att konfigurera en DSC-webbpullserver](../pull-server/pullServer.md).

I det här exemplet ska vi använda båda konfigurationen som beskrivs i föregående avsnitt (**SampleIISInstall**), och följande metaconfiguration:

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>Att mata in metaconfiguration MOF-dokument på den virtuella Hårddisken

1. Montera den virtuella Hårddisken som du vill infoga metaconfiguration genom att anropa den [Montera VHD](/powershell/module/hyper-v/mount-vhd) cmdlet. Till exempel:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. [Konfigurera en DSC-webbpullserver](../pull-server/pullServer.md), och spara den **SampleIISInistall** konfiguration till rätt mapp.

3. På en dator med PowerShell 5.0 eller senare, spara ovan metaconfiguration (**PullClientBootstrap**) som en PowerShell-skriptfil (.ps1).

4. Navigera till mappen där du sparade .ps1-fil i en PowerShell-konsol.

5. Kör följande PowerShell-kommandon för att kompilera MOF-dokument metaconfiguration (information om kompilering av DSC-konfigurationer finns i [DSC-konfigurationer](../configurations/configurations.md):

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. Detta skapar en `localhost.meta.mof` fil i en ny mapp med namnet `PullClientBootstrap`.
   Byt namn på och flytta filen till rätt plats på den virtuella Hårddisken som `MetaConfig.mof` med hjälp av den [flytta objekt](/powershell/module/microsoft.powershell.management/move-item) cmdlet.

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. Demontera den virtuella Hårddisken genom att anropa den [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet. Till exempel:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. Skapa en virtuell dator med hjälp av den virtuella Hårddisken där du installerade DSC MOF-dokument.

När du första uppstart och installationen av operativsystemet, DSC hämtar konfigurationen från hämtningsservern och IIS ska installeras.
Du kan kontrollera detta genom att anropa den [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.

## <a name="disable-dsc-at-boot-time"></a>Inaktivera DSC när datorn startas

Som standard, värdet för den `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` nyckeln har angetts till 2, vilket gör att en DSC-konfiguration för att köra om datorn är i väntande eller aktuella tillstånd. Om du inte vill att en konfiguration körs vid första uppstart måste du därför ange värdet för den här nyckeln till 0:

1. Montera den virtuella Hårddisken genom att anropa den [Montera VHD](/powershell/module/hyper-v/mount-vhd) cmdlet. Till exempel:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Läsa in registret `HKLM\Software` undernycklar från den virtuella Hårddisken genom att anropa `reg load`.

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. Navigera till den `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*` med hjälp av PowerShell register-provider.

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
   ```

4. Ändra värdet för `DSCAutomationHostEnabled` till 0.

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

[Konfigurera en DSC-webbpullserver](../pull-server/pullServer.md)
