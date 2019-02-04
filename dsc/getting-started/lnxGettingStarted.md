---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Kom igång med Desired State Configuration (DSC) för Linux
ms.openlocfilehash: 69f087434455aae8e97ea07c79c52e493412d134
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686602"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Kom igång med Desired State Configuration (DSC) för Linux

Det här avsnittet förklarar hur du kommer igång med PowerShell Desired State Configuration (DSC) för Linux. Allmän information om DSC finns i [Kom igång med Windows PowerShell Desired State Configuration](../overview/overview.md).

## <a name="supported-linux-operation-system-versions"></a>Linux åtgärden system-versioner som stöds

Följande versioner av Linux-operativsystemet stöds för DSC för Linux.

- CentOS 5, 6 och 7 (x86/x64)
- Debian GNU/Linux 6, 7 och 8 (x86/x64)
- Oracle Linux 5, 6 och 7 (x86/x64)
- Red Hat Enterprise Linux Server 5, 6 och 7 (x86/x64)
- SUSE Linux Enterprise Server 10, 11 och 12 (x86/x64)
- Server för Ubuntu 12.04 LTS, 14.04 LTS och 16.04 LTS (x86/x64)

I följande tabell beskrivs paket som krävs beroenden för DSC för Linux.

|  Nödvändigt paket |  Beskrivning |  Lägsta version |
|---|---|---|
| glibc| GNU bibliotek| 2…4 – 31.30|
| python| Python| 2.4 – 3.4|
| omiserver| Open Management Infrastructure| 1.0.8.1|
| openssl| OpenSSL-bibliotek| 0.9.8 eller 1.0|
| ctypes| Python CTypes bibliotek| Måste matcha Python-version|
| libcurl| cURL http-klientbibliotek| 7.15.1|

## <a name="installing-dsc-for-linux"></a>Installera DSC för Linux

Du måste installera den [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) innan du installerar DSC för Linux.

### <a name="installing-omi"></a>Installera OMI

Desired State Configuration för Linux kräver Open Management Infrastructure (OMI) CIM-servern, version 1.0.8.1 eller senare. OMI kan hämtas från The Open Group: [Öppna Management Infrastructure (OMI)](https://github.com/Microsoft/omi).

Om du vill installera OMI, installerar du det paket som är lämpliga för din Linux-system (.rpm eller .deb) och OpenSSL-version (ssl_098 eller ssl_100) och arkitektur (x64/x86). RPM-paket är lämpliga för CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server och Oracle Linux. DEB-paket är lämpliga för Debian GNU/Linux och Ubuntu Server. Ssl_098-paket är lämpliga för datorer med OpenSSL 0.9.8 installerad medan ssl_100-paket är lämpliga för datorer med OpenSSL 1.0 installerat.

> [!NOTE]
> För att avgöra den installerade versionen av OpenSSL, kör du kommandot `openssl version`.

Kör följande kommando för att installera OMI på en CentOS 7 x64-system.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>Installera DSC

DSC för Linux finns att hämta [här](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).

Om du vill installera DSC, installerar du det paket som är lämpliga för din Linux-system (.rpm eller .deb) och OpenSSL-version (ssl_098 eller ssl_100) och arkitektur (x64/x86). RPM-paket är lämpliga för CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server och Oracle Linux. DEB-paket är lämpliga för Debian GNU/Linux och Ubuntu Server. Ssl_098-paket är lämpliga för datorer med OpenSSL 0.9.8 installerad medan ssl_100-paket är lämpliga för datorer med OpenSSL 1.0 installerat.

> [!NOTE]
> För att avgöra den installerade versionen av OpenSSL, kör du kommandot openssl-version.

Kör följande kommando för att installera DSC på en CentOS 7 x64-system.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a>Med DSC för Linux

I följande avsnitt beskrivs hur du skapar och kör DSC-konfigurationer på Linux-datorer.

### <a name="creating-a-configuration-mof-document"></a>Skapa ett configuration MOF-dokument

Nyckelordet Windows PowerShell-konfigurationen används för att skapa en konfiguration för Linux-datorer precis som för Windows-datorer. Följande steg beskriver skapandet av ett konfigurationsdokument för en Linux-dator med hjälp av Windows PowerShell.

1. Importera modulen nx. Windows PowerShell-modulen nx måste innehåller schemat för inbyggda resurser för DSC för Linux och installeras på den lokala datorn och importeras i konfigurationen.

   - Om du vill installera modulen nx kopiera modulkatalogen nx antingen `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` eller `$PSHOME\Modules`. Modulen nx ingår i DSC för Linux-installationspaketet. Om du vill importera modulen nx i din konfiguration, använda den `Import-DSCResource` kommando:

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. Definiera en konfiguration och generera configuration dokumentet:

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

### <a name="push-the-configuration-to-the-linux-computer"></a>Push-konfigurationen till Linux-dator

Av konfigurationsdokument (MOF-filer) kan skickas till Linux-dator med den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet. Om du vill använda denna cmdlet, tillsammans med den [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), eller [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlet: ar, via en fjärranslutning till en Linux-dator, du måste använda en CIMSession. Den [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet används för att skapa en CIMSession på Linux-datorn.

Följande kod visar hur du skapar en CIMSession för DSC för Linux.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90
```

> [!NOTE]
> Användarens autentiseringsuppgifter måste vara rotanvändare på Linux-datorn för ”Push”-läge.
> SSL/TLS-anslutningar stöds för DSC för Linux, den `New-CimSession` måste användas med parametern – UseSSL ange som $true.
> SSL-certifikatet som används av OMI (för DSC) har angetts i filen: `/opt/omi/etc/omiserver.conf` med egenskaper: pemfile och nyckelfilen.
> Om det här certifikatet inte är betrodd av den Windows-dator som du kör den [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet på, som du kan välja att ignorera certifikatsverifiering med CIMSession-alternativ: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`

Kör följande kommando för att skicka DSC-konfigurationen till Linux-noden.

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>Distribuera konfigurationen med en pull-server

Konfigurationer kan distribueras till en Linux-dator med en pull-server, precis som för Windows-datorer. Anvisningar om hur du använder en pull-server finns i [Windows PowerShell Desired State Configuration Pull servrar](../pull-server/pullServer.md). Ytterligare information och begränsningar som rör med Linux-datorer med en pull-server finns i viktig information för Desired State Configuration för Linux.

### <a name="working-with-configurations-locally"></a>Arbeta med konfigurationer lokalt

DSC för Linux innehåller skript för att arbeta med konfigurationen från den lokala Linux-datorn. Dessa skript är hitta i `/opt/microsoft/dsc/Scripts` och inkluderar följande:

- GetDscConfiguration.py

Returnerar den aktuella konfigurationen som tillämpats på datorn. Liknar Windows PowerShell-cmdleten `Get-DscConfiguration` cmdlet.

`# sudo ./GetDscConfiguration.py`

- GetDscLocalConfigurationManager.py

Returnerar den aktuella meta-konfigurationen tillämpas på datorn. Liknar cmdleten [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.

`# sudo ./GetDscLocalConfigurationManager.py`

- InstallModule.py

Installerar en anpassad modul för DSC-resurs. Kräver sökvägen till en .zip-fil som innehåller modulen delade objektbiblioteket och schemat MOF-filer.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- RemoveModule.py

Tar bort en anpassad modul för DSC-resurs. Kräver namnet på modulen att ta bort.

`# sudo ./RemoveModule.py cnx_Resource`

- StartDscLocalConfigurationManager.py

Gäller en MOF-konfigurationsfilen på datorn. Liknar den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet. Kräver sökväg till MOF att tillämpa konfigurationen.

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- SetDscLocalConfigurationManager.py

Gäller en Meta Configuration MOF-fil på datorn. Liknar den [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet. Kräver sökvägen till Meta Configuration MOF tillämpas.

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>PowerShell Desired State Configuration för Linux-loggfiler

Följande loggfiler genereras för DSC för Linux-meddelanden.

|Loggfil|Katalog|Beskrivning|
|---|---|---|
|**omiserver.log**|`/var/opt/omi/log`|Meddelanden som är relaterade till driften av OMI CIM-servern.|
|**dsc.log**|`/var/opt/omi/log`|Meddelanden som är relaterade till användningen av lokala Configuration Manager (LCM) och DSC-resurs som.|
