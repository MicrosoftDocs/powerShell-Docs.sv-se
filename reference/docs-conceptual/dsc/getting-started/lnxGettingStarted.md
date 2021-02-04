---
ms.date: 01/07/2021
keywords: DSC, PowerShell, konfiguration, installation
title: Kom igång med önskad tillstånds konfiguration (DSC) för Linux
description: Det här avsnittet beskriver hur du kommer igång med PowerShell-Desired State Configuration (DSC) för Linux.
ms.openlocfilehash: 6f0dea956b16c0828964a10b43abbbc65879ea33
ms.sourcegitcommit: b9826dcf402db8a2b6d3eab37edb82c6af113343
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98040930"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Kom igång med önskad tillstånds konfiguration (DSC) för Linux

Det här avsnittet beskriver hur du kommer igång med PowerShell-Desired State Configuration (DSC) för Linux.
Allmän information om DSC finns i [Kom igång med önskad tillstånds konfiguration i Windows PowerShell](../overview/overview.md).

## <a name="supported-linux-operation-system-versions"></a>System versioner för Linux operation som stöds

Följande Linux-versioner av operativ systemet stöds av DSC för Linux.

- CentOS 5, 6 och 7 (x86/x64)
- Debian GNU/Linux 6, 7 och 8 (x86/x64)
- Oracle Linux 5, 6 och 7 (x86/x64)
- Red Hat Enterprise Linux Server 5, 6 och 7 (x86/x64)
- SUSE Linux Enterprise Server 10, 11 och 12 (x86/x64)
- Ubuntu Server 12,04 LTS, 14,04 LTS, 16,04 LTS, 18,04 (x86/x64)

## <a name="installing-dsc-for-linux"></a>Installera DSC för Linux

Du måste installera [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) innan du installerar DSC för Linux.

### <a name="installing-omi"></a>Installerar OMI

Önskad tillstånds konfiguration för Linux kräver att CIM-servern Open Management Infrastructure (OMI), version 1.0.8.1 eller senare. OMI kan laddas ned från den öppna gruppen: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).

Installera OMI genom att installera det paket som är lämpligt för Linux-systemet (. rpm eller. deb) och OpenSSL-versionen (ssl_098 eller ssl_100) och arkitekturen (x64/x86). RPM-paket är lämpliga för CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server och Oracle Linux. DEB-paket är lämpliga för Debian GNU/Linux och Ubuntu Server. De ssl_098-paketen är lämpliga för datorer med OpenSSL 0.9.8 installerade medan ssl_100-paket är lämpliga för datorer med OpenSSL 1,0 installerat.

> [!NOTE]
> Om du vill fastställa den installerade OpenSSL-versionen kör du kommandot `openssl version` .

Kör följande kommando för att installera OMI på ett CentOS 7 x64-system.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>Installerar DSC

DSC för Linux är tillgängligt för nedladdning från [PowerShell-DSC-för-Linux](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-926) -lagringsplatsen i lagrings platsen.

Installera DSC genom att installera det paket som är lämpligt för Linux-systemet (. rpm eller. deb) och OpenSSL-versionen (ssl_098 eller ssl_100) och arkitekturen (x64/x86). RPM-paket är lämpliga för CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server och Oracle Linux. DEB-paket är lämpliga för Debian GNU/Linux och Ubuntu Server. De ssl_098-paketen är lämpliga för datorer med OpenSSL 0.9.8 installerade medan ssl_100-paket är lämpliga för datorer med OpenSSL 1,0 installerat.

> [!NOTE]
> För att fastställa den installerade OpenSSL-versionen kör du kommandot openssl-versionen.

Kör följande kommando för att installera DSC på ett CentOS 7 x64-system.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a>Använda DSC för Linux

I följande avsnitt beskrivs hur du skapar och kör DSC-konfigurationer på Linux-datorer.

### <a name="creating-a-configuration-mof-document"></a>Skapa ett MOF-dokument för konfiguration

Nyckelordet Windows PowerShell-konfiguration används för att skapa en konfiguration för Linux-datorer, precis som för Windows-datorer. Följande steg beskriver hur du skapar ett konfigurations dokument för en Linux-dator med hjälp av Windows PowerShell.

1. Importera NX-modulen. Windows PowerShell-modulen NX innehåller schemat för Built-In resurser för DSC för Linux och måste installeras på den lokala datorn och importeras i konfigurationen.

   - Om du vill installera NX-modulen kopierar du NX-modulens katalog till antingen `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` eller `$PSHOME\Modules` . NX-modulen ingår i installations paketet DSC för Linux. Om du vill importera NX-modulen i konfigurationen använder du `Import-DSCResource` kommandot:

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. Definiera en konfiguration och generera konfigurations dokumentet:

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a>Push-överför konfigurationen till Linux-datorn

Konfigurations dokument (MOF-filer) kan flyttas till Linux-datorn med cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) . För att kunna använda denna cmdlet, tillsammans med cmdletarna [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), eller [test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) , via fjärr anslutning till en Linux-dator, måste du använda en CIMSession. Cmdlet: en [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) används för att skapa en **CimSession** till Linux-datorn.

Följande kod visar hur du skapar en CIMSession för DSC för Linux.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
# $opt = New-CimSessionOption -UseSsl -SkipCACheck -SkipCNCheck -SkipRevocationCheck

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl

$sessParams = @{
    Credential = $credential
    ComputerName = $Node
    Port = 5986
    Authentication = 'basic'
    SessionOption = $opt
    OperationTimeoutSec = 90
}

$Sess = New-CimSession @sessParams
```

> [!NOTE]
> För "push"-läge måste användarens autentiseringsuppgifter vara rot användaren på Linux-datorn. Endast SSL/TLS-anslutningar stöds för DSC för Linux. `New-CimSession` måste användas med parametern – UseSSL inställd på $True. SSL-certifikatet som används av OMI (för DSC) anges i filen: `/etc/opt/omi/conf/omiserver.conf` med egenskaperna: pemfile och KeyFile. Om det här certifikatet inte är betrott av Windows-datorn som du kör cmdleten [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) på, kan du välja att ignorera certifikat validering med alternativen för CimSession: `-SkipCACheck -SkipCNCheck -SkipRevocationCheck`

Kör följande kommando för att skicka DSC-konfigurationen till Linux-noden.

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>Distribuera konfigurationen med en hämtnings Server

Konfigurationer kan distribueras till en Linux-dator med en pull-server, precis som för Windows-datorer. Vägledning om hur du använder en hämtnings Server finns i [Windows PowerShell Desired State Configuration pull-servrar](../pull-server/pullServer.md). Mer information och begränsningar som rör användning av Linux-datorer med en hämtnings Server finns i versions anteckningar för önskad tillstånds konfiguration för Linux.

### <a name="working-with-configurations-locally"></a>Arbeta med konfigurationer lokalt

DSC för Linux innehåller skript för att arbeta med konfiguration från den lokala Linux-datorn. Skripten hittar du i `/opt/microsoft/dsc/Scripts` och inkluderar följande:

- GetDscConfiguration.py

  Returnerar den aktuella konfigurationen som tillämpas på datorn. Liknar cmdlet: en för Windows PowerShell cmdlet `Get-DscConfiguration` .

  `# sudo ./GetDscConfiguration.py`

- GetDscLocalConfigurationManager.py

  Returnerar den aktuella meta-konfigurationen som tillämpas på datorn. Liknar cmdlet [Get-DSCLocalConfigurationManager-](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdleten.

  `# sudo ./GetDscLocalConfigurationManager.py`

- InstallModule.py

  Installerar en anpassad DSC-resurs-modul. Kräver sökvägen till en. zip-fil som innehåller modulen delade objekt bibliotek och schema MOF-filer.

  `# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- RemoveModule.py

  Tar bort en anpassad DSC-resurs-modul. Namnet på den modul som ska tas bort krävs.

  `# sudo ./RemoveModule.py cnx_Resource`

- StartDscLocalConfigurationManager.py

  Tillämpar en konfigurations-MOF-fil på datorn. Liknar cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) . Kräver att sökvägen till konfigurations-MOF tillämpas.

  `# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- SetDscLocalConfigurationManager.py

  Använder en MOF-fil för meta-konfiguration på datorn. Liknar cmdleten [set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) . Kräver att sökvägen till MOF-filen för meta-konfiguration tillämpas.

  `# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>PowerShell Desired State Configuration för Linux-loggfiler

Följande loggfiler genereras för DSC-meddelanden för Linux.

|     Loggfil      |     Katalog      |                                               Description                                                |
| ----------------- | ------------------ | -------------------------------------------------------------------------------------------------------- |
| **omiserver. log** | `/var/opt/omi/log` | Meddelanden som rör OMI CIM-serverns funktion.                                                |
| **DSC. log**       | `/var/opt/omi/log` | Meddelanden som rör åtgärden för den lokala Configuration Manager (LCM) och DSC-resurs åtgärder. |
