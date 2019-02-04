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
# <a name="register-a-powershell-repository"></a><span data-ttu-id="88e7a-102">Registrera ett PowerShell-lager</span><span class="sxs-lookup"><span data-stu-id="88e7a-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="88e7a-103">Du kan konfigurera PowerShellGet att arbeta mot interna databaser.</span><span class="sxs-lookup"><span data-stu-id="88e7a-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="88e7a-104">Detta görs med hjälp av följande tillägg:</span><span class="sxs-lookup"><span data-stu-id="88e7a-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="88e7a-105">Register-PSRepository: Registrerar en lagringsplats för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="88e7a-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="88e7a-106">Unregister-PSRepository: Tar bort en registrerad lagringsplats för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="88e7a-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="88e7a-107">Set-PSRepository: Ange värden för en registrerad lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="88e7a-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="88e7a-108">Get-PSRepository: Hämta alla registrerade databaser för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="88e7a-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="88e7a-109">När en databas har registrerats kan använda du Find-Module och Install-Module för att arbeta med den.</span><span class="sxs-lookup"><span data-stu-id="88e7a-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

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
