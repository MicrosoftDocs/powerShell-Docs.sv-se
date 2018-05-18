---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 9a9bdac652512640209c20e3deb20d7abc0142c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="bbcd0-102">Registrera ett PowerShell-lager</span><span class="sxs-lookup"><span data-stu-id="bbcd0-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="bbcd0-103">Du kan konfigurera PowerShellGet ska fungera mot interna databaser.</span><span class="sxs-lookup"><span data-stu-id="bbcd0-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="bbcd0-104">Detta görs med hjälp av följande tillägg:</span><span class="sxs-lookup"><span data-stu-id="bbcd0-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="bbcd0-105">Registrera PSRepository: Registrerar en lagringsplats för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="bbcd0-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="bbcd0-106">Avregistrera PSRepository: Tar bort en registrerad lagringsplats för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="bbcd0-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="bbcd0-107">Set-PSRepository: Ange värden för en registrerad databas.</span><span class="sxs-lookup"><span data-stu-id="bbcd0-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="bbcd0-108">Get-PSRepository: Hämta alla registrerade databaser för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="bbcd0-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="bbcd0-109">När en databas har registrerats kan använda du hitta modulen och installera modulen för att arbeta med den.</span><span class="sxs-lookup"><span data-stu-id="bbcd0-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

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
