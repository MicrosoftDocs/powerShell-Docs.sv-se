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
ms.openlocfilehash: 2c9d6040b7a9c17dc5204c8eb835fd69780f62c5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564265"
---
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="9b0c4-102">Konfigurera rollbaserad auktorisering</span><span class="sxs-lookup"><span data-stu-id="9b0c4-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="9b0c4-103">I det här avsnittet visas hur du konfigurerar den rollbaserade auktoriseringsprincipen för exempel implementeringen av gränssnittet [Microsoft. Management. OData. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) som beskrivs i [implementera anpassad auktorisering för OData IIS-tillägg för hantering](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="9b0c4-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="9b0c4-104">I det här exemplet ska du konfigurera en XML-fil som används av OData-appen exempel hantering för att definiera auktoriseringsprincipen.</span><span class="sxs-lookup"><span data-stu-id="9b0c4-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="9b0c4-105">Du kommer att skapa två roller och associera olika Windows PowerShell-moduler som innehåller arbets flöden med dessa roller.</span><span class="sxs-lookup"><span data-stu-id="9b0c4-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="9b0c4-106">Det schema som definierar XML-filen visas i [konfigurations schema för rollbaserad auktorisering](./role-based-authorization-configuration-schema.md).</span><span class="sxs-lookup"><span data-stu-id="9b0c4-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="9b0c4-107">Ändra filen RBacConfiguration. XML</span><span class="sxs-lookup"><span data-stu-id="9b0c4-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="9b0c4-108">Den här filen definierar auktoriseringsprincipen för programmet.</span><span class="sxs-lookup"><span data-stu-id="9b0c4-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="9b0c4-109">Roller definieras med hjälp av `Group` noder.</span><span class="sxs-lookup"><span data-stu-id="9b0c4-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="9b0c4-110">En `Group` nod definierar de Windows PowerShell-kommandon som användare som tilldelats gruppen kan köra.</span><span class="sxs-lookup"><span data-stu-id="9b0c4-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="9b0c4-111">Användare tilldelas till grupper med hjälp av `User` noder.</span><span class="sxs-lookup"><span data-stu-id="9b0c4-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="9b0c4-112">I de här exemplen ska du lägga till en modul i `Group` noden administratör och lägga till en användare i varje grupp.</span><span class="sxs-lookup"><span data-stu-id="9b0c4-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="9b0c4-113">Lägga till en modul i en gruppnod</span><span class="sxs-lookup"><span data-stu-id="9b0c4-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="9b0c4-114">Skapa en fil med namnet **RBacConfiguration. XML** i en text redigerare.</span><span class="sxs-lookup"><span data-stu-id="9b0c4-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="9b0c4-115">Den här filen ska sparas i huvud program katalogen för din webb tjänst.</span><span class="sxs-lookup"><span data-stu-id="9b0c4-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="9b0c4-116">Infoga följande text i filen.</span><span class="sxs-lookup"><span data-stu-id="9b0c4-116">Insert the following text in the file.</span></span>

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

2. <span data-ttu-id="9b0c4-117">Filen innehåller två `Group` noder.</span><span class="sxs-lookup"><span data-stu-id="9b0c4-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="9b0c4-118">Dessa representerar de två roller som används i det här exemplet, `NonAdminGroup` och `AdminGroup` rollerna och.</span><span class="sxs-lookup"><span data-stu-id="9b0c4-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="9b0c4-119">Direkt efter den avslutande `Cmdlets` taggen i den första `Group` noden lägger du till följande XML:</span><span class="sxs-lookup"><span data-stu-id="9b0c4-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="9b0c4-120">Lägga till en användare till en gruppnod</span><span class="sxs-lookup"><span data-stu-id="9b0c4-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="9b0c4-121">Öppna filen **RBacConfiguration. XML** i en text redigerare.</span><span class="sxs-lookup"><span data-stu-id="9b0c4-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="9b0c4-122">Den här filen finns i mappen C: \\ \inetpub\wwwroot\Modata om du inte ändrade slut punkts namnet före installationen.</span><span class="sxs-lookup"><span data-stu-id="9b0c4-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="9b0c4-123">Lägg till följande XML direkt efter den avslutande taggen i `Users` noden:</span><span class="sxs-lookup"><span data-stu-id="9b0c4-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="9b0c4-124">Direkt efter att XML har lagts till i föregående steg lägger du till följande XML:</span><span class="sxs-lookup"><span data-stu-id="9b0c4-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```
