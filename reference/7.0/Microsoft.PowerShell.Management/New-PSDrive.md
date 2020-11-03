---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-psdrive?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSDrive
ms.openlocfilehash: 71605d2c630cb456a44226ddbe2a99f92347b617
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262838"
---
# New-PSDrive

## SAMMANFATTNING
Skapar tillfälliga och beständiga mappade nätverks enheter.

## SYNTAX

### Alla

```
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Description <String>]
 [-Scope <String>] [-Persist] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`New-PSDrive`Cmdleten skapar temporära och beständiga enheter som mappas till eller associeras med en plats i ett data lager, till exempel en nätverks enhet, en katalog på den lokala datorn eller en register nyckel och beständiga Windows-anslutna nätverks enheter som är associerade med en fil system plats på en fjärrdator.

Tillfälliga enheter finns bara i den aktuella PowerShell-sessionen och i sessioner som du skapar i den aktuella sessionen. De kan ha ett namn som är giltigt i PowerShell och som kan mappas till en lokal eller fjärran sluten resurs. Du kan använda tillfälliga PowerShell-enheter för att komma åt data i det associerade data lagret, precis som du gör med en mappad nätverks enhet. Du kan ändra platser till enheten, genom att använda `Set-Location` och komma åt enhetens innehåll med hjälp av `Get-Item` eller `Get-ChildItem` .

Eftersom temporära enheter bara känner till PowerShell kan du inte komma åt dem med hjälp av Utforskaren, Windows Management Instrumentation (WMI), Component Object Model (COM), Microsoft .NET Framework eller med verktyg som t. ex. **net use**.

Följande funktioner har lagts till `New-PSDrive` i PowerShell 3,0:

- Mappade nätverks enheter. Du kan använda **persist** -parametern för `New-PSDrive` för att skapa Windows-mappade nätverks enheter. Till skillnad från tillfälliga PowerShell-enheter är Windows-mappade nätverks enheter inte sessionsbaserade. De sparas i Windows och de kan hanteras med hjälp av standard verktyg för Windows, till exempel Utforskaren och **net use**. Mappade nätverks enheter måste ha ett enhets betecknings namn och vara anslutet till en fjärrplats i fil systemet. När ditt kommando omfattas lokalt, ingen punkt-källa, behålls inte den **kvarhållna** parametern när en **PSDrive** har skapats utanför den omfattning där kommandot körs. Om du kör `New-PSDrive` i ett skript och du vill att enheten ska vara oändlig, måste du punkt-källa skriptet. För bästa resultat bör du lägga till parametern **scope** i kommandot och ange värdet **Global** för att tvinga en ny enhet att kvarstå i oändlighet. Mer information om punkt-källa finns [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing).
- Externa enheter. När en extern enhet är ansluten till datorn lägger PowerShell automatiskt till en **PSDrive** i fil systemet som representerar den nya enheten. Du behöver inte starta om PowerShell. När en extern enhet kopplas bort från datorn tar PowerShell automatiskt bort den **PSDrive** som representerar den borttagna enheten.
- Autentiseringsuppgifter för Universal Naming Convention (UNC) sökvägar.

När värdet för **rot** parametern är en UNC-sökväg, till exempel `\\Server\Share` , används den autentiseringsuppgift som anges i värdet för parametern **Credential** för att skapa **PSDrive**. Annars gäller inte **autentiseringsuppgiften** när du skapar nya fil system enheter.

I vissa kod exempel används ihopbuntning för att minska rad längden och förbättra läsbarheten. Mer information finns i [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).

## EXEMPEL

### Exempel 1: skapa en tillfällig enhet som är mappad till en nätverks resurs

I det här exemplet skapas en tillfällig PowerShell-enhet som är mappad till en nätverks resurs.

```powershell
New-PSDrive -Name "Public" -PSProvider "FileSystem" -Root "\\Server01\Public"
```

```Output
Name       Provider      Root
----       --------      ----
Public     FileSystem    \\Server01\Public
```

`New-PSDrive` använder **Name** -parametern för att ange PowerShell-enhet med namnet `Public` och parametern **PSProvider** för att ange PowerShell- `FileSystem` providern. **Rot** parametern anger nätverks RESURSens UNC-sökväg.

Så här visar du innehållet från en PowerShell-session: `Get-ChildItem -Path Public:`

### Exempel 2: skapa en tillfällig enhet som är mappad till en lokal katalog

I det här exemplet skapas en tillfällig PowerShell-enhet som ger åtkomst till en katalog på den lokala datorn.

```powershell
$parameters = @{
    Name = "MyDocs"
    PSProvider = "FileSystem"
    Root = "C:\Users\User01\Documents"
    Description = "Maps to my My Documents folder."
}
New-PSDrive @parameters
```

```Output
Name        Provider      Root
----        --------      ----
MyDocs      FileSystem    C:\Users\User01\Documents
```

Ihopbuntning skapar parameter nycklar och-värden. Parametern **Name** anger enhets namnet, mina **dokument**. Parametern **PSProvider** anger PowerShell- `FileSystem` providern. **Root** anger den lokala datorns katalog. Parametern **Description** beskriver enhetens syfte. `New-PSDrive` använder splatted-parametrarna för att skapa `MyDocs` enheten.

Så här visar du innehållet från en PowerShell-session: `Get-ChildItem -Path MyDocs:`

### Exempel 3: skapa en tillfällig enhet för en register nyckel

I det här exemplet skapas en tillfällig PowerShell-enhet som ger åtkomst till en register nyckel. Den skapar en enhet med namnet Company som är mappad till `HKLM:\Software\MyCompany` register nyckeln.

```powershell
New-PSDrive -Name "MyCompany" -PSProvider "Registry" -Root "HKLM:\Software\MyCompany"
```

```Output
Name           Provider      Root
----           --------      ----
MyCompany      Registry      HKLM:\Software\MyCompany
```

`New-PSDrive` använder **Name** -parametern för att ange PowerShell-enhet med namnet `MyCompany` och parametern **PSProvider** för att ange PowerShell- `Registry` providern. **Rot** parametern anger register platsen.

Så här visar du innehållet från en PowerShell-session: `Get-ChildItem -Path MyCompany:`

### Exempel 4: skapa en beständig mappad nätverks enhet med hjälp av autentiseringsuppgifter

Det här exemplet mappar en nätverks enhet som autentiseras med ett domän tjänst kontos autentiseringsuppgifter.
Mer information om **PSCredential** -objektet som lagrar autentiseringsuppgifter och hur lösen ord lagras som en **SecureString** finns i Beskrivning av **Credential** -parametern.

```powershell
$cred = Get-Credential -Credential Contoso\ServiceAccount
New-PSDrive -Name "S" -Root "\\Server01\Scripts" -Persist -PSProvider "FileSystem" -Credential $cred
Net Use
```

```Output
Status       Local     Remote                    Network
---------------------------------------------------------
OK           S:        \\Server01\Scripts        Microsoft Windows Network
```

> [!NOTE]
> Kom ihåg att om du använder ovanstående kodfragment i ett skript, ställer du in värdet för **scope** -parametern till "global" för att se till att enheten fortfarande befinner sig utanför det aktuella omfånget.

`$cred`Variabeln lagrar ett **PSCredential** -objekt som innehåller tjänst kontots autentiseringsuppgifter. `Get-Credential` du blir ombedd att ange lösen ordet som lagras i en **SecureString**.

`New-PSDrive` skapar den mappade nätverks enheten genom att använda flera parametrar. **Namn** anger `S` enhets beteckningen som Windows accepterar. och **rot** definierar `\\Server01\Scripts` som plats på en fjärrdator. **Behåll** skapar en Windows-mappad nätverks enhet som sparas på den lokala datorn. **PSProvider** anger `FileSystem` providern. **Autentiseringsuppgiften** använder `$cred` variabeln för att hämta autentiseringsuppgifterna för tjänst kontot för autentisering.

Den mappade enheten kan visas på den lokala datorn i PowerShell-sessioner, Utforskaren och med verktyg som t. ex. **net use**. Så här visar du innehållet från en PowerShell-session: `Get-ChildItem -Path S:`

### Exempel 5: skapa beständiga och temporära enheter

I det här exemplet visas skillnaden mellan en beständig mappad nätverks enhet och en tillfällig PowerShell-enhet som är mappad till samma nätverks resurs.

Om du stänger PowerShell-sessionen och sedan öppnar en ny session, är den tillfälliga `PSDrive:` inte tillgänglig, men den permanenta `X:` enheten är tillgänglig. När du bestämmer vilken metod som ska användas för att mappa nätverks enheter bör du tänka på hur du ska använda enheten. Till exempel om det måste vara beständigt och om enheten ska vara synlig för andra Windows-funktioner.

```powershell
# Create a temporary PowerShell drive called PSDrive:
# that's mapped to the \\Server01\Public network share.
New-PSDrive -Name "PSDrive" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Use the Persist parameter of New-PSDrive to create the X: mapped network drive,
# which is also mapped to the \\Server01\Public network share.
New-PSDrive -Persist -Name "X" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Now, you can use the Get-PSDrive drive cmdlet to examine the two drives.
# The drives appear to be the same, although the network share name appears only
# in the root of the PSDrive: drive.
Get-PSDrive -Name "PSDrive", "X"
```

```Output
Name       Provider      Root
----       --------      ----

PsDrive    FileSystem    \\Server01\public
X          FileSystem    X:\
```

```powershell
# Get-Member cmdlet shows that the drives have the same object type,
# System.Management.Automation.PSDriveInfo.
Get-PSDrive "PSDrive", "x" | Get-Member
```

```Output
TypeName: System.Management.Automation.PSDriveInfo

Name                MemberType   Definition
----                ----------   ----------
CompareTo           Method       System.Int32 CompareTo(PSDriveInfo drive),
Equals              Method       System.Boolean Equals(Object obj),
GetHashCode         Method       System.Int32 GetHashCode()
...
```

```powershell
# Net Use and Get-CimInstance for the Win32_LogicalDisk class,
# and Win32_NetworkConnection class find only the persistent X: drive.
# PowerShell temporary drives are known only to PowerShell.
Net Use
Get-CimInstance Win32_LogicalDisk | Format-Table -Property DeviceID
Get-CimInstance Win32_NetworkConnection
```

```Output
Status       Local     Remote                    Network
--------------------------------------------------------
OK           X:        \\contoso-pc\data         Microsoft Windows Network

deviceid
--------
C:
D:
X:

LocalName    RemoteName              ConnectionState          Status
---------    ----------              ---------------          ------
X:           \\products\public       Disconnected             Unavailable
```

## PARAMETRAR

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Standard är den aktuella användaren.

Eftersom PowerShell 3,0, när värdet för **rot** parametern är en UNC-sökväg, kan du använda autentiseringsuppgifter för att skapa fil system enheter.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange lösen ordet.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Beskrivning

Anger en kort text Beskrivning av enheten. Skriv valfri sträng.

Om du vill se beskrivningar av alla enheter i sessionen `Get-PSDrive | Format-Table Name, Description` .

Om du vill se en beskrivning av en viss enhet skriver du `(Get-PSDrive <DriveName>).Description` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Anger ett namn på den nya enheten. Använd en enhets beteckning för beständiga mappade nätverks enheter. För temporära PowerShell-enheter är du inte begränsad till enhets beteckningar, Använd en giltig sträng.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Behåll

Anger att denna cmdlet skapar en Windows-mappad nätverks enhet. **Persist** -parametern är endast tillgänglig i Windows.

Mappade nätverks enheter sparas i Windows på den lokala datorn. De är beständiga, inte sessionsbaserade, och kan visas och hanteras i Utforskaren och andra verktyg.

När du omfångerar kommandot lokalt, utan punkt-källa, behålls inte den **kvarhållna** parametern skapandet av en **PSDrive** utanför den omfattning där du kör kommandot. Om du kör `New-PSDrive` inuti ett skript och du vill att den nya enheten ska vara oändlig, måste du punkt-källa skriptet. För bästa resultat bör du, för att tvinga en ny enhet att behållas, ange **Global** som värde för **omfattnings** parametern och inkludera **Spara** i kommandot.

Namnet på enheten måste vara en bokstav, till exempel `D` eller `E` . Värdet för **rot** parametern måste vara en UNC-sökväg till en annan dator. Värdet för parametern **PSProvider** måste vara `FileSystem` .

Använd cmdleten om du vill koppla från en Windows-mappad nätverks enhet `Remove-PSDrive` . När du kopplar från en Windows-mappad nätverks enhet tas mappningen bort permanent från datorn och tas inte bort från den aktuella sessionen.

Mappade nätverks enheter är speciella för ett användar konto. Mappade enheter som har skapats i utökade sessioner eller sessioner som använder autentiseringsuppgifter för en annan användare är inte synliga i sessioner som har startats med andra autentiseringsuppgifter.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

Anger den PowerShell-provider som stöder enheter av den här typen.

Om enheten till exempel är kopplad till en nätverks resurs eller fil system katalog är PowerShell-providern `FileSystem` . Om enheten är associerad med en register nyckel är providern `Registry` .

Tillfälliga PowerShell-enheter kan associeras med valfri PowerShell-Provider. Mappade nätverks enheter kan endast kopplas till `FileSystem` providern.

Om du vill se en lista över providers i PowerShell-sessionen använder du `Get-PSProvider` cmdleten.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Rot

Anger den data lager plats som en PowerShell-enhet mappas till.

Du kan till exempel ange en nätverks resurs, till exempel `\\Server01\Public` en lokal katalog, till exempel `C:\Program Files` eller en register nyckel, till exempel `HKLM:\Software\Microsoft` .

Tillfälliga PowerShell-enheter kan associeras med en lokal plats eller en annan plats på en leverantörs enhet som stöds. Mappade nätverks enheter kan bara kopplas till en fil system plats på en fjärrdator.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Omfattning

Anger ett omfång för enheten. De acceptabla värdena för den här parametern är: **globalt** , **lokalt** och **skript** , eller ett tal i förhållande till det aktuella omfånget. Omfattnings nummer 0 till och med antalet omfattningar. Det aktuella omfångs numret är 0 och dess överordnade är 1. Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte pipeline-ininformation till denna cmdlet.

## UTDATA

### System.Management.Automation.PSDriveInfo

## ANTECKNINGAR

`New-PSDrive` är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i sessionen använder du `Get-PSProvider` . Mer information om providrar finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

Mappade nätverks enheter är speciella för ett användar konto. Mappade enheter som har skapats i utökade sessioner eller sessioner som använder autentiseringsuppgifter för en annan användare är inte synliga i sessioner som har startats med andra autentiseringsuppgifter.

## RELATERADE LÄNKAR

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Get-PSDrive](Get-PSDrive.md)

[Remove-PSDrive](Remove-PSDrive.md)
