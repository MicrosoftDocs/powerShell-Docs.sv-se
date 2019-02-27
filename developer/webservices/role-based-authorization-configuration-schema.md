---
title: Rollbaserad auktorisering konfigurationsschema | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ba6d1d2-7055-4fef-b752-a5ae8b4eeb65
caps.latest.revision: 7
ms.openlocfilehash: 50a02e9a7522fc04b407329f513670215ad051cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851410"
---
# <a name="role-based-authorization-configuration-schema"></a>Konfigurationsschema för rollbaserad auktorisering

Den [PswsRoleBasedPlugins](http://go.microsoft.com/fwlink/?LinkId=243041) exemplet använder XML-filer för att konfigurera principen för auktorisering. Följande XSD definierar ett schema som används för de här filerna.

```
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
   <xs:element name="RbacConfiguration">
       <xs:complexType>
           <xs:all>
               <xs:element name="Groups">
                   <xs:complexType>
                       <xs:sequence>
                           <xs:element name="Group" type="GroupType" maxOccurs="unbounded"/>
                       </xs:sequence>
                   </xs:complexType>
       </xs:element>
               <xs:element name="Users">
                   <xs:complexType>
                       <xs:sequence>
                           <xs:element name="User" type="UserType" maxOccurs="unbounded"/>
                       </xs:sequence>
                   </xs:complexType>
       </xs:element>
           </xs:all>
       </xs:complexType>
   </xs:element>
   <xs:complexType name="GroupType">
       <xs:all>
           <xs:element name="Cmdlets" minOccurs="0">
               <xs:complexType>
                   <xs:sequence>
                       <xs:element name="Cmdlet" type="xs:string" maxOccurs="unbounded"/>
                   </xs:sequence>
               </xs:complexType>
           </xs:element>
           <xs:element name="Scripts" minOccurs="0">
               <xs:complexType>
                   <xs:sequence>
                       <xs:element name="Script" type="xs:string" maxOccurs="unbounded"/>
                   </xs:sequence>
               </xs:complexType>
           </xs:element>
           <xs:element name="Modules" minOccurs="0">
               <xs:complexType>
                   <xs:sequence>
                       <xs:element name="Module" type="xs:string" maxOccurs="unbounded"/>
                   </xs:sequence>
               </xs:complexType>
           </xs:element>
       </xs:all>
       <xs:attribute name="Name" type="xs:string" use="required"/>
       <xs:attribute name="UserName" type="xs:string" use="optional"/>
       <xs:attribute name="Password" type="xs:string" use="optional"/>
       <xs:attribute name="DomainName" type="xs:string" use="optional"/>
       <xs:attribute name="MapIncomingUser" type="xs:boolean" use="optional"/>
   </xs:complexType>
   <xs:complexType name="UserType">
       <xs:all>
           <xs:element name="Quota" minOccurs="0">
               <xs:complexType>
                   <xs:attribute name="MaxConcurrentRequests" type="xs:string" use="optional"/>
                   <xs:attribute name="MaxRequestsPerTimeslot" type="xs:string" use="optional"/>
                   <xs:attribute name="Timeslot" type="xs:string" use="optional"/>
               </xs:complexType>
           </xs:element>
       </xs:all>
       <xs:attribute name="Name" type="xs:string" use="required"/>
       <xs:attribute name="DomainName" type="xs:string" use="optional"/>
       <xs:attribute name="AuthenticationType" type="xs:string" use="required"/>
       <xs:attribute name="GroupName" type="xs:string" use="required"/>
   </xs:complexType>
</xs:schema>
```