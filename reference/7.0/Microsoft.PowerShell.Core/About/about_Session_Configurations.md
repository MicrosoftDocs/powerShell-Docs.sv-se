---
description: Beskriver sessionsinställningar, som bestämmer vilka användare som kan fjärrans luta till datorn och de kommandon som de kan köra.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configurations
ms.openlocfilehash: 5b59d8fb05ee118f5b2d7b5b859efad9be75814a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93269972"
---
# <a name="about-session-configurations"></a>Om sessionsbaserade

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver sessionsinställningar, som bestämmer vilka användare som kan fjärrans luta till datorn och de kommandon som de kan köra.

## <a name="long-description"></a>LÅNG BESKRIVNING

En sessionsinformation, som även kallas "slut punkt", är en grupp inställningar på den lokala datorn som definierar miljön för PowerShell-sessioner som skapas när fjärranslutna eller lokala användare ansluter till PowerShell på den lokala datorn.

Administratörer på datorn kan använda sessionsbaserade för att skydda datorn och definiera anpassade miljöer för användare som ansluter till datorn.

Administratörer kan också använda sessionsbaserade för att avgöra vilka behörigheter som krävs för att fjärrans luta till datorn. Som standard har bara medlemmar i gruppen Administratörer behörighet att använda sessionen för att fjärrans luta, men du kan ändra standardinställningarna så att alla användare eller valda användare kan fjärrans luta till din dator.

Från och med PowerShell 3,0 kan du använda en konfigurations fil för sessionen för att definiera elementen i en sessions konfiguration. Den här funktionen gör det enkelt att anpassa sessioner utan att skriva kod och identifiera egenskaperna för en sessions konfiguration. Använd New-PSSessionConfiguration-cmdleten om du vill skapa en konfigurations fil för sessionen. Mer information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](about_Session_Configuration_Files.md).

Sessionsbaserade är en funktion i WS-Management-baserad (Web Services for Management), PowerShell-fjärrkommunikation. De används endast när du använder cmdletarna New-PSSession, Invoke-Command eller Enter-PSSession för att ansluta till en fjärrdator.

Obs: om du vill hantera sessionens konfigurationer startar du PowerShell med alternativet "kör som administratör".

Om sessionsbaserade

Varje PowerShell-session använder en konfiguration av sessionen. Detta omfattar permanenta sessioner som du skapar med hjälp av New-PSSession-eller Enter-PSSession-cmdletar och de tillfälliga sessioner som PowerShell skapar när du använder parametern ComputerName för en cmdlet som använder WS-Management-baserad fjärr kommunikations teknik, till exempel Invoke-Command.

Administratörer kan använda sessionsbaserade för att skydda datorns resurser och skapa anpassade miljöer för användare som ansluter till datorn. Du kan till exempel använda en sessionshantering för att begränsa storleken på objekt som datorn tar emot i sessionen, för att definiera språk läge för sessionen och för att ange vilka cmdlets, providers och funktioner som är tillgängliga i sessionen.

Genom att konfigurera säkerhets beskrivningen för en konfiguration av sessionen bestämmer du vem som kan använda sessionen för att ansluta till datorn.
Användarna måste ha behörigheten Kör för att kunna använda den i en session. Om en användare inte har de behörigheter som krävs för att använda någon av sessionens konfigurationer på en dator, kan användaren inte fjärrans luta till datorn.

Som standard har bara administratörer på datorn behörighet att använda standardkonfigurationerna för sessioner. Men du kan ändra säkerhets beskrivarna så att alla, ingen eller bara valda användare kan använda dem på din dator.

Inbyggda sessionsbaserade konfigurationer

PowerShell 3,0 innehåller inbyggda sessionsinställningar som heter Microsoft. PowerShell och Microsoft. PowerShell. Workflow. På datorer som kör 64-bitars versioner av Windows tillhandahåller PowerShell även Microsoft. PowerShell32, en 32-bitars konfiguration av sessionen.

Konfigurationen av Microsoft. PowerShell-sessionen används för sessioner som standard, det vill säga när ett kommando för att skapa en session inte innehåller parametern ConfigurationName för cmdleten New-PSSession, retur-PSSession eller Invoke-Command.

Säkerhets beskrivningarna för standardsessions-konfigurationerna tillåter bara medlemmar i gruppen Administratörer på den lokala datorn att använda dem. Därför kan endast medlemmar i gruppen Administratörer fjärrans luta till datorn om du inte ändrar standardinställningarna.

Du kan ändra standardkonfigurationerna för sessioner med hjälp av $PSSessionConfigurationName Preference-variabeln. Mer information finns i about_Preference_Variables.

Visa sessionsinställningar på den lokala datorn

Använd Get-PSSessionConfiguration-cmdleten för att hämta sessionsinställningar på den lokala datorn.

Skriv till exempel:

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property Name, Permission

Name       : microsoft.powershell
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell.workflow
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell32
Permission : BUILTIN\Administrators AccessAllowed
```

Konfigurationsobjektet för sessionen expanderas i PowerShell 3,0 för att visa egenskaperna för den konfiguration av sessionen som konfigureras med hjälp av en konfigurations fil för sessionen.

Om du till exempel vill visa alla egenskaper för ett konfigurations objekt för session skriver du:

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property *
```

Du kan också använda WSMan-providern i PowerShell för att Visa sessionsinställningar. WSMan-providern skapar en WSMAN:-enhet i sessionen.

I WSMAN:-enheten finns sessionens konfigurationer i noden plugin-program. (Alla användarsessioner finns i plugin-noden, men det finns objekt i noden plugin-program som inte är sessionsbaserade.)

Om du till exempel vill visa sessionens konfigurationer på den lokala datorn skriver du:

```powershell
PS C:> dir wsman:\localhost\plugin\microsoft*

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

Visa sessionsinställningar på en fjärrdator

Om du vill visa sessionsinställningar på en fjärrdator använder du cmdleten Connect-WSMan för att lägga till en anteckning för fjärrdatorn på WSMAN:-enheten på den lokala datorn och använder sedan WSMAN:-enheten för att Visa sessionens konfigurationer.

Följande kommando lägger till exempel till en nod för fjärrdatorn Server01 till WSMAN: Drive på den lokala datorn.

```powershell
PS C:> Connect-WSMan server01.corp.fabrikam.com
```

När kommandot har slutförts kan du navigera till noden för Server01-datorn för att Visa sessionens konfigurationer.

Ett exempel:

```powershell
PS C:> cd wsman:

PS WSMan:> dir

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01.corp.fabrikam.com                    Container

PS WSMan:> dir server01\plugin\

WSManConfig: Microsoft.WSMan.Management\WSMan::server01.corp.fabrikam.com\Pl
ugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

Ändra säkerhets beskrivningen för en sessions konfiguration

I Windows Server 2012 och senare versioner av Windows Server, aktive ras de inbyggda sessionerna för fjärran vändare som standard. I andra versioner av Windows som stöds måste du ändra säkerhets beskrivarna för sessionens konfigurationer för att tillåta fjärråtkomst.

Använd Enable-PSRemoting-cmdleten om du vill aktivera fjärråtkomst till sessionsbaserade på datorn. Den här cmdleten skapar två sessionsbaserade konfigurationer:

- med namnet definierat som: "PowerShell." + "aktuell PowerShell-version"
- med namnet "PowerShell. 6", som inte är knutet till någon speciell PowerShell-version.

Som standard har bara medlemmar i gruppen Administratörer på datorn behörigheten Kör för standardsession-konfigurationerna, men du kan ändra säkerhets beskrivarna på standardkonfigurationerna för sessioner och eventuella sessionsinställningar som du skapar.

Om du vill ge andra användare behörighet att fjärrans luta till datorn använder du Set-PSSessionConfiguration-cmdleten för att lägga till "kör"-behörigheter för dessa användare till säkerhets beskrivarna i Microsoft. PowerShell-och Microsoft. PowerShell32-sessionens konfigurationer.

Följande kommando öppnar exempelvis en egenskaps sida där du kan ändra säkerhets beskrivningen för standardsessions-konfigurationen i Microsoft. PowerShell.

```powershell
Set-PSSessionConfiguration -name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

Använd Disable-PSSessionConfiguration-cmdleten om du vill neka alla behörighet till alla sessioner på datorn. Följande kommando inaktiverar till exempel standardkonfigurationerna för sessioner på datorn.

```powershell
PS C:> Disable-PSSessionConfiguration -Name Microsoft.PowerShell
```

För att förhindra att fjärran vändare ansluter till datorn, men Tillåt att lokala användare ansluter, använder du Disable-PSRemoting-cmdleten. Disable-PSRemoting lägger till en "Network_Deny_All"-post till alla sessionsinställningar på datorn.

```powershell
PS C:> Disable-PSRemoting
```

Om du vill tillåta fjärran vändare att använda alla sessionsinställningar på datorn använder du Enable-PSRemoting-eller Enable-PSSessionConfiguration-cmdleten. Följande kommando ger till exempel fjärråtkomst till de inbyggda session-konfigurationerna.

```powershell
PS C:> Enable-PSSessionConfiguration -name Microsoft.Power*
```

Använd Set-PSSessionConfiguration-cmdleten om du vill göra andra ändringar i säkerhets beskrivningen för en konfiguration av sessionen. Använd parametern SecurityDescriptorSDDL för att skicka ett SDDL-sträng värde. Använd parametern ShowSecurityDescriptorUI för att visa en egenskaps sida för användar gränssnitt som hjälper dig att skapa en ny SDDL.

Ett exempel:

```powershell
Set-PSSessionConfiguration -Name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

Skapa en ny konfiguration av sessionen

Använd Register-PSSessionConfiguration-cmdleten om du vill skapa en ny sessionsinformation på den lokala datorn. Om du vill definiera den nya konfigurationen av sessionen kan du använda en C#-sammansättning, ett PowerShell-skript och parametrarna för Register-PSSessionConfiguration-cmdlet.

Följande kommando skapar till exempel en sessionsnyckel som är identisk med konfigurationen av Microsoft. PowerShell-sessionen, förutom att den begränsar de data som tas emot från ett fjärrkommando till 20 megabyte (MB). (Standardvärdet är 50 MB).

```powershell
Register-PSSessionConfiguration -Name NewConfig `
  -MaximumReceivedDataSizePerCommandMB 20
```

När du skapar en sessionsnyckel kan du hantera den med hjälp av de andra cmdletarna för sessions konfiguration och visas i filen WSMAN: Drive.

Mer information finns i register-PSSessionConfiguration.

Tar bort en konfiguration av sessionen

Använd Unregister-PSSessionConfiguration-cmdleten om du vill ta bort en sessionsinformation från den lokala datorn. Följande kommando tar till exempel bort konfigurationen av NewConfig-sessionen från datorn.

```powershell
PS C:> Unregister-PSSessionConfiguration -Name NewConfig
```

Mer information finns i unregister-PSSessionConfiguration.

Återställa en konfiguration av sessionen

Använd Enable-PSRemoting-cmdleten om du vill återställa en standardsessions-konfiguration som har tagits bort (avregistreras) av misstag.

Enable-PSRemoting-cmdleten återskapar alla standardkonfigurationer för sessioner som inte finns på datorn. Den skriver inte över eller ändrar egenskapsvärdena för befintliga sessioner.

Om du vill återställa de ursprungliga egenskapsvärdena för en standardsessions-konfiguration använder du Unregister-PSSessionConfiguration för att ta bort konfigurationen och använder sedan Enable-PSRemoting-cmdlet för att återskapa den.

Välja en konfiguration av sessionen

Om du vill välja en viss sessionsinformation för en session använder du parametern ConfigurationName för New-PSSession, retur-PSSession eller Invoke-Command.

Detta kommando använder till exempel cmdleten New-PSSession för att starta en PSSession på Server01-datorn. Kommandot använder parametern ConfigurationName för att välja WithProfile-konfigurationen på Server01-datorn.

```powershell
PS C:> New-PSSession -ComputerName Server01 -ConfigurationName WithProfile
```

Kommandot fungerar bara om den aktuella användaren har behörighet att använda WithProfile-sessionen eller kan ange autentiseringsuppgifterna för en användare som har de behörigheter som krävs.

Du kan också använda variabeln $PSSessionConfigurationName för att ändra standard konfigurationen för sessionen på datorn. Mer information om variabeln $PSSessionConfigurationName finns about_Preference_Variables.

## <a name="keywords"></a>RESERVERADE

about_Endpoints about_SessionConfigurations

## <a name="see-also"></a>SE ÄVEN

[about_Preference_Variables](about_Preference_Variables.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Session_Configuration_Files](about_Session_Configuration_Files.md)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Disable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[Aktivera – PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[Get-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[New-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[Registrera – PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[Set-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[Test-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[Avregistrera-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)
