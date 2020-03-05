---
ms.date: 08/23/2017
keywords: PowerShell, cmdlet
title: Avinstallera Windows PowerShell-Webbåtkomst
ms.openlocfilehash: 3c2c83525f5a240976eef215b5eac939796c91e8
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279018"
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="613e3-103">Avinstallera Windows PowerShell-webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="613e3-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="613e3-104">Uppdaterad: 24 juni 2013</span><span class="sxs-lookup"><span data-stu-id="613e3-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="613e3-105">Gäller för: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="613e3-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="613e3-106">Stegen i det här avsnittet tar bort webbplatsen för Windows PowerShell-webbåtkomsten och motsvarande program från Gateway-servern där den är installerad.</span><span class="sxs-lookup"><span data-stu-id="613e3-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="613e3-107">Meddela användare</span><span class="sxs-lookup"><span data-stu-id="613e3-107">Notify users</span></span>

<span data-ttu-id="613e3-108">Innan du börjar, meddela användare av den webbaserade konsolen att du kommer ta bort webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="613e3-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="613e3-109">Om du avinstallerar Windows PowerShell-webbåtkomsten avinstalleras inte IIS eller andra funktioner som installerades automatiskt eftersom Windows PowerShell-webbåtkomsten kräver att de körs.</span><span class="sxs-lookup"><span data-stu-id="613e3-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span> <span data-ttu-id="613e3-110">Avinstallations processen lämnar funktioner som är installerade när Windows PowerShell-webbåtkomsten var beroende. Du kan avinstallera dessa funktioner separat om det behövs.</span><span class="sxs-lookup"><span data-stu-id="613e3-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="613e3-111">Rekommenderad (snabb) avinstallation</span><span class="sxs-lookup"><span data-stu-id="613e3-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="613e3-112">Procedurerna i det här avsnittet hjälper dig att avinstallera båda:</span><span class="sxs-lookup"><span data-stu-id="613e3-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="613e3-113">webb programmet för Windows PowerShell-webbåtkomst och</span><span class="sxs-lookup"><span data-stu-id="613e3-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="613e3-114">Windows PowerShell-funktionen för webb åtkomst</span><span class="sxs-lookup"><span data-stu-id="613e3-114">the Windows PowerShell Web Access feature</span></span>

<span data-ttu-id="613e3-115">med hjälp av Windows PowerShell-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="613e3-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="613e3-116">Steg 1: ta bort webb programmet med cmdletar</span><span class="sxs-lookup"><span data-stu-id="613e3-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="613e3-117">Gör något av följande för att öppna en Windows PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="613e3-117">Do one of the following to open a Windows PowerShell session.</span></span>

   - <span data-ttu-id="613e3-118">På Windows-skrivbordet, högerklickar du på **Windows PowerShell** i aktivitetsfältet.</span><span class="sxs-lookup"><span data-stu-id="613e3-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>
   - <span data-ttu-id="613e3-119">På **Start**skärmen i Windows klickar du på **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="613e3-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="613e3-120">Skriv `Uninstall-PswaWebApplication`och tryck sedan på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="613e3-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>

   1. <span data-ttu-id="613e3-121">Om du har angett ditt eget, anpassade webbplatsnamn, lägg då till `-WebsiteName`-parametern till ditt kommando och ange webbplatsnamnet.</span><span class="sxs-lookup"><span data-stu-id="613e3-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

      `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`

   1. <span data-ttu-id="613e3-122">Om du har använt ett anpassat webb program (inte standard programmet, **pswa**, lägger du till parametern `-WebApplicationName` till ditt kommando och anger namnet på webb programmet.</span><span class="sxs-lookup"><span data-stu-id="613e3-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

      `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`

   1. <span data-ttu-id="613e3-123">Om du använder ett testcertifikat, lägger du till parametern `DeleteTestCertificate` till cmdleten, på det sätt som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="613e3-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

      `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="613e3-124">Steg 2: Avinstallera Windows PowerShell-webbåtkomst med hjälp av cmdletar</span><span class="sxs-lookup"><span data-stu-id="613e3-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="613e3-125">Gör något av följande för att öppna en Windows PowerShell-session med utökade användar rättigheter.</span><span class="sxs-lookup"><span data-stu-id="613e3-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="613e3-126">Om en session redan är öppen, går du vidare till nästa steg.</span><span class="sxs-lookup"><span data-stu-id="613e3-126">If a session is already open, go on to the next step.</span></span>

    - <span data-ttu-id="613e3-127">På Windows-skrivbordet högerklickar du på **Windows PowerShell** i aktivitets fältet och klickar sedan på **Kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="613e3-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>
    - <span data-ttu-id="613e3-128">På Windows **start**skärm högerklickar du på **Windows PowerShell** och klickar sedan på **Kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="613e3-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="613e3-129">Skriv följande och tryck sedan på **RETUR**, där *computer_name* representerar en fjärrserver från vilken du vill ta bort Windows PowerShell-webbåtkomst.</span><span class="sxs-lookup"><span data-stu-id="613e3-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="613e3-130">Parametern `-Restart`, startar automatiskt om målservrar om det krävs för borttagningen.</span><span class="sxs-lookup"><span data-stu-id="613e3-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

    `Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart`

    <span data-ttu-id="613e3-131">För att ta bort roller och funktioner från en offline-VHD, behöver du lägga till både `-ComputerName`-parametern och `-VHD`-parametern.</span><span class="sxs-lookup"><span data-stu-id="613e3-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="613e3-132">Parametern `-ComputerName` innehåller namnet på den server som den virtuella hård disken ska monteras på och parametern `-VHD` innehåller sökvägen till VHD-filen på den angivna servern.</span><span class="sxs-lookup"><span data-stu-id="613e3-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

    `Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart`

1. <span data-ttu-id="613e3-133">När borttagningen är klar kontrollerar du att du har tagit bort Windows PowerShell-webbåtkomsten genom att öppna sidan **alla servrar** i Serverhanteraren, välja en server som du tog bort funktionen från och sedan Visa panelen **roller och funktioner** på sidan för den valda servern.</span><span class="sxs-lookup"><span data-stu-id="613e3-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="613e3-134">Du kan också köra den `Get-WindowsFeature`-cmdlet som är riktad mot den valda servern (Get-WindowsFeature-ComputerName &lt;*computer_name*&gt;) om du vill visa en lista över roller och funktioner som är installerade på servern.</span><span class="sxs-lookup"><span data-stu-id="613e3-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server  (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features  that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="613e3-135">Anpassad avinstallation</span><span class="sxs-lookup"><span data-stu-id="613e3-135">Custom uninstallation</span></span>

<span data-ttu-id="613e3-136">Procedurerna i det här avsnittet hjälper dig att avinstallera både webb programmet Windows PowerShell-webbåtkomst och Windows PowerShell-webbåtkomst med hjälp av guiden ta bort roller och funktioner i Serverhanteraren och konsolen IIS-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="613e3-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="613e3-137">Steg 1: ta bort webb programmet med IIS-hanteraren</span><span class="sxs-lookup"><span data-stu-id="613e3-137">Step 1: Delete the web application using IIS Manager</span></span>

1. <span data-ttu-id="613e3-138">Öppna IIS-hanteringskonsolen genom att göra något av följande.</span><span class="sxs-lookup"><span data-stu-id="613e3-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="613e3-139">Om den redan är öppen, går du vidare till nästa steg.</span><span class="sxs-lookup"><span data-stu-id="613e3-139">If it is already open, go on to the next step.</span></span>

   - <span data-ttu-id="613e3-140">På Windows-skrivbordet startar du Serverhanteraren genom att klicka på **Serverhanteraren** i aktivitets fältet i Windows.</span><span class="sxs-lookup"><span data-stu-id="613e3-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="613e3-141">I **verktyg** -menyn i Serverhanteraren klickar du på **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="613e3-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

   - <span data-ttu-id="613e3-142">På Windows **Start**-skärmen, fyller du i valfri del av namnet **IIS (Internet Information Services)-hanteraren**.</span><span class="sxs-lookup"><span data-stu-id="613e3-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="613e3-143">Klicka på genvägen när den visas i **Appar**-resultaten.</span><span class="sxs-lookup"><span data-stu-id="613e3-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="613e3-144">I träd fönstret i IIS-hanteraren väljer du den webbplats som kör webb programmet för Windows PowerShell-webbåtkomst.</span><span class="sxs-lookup"><span data-stu-id="613e3-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="613e3-145">I **Åtgärds**-panelen, under **Hantera webbplats**, klickar du på **Stoppa**.</span><span class="sxs-lookup"><span data-stu-id="613e3-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="613e3-146">I trädvyn högerklickar du på webb programmet på webbplatsen som kör webb programmet för Windows PowerShell-webbåtkomst och klickar sedan på **ta bort**.</span><span class="sxs-lookup"><span data-stu-id="613e3-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="613e3-147">I trädvyn väljer du **programpooler**, väljer mappen programpool för Windows PowerShell-programpool, klickar på **stoppa** i rutan **åtgärder** och klickar sedan på **ta bort** i innehålls rutan.</span><span class="sxs-lookup"><span data-stu-id="613e3-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="613e3-148">Stäng IIS-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="613e3-148">Close IIS Manager.</span></span>

   > [!WARNING]
   > <span data-ttu-id="613e3-149">Certifikatet tas inte bort under avinstallationen.</span><span class="sxs-lookup"><span data-stu-id="613e3-149">The certificate is not deleted during uninstallation.</span></span> <span data-ttu-id="613e3-150">Om du skapat ett självsignerat certifikat eller om du använde ett testcertfikat och vill ta bort det, radera certifikatet i IIS-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="613e3-150">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span>

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="613e3-151">Steg 2: Avinstallera Windows PowerShell-webbåtkomst med hjälp av guiden ta bort roller och funktioner</span><span class="sxs-lookup"><span data-stu-id="613e3-151">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="613e3-152">Om Serverhanteraren redan är öppet går du vidare till nästa steg.</span><span class="sxs-lookup"><span data-stu-id="613e3-152">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="613e3-153">Om Serverhanteraren inte redan är öppet öppnar du det genom att göra något av följande.</span><span class="sxs-lookup"><span data-stu-id="613e3-153">If Server Manager is not already open, open it by doing one of the following.</span></span>

    - <span data-ttu-id="613e3-154">På Windows-skrivbordet startar du Serverhanteraren genom att klicka på **Serverhanteraren** i aktivitets fältet i Windows.</span><span class="sxs-lookup"><span data-stu-id="613e3-154">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>
    - <span data-ttu-id="613e3-155">På **Start**skärmen i Windows klickar du på **Serverhanteraren**.</span><span class="sxs-lookup"><span data-stu-id="613e3-155">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="613e3-156">I **Hantera**-menyn, klickar du på **Ta bort roller och funktioner**.</span><span class="sxs-lookup"><span data-stu-id="613e3-156">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="613e3-157">På sidan **Välj målserver**, väljer du den server eller offline-VHD som du vill ta bort funktionen från.</span><span class="sxs-lookup"><span data-stu-id="613e3-157">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="613e3-158">Om du vill välja en offline-VHD väljer du först den server som du vill montera den virtuella hård disken på och väljer sedan VHD-filen.</span><span class="sxs-lookup"><span data-stu-id="613e3-158">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="613e3-159">När du har valt målservern klickar du på **Nästa**.</span><span class="sxs-lookup"><span data-stu-id="613e3-159">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="613e3-160">Klicka på **Nästa** igen för att hoppa vidare till sidan **Ta bort funktioner**.</span><span class="sxs-lookup"><span data-stu-id="613e3-160">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="613e3-161">Avmarkera kryssrutan för **Windows PowerShell-webbåtkomst** och klicka sedan på **Nästa**.</span><span class="sxs-lookup"><span data-stu-id="613e3-161">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="613e3-162">På sidan **Bekräfta borttagnings inställningarna** klickar du på **ta bort**.</span><span class="sxs-lookup"><span data-stu-id="613e3-162">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="613e3-163">Se även</span><span class="sxs-lookup"><span data-stu-id="613e3-163">See Also</span></span>

- [<span data-ttu-id="613e3-164">Installera och använda Windows PowerShell-Webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="613e3-164">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="613e3-165">Hjälp om IIS-hanteraren 7,0</span><span class="sxs-lookup"><span data-stu-id="613e3-165">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)