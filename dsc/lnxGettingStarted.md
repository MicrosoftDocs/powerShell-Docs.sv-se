---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Kom igång med önskad (DSC tillstånd Configuration) för Linux"
ms.openlocfilehash: fd4820d27de5958a325032ca3fc202a521c131b4
ms.sourcegitcommit: 28e71b0ae868014523631fec3f5417de751944f3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2017
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Kom igång med önskad (DSC tillstånd Configuration) för Linux

Det här avsnittet beskriver hur du kommer igång med hjälp av PowerShell önskad tillstånd Configuration (DSC) för Linux. Allmän information om DSC finns [Kom igång med Windows PowerShell Desired State Configuration](overview.md).

## <a name="supported-linux-operation-system-versions"></a>Linux åtgärden system-versioner som stöds

Följande versioner av Linux-operativsystemet stöds för DSC för Linux.
- CentOS 5, 6 och 7 (x86/x64)
- Debian GNU/Linux 6, 7 och 8 (x86/x64)
- Oracle Linux 5, 6 och 7 (x86/x64)
- Red Hat Enterprise Linux Server 5, 6 och 7 (x86/x64)
- SUSE Linux Enterprise Server 10, 11 och 12 (x86/x64)
- Ubuntu Server 12.04 LTS, 14.04 LTS och 16.04 LTS (x86/x64)

I följande tabell beskrivs paket som krävs beroenden för DSC för Linux.

|  Nödvändigt paket |  Beskrivning |  Lägsta version | 
|---|---|---|
| Glibc| GNU Library| 2…4 – 31.30| 
| Python| Python| 2.4 – 3.4| 
| omiserver| Open Management Infrastructure| 1.0.8.1| 
| Openssl| OpenSSL-bibliotek| 0.9.8 eller 1.0| 
| ctypes| Python CTypes bibliotek| Måste matcha versionen av Python| 
| libcurl| cURL http-klientbibliotek| 7.15.1| 

## <a name="installing-dsc-for-linux"></a>Installera DSC för Linux

Du måste installera den [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) innan du installerar DSC för Linux.

### <a name="installing-omi"></a>Installera OMI

Desired State Configuration för Linux kräver Open Management Infrastructure (OMI) CIM-servern, version 1.0.8.1 eller senare. OMI kan hämtas från Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).

Installera OMI installera det paket som är lämpliga för ditt Linux-system (.rpm eller .deb) och OpenSSL version (ssl_098 eller ssl_100) och arkitektur (x64/x86). RPM-paket är lämpliga för CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server och Oracle Linux. DEB-paket är lämpliga för Debian GNU/Linux- och Ubuntu Server. Ssl_098-paket är lämpliga för datorer med OpenSSL 0.9.8 installerat under ssl_100-paket är lämpliga för datorer med OpenSSL 1.0 installeras.

> **Obs**: för att fastställa den installerade versionen av OpenSSL, kör du kommandot `openssl version`.

Kör följande kommando för att installera OMI på ett CentOS 7 x64 system.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>Installera DSC

DSC för Linux finns att hämta [här](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest). 

Installera DSC, installera det paket som är lämpliga för ditt Linux-system (.rpm eller .deb) och OpenSSL version (ssl_098 eller ssl_100) och arkitektur (x64/x86). RPM-paket är lämpliga för CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server och Oracle Linux. DEB-paket är lämpliga för Debian GNU/Linux- och Ubuntu Server. Ssl_098-paket är lämpliga för datorer med OpenSSL 0.9.8 installerat under ssl_100-paket är lämpliga för datorer med OpenSSL 1.0 installeras.

> **Obs**: för att fastställa den installerade versionen av OpenSSL, kör du kommandot openssl version.
 
Kör följande kommando för att installera DSC på ett CentOS 7 x64 system.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## <a name="using-dsc-for-linux"></a>Använder DSC för Linux

I följande avsnitt beskrivs hur du skapar och kör DSC-konfigurationer på Linux-datorer.

### <a name="creating-a-configuration-mof-document"></a>Skapa ett configuration MOF-dokument

Nyckelordet Windows PowerShell-konfigurationen används för att skapa en konfiguration för Linux-datorer precis som för Windows-datorer. Följande steg beskriver skapandet av ett konfigurationsdokument för en Linux-dator med Windows PowerShell.

1. Importera modulen nx. Windows PowerShell-modulen nx måste innehåller schemat för inbyggda resurser för DSC för Linux och installeras på den lokala datorn och importeras i konfigurationen.

    -Om du vill installera modulen nx kopiera modulkatalogen nx antingen `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` eller `$PSHOME\Modules`. Modulen nx ingår i DSC för installationspaketet för Linux (MSI). Importera modulen nx i din konfiguration genom att använda den __importera DSCResource__ kommando:
    
```powershell
Configuration ExampleConfiguration{
   
    Import-DSCResource -Module nx

}
```
2. Definierar en konfiguration och generera konfigurationsdokument:

```powershell
Configuration ExampleConfiguration{
   
    Import-DscResource -Module nx
 
    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

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

Av konfigurationsdokument (MOF) flyttas till Linux-datorn med den [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet. För att kunna använda denna cmdlet, tillsammans med den [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), eller [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlets, via en fjärranslutning till en Linux-dator, du måste använda en CIMSession. Den [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet som används för att skapa en CIMSession till Linux-datorn.

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

> **Obs**:
* Användarens autentiseringsuppgifter måste vara rotanvändaren på Linux-dator för ”Push” läge.
* SSL/TLS-anslutningar stöds för DSC för Linux, New-CimSession måste användas med parametern – UseSSL värdet $true.
* SSL-certifikatet som används av OMI (för DSC) har angetts i filen: `/opt/omi/etc/omiserver.conf` med egenskaper: pemfile och nyckelfil.
Om det här certifikatet inte är betrott av Windows-dator som du kör den [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet på, kan du ignorera certifikatvalidering med CIMSession alternativ:`-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`

Kör följande kommando för att push-DSC-konfigurationen till Linux-nod.

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>Distribuera konfigurationen med en pull-server

Konfigurationer som kan distribueras till en Linux-dator med en pull-server, precis som för Windows-datorer. Anvisningar om hur du använder en pull-server finns [Windows PowerShell önskad tillstånd Pull Konfigurationsservrar](pullServer.md). För ytterligare information och begränsningar som rör bruket av Linux-datorer med en pull-server finns i viktig information för Desired State Configuration för Linux.

### <a name="working-with-configurations-locally"></a>Arbeta med konfigurationer lokalt

DSC för Linux innehåller skript för att arbeta med konfigurationen från den lokala Linux-datorn. Dessa skript hitta i `/opt/microsoft/dsc/Scripts` och inkluderar följande:
* GetDscConfiguration.py

 Returnerar den aktuella konfigurationen som används på datorn. Liknar Windows PowerShell-cmdleten Get-DscConfiguration cmdlet.

`# sudo ./GetDscConfiguration.py`

* GetDscLocalConfigurationManager.py

 Returnerar den aktuella meta-konfigurationen används på datorn. Liknar cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.

`# sudo ./GetDscLocalConfigurationManager.py`

* InstallModule.py

 Installerar en anpassad modul för DSC-resurs. Kräver sökvägen till en ZIP-fil som innehåller modulen delade objektbiblioteket och schemat MOF-filer.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* RemoveModule.py

 Tar bort en anpassad modul för DSC-resurs. Du måste ange namn på modulen som ska tas bort.

`# sudo ./RemoveModule.py cnx_Resource`

* StartDscLocalConfigurationManager.py 

 Gäller en konfiguration MOF-filen till datorn. Liknar den [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet. Kräver sökväg till MOF att tillämpa konfigurationen.

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* SetDscLocalConfigurationManager.py

 Gäller en Meta Configuration MOF-filen till datorn. Liknar den [Set DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet. Kräver sökväg till MOF Meta konfigurationen ska tillämpas.

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>PowerShell önskad Tillståndskonfiguration för Linux-loggfiler

Följande loggfiler genereras för DSC för Linux-meddelanden.

|Loggfil|Katalog|Beskrivning|
|---|---|---|
|omiserver.log|/var/OPT/omi/log|Meddelanden om driften av OMI CIM-servern.|
|DSC.log|/var/OPT/omi/log|Meddelanden om åtgärden med de lokala Configuration Manager (MGM) och DSC resurs.|

