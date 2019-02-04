---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 5ac9566979e1b761249f5cc7c62ed44047a2b9f6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685237"
---
# <a name="register-a-powershell-repository"></a>Registrera ett PowerShell-lager
Du kan konfigurera PowerShellGet att arbeta mot interna databaser. Detta görs med hjälp av följande tillägg:
- Register-PSRepository: Registrerar en lagringsplats för den aktuella användaren.
- Unregister-PSRepository: Tar bort en registrerad lagringsplats för den aktuella användaren.
- Set-PSRepository: Ange värden för en registrerad lagringsplats.
- Get-PSRepository: Hämta alla registrerade databaser för den aktuella användaren.

När en databas har registrerats kan använda du Find-Module och Install-Module för att arbeta med den.

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```
