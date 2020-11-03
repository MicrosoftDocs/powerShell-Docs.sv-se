---
description: PackageManagement är en aggregator för program pakets hanterare.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_packagemanagement?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PackageManagement
ms.openlocfilehash: 5af3095675015eb043ca3299f5e44b0bc7ac4aa1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272516"
---
# <a name="about-packagemanagement"></a>Om PackageManagement

## <a name="short-description"></a>KORT BESKRIVNING
PackageManagement är en aggregator för program pakets hanterare.

## <a name="long-description"></a>LÅNG BESKRIVNING

PackageManagement-funktionen introducerades i Windows PowerShell 5,0.

PackageManagement är ett enhetligt gränssnitt för hanterings system för program varu paket. Du kan köra PackageManagement-cmdletar för att utföra program identifiering, installation och inventering (SDII)-uppgifter. Oberoende av den underliggande installations tekniken kan du köra de vanliga cmdletarna i PackageManagement-modulen för att söka efter, installera eller avinstallera paket. Lägg till, ta bort och fråga paket databaser; och kör frågor på en dator för att avgöra vilka program varu paket som är installerade.

PackageManagement stöder en flexibel plugin-modell som möjliggör stöd för andra hanterings system för program varu paket.

PackageManagement-modulen ingår i Windows PowerShell 5,0 och senare versioner av PowerShell och fungerar på tre nivåer av paket hanterings strukturen: paket leverantörer, paket källor och själva paketen. Låt oss definiera några villkor:

- Paket hanterare: program vara pakethanteringssystem. I PackageManagement villkor är detta en paket leverantör.
- Package provider: PackageManagement term för en paket hanterare. Exempel kan vara Windows Installer, choklad och andra.
- Paket Källa: en URL, lokal mapp eller delad nätverksmapp som du konfigurerar paket leverantörer att använda som en lagrings plats.
- Paket: en program vara som en Package provider hanterar och som lagras i en viss paket källa.

PackageManagement-modulen innehåller följande cmdletar. Mer information finns i [PackageManagement](/powershell/module/packagemanagement) -hjälpen.

- `Get-PackageProvider`: Returnerar en lista med paket leverantörer som är anslutna till PackageManagement.
- `Get-PackageSource`: Hämtar en lista över paket källor som har registrerats för en paket leverantör.
- `Register-PackageSource`: Lägger till en paket källa för en angiven paket leverantör.
- `Set-PackageSource`: Anger egenskaper för en befintlig paket källa.
- `Unregister-PackageSource`: Tar bort en registrerad paket källa.
- `Get-Package`: Returnerar en lista över installerade program varu paket.
- `Find-Package`: Söker efter program varu paket i tillgängliga paket källor.
- `Install-Package`: Installerar ett eller flera program varu paket.
- `Save-Package`: Sparar paket på den lokala datorn utan att installera dem.
- `Uninstall-Package`: Avinstallerar ett eller flera program varu paket.

### <a name="package-provider-bootstrapping-and-dynamic-cmdlet-parameters"></a>Parametrar för start och dynamisk cmdlet för paketera Provider

Som standard levereras PackageManagement med en Core bootstrap-Provider. Du kan installera ytterligare paket leverantörer när du behöver dem genom att starta providern. det vill säga att du svarar på en uppfråga för att installera providern automatiskt från en webb tjänst. Du kan ange en paket leverantör med valfri PackageManagement-cmdlet; om den angivna providern inte är tillgänglig, kommer PackageManagement att bli ombedd att starta (eller installera automatiskt) providern. I följande exempel, om den choklad leverantören inte redan är installerad, installerar PackageManagement-providern.

```powershell
Find-Package -Provider Chocolatey <PackageName>
```

Om den choklad leverantören inte redan är installerad, uppmanas du att installera det när du kör föregående kommando.

```powershell
Install-Package <Chocolatey package Name> -ForceBootstrap
```

Om den choklad leverantören inte redan är installerad när du kör föregående kommando, installeras providern. men eftersom parametern ForceBootstrap har lagts till i kommandot, uppmanas du inte att installera den. både providern och paketet installeras automatiskt.

Om du försöker installera ett paket, om du inte redan har den stödda providern installerad, och du inte lägger till parametern ForceBootstrap i ditt kommando, kommer PackageManagement att be dig att installera providern.

Om du anger en paket leverantör i ditt PackageManagement-kommando kan du göra dynamiska parametrar som är tillgängliga för den paket leverantören. När du kör Get-Help för en särskild PackageManagement-cmdlet returneras en lista med parameter uppsättningar, grupper dynamiska parametrar för tillgängliga paket leverantörer i separata parameter uppsättningar.

Mer information om PackageManagement-projektet

Mer information om PackageManagement Open Development Project, inklusive hur du skapar en PackageManagement-paket leverantör finns i PackageManagement-projektet på GitHub på https://oneget.org .

## <a name="see-also"></a>SE ÄVEN

[Get-PackageProvider](xref:PackageManagement.Get-PackageProvider)

[Get-PackageSource](xref:PackageManagement.Get-PackageSource)

[Registrera – PackageSource](xref:PackageManagement.Register-PackageSource)

[Set-PackageSource](xref:PackageManagement.Set-PackageSource)

[Unregister-PackageSource](xref:PackageManagement.Unregister-PackageSource)

[Get-Package](xref:PackageManagement.Get-Package)

[Sök-paket](xref:PackageManagement.Find-Package)

[Installationspaket](xref:PackageManagement.Install-Package)

[Spara paket](xref:PackageManagement.Save-Package)

[Avinstallera paket](xref:PackageManagement.Uninstall-Package)

