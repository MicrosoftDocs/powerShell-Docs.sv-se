---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Package manifest values that impact the PowerShell Gallery UI
ms.openlocfilehash: 9e37fec879f2f5cbe3926c7dbc946389425d856a
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417041"
---
# <a name="package-manifest-values-that-impact-the-powershell-gallery-ui"></a>Package manifest values that impact the PowerShell Gallery UI

This topic provides publishers with summary information on how to modify the manifest for their PowerShell Gallery publications so that features of PowerShellGet cmdlets and the PowerShell Gallery UI will be affected. This content is organized by where the change will appear, starting with the center section, then the navigation area on the left. There is a detail section covering tags, which identifies important tags, as well as some of the more commonly used tags. There are two topics that provide manifest examples:

- For modules, see [Update Module Manifest](/powershell/module/powershellget/Update-ModuleManifest)
- For scripts, see [Create Script File with Metadata](/powershell/module/powershellget/New-ScriptFileInfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>PowerShell Gallery Feature Elements Controlled by the Manifest

The table below shows the elements of the PowerShell Gallery package page UI that are controlled by the publisher. Each item indicates if it may be controlled by the module or script manifest.

| UI Element | Beskrivning | Modul | Skript |
| --- | --- | --- | --- |
| **Title** | This is the name of the package that is published to the Gallery  | Nej | Nej |
| **Version** | The version displayed is the version string in the metadata, and a prerelease if is specified. The primary portion of the version in a Module manifest is the ModuleVersion. For a script, it is identified as .VERSION. If a prerelease version string is specified, it will be appended to the ModuleVersion for modules, or specified as part of .VERSION for scripts. There is documentation for specifying prerelease strings in [modules](module-prerelease-support.md), and in [scripts](script-prerelease-support.md) | Ja | Ja |
| **Beskrivning** | This is the Description in the module manifest, and in a script file manifest it is .DESCRIPTION | Ja | Ja |
| **Require license acceptance** | A module can require that the user accept a license, by modifying the module manifest with RequireLicenseAcceptance = $true, supplying a LicenseURI, and providing a license.txt file in the root of the module folder. Additional information is available in the [Require License Acceptance](../how-to/working-with-packages/packages-that-require-license-acceptance.md) topic. | Ja | Nej |
| **Versionsanmärkningar** | For modules, this information is drawn from the ReleaseNotes section, under PSData\PrivateData. In script manifests, it is the .RELEASENOTES element. | Ja | Ja |
| **Owners** | Owners are the list of users in the PowerShell Gallery who can update a package. The owner list is not included in the package manifest. Additional documentation describes how to [manage item owners](../how-to/publishing-packages/managing-package-owners.md). | Nej | Nej |
| **Author** | This is included in the module manifest as the Author, and in a script manifest as .AUTHOR. The Author field is often used to specify a company or organization associated with a package. | Ja | Ja |
| **Copyright** | This is the Copyright field in the module manifest, and .COPYRIGHT in a script manifest. | Ja | Ja |
| **FileList** | The file list is drawn from the package when it is published to the PowerShell Gallery. It is not controllable by the manifest information. Note: there is an additional .nuspec file listed with each package in the PowerShell Gallery that is not present after installing the package on a system. This is the Nuget package manifest for the package, and may be ignored. | Nej | Nej |
| **Tags** | For modules, Tags are included under PSData\PrivateData. For scripts, the section is labelled .TAGS. Note that tags cannot contain spaces, even when they are in quotes. Tags have additional requirements and meanings, which are described later in this topic in the Tag Details section. | Ja | Ja |
| **Cmdletar** | This is provided in the module manifest using CmdletsToExport. Note that the best practice is to explicitly list the items, rather than using the wildcard “*”, as that will improve the load-module performance for users. | Ja | Nej |
| **Functions** | This is provided in the module manifest using FunctionsToExport. Note that the best practice is to explicitly list the items, rather than using the wildcard “*”, as that will improve the load-module performance for users. | Ja | Nej |
| **DSC Resources** | For modules that will be used on PowerShell version 5.0 and above, this is provided in the manifest using DscResourcesToExport. If the module is to be used in PowerShell 4, the DSCResourcesToExport should not be used as it is not a supported manifest key. (DSC was not available prior to PowerShell 4.) | Ja | Nej |
| **Arbetsflöden** | Workflows are published to the PowerShell Gallery as scripts, and identified as workflows (see [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) for an example) in the code. This is not controlled by the manifest. | Nej | Nej |
| **Role capabilities** | This will be listed when the module published to the PowerShell Gallery contains one or more role capability (.psrc) files, which are used by JEA. See the JEA documentation for more details on [role capabilities](/powershell/scripting/learn/remoting/jea/role-capabilities). | Ja | Nej |
| **PowerShell Editions** | This is specified in a script or module manifest. For modules designed to be used with PowerShell 5.0 and below, this is controlled using Tags. For Desktop, use the tag PSEdition_Desktop, and for core, use the tag PSEdition_Core. For modules that will be used only on PowerShell 5.1 and above, there is a CompatiblePSEditions key in the main manifest. For additional detail, review the PS Edition feature in [the PowerShell Get documentation](module-psedition-support.md). | Ja | Ja |
| **Dependencies** | Dependencies are the modules in the PowerShell Gallery that are declared in either the module as RequiredModules, or in the script manifest as #Requires –Module (name). | Ja | Ja |
| **Minimum PowerShell version** | This can be specified in a module manifest as PowerShellVersion | Ja | Nej |
| **Version History** | The version history reflects the updates made to a module in the PowerShell Gallery. If a version of a package is hidden using the Delete feature, it will not be displayed in the version history, except to the package owners. | Nej | Nej |
| **Project Site** | The project site is provided for modules in the Privatedata\PSData section of the module manifest by specifying a ProjectURI. In the script manifest, it is controlled by specifying .PROJECTURI. | Ja | Ja |
| **License** | A license link is provided for modules in the Privatedata\PSData section of the module manifest by specifying a LicenseURI. In the script manifest, it is controlled by specifying .LICENSEURI. It is important to note that if a license is not provided via the LicenseURI, or within a module, then the terms of use for the PowerShell Gallery specify the terms of use for the package. See the terms of use for details. | Ja | Ja |
| **Icon** | An icon can be specified for any package in the PowerShell Gallery by supplying the IconURI flag in the script manifest, or in the Privatedata-PSData section of the module manifest. The IconURI should point to a 32x32 image with transparency background. The URI **must** be a direct image URL and **must not** go to a web page containing the image, or a file in the PowerShell Gallery package. | Ja | Ja |


## <a name="editing-package-details"></a>Editing package details

The PowerShell Gallery Edit package page allows publishers to change several of the fields displayed for a package, specifically:

- Titel
- Beskrivning
- Sammanfattning
- Icon URL
- Project home page URL
- Authors
- Copyright
- Taggar
- Versionskommentarer
- Require license

This approach is not generally recommended, except when needed to correct what is displayed for an older version of a module. Users who acquire the module will see the metadata does not match what is displayed in the PowerShell Gallery, which raises concerns about the package. This will frequently result in inquiries going to the package owners to confirm the change. It is strongly recommended that any time this approach is used, a new version of the package should be published with the same changes.

## <a name="tag-details"></a>Tag Details

Tags are simple strings consumers use to find packages. Tags are most valuable when they are used consistently across many packages related to the same topic. Using multiple flavors of the same word (for example database and databases, or test and testing) typically provides little benefit. Tags are single-word case-insensitive strings and cannot include blanks. If there is a phrase you believe users will search for, add that to the package description and it will be found in the search results. Use Pascal casing, hyphen, underscore, or period if you are trying to improve readability.
Be cautious about creating long, complex, and unusual tags, as they are often misspelled.

There are tags that are important to note, as the PowerShell Gallery and PowerShellGet cmdlets treat them uniquely. PSEdition_Desktop and PSEdition_Core are the specific examples, and are described above.

As noted above, tags provide the most value when they are specific, and used consistently across many packages. As a publisher trying to locate the best tags to use, the easiest approach is to search the PowerShell Gallery for tags you are considering. Ideally, there will be many packages returned, and the package descriptions will align with your use of that key word.

For reference, here are some most commonly used tags as of 12/14/2017. In some cases, there are similar but perhaps less ideal options listed beside the tag. It is a best practice to use the Preferred Tag, as that will result in less noise, and better search results for consumers.

| Preferred tag | Alternatives and notes |
| --- | --- |
| Azure |  |
| DSC | DesiredStateConfiguration is less desirable, it’s too long |
| ResourceManager | ARM is used to describe group of processors, and should not be used for Azure Resource Manager |
| DSCResourceKit |  |
| SQL |  |
| AWS |  |
| DSCResource |  |
| Automatisering |  |
| REST |  |
| ActiveDirectory | AD is not currently used by itself  |
| SQLServer |  |
| DBA |  |
| Säkerhet | Defense is less precise |
| Databas | Databases (plural) is less desirable |
| DevOps |  |
| Windows |  |
| Build |  |
| Distribution | Deploy is used somewhat less often |
| Cloud |  |
| GIT |  |
| Testa | Testing is less desirable |
| VersionControl | Version is less precise, although used more frequently  |
| Loggning | Preferred use of logging as an action |
| Logg | Preferred use of Log as a thing |
| Säkerhetskopiering |  |
| IaaS |  |
| Linux |  |
| IIS |  |
| AzureAutomation |  |
| Lagring |  |
| GitHub |  |
| Json |  |
| Exchange |  |
| Nätverk | Networking is similar, less often used |
| SharePoint |  |
| Rapporter | Reporting is an action, report is a thing |
| Report | Report is a thing |
| WinRM |  |
| Övervakning |  |
| VSTS |  |
| Excel |  |
| Google |  |
| Color |  |
| DNS |  |
| Office365 | Spelling out Office is preferable. O365 is less commonly used, although shorter |
| Gitlab |  |
| Pester |  |
| AzureAD |  |
| HTML |  |
| Hyper-V | HyperV is less common as a tag |
| Konfiguration |  |
| ChatOps |  |
| PackageManagement |  |
| WMI |  |
| Brandvägg |  |
| Docker |  |
| Appveyor |  |
| AzureRm | Used primarily for the AzureRM modules |
| Zip |  |
| MSI |  |
| MacOS |  |
| PoshBot |  |
