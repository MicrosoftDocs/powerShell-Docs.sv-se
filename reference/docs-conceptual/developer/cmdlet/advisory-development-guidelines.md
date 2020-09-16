---
title: Rikt linjer för utveckling av råd | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: dc8ef586954106f6d7fbce550dc22cd935018936
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782437"
---
# <a name="advisory-development-guidelines"></a>Rekommenderade riktlinjer för utveckling

I det här avsnittet beskrivs rikt linjer som du bör tänka på för att säkerställa bra utvecklings-och användar upplevelser. Ibland kan de tillkomma, och ibland kanske de inte är det.

## <a name="design-guidelines"></a>Design rikt linjer

Följande rikt linjer bör beaktas när du utformar cmdletar. När du hittar en design rikt linje som gäller din situation bör du titta närmare på kod rikt linjerna för liknande rikt linjer.

### <a name="support-an-inputobject-parameter-ad01"></a>Stöd för en InputObject-parameter (AD01)

Eftersom Windows PowerShell fungerar direkt med Microsoft .NET Framework-objekt är ett .NET Framework-objekt ofta tillgängligt som exakt matchar den typ användaren behöver för att utföra en viss åtgärd. `InputObject` är standard namnet för en parameter som tar ett sådant objekt som inmatade. Exempel: **Stop-proc-** cmdleten i StopProc- [självstudien](./stopproc-tutorial.md) definierar till exempel en `InputObject` parameter av typen process som stöder indatamängden från pipelinen. Användaren kan få en uppsättning process objekt, ändra dem för att välja de exakta objekt som ska stoppas och sedan skicka dem till **Stop-proc-** cmdleten direkt.

### <a name="support-the-force-parameter-ad02"></a>Stöd för Force-parametern (AD02)

Ibland måste en cmdlet skydda användaren från att utföra en begärd åtgärd. En sådan cmdlet bör ha stöd `Force` för en parameter så att användaren kan åsidosätta det skyddet om användaren har behörighet att utföra åtgärden.

Till exempel tar [Remove-item-](/powershell/module/microsoft.powershell.management/remove-item) cmdleten normalt inte bort en skrivskyddad fil. Denna cmdlet stöder dock en `Force` parameter så att en användare kan tvinga borttagning av en skrivskyddad fil. Om användaren redan har behörighet att ändra skrivskyddade attribut, och användaren tar bort filen, underlättar åtgärden med hjälp av `Force` parametern. Men om användaren inte har behörighet att ta bort filen `Force` har parametern ingen inverkan.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Hantera autentiseringsuppgifter via Windows PowerShell (AD03)

En cmdlet bör definiera en `Credential` parameter som representerar autentiseringsuppgifter. Den här parametern måste vara av typen [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) och måste definieras med en deklaration för Credential-attribut. Det här stödet efterfrågar automatiskt användaren för användar namnet, lösen ordet eller både och när en fullständig autentiseringsuppgift inte anges direkt. Mer information om attributet Credential finns i deklaration för [Credential-attribut](./credential-attribute-declaration.md).

### <a name="support-encoding-parameters-ad04"></a>Stöd för kodnings parametrar (AD04)

Om din cmdlet läser eller skriver text till eller från ett binärformat, till exempel att skriva till eller läsa från en fil i ett fil system, måste cmdlet: en ha en encoding-parameter som anger hur texten kodas i binärformat.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>Test-cmdletar ska returnera ett booleskt värde (AD05)

Cmdletar som utför tester mot sina resurser bör returnera en [system. Boolean](/dotnet/api/System.Boolean) -typ till pipelinen så att de kan användas i villkors uttryck.

## <a name="code-guidelines"></a>Kod rikt linjer

Följande rikt linjer bör beaktas när du skriver cmdlet-kod. När du hittar en rikt linje som gäller för din situation bör du läsa rikt linjerna för utformning av liknande rikt linjer.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>Följ klass namns konventioner för cmdlet (AC01)

Genom att följa standard konventioner för namngivning gör du dina cmdlets mer synliga och du kan hjälpa användaren att förstå exakt vad cmdletarna gör. Den här metoden är särskilt viktig för andra utvecklare som använder Windows PowerShell eftersom cmdlets är offentliga typer.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>Definiera en cmdlet i rätt namnrymd

Du definierar vanligt vis klassen för en cmdlet i ett .NET Framework namn område som lägger till ". Kommandon "i namn området som representerar den produkt där cmdleten körs. Till exempel definieras cmdletar som ingår i Windows PowerShell i `Microsoft.PowerShell.Commands` namn området.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Namnge cmdlet-klassen så att den matchar cmdlet-namnet

När du namnger .NET Framework-klassen som implementerar en cmdlet, namnger du klassen " *\<Verb>**\<Noun>**\<Command>* ", där du ersätter *\<Verb>* *\<Noun>* plats hållarna och med verbet och substantiv som används för cmdlet-namnet. Till exempel implementeras cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) av en klass som kallas `GetProcessCommand` .

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>Om ingen pipeline-inmatare åsidosätter metoden BeginProcessing (AC02)

Om cmdleten inte accepterar indata från pipelinen bör bearbetningen implementeras i metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) . Användningen av den här metoden gör det möjligt för Windows PowerShell att underhålla ordningen mellan cmdletar. Den första cmdleten i pipelinen returnerar alltid sina objekt innan de återstående cmdletarna i pipelinen får en chans att starta bearbetningen.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>För att hantera stopp förfrågningar åsidosätter du StopProcessing-metoden (AC03)

Åsidosätt metoden [system. Management. Automation. cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) så att din cmdlet kan hantera stopp signal. Vissa cmdletar tar lång tid att slutföra sin åtgärd och de kan ge lång tid mellan anrop till Windows PowerShell-körningsmiljön, till exempel när cmdleten blockerar tråden i långvariga RPC-anrop. Detta inkluderar cmdletar som gör anrop till metoden [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) , till metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) och andra feedback-mekanismer som kan ta lång tid att slutföra. I dessa fall kan användaren behöva skicka en stopp signal till dessa cmdletar.

### <a name="implement-the-idisposable-interface-ac04"></a>Implementera IDisposable-gränssnittet (AC04)

Om cmdleten har objekt som inte har avslut ATS (skrivs till pipelinen) av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) kan cmdleten kräva ytterligare objekt kasse ring. Om din cmdlet till exempel öppnar en fil referens i dess [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Metod och låter referensen vara öppen för användning av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , måste den här referensen stängas i slutet av bearbetningen.

Windows PowerShell-körningsmiljön anropar inte alltid metoden  [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Till exempel kanske metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) inte anropas om cmdleten avbryts halvvägs genom åtgärden eller om ett avslutande fel inträffar i någon del av cmdleten. Därför bör .NET Framework-klassen för en cmdlet som kräver rensning av objekt, implementera det fullständiga  [system. IDisposable](/dotnet/api/System.IDisposable) -användargränssnittet, inklusive slut för ande processen, så att Windows PowerShell-körningsmiljön kan anropa både [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) och [system. IDisposable. disattityd *](/dotnet/api/System.IDisposable.Dispose) metoder i slutet av bearbetningen.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Använd serialisering-läsvänlig parameter typer (AC05)

Om du vill ha stöd för att köra din cmdlet på fjärrdatorer använder du typer som enkelt kan serialiseras på klient datorn och sedan omtorkas på serverdatorn. Följande typer är Serializable serializing-vänliga.

Primitiva typer:

- Byte, SByte, decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32 och UInt64.

- Boolean, GUID, byte [], TimeSpan, DateTime, URI och version.

- Char, String, XmlDocument.

Inbyggda rehydratable-typer:

- PSPrimitiveDictionary

- SwitchParameter

- PSListModifier

- PSCredential

- IP-adress, adress

- CultureInfo

- X509Certificate2, X500DistinguishedName

- DirectorySecurity, FileSecurity, RegistrySecurity

Andra typer:

- SecureString

- Behållare (listor och ord listor av ovanstående typ)

### <a name="use-securestring-for-sensitive-data-ac06"></a>Använda SecureString för känsliga data (AC06)

När du hanterar känsliga data använder du alltid data typen [system. Security. SecureString](/dotnet/api/System.Security.SecureString) . Detta kan omfatta pipeline-indata till parametrar, samt för att returnera känsliga data till pipelinen.

## <a name="see-also"></a>Se även

[Obligatoriska riktlinjer för utveckling](./required-development-guidelines.md)

[Starkt rekommenderade riktlinjer för utveckling](./strongly-encouraged-development-guidelines.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
