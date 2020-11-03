---
description: Beskriver körnings principerna för PowerShell och förklarar hur du hanterar dem.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Execution_Policies
ms.openlocfilehash: 3332adb76c76fa644d23060abe2af43bd45a15a6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272157"
---
# <a name="about-execution-policies"></a>Om körnings principer

## <a name="short-description"></a>Kort beskrivning

Beskriver körnings principerna för PowerShell och förklarar hur du hanterar dem.

## <a name="long-description"></a>Lång beskrivning

PowerShell: s körnings princip är en säkerhetsfunktion som styr de villkor under vilka PowerShell läser in konfigurationsfiler och kör skript. Den här funktionen hjälper till att förhindra körning av skadliga skript.

På en Windows-dator kan du ange en körnings princip för den lokala datorn, för den aktuella användaren eller för en viss session. Du kan också använda en grupprincip inställning för att ange körnings principer för datorer och användare.

Körnings principer för den lokala datorn och den aktuella användaren lagras i registret. Du behöver inte ange körnings principer i din PowerShell-profil.
Körnings principen för en viss session lagras endast i minnet och går förlorad när sessionen stängs.

Körnings principen är inte ett säkerhets system som begränsar användar åtgärder. Användare kan till exempel enkelt kringgå en princip genom att skriva skript innehållet på kommando raden när de inte kan köra ett skript. I stället hjälper körnings principen användarna att ange grundläggande regler och förhindrar att de bryter mot dem.

## <a name="powershell-execution-policies"></a>Körnings principer för PowerShell

PowerShell-körnings principerna är följande:

### <a name="allsigned"></a>AllSigned

- Skript kan köras.
- Kräver att alla skript och konfigurationsfiler signeras av en betrodd utgivare, inklusive skript som du skriver på den lokala datorn.
- Du får frågan innan du kör skript från utgivare som du ännu inte har klassificerat som betrott eller ej betrott.
- Risker som kör signerade, men skadliga, skript.

### <a name="bypass"></a>Förbikoppling

- Inget blockeras och det finns inga varningar eller prompter.
- Den här körnings principen är utformad för konfigurationer där ett PowerShell-skript är inbyggt i ett större program eller för konfigurationer där PowerShell är grunden för ett program som har en egen säkerhets modell.

### <a name="default"></a>Default

- Anger standard körnings principen.
- **Begränsat** för Windows-klienter.
- **RemoteSigned** för Windows-servrar.

### <a name="remotesigned"></a>RemoteSigned

- Standard körnings principen för Windows Server-datorer.
- Skript kan köras.
- Kräver en digital signatur från en betrodd utgivare på skript och konfigurationsfiler som hämtas från Internet, som inkluderar e-post och snabb meddelande program.
- Kräver inte digitala signaturer i skript som är skrivna på den lokala datorn och som inte har hämtats från Internet.
- Kör skript som hämtas från Internet och inte signerade, om skripten är avblockerade, till exempel genom att använda `Unblock-File` cmdleten.
- Risker som kör osignerade skript från andra källor än Internet och signerade skript som kan vara skadliga.

### <a name="restricted"></a>Begränsade

- Standard körnings principen för Windows-klientdatorer.
- Tillåter enskilda kommandon, men tillåter inte skript.
- Förhindrar körning av alla skriptfiler, inklusive formatering och konfigurationsfiler ( `.ps1xml` ), modulens skript fil ( `.psm1` ) och PowerShell-profiler ( `.ps1` ).

### <a name="undefined"></a>Undefined (Odefinierad)

- Ingen körnings princip har angetts i det aktuella omfånget.
- Om körnings principen i alla omfattningar är **Odefinierad** , **begränsas** den effektiva körnings principen för Windows-klienter och **RemoteSigned** för Windows Server.

### <a name="unrestricted"></a>Obegränsat

- Osignerade skript kan köras. Det finns en risk för att skadliga skript körs.
- Varnar användaren innan skript och konfigurationsfiler som inte kommer från zonen Lokalt intranät körs.

> [!NOTE]
> På system som inte skiljer Universal Naming Convention (UNC) sökvägar från Internet vägar kan skript som identifieras av en UNC-sökväg inte tillåtas att köras med **RemoteSigned** körnings princip.

## <a name="execution-policy-scope"></a>Omfattning för körnings princip

Du kan ange en princip för körning som bara är effektiv i ett visst omfång.

Giltiga värden för **scope** är **MachinePolicy** , **UserPolicy** , **process** , **CurrentUser** och **LocalMachine**. **LocalMachine** är standard när du anger en körnings princip.

**Omfångs** värden visas i prioritetsordning. Den princip som har företräde är gällande i den aktuella sessionen, även om en mer restriktiv princip har ställts in på en lägre prioritets nivå.

Mer information finns i [set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy).

### <a name="machinepolicy"></a>MachinePolicy

Anges av en grupprincip för alla användare av datorn.

### <a name="userpolicy"></a>UserPolicy

Anges av en grupprincip för datorns aktuella användare.

### <a name="process"></a>Process

**Process** omfånget påverkar endast den aktuella PowerShell-sessionen. Körnings principen sparas i miljövariabeln i `$env:PSExecutionPolicyPreference` stället för registret. När PowerShell-sessionen stängs raderas variabeln och värdet.

### <a name="currentuser"></a>CurrentUser

Körnings principen påverkar endast den aktuella användaren. Den lagras i **HKEY_CURRENT_USER** register under nyckel.

### <a name="localmachine"></a>LocalMachine

Körnings principen påverkar alla användare på den aktuella datorn. Den lagras i **HKEY_LOCAL_MACHINE** register under nyckel.

## <a name="managing-the-execution-policy-with-powershell"></a>Hantera körnings principen med PowerShell

Använd cmdleten för att få en effektiv körnings princip för den aktuella PowerShell-sessionen `Get-ExecutionPolicy` .

Följande kommando hämtar den effektiva körnings principen:

```powershell
Get-ExecutionPolicy
```

Så här hämtar du alla körnings principer som påverkar den aktuella sessionen och visar dem i prioritetsordning:

```powershell
Get-ExecutionPolicy -List
```

Resultatet liknar följande exempel på utdata:

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine       AllSigned
```

I det här fallet är den effektiva körnings principen **RemoteSigned** eftersom körnings principen för den aktuella användaren prioriteras över körnings principen som angetts för den lokala datorn.

Om du vill hämta körnings principen för ett visst omfång använder du **omfattnings** parametern för `Get-ExecutionPolicy` .

Följande kommando hämtar till exempel körnings principen för **CurrentUser** -omfånget:

```powershell
Get-ExecutionPolicy -Scope CurrentUser
```

### <a name="change-the-execution-policy"></a>Ändra körnings principen

Använd cmdleten om du vill ändra körnings principen för PowerShell på Windows-datorn `Set-ExecutionPolicy` . Ändringen träder i kraft omedelbart. Du behöver inte starta om PowerShell.

Om du anger körnings principen för omfattningarna **LocalMachine** eller **CurrentUser** sparas ändringen i registret och fortsätter att gälla tills du ändrar den igen.

Om du anger körnings principen för **process** omfånget sparas den inte i registret. Körnings principen behålls tills den aktuella processen och eventuella underordnade processer stängs.

> [!NOTE]
> I Windows Vista och senare versioner av Windows kan du köra kommandon som ändrar körnings principen för den lokala datorn, **LocalMachine** scope, starta PowerShell med alternativet **Kör som administratör** .

Ändra körnings princip:

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName>
```

Ett exempel:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

Ange körnings principen i ett visst omfång:

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName> -Scope <scope>
```

Ett exempel:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Ett kommando för att ändra en körnings princip kan lyckas men ändå inte ändra den effektiva körnings principen.

Till exempel kan ett kommando som anger körnings principen för den lokala datorn lyckas, men åsidosätts av körnings principen för den aktuella användaren.

### <a name="remove-the-execution-policy"></a>Ta bort körnings principen

Om du vill ta bort körnings principen för ett visst omfång anger du att körnings principen ska vara **Odefinierad**.

Till exempel för att ta bort körnings principen för alla användare av den lokala datorn:

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope LocalMachine
```

Ta bort körnings principen för ett **omfång** :

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
```

Om ingen körnings princip anges i någon omfattning är den effektiva körnings principen **begränsad** , vilket är standardinställningen för Windows-klienter.

### <a name="set-a-different-policy-for-one-session"></a>Ange en annan princip för en session

Du kan använda parametern **ExecutionPolicy** för **powershell.exe** om du vill ange en körnings princip för en ny PowerShell-session. Principen påverkar endast den aktuella sessionen och de underordnade sessionerna.

Ange körnings principen för en ny session genom att starta PowerShell på kommando raden, till exempel **cmd.exe** eller från PowerShell, och sedan använda parametern **ExecutionPolicy** för **powershell.exe** för att ange körnings principen.

Ett exempel:

```powershell
powershell.exe -ExecutionPolicy AllSigned
```

Den körnings princip som du anger lagras inte i registret. I stället lagras den i `$env:PSExecutionPolicyPreference` miljö variabeln. Variabeln tas bort när du stänger sessionen där principen har angetts. Du kan inte ändra principen genom att redigera variabelvärdet.

Under sessionen har körnings principen som ställts in för sessionen företräde framför en körnings princip som anges i registret för den lokala datorn eller den aktuella användaren. Den har dock inte företräde framför körnings principen som angetts med hjälp av en grupprincip.

## <a name="use-group-policy-to-manage-execution-policy"></a>Använd grupprincip för att hantera körnings principen

Du kan använda inställningen **Aktivera** körning av skript grupprincip för att hantera körnings principen för datorer i företaget. Inställningen grupprincip åsidosätter körnings principerna som angetts i PowerShell i alla omfång.

Inställningarna för att **Aktivera skript körnings** principer är följande:

- Om du inaktiverar **Aktivera skript körning** körs inte skripten. Detta motsvarar principen för **begränsade** körningar.
- Om du aktiverar **Aktivera skript körning** kan du välja en körnings princip. Grupprincip inställningarna motsvarar följande princip inställningar för körning:

  | Grupprincip                                  | Körnings princip |
  | --------------------------------------------- | ---------------- |
  | Tillåt alla skript                             | Obegränsat     |
  | Tillåt lokala skript och fjärrsignerade skript | RemoteSigned     |
  | Tillåt endast signerade skript                     | AllSigned        |

- Om **Aktivera skript körning** inte har kon figurer ATS har det ingen påverkan. Körnings principen som angetts i PowerShell är effektiv.

Filerna PowerShellExecutionPolicy. adm och PowerShellExecutionPolicy. admx lägger till **Aktivera skript körnings** principen i noderna dator konfiguration och användar konfiguration i grupprincip redigeraren i följande sökvägar.

För Windows XP och Windows Server 2003:

Administrativa Mallar\windows-komponenter\Windows-PowerShell

För Windows Vista och senare versioner av Windows:

Administrativ Templates\Classic Administrativa mallar \
Windows Mallar\windows-komponenter\Windows PowerShell

Principer som anges i noden dator konfiguration åsidosätter principer som angetts i noden användar konfiguration.

Mer information finns i [about_Group_Policy_Settings](about_Group_Policy_Settings.md).

### <a name="execution-policy-precedence"></a>Princip prioritet för körning

När du bestämmer den effektiva körnings principen för en session, utvärderar PowerShell körnings principerna i följande prioritetsordning:

- Grupprincip: MachinePolicy
- Grupprincip: UserPolicy
- Körnings princip: process (eller `powershell.exe -ExecutionPolicy` )
- Körnings princip: CurrentUser
- Körnings princip: LocalMachine

## <a name="manage-signed-and-unsigned-scripts"></a>Hantera signerade och osignerade skript

I Windows lägger program som Internet Explorer och Microsoft Edge till en alternativ data ström till filer som hämtas. Detta markerar filen som "kommer från Internet". Om din PowerShell-körnings princip är **RemoteSigned** kör PowerShell inte osignerade skript som hämtas från Internet, som innehåller e-post och snabb meddelande program.

Du kan signera skriptet eller välja att köra ett osignerat skript utan att ändra körnings principen.

Från och med PowerShell 3,0 kan du använda cmdleten **Stream** för `Get-Item` att identifiera filer som blockeras eftersom de har hämtats från Internet. Använd `Unblock-File` cmdleten för att avblockera skripten så att du kan köra dem i PowerShell.

Mer information finns i [about_Signing](about_Signing.md), [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)och [unblock-File](xref:Microsoft.PowerShell.Utility.Unblock-File).

> [!NOTE]
> Andra metoder för att hämta filer kanske inte markerar filerna som de kommer från zonen Internet. Några exempel är:
>
> - `curl.exe`
> - `Invoke-RestMethod`
> - `Invoke-WebRequest`

## <a name="execution-policy-on-windows-server-core-and-window-nano-server"></a>Körnings princip på Windows Server Core och Window Nano Server

När PowerShell 5,1 körs på Windows Server Core eller Windows Nano Server under vissa förhållanden, kan körnings principer inte köras med följande fel:

```Output
AuthorizationManager check failed.
At line:1 char:1
+ C:\scriptpath\scriptname.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

PowerShell använder API: er i Windows Skriv bords gränssnitt ( `explorer.exe` ) för att verifiera zonen i en skript fil. Windows-gränssnittet är inte tillgängligt på Windows Server Core och Windows Nano Server.

Du kan också få det här felet på ett Windows-system om Windows Desktop Shell inte är tillgänglig eller inte svarar. Vid inloggning kan exempelvis ett PowerShell-inloggningsnamn starta körningen innan Windows-skrivbordet är klart, vilket resulterar i ett haveri.

Om du använder en körnings princip för **bypass** eller **AllSigned** krävs ingen zon kontroll som undviker problemet.

## <a name="see-also"></a>Se även

[about_Environment_Variables](about_Environment_Variables.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Signing](about_Signing.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Hämta objekt](xref:Microsoft.PowerShell.Management.Get-Item)

[PowerShell.exe Command-Line hjälp](about_PowerShell_exe.md)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Avblockera – fil](xref:Microsoft.PowerShell.Utility.Unblock-File)
