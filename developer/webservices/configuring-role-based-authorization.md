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
# <a name="configuring-role-based-authorization"></a>Konfigurera rollbaserad auktorisering

Det här avsnittet visar hur du konfigurerar rollbaserad auktoriseringsprincip för exemplet genomförandet av den [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) gränssnitt som beskrivs i [implementera anpassade Auktorisering för Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).

I det här exemplet konfigurerar du en XML-fil som används av Management OData exempelprogrammet för att definiera principen för auktorisering. Du skapar två roller och koppla olika Windows PowerShell-moduler som innehåller arbetsflöden med dessa roller. Det schema som definierar XML-filen visas i [Role-Based auktorisering konfigurationsschema](./role-based-authorization-configuration-schema.md).

## <a name="modifying-the-rbacconfigurationxml-file"></a>Ändra RBacConfiguration.xml-filen

Den här filen definierar auktoriseringsprincip för programmet. Roller definieras med hjälp av `Group` noder. En `Group` noden definierar du Windows PowerShell-kommandon som användare som är tilldelade till den gruppen kan köras. Användare tilldelas till grupper med hjälp av `User` noder.

I det här exemplet ska du lägga till en modul till administratören `Group` nod, och lägga till en användare i varje grupp.

#### <a name="adding-a-module-to-a-group-node"></a>Att lägga till en modul till en gruppnod

1. Skapa en fil med namnet **RBacConfiguration.xml** i en textredigerare. Den här filen ska sparas till katalogen huvudprogrammet för webbtjänsten. Lägg till följande text i filen.

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

2. Filen innehåller två `Group` noder. Dessa representerar de två rollerna som används i det här exemplet är den `NonAdminGroup` och `AdminGroup` roller.

   Direkt efter avslutande `Cmdlets` tagg i först `Group` nod, Lägg till följande XML:

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>Om du lägger till en användare till en gruppnod

1. Öppna den **RBacConfiguration.xml** filen i en textredigerare. Den här filen finns i mappen C:\\\inetpub\wwwroot\Modata om du inte har ändrat namnet på slutpunkten innan du kör installationen.

2. Direkt efter den avslutande taggen i den `Users` nod, Lägg till följande XML:

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Direkt efter att XML-filen har lagts till i föregående steg, lägger du till följande XML:

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```