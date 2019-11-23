---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Metodtips för hämtningsservern
ms.openlocfilehash: 5cb47598b11f7884dddf1440cec21afeab49bebb
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417724"
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="004cc-103">Metodtips för hämtningsservern</span><span class="sxs-lookup"><span data-stu-id="004cc-103">Pull server best practices</span></span>

<span data-ttu-id="004cc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="004cc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="004cc-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span><span class="sxs-lookup"><span data-stu-id="004cc-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="004cc-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](/powershell/scripting/dsc/pull-server/pullserver#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="004cc-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](/powershell/scripting/dsc/pull-server/pullserver#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="004cc-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span><span class="sxs-lookup"><span data-stu-id="004cc-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="004cc-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span><span class="sxs-lookup"><span data-stu-id="004cc-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="004cc-109">Doc Info</span><span class="sxs-lookup"><span data-stu-id="004cc-109">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="004cc-110">Author</span><span class="sxs-lookup"><span data-stu-id="004cc-110">Author</span></span> | <span data-ttu-id="004cc-111">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="004cc-111">Michael Greene</span></span>
<span data-ttu-id="004cc-112">Granskare</span><span class="sxs-lookup"><span data-stu-id="004cc-112">Reviewers</span></span> | <span data-ttu-id="004cc-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="004cc-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
<span data-ttu-id="004cc-114">Published</span><span class="sxs-lookup"><span data-stu-id="004cc-114">Published</span></span> | <span data-ttu-id="004cc-115">April, 2015</span><span class="sxs-lookup"><span data-stu-id="004cc-115">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="004cc-116">Abstract</span><span class="sxs-lookup"><span data-stu-id="004cc-116">Abstract</span></span>

<span data-ttu-id="004cc-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span><span class="sxs-lookup"><span data-stu-id="004cc-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="004cc-118">A pull server is a simple service that should take only minutes to deploy.</span><span class="sxs-lookup"><span data-stu-id="004cc-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="004cc-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span><span class="sxs-lookup"><span data-stu-id="004cc-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="004cc-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span><span class="sxs-lookup"><span data-stu-id="004cc-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="004cc-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview)  topic.</span><span class="sxs-lookup"><span data-stu-id="004cc-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview)  topic.</span></span>
<span data-ttu-id="004cc-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span><span class="sxs-lookup"><span data-stu-id="004cc-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="004cc-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span><span class="sxs-lookup"><span data-stu-id="004cc-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="004cc-124">The two major sections of this document:</span><span class="sxs-lookup"><span data-stu-id="004cc-124">The two major sections of this document:</span></span>

- <span data-ttu-id="004cc-125">Configuration Planning</span><span class="sxs-lookup"><span data-stu-id="004cc-125">Configuration Planning</span></span>
- <span data-ttu-id="004cc-126">Installation Guide</span><span class="sxs-lookup"><span data-stu-id="004cc-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="004cc-127">Versions of the Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="004cc-127">Versions of the Windows Management Framework</span></span>

<span data-ttu-id="004cc-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span><span class="sxs-lookup"><span data-stu-id="004cc-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="004cc-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span><span class="sxs-lookup"><span data-stu-id="004cc-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="004cc-130">Windows PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="004cc-130">Windows PowerShell Desired State Configuration</span></span>

<span data-ttu-id="004cc-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span><span class="sxs-lookup"><span data-stu-id="004cc-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="004cc-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span><span class="sxs-lookup"><span data-stu-id="004cc-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="004cc-133">For more information, see the [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="004cc-133">For more information, see the [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="004cc-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span><span class="sxs-lookup"><span data-stu-id="004cc-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="004cc-135">Pull server role</span><span class="sxs-lookup"><span data-stu-id="004cc-135">Pull server role</span></span>

<span data-ttu-id="004cc-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span><span class="sxs-lookup"><span data-stu-id="004cc-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="004cc-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span><span class="sxs-lookup"><span data-stu-id="004cc-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="004cc-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span><span class="sxs-lookup"><span data-stu-id="004cc-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="004cc-139">This functionality is useful in environments where there are a large number of target nodes.</span><span class="sxs-lookup"><span data-stu-id="004cc-139">This functionality is useful in environments where there are a large number of target nodes.</span></span>
<span data-ttu-id="004cc-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span><span class="sxs-lookup"><span data-stu-id="004cc-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="004cc-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span><span class="sxs-lookup"><span data-stu-id="004cc-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="004cc-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](/powershell/scripting/dsc/pullServer/pullserver) and</span><span class="sxs-lookup"><span data-stu-id="004cc-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](/powershell/scripting/dsc/pullServer/pullserver) and</span></span>

<span data-ttu-id="004cc-143">[Push and Pull Configuration Modes](/powershell/scripting/dsc/pullServer/pullserver).</span><span class="sxs-lookup"><span data-stu-id="004cc-143">[Push and Pull Configuration Modes](/powershell/scripting/dsc/pullServer/pullserver).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="004cc-144">Configuration planning</span><span class="sxs-lookup"><span data-stu-id="004cc-144">Configuration planning</span></span>

<span data-ttu-id="004cc-145">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span><span class="sxs-lookup"><span data-stu-id="004cc-145">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="004cc-146">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span><span class="sxs-lookup"><span data-stu-id="004cc-146">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="004cc-147">Programvarukrav</span><span class="sxs-lookup"><span data-stu-id="004cc-147">Software requirements</span></span>

<span data-ttu-id="004cc-148">Deployment of a pull server requires the DSC Service feature of Windows Server.</span><span class="sxs-lookup"><span data-stu-id="004cc-148">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="004cc-149">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="004cc-149">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="004cc-150">Software downloads</span><span class="sxs-lookup"><span data-stu-id="004cc-150">Software downloads</span></span>

<span data-ttu-id="004cc-151">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span><span class="sxs-lookup"><span data-stu-id="004cc-151">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="004cc-152">WMF</span><span class="sxs-lookup"><span data-stu-id="004cc-152">WMF</span></span>

<span data-ttu-id="004cc-153">Windows Server 2012 R2 includes a feature named the DSC Service.</span><span class="sxs-lookup"><span data-stu-id="004cc-153">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="004cc-154">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span><span class="sxs-lookup"><span data-stu-id="004cc-154">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span>
<span data-ttu-id="004cc-155">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span><span class="sxs-lookup"><span data-stu-id="004cc-155">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="004cc-156">[New versions of WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616)  can include updates to the DSC Service feature.</span><span class="sxs-lookup"><span data-stu-id="004cc-156">[New versions of WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="004cc-157">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span><span class="sxs-lookup"><span data-stu-id="004cc-157">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="004cc-158">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span><span class="sxs-lookup"><span data-stu-id="004cc-158">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span>
<span data-ttu-id="004cc-159">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span><span class="sxs-lookup"><span data-stu-id="004cc-159">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="004cc-160">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span><span class="sxs-lookup"><span data-stu-id="004cc-160">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

- <span data-ttu-id="004cc-161">Windows PowerShell Windows PowerShell Integrated Scripting</span><span class="sxs-lookup"><span data-stu-id="004cc-161">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
- <span data-ttu-id="004cc-162">Environment (ISE) Windows PowerShell Web Services (Management OData</span><span class="sxs-lookup"><span data-stu-id="004cc-162">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
- <span data-ttu-id="004cc-163">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="004cc-163">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="004cc-164">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="004cc-164">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="004cc-165">DSC resource</span><span class="sxs-lookup"><span data-stu-id="004cc-165">DSC resource</span></span>

<span data-ttu-id="004cc-166">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span><span class="sxs-lookup"><span data-stu-id="004cc-166">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="004cc-167">This document includes configuration scripts that can be used to deploy a production ready server node.</span><span class="sxs-lookup"><span data-stu-id="004cc-167">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="004cc-168">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span><span class="sxs-lookup"><span data-stu-id="004cc-168">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="004cc-169">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="004cc-169">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="004cc-170">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="004cc-170">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="004cc-171">Use the `Install-Module` cmdlet from the **PowerShellGet** module.</span><span class="sxs-lookup"><span data-stu-id="004cc-171">Use the `Install-Module` cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="004cc-172">The **PowerShellGet** module will download the module to:</span><span class="sxs-lookup"><span data-stu-id="004cc-172">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="004cc-173">Planning task</span><span class="sxs-lookup"><span data-stu-id="004cc-173">Planning task</span></span>|
---|
<span data-ttu-id="004cc-174">Do you have access to the installation files for Windows Server 2012 R2?</span><span class="sxs-lookup"><span data-stu-id="004cc-174">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="004cc-175">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span><span class="sxs-lookup"><span data-stu-id="004cc-175">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="004cc-176">How will you install the latest security updates after installing the operating system?</span><span class="sxs-lookup"><span data-stu-id="004cc-176">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="004cc-177">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span><span class="sxs-lookup"><span data-stu-id="004cc-177">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="004cc-178">Do you have access to Windows Server installation files that already include updates through offline injection?</span><span class="sxs-lookup"><span data-stu-id="004cc-178">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="004cc-179">Maskinvarukrav</span><span class="sxs-lookup"><span data-stu-id="004cc-179">Hardware requirements</span></span>

<span data-ttu-id="004cc-180">Pull server deployments are supported on both physical and virtual servers.</span><span class="sxs-lookup"><span data-stu-id="004cc-180">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="004cc-181">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="004cc-181">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="004cc-182">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span><span class="sxs-lookup"><span data-stu-id="004cc-182">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="004cc-183">Planning task</span><span class="sxs-lookup"><span data-stu-id="004cc-183">Planning task</span></span>|
---|
<span data-ttu-id="004cc-184">Will you deploy on physical hardware or on a virtualization platform?</span><span class="sxs-lookup"><span data-stu-id="004cc-184">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="004cc-185">What is the process to request a new server for your target environment?</span><span class="sxs-lookup"><span data-stu-id="004cc-185">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="004cc-186">What is the average turnaround time for a server to become available?</span><span class="sxs-lookup"><span data-stu-id="004cc-186">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="004cc-187">What size server will you request?</span><span class="sxs-lookup"><span data-stu-id="004cc-187">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="004cc-188">Konton</span><span class="sxs-lookup"><span data-stu-id="004cc-188">Accounts</span></span>

<span data-ttu-id="004cc-189">There are no service account requirements to deploy a pull server instance.</span><span class="sxs-lookup"><span data-stu-id="004cc-189">There are no service account requirements to deploy a pull server instance.</span></span>
<span data-ttu-id="004cc-190">However, there are scenarios where the website could run in the context of a local user account.</span><span class="sxs-lookup"><span data-stu-id="004cc-190">However, there are scenarios where the website could run in the context of a local user account.</span></span>
<span data-ttu-id="004cc-191">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span><span class="sxs-lookup"><span data-stu-id="004cc-191">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="004cc-192">DNS records</span><span class="sxs-lookup"><span data-stu-id="004cc-192">DNS records</span></span>

<span data-ttu-id="004cc-193">You will need a server name to use when configuring clients to work with a pull server environment.</span><span class="sxs-lookup"><span data-stu-id="004cc-193">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="004cc-194">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span><span class="sxs-lookup"><span data-stu-id="004cc-194">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span>
<span data-ttu-id="004cc-195">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span><span class="sxs-lookup"><span data-stu-id="004cc-195">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="004cc-196">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span><span class="sxs-lookup"><span data-stu-id="004cc-196">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span>
<span data-ttu-id="004cc-197">The intent of the additional name record is to increase flexibility should a change be required in the future.</span><span class="sxs-lookup"><span data-stu-id="004cc-197">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span>
<span data-ttu-id="004cc-198">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span><span class="sxs-lookup"><span data-stu-id="004cc-198">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="004cc-199">When choosing a name for the DNS record, keep the solution architecture in mind.</span><span class="sxs-lookup"><span data-stu-id="004cc-199">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="004cc-200">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span><span class="sxs-lookup"><span data-stu-id="004cc-200">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

<span data-ttu-id="004cc-201">Scenario</span><span class="sxs-lookup"><span data-stu-id="004cc-201">Scenario</span></span> |<span data-ttu-id="004cc-202">Best Practice</span><span class="sxs-lookup"><span data-stu-id="004cc-202">Best Practice</span></span>
:---|:---
<span data-ttu-id="004cc-203">Testmiljö</span><span class="sxs-lookup"><span data-stu-id="004cc-203">Test Environment</span></span> |<span data-ttu-id="004cc-204">Reproduce the planned production environment, if possible.</span><span class="sxs-lookup"><span data-stu-id="004cc-204">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="004cc-205">A server hostname is suitable for simple configurations.</span><span class="sxs-lookup"><span data-stu-id="004cc-205">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="004cc-206">If DNS is not available, an IP address may be used in lieu of a hostname.</span><span class="sxs-lookup"><span data-stu-id="004cc-206">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="004cc-207">Single Node Deployment</span><span class="sxs-lookup"><span data-stu-id="004cc-207">Single Node Deployment</span></span> |<span data-ttu-id="004cc-208">Create a DNS CNAME record that points to the server hostname.</span><span class="sxs-lookup"><span data-stu-id="004cc-208">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="004cc-209">For more information, see [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="004cc-209">For more information, see [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span></span>

<span data-ttu-id="004cc-210">Planning task</span><span class="sxs-lookup"><span data-stu-id="004cc-210">Planning task</span></span>|
---|
<span data-ttu-id="004cc-211">Do you know who to contact to have DNS records created and changed?</span><span class="sxs-lookup"><span data-stu-id="004cc-211">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="004cc-212">What is the average turnaround for a request for a DNS record?</span><span class="sxs-lookup"><span data-stu-id="004cc-212">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="004cc-213">Do you need to request static Hostname (A) records for servers?</span><span class="sxs-lookup"><span data-stu-id="004cc-213">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="004cc-214">What will you request as a CNAME?</span><span class="sxs-lookup"><span data-stu-id="004cc-214">What will you request as a CNAME?</span></span>|
<span data-ttu-id="004cc-215">If needed, what type of Load Balancing solution will you utilize?</span><span class="sxs-lookup"><span data-stu-id="004cc-215">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="004cc-216">(see section titled Load Balancing for details)</span><span class="sxs-lookup"><span data-stu-id="004cc-216">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="004cc-217">Public Key Infrastructure</span><span class="sxs-lookup"><span data-stu-id="004cc-217">Public Key Infrastructure</span></span>

<span data-ttu-id="004cc-218">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span><span class="sxs-lookup"><span data-stu-id="004cc-218">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="004cc-219">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span><span class="sxs-lookup"><span data-stu-id="004cc-219">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="004cc-220">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="004cc-220">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="004cc-221">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span><span class="sxs-lookup"><span data-stu-id="004cc-221">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="004cc-222">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span><span class="sxs-lookup"><span data-stu-id="004cc-222">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="004cc-223">Planning task</span><span class="sxs-lookup"><span data-stu-id="004cc-223">Planning task</span></span>|
---|
<span data-ttu-id="004cc-224">If certificate requests are not automated, who will you need to contact to requests a certificate?</span><span class="sxs-lookup"><span data-stu-id="004cc-224">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="004cc-225">What is the average turnaround for the request?</span><span class="sxs-lookup"><span data-stu-id="004cc-225">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="004cc-226">How will the certificate file be transferred to you?</span><span class="sxs-lookup"><span data-stu-id="004cc-226">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="004cc-227">How will the certificate private key be transferred to you?</span><span class="sxs-lookup"><span data-stu-id="004cc-227">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="004cc-228">How long is the default expiration time?</span><span class="sxs-lookup"><span data-stu-id="004cc-228">How long is the default expiration time?</span></span>|
<span data-ttu-id="004cc-229">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span><span class="sxs-lookup"><span data-stu-id="004cc-229">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="004cc-230">Choosing an architecture</span><span class="sxs-lookup"><span data-stu-id="004cc-230">Choosing an architecture</span></span>

<span data-ttu-id="004cc-231">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span><span class="sxs-lookup"><span data-stu-id="004cc-231">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="004cc-232">In most situations, the web service option will provide greater flexibility.</span><span class="sxs-lookup"><span data-stu-id="004cc-232">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="004cc-233">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span><span class="sxs-lookup"><span data-stu-id="004cc-233">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="004cc-234">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span><span class="sxs-lookup"><span data-stu-id="004cc-234">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span>
<span data-ttu-id="004cc-235">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span><span class="sxs-lookup"><span data-stu-id="004cc-235">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span>
<span data-ttu-id="004cc-236">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span><span class="sxs-lookup"><span data-stu-id="004cc-236">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="004cc-237">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span><span class="sxs-lookup"><span data-stu-id="004cc-237">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="004cc-238">Belastningsutjämning</span><span class="sxs-lookup"><span data-stu-id="004cc-238">Load balancing</span></span>

<span data-ttu-id="004cc-239">Clients interacting with the web service make a request for information that is returned in a single response.</span><span class="sxs-lookup"><span data-stu-id="004cc-239">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="004cc-240">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span><span class="sxs-lookup"><span data-stu-id="004cc-240">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="004cc-241">Planning task</span><span class="sxs-lookup"><span data-stu-id="004cc-241">Planning task</span></span>|
---|
<span data-ttu-id="004cc-242">What solution will be used for load balancing traffic across servers?</span><span class="sxs-lookup"><span data-stu-id="004cc-242">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="004cc-243">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span><span class="sxs-lookup"><span data-stu-id="004cc-243">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="004cc-244">What is the average turnaround for a request to configure a new load balanced web service?</span><span class="sxs-lookup"><span data-stu-id="004cc-244">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="004cc-245">What information will be required for the request?</span><span class="sxs-lookup"><span data-stu-id="004cc-245">What information will be required for the request?</span></span>|
<span data-ttu-id="004cc-246">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span><span class="sxs-lookup"><span data-stu-id="004cc-246">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="004cc-247">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span><span class="sxs-lookup"><span data-stu-id="004cc-247">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="004cc-248">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span><span class="sxs-lookup"><span data-stu-id="004cc-248">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="004cc-249">Staging configurations and modules on the pull server</span><span class="sxs-lookup"><span data-stu-id="004cc-249">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="004cc-250">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span><span class="sxs-lookup"><span data-stu-id="004cc-250">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="004cc-251">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span><span class="sxs-lookup"><span data-stu-id="004cc-251">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="004cc-252">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span><span class="sxs-lookup"><span data-stu-id="004cc-252">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="004cc-253">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span><span class="sxs-lookup"><span data-stu-id="004cc-253">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="004cc-254">DSC modules</span><span class="sxs-lookup"><span data-stu-id="004cc-254">DSC modules</span></span>

<span data-ttu-id="004cc-255">Clients that request a configuration will need the required DSC modules.</span><span class="sxs-lookup"><span data-stu-id="004cc-255">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="004cc-256">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span><span class="sxs-lookup"><span data-stu-id="004cc-256">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="004cc-257">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span><span class="sxs-lookup"><span data-stu-id="004cc-257">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="004cc-258">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span><span class="sxs-lookup"><span data-stu-id="004cc-258">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="004cc-259">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span><span class="sxs-lookup"><span data-stu-id="004cc-259">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="004cc-260">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span><span class="sxs-lookup"><span data-stu-id="004cc-260">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="004cc-261">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span><span class="sxs-lookup"><span data-stu-id="004cc-261">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="004cc-262">After the file is copied to the server a checksum file must be created.</span><span class="sxs-lookup"><span data-stu-id="004cc-262">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="004cc-263">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span><span class="sxs-lookup"><span data-stu-id="004cc-263">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="004cc-264">Planning task</span><span class="sxs-lookup"><span data-stu-id="004cc-264">Planning task</span></span>|
---|
<span data-ttu-id="004cc-265">If you are planning a test or lab environment which scenarios are key to validate?</span><span class="sxs-lookup"><span data-stu-id="004cc-265">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="004cc-266">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span><span class="sxs-lookup"><span data-stu-id="004cc-266">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="004cc-267">Will your environment have Internet access to retrieve public modules?</span><span class="sxs-lookup"><span data-stu-id="004cc-267">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="004cc-268">Who will be responsible for reviewing DSC modules?</span><span class="sxs-lookup"><span data-stu-id="004cc-268">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="004cc-269">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span><span class="sxs-lookup"><span data-stu-id="004cc-269">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="004cc-270">Will a central team accept DSC modules from application teams?</span><span class="sxs-lookup"><span data-stu-id="004cc-270">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="004cc-271">What will the process be?</span><span class="sxs-lookup"><span data-stu-id="004cc-271">What will the process be?</span></span>|
<span data-ttu-id="004cc-272">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span><span class="sxs-lookup"><span data-stu-id="004cc-272">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="004cc-273">Will your team be responsible for managing the automation platform as well?</span><span class="sxs-lookup"><span data-stu-id="004cc-273">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="004cc-274">DSC configurations</span><span class="sxs-lookup"><span data-stu-id="004cc-274">DSC configurations</span></span>

<span data-ttu-id="004cc-275">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span><span class="sxs-lookup"><span data-stu-id="004cc-275">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="004cc-276">The configurations are stored on the server as MOF documents.</span><span class="sxs-lookup"><span data-stu-id="004cc-276">The configurations are stored on the server as MOF documents.</span></span>
<span data-ttu-id="004cc-277">Each document will be named with a unique **Guid**.</span><span class="sxs-lookup"><span data-stu-id="004cc-277">Each document will be named with a unique **Guid**.</span></span> <span data-ttu-id="004cc-278">When clients are configured to connect with a pull server, they are also given the **Guid** for the configuration they should request.</span><span class="sxs-lookup"><span data-stu-id="004cc-278">When clients are configured to connect with a pull server, they are also given the **Guid** for the configuration they should request.</span></span> <span data-ttu-id="004cc-279">This system of referencing configurations by **Guid** guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span><span class="sxs-lookup"><span data-stu-id="004cc-279">This system of referencing configurations by **Guid** guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="004cc-280">Guids</span><span class="sxs-lookup"><span data-stu-id="004cc-280">Guids</span></span>

<span data-ttu-id="004cc-281">Planning for configuration **Guids** is worth additional attention when thinking through a pull server deployment.</span><span class="sxs-lookup"><span data-stu-id="004cc-281">Planning for configuration **Guids** is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="004cc-282">There is no specific requirement for how to handle **Guids** and the process is likely to be unique for each environment.</span><span class="sxs-lookup"><span data-stu-id="004cc-282">There is no specific requirement for how to handle **Guids** and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="004cc-283">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span><span class="sxs-lookup"><span data-stu-id="004cc-283">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="004cc-284">There are two general approaches:</span><span class="sxs-lookup"><span data-stu-id="004cc-284">There are two general approaches:</span></span>

- <span data-ttu-id="004cc-285">**Assigning Guids per server** — Provides a measure of assurance that every server configuration is controlled individually.</span><span class="sxs-lookup"><span data-stu-id="004cc-285">**Assigning Guids per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="004cc-286">This provides a level of precision around updates and can work well in environments with few servers.</span><span class="sxs-lookup"><span data-stu-id="004cc-286">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
- <span data-ttu-id="004cc-287">**Assigning Guids per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span><span class="sxs-lookup"><span data-stu-id="004cc-287">**Assigning Guids per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="004cc-288">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span><span class="sxs-lookup"><span data-stu-id="004cc-288">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

  <span data-ttu-id="004cc-289">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span><span class="sxs-lookup"><span data-stu-id="004cc-289">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="004cc-290">For more information, see [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span><span class="sxs-lookup"><span data-stu-id="004cc-290">For more information, see [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span></span>

<span data-ttu-id="004cc-291">Planning task</span><span class="sxs-lookup"><span data-stu-id="004cc-291">Planning task</span></span>|
---|
<span data-ttu-id="004cc-292">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span><span class="sxs-lookup"><span data-stu-id="004cc-292">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="004cc-293">If Configurations are authored by an application team, what will the process be to hand them off?</span><span class="sxs-lookup"><span data-stu-id="004cc-293">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="004cc-294">Will you leverage a repository to store configurations as they are being authored, across teams?</span><span class="sxs-lookup"><span data-stu-id="004cc-294">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="004cc-295">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span><span class="sxs-lookup"><span data-stu-id="004cc-295">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="004cc-296">How will you map Guids to servers or roles, and where will this be stored?</span><span class="sxs-lookup"><span data-stu-id="004cc-296">How will you map Guids to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="004cc-297">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration Guids?</span><span class="sxs-lookup"><span data-stu-id="004cc-297">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration Guids?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="004cc-298">Installation Guide</span><span class="sxs-lookup"><span data-stu-id="004cc-298">Installation Guide</span></span>

<span data-ttu-id="004cc-299">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span><span class="sxs-lookup"><span data-stu-id="004cc-299">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="004cc-300">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="004cc-300">Prerequisites</span></span>

<span data-ttu-id="004cc-301">To verify the version of PowerShell on your server use the following command.</span><span class="sxs-lookup"><span data-stu-id="004cc-301">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="004cc-302">If possible, upgrade to the latest version of Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="004cc-302">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="004cc-303">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span><span class="sxs-lookup"><span data-stu-id="004cc-303">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="004cc-304">The command will ask for your approval before downloading the module.</span><span class="sxs-lookup"><span data-stu-id="004cc-304">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="004cc-305">Installation and configuration scripts</span><span class="sxs-lookup"><span data-stu-id="004cc-305">Installation and configuration scripts</span></span>

<span data-ttu-id="004cc-306">The best method to deploy a DSC pull server is to use a DSC configuration script.</span><span class="sxs-lookup"><span data-stu-id="004cc-306">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="004cc-307">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span><span class="sxs-lookup"><span data-stu-id="004cc-307">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="004cc-308">Note:  Currently the `xPSDesiredStateConfiguration` DSC module requires the server to be EN-US locale.</span><span class="sxs-lookup"><span data-stu-id="004cc-308">Note:  Currently the `xPSDesiredStateConfiguration` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="004cc-309">Basic configuration for Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="004cc-309">Basic configuration for Windows Server 2012</span></span>

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="004cc-310">Advanced configuration for Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="004cc-310">Advanced configuration for Windows Server 2012 R2</span></span>

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a><span data-ttu-id="004cc-311">Verify pull server functionality</span><span class="sxs-lookup"><span data-stu-id="004cc-311">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="004cc-312">Configure clients</span><span class="sxs-lookup"><span data-stu-id="004cc-312">Configure clients</span></span>

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="004cc-313">Additional references, snippets, and examples</span><span class="sxs-lookup"><span data-stu-id="004cc-313">Additional references, snippets, and examples</span></span>

<span data-ttu-id="004cc-314">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span><span class="sxs-lookup"><span data-stu-id="004cc-314">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DscConfiguration –Wait -Verbose
```

<span data-ttu-id="004cc-315">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span><span class="sxs-lookup"><span data-stu-id="004cc-315">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="004cc-316">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span><span class="sxs-lookup"><span data-stu-id="004cc-316">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="004cc-317">Appendix - Understanding ODATA service data file types</span><span class="sxs-lookup"><span data-stu-id="004cc-317">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="004cc-318">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span><span class="sxs-lookup"><span data-stu-id="004cc-318">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="004cc-319">The type of file depends on the operating system, as described below.</span><span class="sxs-lookup"><span data-stu-id="004cc-319">The type of file depends on the operating system, as described below.</span></span>

- <span data-ttu-id="004cc-320">**Windows Server 2012** The file type will always be   .mdb</span><span class="sxs-lookup"><span data-stu-id="004cc-320">**Windows Server 2012** The file type will always be   .mdb</span></span>
- <span data-ttu-id="004cc-321">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span><span class="sxs-lookup"><span data-stu-id="004cc-321">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="004cc-322">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span><span class="sxs-lookup"><span data-stu-id="004cc-322">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>
