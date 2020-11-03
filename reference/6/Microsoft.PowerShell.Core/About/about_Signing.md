---
description: Förklarar hur du signerar skript så att de följer PowerShell-körnings principerna.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_signing?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Signing
ms.openlocfilehash: ae0e9290696d8b50fce29137f98721220e7511c7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270392"
---
# <a name="about-signing"></a>Om signering

## <a name="short-description"></a>Kort beskrivning
Förklarar hur du signerar skript så att de följer PowerShell-körnings principerna.

## <a name="long-description"></a>Lång beskrivning

Principen för begränsade körningar tillåter inte att skript körs. **AllSigned** -och **RemoteSigned** -körnings principerna förhindrar att PowerShell kör skript som inte har någon digital signatur.

I det här avsnittet beskrivs hur du kör valda skript som inte är signerade, även om körnings principen är **RemoteSigned** och hur du signerar skript för egen användning.

Mer information om körnings principer för PowerShell finns i [about_Execution_Policies](about_Execution_Policies.md).

## <a name="to-permit-signed-scripts-to-run"></a>Tillåta att signerade skript körs

När du startar PowerShell på en dator för första gången är den **begränsade** körnings principen (standard) förmodligen aktiv.

Den **begränsade** principen tillåter inte att skript körs.

Du hittar den effektiva körnings principen på datorn genom att skriva:

```powershell
Get-ExecutionPolicy
```

Om du vill köra osignerade skript som du skriver på din lokala dator och signerade skript från andra användare, startar du PowerShell med alternativet Kör som administratör och använder sedan följande kommando för att ändra körnings principen på datorn till **RemoteSigned** :

```powershell
Set-ExecutionPolicy RemoteSigned
```

Mer information finns i hjälp avsnittet för `Set-ExecutionPolicy` cmdleten.

## <a name="running-unsigned-scripts-using-the-remotesigned-execution-policy"></a>Köra osignerade skript med körnings principen för RemoteSigned

Om din PowerShell-körnings princip är **RemoteSigned** kör PowerShell inte osignerade skript som hämtas från Internet, inklusive osignerade skript som du får via e-post och snabb meddelande program.

Om du försöker köra ett nedladdat skript visas följande fel meddelande i PowerShell:

```Output
The file <file-name> cannot be loaded. The file <file-name> is not digitally
signed. The script will not execute on the system. Please see "Get-Help
about_Signing" for more details.
```

Innan du kör skriptet bör du granska koden för att vara säker på att du litar på den.
Skript har samma resultat som alla körbara program.

Om du vill köra ett osignerat skript använder du Unblock-File-cmdleten eller så använder du följande procedur.

1. Spara skript filen på datorn.
2. Klicka på Start, klicka på den här datorn och leta upp den sparade skript filen.
3. Högerklicka på skript filen och klicka sedan på egenskaper.
4. Klicka på avblockera.

Om ett skript som hämtades från Internet har signerats digitalt, men du ännu inte har valt att lita på utgivaren, visas följande meddelande i PowerShell:

```Output
Do you want to run software from this untrusted publisher?
The file <file-name> is published by CN=<publisher-name>. This
publisher is not trusted on your system. Only run scripts
from trusted publishers.

[V] Never run  [D] Do not run  [R] Run once  [A] Always run
[?] Help (default is "D"):
```

Om du litar på utgivaren väljer du kör en gång eller kör alltid. Om du inte litar på utgivaren väljer du antingen "Kör aldrig" eller "kör inte". Om du väljer "aldrig körning" eller "kör alltid" uppmanas du inte att göra det igen för den här utgivaren.

## <a name="methods-of-signing-scripts"></a>Metoder för signering av skript

Du kan signera de skript som du skriver och skript som du hämtar från andra källor. Innan du signerar ett skript kontrollerar du varje kommando för att kontrol lera att det är säkert att köra.

Bästa praxis om kod signering finns i [metod tips för kod signering](/previous-versions/windows/hardware/design/dn653556(v=vs.85)).

Mer information om hur du signerar en skript fil finns i [set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature).

`New-SelfSignedCertificate`Cmdleten, som introducerades i PKI-modulen i PowerShell 3,0, skapar ett självsignerat certifikat som är lämpligt för testning. Mer information finns i hjälp avsnittet för New-SelfSignedCertificate-cmdleten.

Om du vill lägga till en digital signatur i ett skript måste du signera den med ett kod signerings certifikat. Två typer av certifikat är lämpliga för signering av en skript fil:

- Certifikat som har skapats av en certifikat utfärdare: för en avgift verifierar en offentlig certifikat utfärdare din identitet och ger dig ett kod signerings certifikat. När du köper ditt certifikat från en betrodd certifikat utfärdare kan du dela ditt skript med användare på andra datorer som kör Windows eftersom de andra datorerna litar på certifikat utfärdaren.

- Certifikat som du skapar: du kan skapa ett självsignerat certifikat för vilket datorn är den myndighet som skapar certifikatet. Det här certifikatet är kostnads fritt och du kan skriva, signera och köra skript på din dator. Ett skript som signerats av ett självsignerat certifikat kommer dock inte att köras på andra datorer.

Normalt använder du bara ett självsignerat certifikat för att signera skript som du skriver för eget bruk och för att signera skript som du får från andra källor som du har kontrollerat är säkra. Det är inte lämpligt för skript som ska delas, även inom ett företag.

Om du skapar ett självsignerat certifikat måste du Aktivera starkt skydd av den privata nyckeln på ditt certifikat. Detta förhindrar att skadliga program signerar skript åt dig. Anvisningarna finns i slutet av det här avsnittet.

## <a name="create-a-self-signed-certificate"></a>Skapa ett självsignerat certifikat

Om du vill skapa ett självsignerat certifikat använder du `New-SelfSignedCertificate` cmdleten i PKI-modulen. Den här modulen introduceras i PowerShell 3,0 och ingår i Windows 8 och Windows Server 2012. Mer information finns i hjälp avsnittet för `New-SelfSignedCertificate` cmdleten.

Om du vill skapa ett självsignerat certifikat i tidigare versioner av Windows använder du verktyget för att skapa certifikat `MakeCert.exe` . Det här verktyget ingår i Microsoft .NET SDK (version 1,1 och senare) och i Microsoft Windows SDK.

Mer information om syntaxen och parameter beskrivningarna för MakeCert.exe-verktyget finns i verktyget för att [Skapa certifikat (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80)).

Om du vill använda MakeCert.exe-verktyget för att skapa ett certifikat kör du följande kommandon i ett kommando tolks fönster för SDK.

Obs: det första kommandot skapar en lokal certifikat utfärdare för datorn. Det andra kommandot genererar ett personligt certifikat från certifikat utfärdaren.

Obs: du kan kopiera eller skriva kommandon exakt som de visas. Inga ersättningar krävs, men du kan ändra certifikat namnet.

```powershell
makecert -n "CN=PowerShell Local Certificate Root" -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -r -sv root.pvk root.cer `
-ss Root -sr localMachine

makecert -pe -n "CN=PowerShell User" -ss MY -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -iv root.pvk -ic root.cer
```

I MakeCert.exes verktyget uppmanas du att ange ett lösen ord för den privata nyckeln. Lösen ordet garanterar att ingen kan använda eller komma åt certifikatet utan ditt medgivande.
Skapa och ange ett lösen ord som du kan komma ihåg. Du kommer att använda det här lösen ordet senare för att hämta certifikatet.

Kontrol lera att certifikatet har genererats korrekt genom att använda följande kommando för att hämta certifikatet i certifikat arkivet på datorn. Du kommer inte att hitta någon certifikat fil i fil system katalogen.

I PowerShell-prompten skriver du:

```powershell
Get-ChildItem cert:\CurrentUser\my -codesigning
```

Detta kommando använder PowerShell-certifikat leverantören för att visa information om certifikatet.

Om certifikatet har skapats visar utdata det **tumavtryck** som identifierar certifikatet i en bildskärm som liknar följande:

```Output
Directory: Microsoft.PowerShell.Security\Certificate::CurrentUser\My

Thumbprint                                Subject
----------                                -------
4D4917CB140714BA5B81B96E0B18AAF2C4564FDF  CN=PowerShell User ]
```

## <a name="sign-a-script"></a>Signera ett skript

När du har skapat ett självsignerat certifikat kan du signera skript. Om du använder **AllSigned** körnings princip kan du signera ett skript för att köra skriptet på datorn.

Följande exempel skript, `Add-Signature.ps1` signerar ett skript. Om du använder **AllSigned** körnings princip måste du dock signera `Add-Signature.ps1` skriptet innan du kör det.

> [!IMPORTANT]
> Skriptet måste sparas med ASCII-eller UTF8NoBOM-kodning. Du kan signera en skript fil som använder en annan kodning. Men skriptet kan inte köras eller också går det inte att importera den modul som innehåller skriptet.

Om du vill använda det här skriptet kopierar du följande text till en textfil och namnger den `Add-Signature.ps1` .

```powershell
## Signs a file
param([string] $file=$(throw "Please specify a filename."))
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature $file $cert
```

Om du vill signera `Add-Signature.ps1` skript filen skriver du följande kommandon i PowerShell-kommando tolken:

```powershell
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature add-signature.ps1 $cert
```

När skriptet har signerats kan du köra det på den lokala datorn. Men skriptet kan inte köras på datorer där PowerShell-körnings principen kräver en digital signatur från en betrodd utfärdare. Om du försöker igen visas följande fel meddelande i PowerShell:

```Output
The file C:\remote_file.ps1 cannot be loaded. The signature of the
certificate cannot be verified.
At line:1 char:15
+ .\ remote_file.ps1 <<<<
```

Om PowerShell visar det här meddelandet när du kör ett skript som du inte har skrivit, behandla filen som du skulle behandla alla osignerade skript. Granska koden för att avgöra om du kan lita på skriptet.

## <a name="enable-strong-private-key-protection-for-your-certificate"></a>Aktivera starkt skydd av den privata nyckeln för ditt certifikat

Om du har ett privat certifikat på datorn kan skadliga program kunna signera skript åt dig, vilket ger PowerShell möjlighet att köra dem.

Använd Certificate Manager `Certmgr.exe` för att exportera ditt signerings certifikat till en fil för att förhindra automatisk signering för din räkning `.pfx` . Certifikat hanteraren ingår i Microsoft .NET SDK, Microsoft Windows SDK och i Internet Explorer.

Så här exporterar du certifikatet:

1. Starta certifikat hanteraren.
2. Välj det certifikat som utfärdats av den lokala PowerShell-certifikat roten.
3. Klicka på Exportera för att starta guiden Exportera certifikat.
4. Välj "Ja, exportera den privata nyckeln" och klicka sedan på Nästa.
5. Välj "Aktivera starkt skydd".
6. Skriv ett lösen ord och skriv det igen för att bekräfta.
7. Ange ett fil namn som har fil namns tillägget. pfx.
8. Klicka på Slutför.

Så här importerar du certifikatet på nytt:

1. Starta certifikat hanteraren.
2. Klicka på Importera för att starta guiden Importera certifikat.
3. Öppna till platsen för den. pfx-fil som du skapade under export processen.
4. På sidan lösen ord väljer du Aktivera starkt skydd av den privata nyckeln och anger sedan det lösen ord som du tilldelade under export processen.
5. Välj det personliga certifikat arkivet.
6. Klicka på Slutför.

## <a name="prevent-the-signature-from-expiring"></a>Förhindra att signaturen upphör att gälla

Den digitala signaturen i ett skript är giltig tills signerings certifikatet upphör att gälla eller så länge en tids stämplings Server kan verifiera att skriptet signerades medan signerings certifikatet var giltigt.

Eftersom de flesta signerings certifikaten endast är giltiga i ett år, garanterar att användarna kan använda ditt skript i flera år för att komma åt dem med hjälp av en tids stämplings Server.

## <a name="see-also"></a>Se även

[about_Execution_Policies](about_Execution_Policies.md)

[about_Profiles](about_Profiles.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[Introduktion till kod signering](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))
