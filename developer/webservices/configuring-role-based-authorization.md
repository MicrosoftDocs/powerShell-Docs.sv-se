---
title: Konfigurera rollbaserad auktorisering | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080687"
---
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="ad0a0-102">Konfigurera rollbaserad auktorisering</span><span class="sxs-lookup"><span data-stu-id="ad0a0-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="ad0a0-103">Det här avsnittet visar hur du konfigurerar rollbaserad auktoriseringsprincip för exemplet genomförandet av den [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) gränssnitt som beskrivs i [implementera anpassade Auktorisering för Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="ad0a0-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="ad0a0-104">I det här exemplet konfigurerar du en XML-fil som används av Management OData exempelprogrammet för att definiera principen för auktorisering.</span><span class="sxs-lookup"><span data-stu-id="ad0a0-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="ad0a0-105">Du skapar två roller och koppla olika Windows PowerShell-moduler som innehåller arbetsflöden med dessa roller.</span><span class="sxs-lookup"><span data-stu-id="ad0a0-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="ad0a0-106">Det schema som definierar XML-filen visas i [Role-Based auktorisering konfigurationsschema](./role-based-authorization-configuration-schema.md).</span><span class="sxs-lookup"><span data-stu-id="ad0a0-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="ad0a0-107">Ändra RBacConfiguration.xml-filen</span><span class="sxs-lookup"><span data-stu-id="ad0a0-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="ad0a0-108">Den här filen definierar auktoriseringsprincip för programmet.</span><span class="sxs-lookup"><span data-stu-id="ad0a0-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="ad0a0-109">Roller definieras med hjälp av `Group` noder.</span><span class="sxs-lookup"><span data-stu-id="ad0a0-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="ad0a0-110">En `Group` noden definierar du Windows PowerShell-kommandon som användare som är tilldelade till den gruppen kan köras.</span><span class="sxs-lookup"><span data-stu-id="ad0a0-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="ad0a0-111">Användare tilldelas till grupper med hjälp av `User` noder.</span><span class="sxs-lookup"><span data-stu-id="ad0a0-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="ad0a0-112">I det här exemplet ska du lägga till en modul till administratören `Group` nod, och lägga till en användare i varje grupp.</span><span class="sxs-lookup"><span data-stu-id="ad0a0-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="ad0a0-113">Att lägga till en modul till en gruppnod</span><span class="sxs-lookup"><span data-stu-id="ad0a0-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="ad0a0-114">Skapa en fil med namnet **RBacConfiguration.xml** i en textredigerare.</span><span class="sxs-lookup"><span data-stu-id="ad0a0-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="ad0a0-115">Den här filen ska sparas till katalogen huvudprogrammet för webbtjänsten.</span><span class="sxs-lookup"><span data-stu-id="ad0a0-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="ad0a0-116">Lägg till följande text i filen.</span><span class="sxs-lookup"><span data-stu-id="ad0a0-116">Insert the following text in the file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <RbacConfiguration>
     <Groups>
       <!--Group consists of the following:
         Name:  Name of the group
         UserName (Optional): Windows Identity user name
         Password (Optional): Password of the Windows user name
         DomainName (Optional): Domain for the user. For local machine account either do not include them or give the machine name. Do not give empty string
         MapIncomingUser (Optional): Boolean value indicating whether to execute cmdlet in the context of network client.

         User credentials and MapIncomingUser=true are exclusive.
       -->
       <Group Name="NonAdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Set-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
       </Group>
       <Group Name="AdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
         <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
       </Group>
     </Groups>
     <Users>
       <!-- User consists of the following :
         Name: Name of the user. If a user is from a cer
         AuthenticationType: Authentication type used.
         DomainName (Optional): Domain for the user
       -->
       <User Name="localNonAdmin" AuthenticationType="Basic" GroupName="NonAdminGroup" />
       <User Name="localAdmin" AuthenticationType="Basic" GroupName="AdminGroup" />
     </Users>
   </RbacConfiguration>
   ```

2. <span data-ttu-id="ad0a0-117">Filen innehåller två `Group` noder.</span><span class="sxs-lookup"><span data-stu-id="ad0a0-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="ad0a0-118">Dessa representerar de två rollerna som används i det här exemplet är den `NonAdminGroup` och `AdminGroup` roller.</span><span class="sxs-lookup"><span data-stu-id="ad0a0-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="ad0a0-119">Direkt efter avslutande `Cmdlets` tagg i först `Group` nod, Lägg till följande XML:</span><span class="sxs-lookup"><span data-stu-id="ad0a0-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="ad0a0-120">Om du lägger till en användare till en gruppnod</span><span class="sxs-lookup"><span data-stu-id="ad0a0-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="ad0a0-121">Öppna den **RBacConfiguration.xml** filen i en textredigerare.</span><span class="sxs-lookup"><span data-stu-id="ad0a0-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="ad0a0-122">Den här filen finns i mappen C:\\\inetpub\wwwroot\Modata om du inte har ändrat namnet på slutpunkten innan du kör installationen.</span><span class="sxs-lookup"><span data-stu-id="ad0a0-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="ad0a0-123">Direkt efter den avslutande taggen i den `Users` nod, Lägg till följande XML:</span><span class="sxs-lookup"><span data-stu-id="ad0a0-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="ad0a0-124">Direkt efter att XML-filen har lagts till i föregående steg, lägger du till följande XML:</span><span class="sxs-lookup"><span data-stu-id="ad0a0-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```