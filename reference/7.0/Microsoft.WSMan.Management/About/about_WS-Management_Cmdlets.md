---
description: Innehåller en översikt över hantering av webb tjänster (WS-Management) som bakgrund för att använda WS-Management-cmdlets i Windows PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WS Management_Cmdlets
ms.openlocfilehash: d11b8ca72951409a1b9a508623b3f39cae46e318
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390481"
---
# <a name="about-ws-management-cmdlets"></a>Om WS-Management-cmdletar

## <a name="short-description"></a>KORT BESKRIVNING

Innehåller en översikt över hantering av webb tjänster (WS-Management) som bakgrund för att använda WS-Management-cmdlets i Windows PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

Det här avsnittet innehåller en översikt över hantering av webb tjänster (WS-Management) som bakgrund för att använda WS-Management-cmdlets i Windows PowerShell. Det här avsnittet innehåller också länkar till mer information om WS-Management. Microsoft-implementeringen av WS-Management kallas även Windows Remote Management (WinRM).

## <a name="about-ws-management"></a>Om WS-Management

Windows Remote Management är Microsofts implementering av WS-Management protokoll, ett standardiserat SOAP-baserat, brand Väggs vänligt protokoll som gör det möjligt för maskin vara och operativ system från olika leverantörer att samverka. WS-Management protokoll specifikationen är ett vanligt sätt för system att komma åt och utbyta hanterings information över en IT-infrastruktur. WS-Management och Intelligent Platform Management Interface (IPMI) tillsammans med händelse insamlaren är komponenter i Windows Hardware Management-funktioner.

WS-Management protokollet baseras på följande standard-webb tjänst specifikationer: HTTPS, SOAP över HTTP (WS-I-profil), SOAP 1,2, WS-Addressing, WS-transfer, WS-Enumeration och WS-Eventing.

## <a name="ws-management-and-wmi"></a>WS-Management och WMI

WS-Management kan användas för att hämta data som exponeras av Windows Management Instrumentation (WMI). Du kan hämta WMI-data med skript eller program som använder skript-API: et för WS-Management eller via kommando rads verktyget WinRM. WS-Management stöder de flesta välkända WMI-klasser och-åtgärder, inklusive inbäddade objekt. WS-Management kan utnyttja WMI för att samla in data om resurser eller hantera resurser på en Windows-baserad dator. Det innebär att du kan hämta data om objekt som diskar, nätverkskort, tjänster eller processer i företaget via den befintliga uppsättningen WMI-klasser. Du kan också komma åt de maskin varu data som är tillgängliga från standard-WMI IPMI-providern.

## <a name="ws-management-windows-powershell-provider-wsman"></a>WS-Management Windows PowerShell-Provider (WSMan)

WSMan-providern tillhandahåller en hierarkisk vy över tillgängliga WS-Management konfigurations inställningar. Med providern kan du utforska och ange de olika WS-Management konfigurations alternativen.

## <a name="ws-management-configuration"></a>WS-Management konfiguration

Om WS-Management inte har installerats och kon figurer ATS är Windows PowerShell-fjärrkommunikation inte tillgänglig, WS-Management-cmdletarna inte körs, WS-Management skript inte körs och WSMan-providern kan inte utföra data åtgärder. Kommando rads verktyget WS-Management, WinRM och event Forwarding är också beroende av WS-Management-konfigurationen.

## <a name="ws-management-cmdlets"></a>WS-Management-cmdletar

WS-Management funktioner implementeras i Windows PowerShell via en modul som innehåller en uppsättning cmdlets och WSMan-providern. Du kan använda dessa cmdletar för att slutföra de slut punkt till slut punkts aktiviteter som krävs för att hantera WS-Management inställningar på lokala datorer och fjärrdatorer.

Följande WS-Management-cmdletar är tillgängliga.

## <a name="connection-cmdlets"></a>Anslutnings-cmdletar

- Connect-WSMan: ansluter den lokala datorn till tjänsten WS-Management (WinRM) på en fjärrdator.

- Koppla från-WSMan: kopplar från den lokala datorn från tjänsten WS-Management (WinRM) på en fjärrdator.

## <a name="management-data-cmdlets"></a>Management-Data-cmdletar

- Get-WSManInstance: visar hanterings information för en resurs instans som anges av en resurs-URI.

- Invoke-WSManAction: anropar en åtgärd på målobjektet som anges av resurs-URI och av väljare.

- New-WSManInstance: skapar en ny hanterings resurs instans.

- Remove-WSManInstance: tar bort en hanterings resurs instans.

- Set-WSManInstance: ändrar hanterings information som är relaterad till en resurs.

## <a name="setup-and-configuration-cmdlets"></a>Installations-och konfigurations-cmdletar

- Set-WSManQuickConfig: konfigurerar den lokala datorn för fjärrhantering.
  Du kan använda Set-WSManQuickConfig-cmdlet för att konfigurera WS-Management för att tillåta fjärr anslutningar till tjänsten WS-Management (WinRM). Set-WSManQuickConfig cmdlet utför följande åtgärder:
  - Den avgör om tjänsten WS-Management (WinRM) körs. Om WinRM-tjänsten inte körs startar Set-WSManQuickConfig cmdleten tjänsten.
  - Den anger start typen för tjänsten WS-Management (WinRM) till automatisk.
  - Den skapar en lyssnare som accepterar begär Anden från alla IP-adresser. Standard transport protokollet är HTTP.
  - Det aktiverar ett brand Väggs undantag för WS-Management trafik.

  Obs! Om du vill köra den här cmdleten i Windows Vista, Windows Server 2008 och senare versioner av Windows, måste du starta Windows PowerShell med alternativet "kör som administratör".

- Test-WSMan: verifierar att WS-Management har installerats och kon figurer ATS. Test-WSMan-cmdleten testar om tjänsten WS-Management (WinRM) körs och är konfigurerad på en lokal dator eller fjärrdator.

- Disable-WSManCredSSP: inaktiverar CredSSP-autentisering på en klient dator.

- Enable-WSManCredSSP: aktiverar CredSSP-autentisering på en klient dator.

- Get-WSManCredSSP: hämtar den CredSSP-relaterade konfigurationen för en klient dator.

## <a name="ws-management-specific-cmdlets"></a>WS-Management-Specific-cmdletar

- New-WSManSessionOption: skapar ett WSManSessionOption-objekt som ska användas som inmatat för en eller flera parametrar för en WS-Management-cmdlet.

## <a name="additional-ws-management-information"></a>Ytterligare WS-Management information

Mer information om WS-Management finns i följande avsnitt i Windows-dokumentationen.

[Windows Remote Management](/windows/win32/winrm/portal)

[Om Windows Remote Management](/windows/win32/winrm/about-windows-remote-management)

[Installation och konfigurering för Windows Remote Management](/windows/win32/winrm/installation-and-configuration-for-windows-remote-management)

[Windows Remote Management-arkitektur](/windows/win32/winrm/windows-remote-management-architecture)

[WS-Managementprotokollet](/windows/win32/winrm/ws-management-protocol)

[Windows Remote Management och WMI](/windows/win32/winrm/windows-remote-management-and-wmi)

[Resurs-URI: er](/windows/win32/winrm/resource-uris)

[Hantering av fjärrmaskinvara](/windows/win32/winrm/remote-hardware-management)

[Händelser](/windows/win32/winrm/events)

## <a name="see-also"></a>SE ÄVEN

[Anslut-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)

[Disable-WSManCredSSP](xref:Microsoft.WSMan.Management.Disable-WSManCredSSP)

[Koppla från-WSMan](xref:Microsoft.WSMan.Management.Disconnect-WSMan)

[Aktivera – WSManCredSSP](xref:Microsoft.WSMan.Management.Enable-WSManCredSSP)

[Get-WSManCredSSP](xref:Microsoft.WSMan.Management.Get-WSManCredSSP)

[Get-WSManInstance](xref:Microsoft.WSMan.Management.Get-WSManInstance)

[Invoke-WSManAction](xref:Microsoft.WSMan.Management.Invoke-WSManAction)

[New-WSManInstance](xref:Microsoft.WSMan.Management.New-WSManInstance)

[Remove-WSManInstance](xref:Microsoft.WSMan.Management.Remove-WSManInstance)

[Set-WSManInstance](xref:Microsoft.WSMan.Management.Set-WSManInstance)

[Set-WSManQuickConfig](xref:Microsoft.WSMan.Management.Set-WSManQuickConfig)

[Test-WSMan](xref:Microsoft.WSMan.Management.Test-WSMan)
