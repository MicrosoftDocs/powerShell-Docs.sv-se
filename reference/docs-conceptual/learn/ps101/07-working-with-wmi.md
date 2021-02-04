---
title: Arbeta med WMI
description: PowerShell har haft cmdletar för att arbeta med WMI sedan början.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 119bb3381ee55c70340da89d1c0690d84b3e70d2
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216132"
---
# <a name="chapter-7---working-with-wmi"></a>Kapitel 7 – arbeta med WMI

## <a name="wmi-and-cim"></a>WMI och CIM

PowerShell levereras som standard med cmdlets för att arbeta med andra tekniker som Windows Management Instrumentation (WMI). Det finns flera inbyggda WMI-cmdletar som finns i PowerShell utan att behöva installera ytterligare program vara eller moduler.

PowerShell har haft cmdletar för att arbeta med WMI sedan början. `Get-Command` kan användas för att avgöra vilka WMI-cmdletar som finns i PowerShell. Följande resultat är från min Windows 10 Lab Environment-dator som kör PowerShell version 5,1. Resultaten kan variera beroende på vilken PowerShell-version som körs.

```powershell
Get-Command -Noun WMI*
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-WmiObject                                      3.1.0.0    Microsof...
Cmdlet          Invoke-WmiMethod                                   3.1.0.0    Microsof...
Cmdlet          Register-WmiEvent                                  3.1.0.0    Microsof...
Cmdlet          Remove-WmiObject                                   3.1.0.0    Microsof...
Cmdlet          Set-WmiInstance                                    3.1.0.0    Microsof...
```

CIM-cmdlets (Common Information Model) introducerades i PowerShell version 3,0. CIM-cmdletarna är utformade så att de kan användas på både Windows-och icke-Windows-datorer. WMI-cmdletarna är inaktuella, så min rekommendation är att använda CIM-cmdlets i stället för de äldre WMI-datorerna.

CIM-cmdletarna finns i en modul. Om du vill hämta en lista över CIM-cmdletar använder du `Get-Command` med parametern **modul** som visas i följande exempel.

```powershell
Get-Command -Module CimCmdlets
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Export-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Get-CimAssociatedInstance                          1.0.0.0    CimCmdlets
Cmdlet          Get-CimClass                                       1.0.0.0    CimCmdlets
Cmdlet          Get-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          Get-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          Import-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Invoke-CimMethod                                   1.0.0.0    CimCmdlets
Cmdlet          New-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          New-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          New-CimSessionOption                               1.0.0.0    CimCmdlets
Cmdlet          Register-CimIndicationEvent                        1.0.0.0    CimCmdlets
Cmdlet          Remove-CimInstance                                 1.0.0.0    CimCmdlets
Cmdlet          Remove-CimSession                                  1.0.0.0    CimCmdlets
Cmdlet          Set-CimInstance                                    1.0.0.0    CimCmdlets
```

CIM-cmdletarna tillåter fortfarande att du arbetar med WMI, så du kan inte förväxlas när någon gör instruktionen "när jag frågar WMI med PowerShell CIM-cmdletar..."

Som tidigare nämnts är WMI en separat teknik från PowerShell och du använder bara CIM-cmdletar för att få åtkomst till WMI. Du kan hitta en gammal VBScript som använder WMI Query Language (WQL) för att fråga WMI, som i följande exempel.

```vb
strComputer = "."
Set objWMIService = GetObject("winmgmts:" _
    & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\cimv2")

Set colBIOS = objWMIService.ExecQuery _
    ("Select * from Win32_BIOS")

For each objBIOS in colBIOS
    Wscript.Echo "Manufacturer: " & objBIOS.Manufacturer
    Wscript.Echo "Name: " & objBIOS.Name
    Wscript.Echo "Serial Number: " & objBIOS.SerialNumber
    Wscript.Echo "SMBIOS Version: " & objBIOS.SMBIOSBIOSVersion
    Wscript.Echo "Version: " & objBIOS.Version
Next
```

Du kan ta WQL-frågan från den VBScript-filen och använda den med `Get-CimInstance` cmdleten utan några ändringar.

```powershell
Get-CimInstance -Query 'Select * from Win32_BIOS'
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

Det är inte hur jag normalt frågar WMI med PowerShell. Men det fungerar och gör att du enkelt kan migrera befintliga VBScript till PowerShell. När jag börjar skriva en one-liner för att fråga WMI använder jag följande syntax.

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

Om jag bara vill ha serie numret kan jag lägga till utdata till `Select-Object` och bara ange egenskapen **serialnumber** .

```powershell
Get-CimInstance -ClassName Win32_BIOS | Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

Som standard finns det flera egenskaper som hämtas bakom de scener som aldrig används.
Det kanske inte är mycket viktigt när du frågar efter WMI på den lokala datorn. Men när du har startat frågor mot fjärrdatorer är det inte bara ytterligare bearbetnings tid att returnera den informationen, utan även ytterligare onödig information att behöva hämta över nätverket. `Get-CimInstance` har en **egenskaps** parameter som begränsar den information som hämtas. Detta gör att frågan till WMI är mer effektiv.

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

Föregående resultat returnerade ett objekt. Om du vill returnera en enkel sträng använder du parametern **ExpandProperty** .

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -ExpandProperty SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

Du kan också använda det punktavgränsade formatet med syntax för att returnera en enkel sträng. Detta eliminerar behovet av att skicka vidare till `Select-Object` .

```powershell
(Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber).SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

## <a name="query-remote-computers-with-the-cim-cmdlets"></a>Fråga fjärrdatorer med CIM-cmdletar

Jag kör fortfarande PowerShell som en lokal administratör som är en domän användare. När jag försöker fråga efter information från en fjärrdator med hjälp av `Get-CimInstance` cmdleten visas ett fel meddelande om nekad åtkomst.

```powershell
Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
```

```Output
Get-CimInstance : Access is denied.
At line:1 char:1
+ Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
+ ``````````````````````````````````````````````````````~~
    + CategoryInfo          : PermissionDenied: (root\cimv2:Win32_BIOS:String) [Get-CimI
   nstance], CimException
    + FullyQualifiedErrorId : HRESULT 0x80070005,Microsoft.Management.Infrastructure.Cim
   Cmdlets.GetCimInstanceCommand
    + PSComputerName        : dc01
```

Många personer har säkerhets problem när de kommer till PowerShell, men sanningen har exakt samma behörigheter i PowerShell som du gör i det grafiska användar gränssnittet. Varken mer eller mindre. Problemet i föregående exempel är att användaren som kör PowerShell inte har behörighet att fråga WMI-information från DC01-servern. Jag kan starta om PowerShell som domän administratör eftersom det `Get-CimInstance` inte finns någon **Credential** -parameter. Men litar på mig, som inte är en bra idé, eftersom allt som jag kör från PowerShell skulle köras som en domän administratör. Det kan vara farligt från en säkerhets synpunkt beroende på situationen.

Genom att använda principen om minsta behörighet, höjer jag till mitt domän administratörs konto på ett per kommando med hjälp av parametern **Credential** , om ett kommando har ett. `Get-CimInstance` har inte någon **Credential** -parameter, så lösningen i det här scenariot är att skapa en **CimSession** först. Använd sedan **CimSession** i stället för ett dator namn för att fråga WMI på fjärrdatorn.

```powershell
$CimSession = New-CimSession -ComputerName dc01 -Credential (Get-Credential)
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

CIM-sessionen lagrades i en variabel med namnet `$CimSession` . Observera att jag också har angett `Get-Credential` cmdleten inom parentes så att den körs först, efter fråga mig om alternativa autentiseringsuppgifter innan du skapar den nya sessionen. Jag visar ett annat effektivt sätt att ange alternativa autentiseringsuppgifter senare i det här kapitlet, men det är viktigt att förstå detta grundläggande koncept innan du gör det mer komplicerat.

CIM-sessionen som skapades i föregående exempel kan nu användas med `Get-CimInstance` cmdleten för att fråga BIOS-informationen från WMI på fjärrdatorn.

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01
```

Det finns flera ytterligare fördelar med att använda CIM-sessioner i stället för att bara ange ett dator namn. När du kör flera frågor till samma dator är det mer effektivt att använda en CIM-session än att använda dator namnet för varje fråga. När du skapar en CIM-session konfigureras bara anslutningen en gång.
Sedan använder flera frågor samma session för att hämta information. Om du använder dator namnet måste cmdletarna konfigureras och avskilja anslutningen till varje enskild fråga.

`Get-CimInstance`Cmdlet: en använder WSMan-protokollet som standard, vilket innebär att fjärrdatorn behöver PowerShell version 3,0 eller senare för att ansluta. Det är faktiskt inte den PowerShell-version som är viktig, den är stack versionen. Stack versionen kan fastställas med hjälp av `Test-WSMan` cmdleten.
Den måste vara version 3,0. Det är den version du hittar med PowerShell version 3,0 och högre.

```powershell
Test-WSMan -ComputerName dc01
```

```Output
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd
ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd
ProductVendor   : Microsoft Corporation
ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 3.0
```

Äldre WMI-cmdletar använder DCOM-protokollet, som är kompatibelt med äldre versioner av Windows. Men DCOM blockeras vanligt vis av brand väggen i nyare versioner av Windows. `New-CimSessionOption`Med cmdleten kan du skapa en DCOM-protokoll anslutning för användning med `New-CimSession` . Detta gör att `Get-CimInstance` cmdleten kan användas för att kommunicera med Windows-versioner som gamla som Windows Server 2000. Det innebär också att PowerShell inte krävs på fjärrdatorn när du använder `Get-CimInstance` cmdleten med en CimSession som har kon figurer ATS för att använda DCOM-protokollet.

Skapa alternativet DCOM-protokoll med hjälp av `New-CimSessionOption` cmdleten och lagra det i en variabel.

```powershell
$DCOM = New-CimSessionOption -Protocol Dcom
```

För att vara effektiv kan du lagra domän administratören eller utökade autentiseringsuppgifter i en variabel så att du inte behöver ange dem hela tiden för varje kommando.

```powershell
$Cred = Get-Credential
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

Jag har en server med namnet SQL03 som kör Windows Server 2008 (ej R2). Det är det senaste operativ systemet Windows Server som inte har PowerShell installerat som standard.

Skapa en **CimSession** till SQL03 med DCOM-protokollet.

```powershell
$CimSession = New-CimSession -ComputerName sql03 -SessionOption $DCOM -Credential $Cred
```

Observera i föregående kommando, den här gången jag angav variabeln med namnet `$Cred` som värde för parametern **Credential** i stället för att behöva ange dem manuellt.

Resultatet av frågan är detsamma oavsett vilket underliggande protokoll som används.

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

`Get-CimSession`Cmdleten används för att se vilka **CimSessions** som för närvarande är anslutna och vilka protokoll de använder.

```powershell
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : 80742787-e38e-41b1-a7d7-fa1369cf1402
ComputerName : dc01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : 8fcabd81-43cf-4682-bd53-ccce1e24aecb
ComputerName : sql03
Protocol     : DCOM
```

Hämta och lagra båda de tidigare skapade **CimSessions** i en variabel med namnet `$CimSession` .

```powershell
$CimSession = Get-CimSession
```

Fråga båda datorerna med ett kommando, ett med hjälp av WSMan-protokollet och det andra med DCOM.

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01

SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

Jag har skrivit många blogg artiklar om WMI-och CIM-cmdletar. En av de mest användbara är om en funktion som jag skapade för att automatiskt avgöra om WSMan eller DCOM ska användas och konfigurera CIM-sessionen automatiskt utan att behöva ta reda på vilken som manuellt. Blogg artikeln heter [PowerShell-funktionen för att skapa CimSessions till fjärrdatorer med fallback till DCOM][].

När du är klar med CIM-sessionerna bör du ta bort dem med `Remove-CimSession` cmdleten. Ta bort alla CIM-sessioner genom att bara skicka vidare `Get-CimSession` till `Remove-CimSession` .

```powershell
Get-CimSession | Remove-CimSession
```

## <a name="summary"></a>Sammanfattning

I det här kapitlet har du lärt dig att använda PowerShell för att arbeta med WMI på både lokala och fjärranslutna datorer. Du har också lärt dig hur du använder CIM-cmdletar för att arbeta med fjärrdatorer med både WSMan-eller DCOM-protokollet.

## <a name="review"></a>Genomgång

1. Vad är skillnaden i WMI-och CIM-cmdletarna?
1. Som standard använder-protokollet `Get-CimInstance` cmdleten?
1. Vilka är fördelarna med att använda en CIM-session i stället för att ange ett dator namn med `Get-CimInstance` ?
1. Hur kan du ange ett annat protokoll än det som är standard som används med `Get-CimInstance` ?
1. Hur stänger eller tar du bort CIM-sessioner?

## <a name="recommended-reading"></a>Rekommenderad läsning

- [about_WMI][]
- [about_WMI_Cmdlets][]
- [about_WQL][]
- [CimCmdlets-modul][]
- [Video: använda CIM-cmdlets och CIM-sessioner][]

<!-- link references -->
[about_WMI]: /powershell/module/microsoft.powershell.core/about/about_wmi
[about_WMI_Cmdlets]: /powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets
[about_WQL]: /powershell/module/microsoft.powershell.core/about/about_wql
[CimCmdlets-modul]: /powershell/module/cimcmdlets/
[Video: använda CIM-cmdlets och CIM-sessioner]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[PowerShell-funktion för att skapa CimSessions till fjärrdatorer med återgång till DCOM]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
