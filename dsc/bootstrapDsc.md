---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Konfigurera en virtuella datorer på första uppstart med hjälp av DSC"
ms.openlocfilehash: ff06aafa6db49d93a9b42e38ac7c3e9a11657bd5
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
>Gäller för: Windows PowerShell 5.0

>**Obs:** den **DSCAutomationHostEnabled** registernyckel som beskrivs i det här avsnittet är inte tillgänglig i PowerShell 4.0.
Mer information om hur du konfigurerar nya virtuella datorer på första uppstart i PowerShell 4.0 finns [vill automatiskt konfigurera dina datorer med hjälp av DSC vid första uppstart?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>Konfigurera en virtuella datorer på första uppstart med hjälp av DSC

## <a name="requirements"></a>Krav

Om du vill köra exemplen behöver du:

- En startbar VHD att arbeta med. Du kan ladda ned en ISO med en utvärderingsversion av Windows Server 2016 vid [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016). Du hittar anvisningar om hur du skapar en VHD från en ISO-avbildning på [skapa startbara virtuella hårddiskar](https://technet.microsoft.com/library/gg318049.aspx).
- En värddator som har Hyper-V aktiverat. Mer information finns i [översikt över Hyper-V](https://technet.microsoft.com/library/hh831531.aspx).

Med hjälp av DSC, kan du automatisera installationen och konfigurationen för en dator vid första uppstart.
Det gör du genom att antingen Injicera en konfiguration MOF-dokument eller en metakonfigurationen i startbart medium (till exempel en virtuell Hårddisk) så att de körs under den första startprocessen.
Det här beteendet anges av den [DSCAutomationHostEnabled registernyckeln](DSCAutomationHostEnabled.md) registernyckel under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**.
Som standard är värdet för den här nyckeln 2, vilket gör att DSC ska köras när datorn startas.

Om du inte vill DSC ska köras vid starten, ange värdet för den [DSCAutomationHostEnabled registernyckeln](DSCAutomationHostEnabled.md) registernyckeln till 0.

- Mata in ett konfiguration MOF-dokument i en virtuell Hårddisk
- Mata in en DSC-metakonfigurationen i en virtuell Hårddisk
- Inaktivera DSC vid start

>**Obs:** kan mata in både `Pending.mof` och `MetaConfig.mof` i en dator samtidigt.
Om båda filerna finns inställningarna som anges i `MetaConfig.mof` företräde.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Mata in ett konfiguration MOF-dokument i en virtuell Hårddisk

För att införa en konfiguration på första uppstart du mata in ett kompilerade configuration MOF-dokument i den virtuella Hårddisken som dess `Pending.mof` fil.
Om den **DSCAutomationHostEnabled** registernyckeln har värdet 2 (standardvärdet), DSC gäller konfigurationen av `Pending.mof` när datorn startas för första gången.

I det här exemplet ska vi använda följande konfiguration, som kommer att installera IIS på den nya datorn:

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

1. Montera VHD: N som du vill mata in konfigurationen genom att anropa den [Montera VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet. Till exempel:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```
2. På en dator som kör PowerShell 5.0 eller senare, spara konfigurationen ovan (**SampleIISInstall**) som en PowerShell-skriptfil (.ps1).

3. Navigera till mappen där du sparade .ps1-fil i en PowerShell-konsol.

4. Kör följande PowerShell-kommandon för att kompilera MOF-dokumentet (information om kompilering av DSC-konfigurationer finns [DSC-konfigurationer](configurations.md):

    ```powershell
    . .\SampleIISInstall.ps1
    SampleIISInstall
    ```

5. Detta skapar en `localhost.mof` fil i en ny mapp med namnet `SampleIISInstall`.
Byt namn på och flytta filen till rätt plats på den virtuella Hårddisken som `Pending.mof` med hjälp av den [flytta objekt](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet. Till exempel:

    ```powershell
        Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
    ```
6. Demontera den virtuella Hårddisken genom att anropa den [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet. Till exempel:

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

7. Skapa en virtuell dator med hjälp av den virtuella Hårddisken där du installerade DSC MOF-dokumentet. Efter första uppstart och installation av operativsystemet, kommer IIS att installeras.
Du kan kontrollera detta genom att anropa den [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Mata in en DSC-metakonfigurationen i en virtuell Hårddisk

Du kan också konfigurera en dator om du vill dra en konfiguration på första uppstart genom att injicera en metakonfigurationen (se [konfigurera den lokala Configuration Manager (MGM)](metaConfig.md)) till den virtuella Hårddisken som dess `MetaConfig.mof` fil.
Om den **DSCAutomationHostEnabled** registernyckeln har värdet 2 (standardvärdet) gäller DSC metakonfigurationen definieras av `MetaConfig.mof` till MGM när datorn startas för första gången.
Om metakonfigurationen anger att MGM bör pull-konfigurationer från en pull-server, försöker datorn hämtar en konfiguration från den pull-servern vid första uppstart.
Information om hur du konfigurerar en DSC pull-server finns i [ställer in en pull webbserver DSC](pullServer.md).

I det här exemplet kommer vi att använda både konfigurationen som beskrivs i föregående avsnitt (**SampleIISInstall**), och följande metakonfigurationen:

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>Att mata in metakonfigurationen MOF-dokument på den virtuella Hårddisken

1. Montera VHD: N som du vill mata in metakonfigurationen genom att anropa den [Montera VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet. Till exempel:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. [Konfigurera en pull-DSC webbserver](pullServer.md), och spara den **SampleIISInistall** konfiguration till rätt mapp.

3. På en dator som kör PowerShell 5.0 eller senare, spara ovan metakonfigurationen (**PullClientBootstrap**) som en PowerShell-skriptfil (.ps1).

4. Navigera till mappen där du sparade .ps1-fil i en PowerShell-konsol.

5. Kör följande PowerShell-kommandon för att kompilera MOF-dokumentet metakonfigurationen (information om kompilering av DSC-konfigurationer finns [DSC-konfigurationer](configurations.md):

    ```powershell
    . .\PullClientBootstrap.ps1
    PullClientBootstrap
    ```

6. Detta skapar en `localhost.meta.mof` fil i en ny mapp med namnet `PullClientBootstrap`.
Byt namn på och flytta filen till rätt plats på den virtuella Hårddisken som `MetaConfig.mof` med hjälp av den [flytta objekt](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.

    ```powershell
    Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\Sytem32\Configuration\MetaConfig.mof
    ```

7. Demontera den virtuella Hårddisken genom att anropa den [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet. Till exempel:

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

8. Skapa en virtuell dator med hjälp av den virtuella Hårddisken där du installerade DSC MOF-dokumentet.
Efter första uppstart och installation av operativsystemet, DSC hämtar konfigurationen från den pull-servern och IIS installeras.
Du kan kontrollera detta genom att anropa den [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.

## <a name="disable-dsc-at-boot-time"></a>Inaktivera DSC vid start

Som standard värdet för den **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** nyckeln anges till 2, vilket gör att en DSC-konfiguration för att köra om datorn är i väntande eller aktuella tillstånd. Om du inte vill att en konfiguration som ska köras vid första uppstart måste du ange värdet för den här nyckeln så till 0:

1. Montera VHD: N genom att anropa den [Montera VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet. Till exempel:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. Läsa in registret **HKLM\Software** undernycklar från den virtuella Hårddisken genom att anropa `reg load`.

    ```
    reg load HKLM\Vhd E:\Windows\System32\Config\Software`
    ```

3. Navigera till den **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\***  med hjälp av PowerShell register-provider.

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

- [DSC-konfigurationer](configurations.md)
- [DSCAutomationHostEnabled-registernyckel](DSCAutomationHostEnabled.md)
- [Konfigurera den lokala konfigurationshanteraren (LCM)](metaConfig.md)
- [Ställer in en pull webbserver DSC](pullServer.md)

