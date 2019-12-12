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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352257"
---
# <a name="configuring-role-based-authorization"></a>Konfigurera rollbaserad auktorisering

I det här avsnittet visas hur du konfigurerar den rollbaserade auktoriseringsprincipen för exempel implementeringen av gränssnittet [Microsoft. Management. OData. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) som beskrivs i [implementera anpassad auktorisering för OData IIS-tillägg för hantering](./implementing-custom-authorization-for-a-management-odata-web-service.md).

I det här exemplet ska du konfigurera en XML-fil som används av OData-appen exempel hantering för att definiera auktoriseringsprincipen. Du kommer att skapa två roller och associera olika Windows PowerShell-moduler som innehåller arbets flöden med dessa roller. Det schema som definierar XML-filen visas i [konfigurations schema för rollbaserad auktorisering](./role-based-authorization-configuration-schema.md).

## <a name="modifying-the-rbacconfigurationxml-file"></a>Ändra filen RBacConfiguration. XML

Den här filen definierar auktoriseringsprincipen för programmet. Roller definieras med hjälp av `Group` noder. En `Group` nod definierar de Windows PowerShell-kommandon som användare som tilldelats gruppen kan köra. Användare tilldelas grupper genom att använda `User` noder.

I de här exemplen ska du lägga till en modul till administratören `Group` noden och lägga till en användare i varje grupp.

#### <a name="adding-a-module-to-a-group-node"></a>Lägga till en modul i en gruppnod

1. Skapa en fil med namnet **RBacConfiguration. XML** i en text redigerare. Den här filen ska sparas i huvud program katalogen för din webb tjänst. Infoga följande text i filen.

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

2. Filen innehåller två `Group` noder. Dessa representerar de två roller som används i det här exemplet, `NonAdminGroup` och `AdminGroup` roller.

   Lägg till följande XML direkt efter stängnings `Cmdlets`s tag gen i den första `Group` noden:

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>Lägga till en användare till en gruppnod

1. Öppna filen **RBacConfiguration. XML** i en text redigerare. Den här filen finns i mappen C:\\\inetpub\wwwroot\Modata om du inte ändrade slut punkts namnet före installationen.

2. Lägg till följande XML direkt efter den avslutande taggen i `Users`-noden:

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Direkt efter att XML har lagts till i föregående steg lägger du till följande XML:

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```