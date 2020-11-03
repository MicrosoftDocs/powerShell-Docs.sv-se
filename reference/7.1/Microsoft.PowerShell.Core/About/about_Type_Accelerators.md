---
description: Beskriver de typ acceleratorer som är tillgängliga för .NET Framework-klasser
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/01/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_accelerators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Accelerators
ms.openlocfilehash: 3c7f7f0d993819da1efbc7ba9f4c26bd2827bc84
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271275"
---
# <a name="about-type-accelerators"></a>Om typ acceleratorer

## <a name="short-desription"></a>KORT BESKRIVNING
Beskriver de typ acceleratorer som är tillgängliga för .NET Framework-klasser

## <a name="long-description"></a>LÅNG BESKRIVNING

Typ acceleratorer är alias för .NET Framework-klasser. De gör att du kan komma åt vissa .NET Framework-klasser utan att uttryckligen ange hela klass namnet. Du kan till exempel förkorta klassen **AliasAttribute** från `[System.Management.Automation.AliasAttribute]` till `[Alias]` .

> [!NOTE]
> Alla typ acceleratorer måste fortfarande omslutas med hakparenteser ( `[]` ).

## <a name="available-type-accelerators"></a>Tillgängliga typ acceleratorer

|        Gas          |                           Fullständigt klass namn                           |
|---------------------------- | ------------------------------------------------------------------- |
|ADSI                         | System. DirectoryServices. DirectoryEntry                             |
|adsisearcher                 | System. DirectoryServices. DirectorySearcher                          |
|Alias                        | System. Management. Automation. AliasAttribute                         |
|AllowEmptyCollection         | System. Management. Automation. AllowEmptyCollectionAttribute          |
|AllowEmptyString             | System. Management. Automation. AllowEmptyStringAttribute              |
|AllowNull                    | System. Management. Automation. AllowNullAttribute                     |
|ArgumentCompleter            | System. Management. Automation. ArgumentCompleterAttribute             |
|ArgumentCompletions          | System. Management. Automation. ArgumentCompletionsAttribute           |
|matris                        | System. array                                                        |
|bigint                       | System. Numerics. BigInteger                                          |
|boolesk                         | System. Boolean                                                      |
|stor                         | System. byte                                                         |
|char                         | System. char                                                         |
|cimclass                     | Microsoft. Management. Infrastructure. CimClass                        |
|cimconverter                 | Microsoft. Management. Infrastructure. CimConverter                    |
|ciminstance                  | Microsoft. Management. Infrastructure. CimInstance                     |
|CimSession                   | Microsoft. Management. Infrastructure. CimSession                      |
|cimtype                      | Microsoft. Management. Infrastructure. CimType                         |
|CmdletBinding                | System. Management. Automation. CmdletBindingAttribute                 |
|CultureInfo                  | System. globalisering. CultureInfo                                    |
|datetime                     | System. DateTime                                                     |
|decimal                      | System. decimal                                                      |
|double                       | System. Double                                                       |
|DscLocalConfigurationManager | System. Management. Automation. DscLocalConfigurationManagerAttribute  |
|DscProperty                  | System. Management. Automation. DscPropertyAttribute                   |
|Dscresource Keyword Supports                  | System. Management. Automation. DscResourceAttribute                   |
|ExperimentAction             | System. Management. Automation. ExperimentAction                       |
|Experimentell                 | System. Management. Automation. ExperimentalAttribute                  |
|ExperimentalFeature          | System. Management. Automation. ExperimentalFeature                    |
|flyt                        | System. Single                                                       |
|guid                         | System. GUID                                                         |
|hash                    | System. Collections. hash                                        |
|initialsessionstate          | System.Management.Automation.Runspaces.InitialSessionState          |
|int                          | System. Int32                                                        |
|Int16                        | System. Int16                                                        |
|Int32                        | System. Int32                                                        |
|Int64                        | System. Int64                                                        |
|adresser                    | System .net. IPAddress                                                |
|IPEndpoint                   | System .net. IPEndPoint                                               |
|long                         | System. Int64                                                        |
|adress                  | System .net. mail. mail-adress                                         |
|NullString                   | System. Management. Automation. language. NullString                    |
|ObjectSecurity               | System. Security. AccessControl. ObjectSecurity                        |
|OutputType                   | System. Management. Automation. OutputTypeAttribute                    |
|Parameter                    | System. Management. Automation. ParameterAttribute                     |
|PhysicalAddress              | System .net. NetworkInformation. PhysicalAddress                       |
|powershell                   | System. Management. Automation. PowerShell                             |
|psaliasproperty              | System. Management. Automation. PSAliasProperty                        |
|PSCredential                 | System. Management. Automation. PSCredential                           |
|PSCustomObject               | System. Management. Automation. PSObject                               |
|PSDefaultValue               | System.Management.Automation.PSDefaultValueAttribute                |
|pslistmodifier               | System. Management. Automation. PSListModifier                         |
|psmoduleinfo                 | System. Management. Automation. PSModuleInfo                           |
|psnoteproperty               | System. Management. Automation. PSNoteProperty                         |
|psobject                     | System. Management. Automation. PSObject                               |
|psprimitivedictionary        | System. Management. Automation. PSPrimitiveDictionary                  |
|pspropertyexpression         | Microsoft. PowerShell. commands. PSPropertyExpression                  |
|psscriptmethod               | System. Management. Automation. PSScriptMethod                         |
|psscriptproperty             | System. Management. Automation. PSScriptProperty                       |
|PSTypeNameAttribute          | System. Management. Automation. PSTypeNameAttribute                    |
|psvariable                   | System. Management. Automation. PSVariable                             |
|psvariableproperty           | System. Management. Automation. PSVariableProperty                     |
|Ref                          | System. Management. Automation. PSReference                            |
|verifiering                        | System. text. RegularExpressions. regex                                |
|körnings utrymme                     | System. Management. Automation. körnings utrymmen. körnings utrymme                     |
|runspacefactory              | System. Management. Automation. körnings utrymmen. RunspaceFactory              |
|SByte                        | System. SByte                                                        |
|script block                  | System. Management. Automation. script block                            |
|SecureString                 | System. Security. SecureString                                        |
|semver                       | System. Management. Automation. SemanticVersion                        |
|short                        | System. Int16                                                        |
|samma                       | System. Single                                                       |
|sträng                       | System. String                                                       |
|SupportsWildcards            | System. Management. Automation. SupportsWildcardsAttribute             |
|växla                       | System. Management. Automation. SwitchParameter                        |
|tidsintervall                     | System. TimeSpan                                                     |
|typ                         | System. Type                                                         |
|uint                         | System. UInt32                                                       |
|UInt16                       | System. UInt16                                                       |
|UInt32                       | System. UInt32                                                       |
|UInt64                       | System. UInt64                                                       |
|ulong                        | System. UInt64                                                       |
|URI                          | System. URI                                                          |
|ushort                       | System. UInt16                                                       |
|ValidateCount                | System. Management. Automation. ValidateCountAttribute                 |
|ValidateDrive                | System. Management. Automation. ValidateDriveAttribute                 |
|ValidateLength               | System. Management. Automation. ValidateLengthAttribute                |
|ValidateNotNull              | System. Management. Automation. ValidateNotNullAttribute               |
|ValidateNotNullOrEmpty       | System. Management. Automation. ValidateNotNullOrEmptyAttribute        |
|ValidatePattern              | System. Management. Automation. ValidatePatternAttribute               |
|ValidateRange                | System. Management. Automation. ValidateRangeAttribute                 |
|ValidateScript               | System. Management. Automation. ValidateScriptAttribute                |
|ValidateSet                  | System. Management. Automation. ValidateSetAttribute                   |
|ValidateTrustedData          | System. Management. Automation. ValidateTrustedDataAttribute           |
|ValidateUserDrive            | System. Management. Automation. ValidateUserDriveAttribute             |
|version                      | System. version                                                      |
|void                         | System. Void                                                         |
|WildcardPattern              | System. Management. Automation. WildcardPattern                        |
|tjänst                          | System. Management. ManagementObject                                  |
|wmiclass                     | System. Management. ManagementClass                                   |
|wmisearcher                  | System. Management. ManagementObjectSearcher                          |
|X500DistinguishedName        | System. Security. Cryptography. X509Certificates. X500DistinguishedName |
|X509Certificate              | System. Security. Cryptography. X509Certificates. X509Certificate       |
|xml                          | System.Xml.Xmldokument                                              |

