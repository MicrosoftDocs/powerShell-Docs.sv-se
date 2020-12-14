---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 4ae9fd46-338a-459c-8186-07f910774cb8
Module Name: PackageManagement
ms.date: 06/09/2017
schema: 2.0.0
title: PackageManagement
ms.openlocfilehash: 86e6f37f6f7f0527c5dcca309cf581cb6f1b4de5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889333"
---
# PackageManagement-modul

## Beskrivning

I det här avsnittet visas hjälp avsnitt för Package Management-cmdletar.

> [!IMPORTANT]
> Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1. Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet. Använd följande kommando för att se till att du använder TLS 1,2:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.

## PackageManagement-cmdletar

### [Sök-paket](Find-Package.md)
Söker efter program varu paket i tillgängliga paket källor.

### [Find-PackageProvider](Find-PackageProvider.md)
Returnerar en lista med paket hanterings paket leverantörer som är tillgängliga för installation.

### [Get-Package](Get-Package.md)
Returnerar en lista med alla program varu paket som har installerats med **PackageManagement**.

### [Get-PackageProvider](Get-PackageProvider.md)
Returnerar en lista med paket leverantörer som är anslutna till paket hantering.

### [Get-PackageSource](Get-PackageSource.md)
Hämtar en lista med paket källor som har registrerats för en paket leverantör.

### [Importera – PackageProvider](Import-PackageProvider.md)
Lägger till leverantörer av paket hanterings paket i den aktuella sessionen.

### [Installationspaket](Install-Package.md)
Installerar ett eller flera program varu paket.

### [Installera-PackageProvider](Install-PackageProvider.md)
Installerar en eller flera leverantörer av paket hanterings paket.

### [Registrera – PackageSource](Register-PackageSource.md)
Lägger till en paket källa för en angiven paket leverantör.

### [Spara paket](Save-Package.md)
Sparar paket på den lokala datorn utan att installera dem.

### [Set-PackageSource](Set-PackageSource.md)
Ersätter en paket källa för en angiven paket leverantör.

### [Avinstallera paket](Uninstall-Package.md)
Avinstallerar ett eller flera program varu paket.

### [Unregister-PackageSource](Unregister-PackageSource.md)
Tar bort en registrerad paket källa.
