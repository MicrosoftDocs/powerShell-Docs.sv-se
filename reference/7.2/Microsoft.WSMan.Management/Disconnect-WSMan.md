---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disconnect-wsman?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-WSMan
ms.openlocfilehash: 948b870948f51bd51424beaeca45ed2b2d195891
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710321"
---
# <span data-ttu-id="dff6c-102">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="dff6c-102">Disconnect-WSMan</span></span>

## <span data-ttu-id="dff6c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="dff6c-103">SYNOPSIS</span></span>
<span data-ttu-id="dff6c-104">Kopplar från klienten från WinRM-tjänsten på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="dff6c-104">Disconnects the client from the WinRM service on a remote computer.</span></span>

## <span data-ttu-id="dff6c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dff6c-105">SYNTAX</span></span>

```
Disconnect-WSMan [[-ComputerName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="dff6c-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="dff6c-106">DESCRIPTION</span></span>
<span data-ttu-id="dff6c-107">Cmdleten **unconnect-WSMan** kopplar från klienten från WinRM-tjänsten på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="dff6c-107">The **Disconnect-WSMan** cmdlet disconnects the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="dff6c-108">Om du sparade WS-Management-sessionen i en variabel, behålls sessionsobjekt i variabeln, men läget för WS-Management-sessionen stängs.</span><span class="sxs-lookup"><span data-stu-id="dff6c-108">If you saved the WS-Management session in a variable, the session object remains in the variable, but the state of the WS-Management session is Closed.</span></span>
<span data-ttu-id="dff6c-109">Du kan använda den här cmdleten i kontexten för WSMan-providern för att koppla bort klienten från WinRM-tjänsten på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="dff6c-109">You can use this cmdlet within the context of the WSMan provider to disconnect the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="dff6c-110">Du kan också använda denna cmdlet för att koppla från WinRM-tjänsten på fjärrdatorer innan du byter till WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="dff6c-110">However, you can also use this cmdlet to disconnect from the WinRM service on remote computers before you change to the WSMan provider.</span></span>

<span data-ttu-id="dff6c-111">Mer information om hur du ansluter till WinRM-tjänsten på en fjärrdator finns i Connect-WSMan.</span><span class="sxs-lookup"><span data-stu-id="dff6c-111">For more information about how to connect to the WinRM service on a remote computer, see Connect-WSMan.</span></span>

## <span data-ttu-id="dff6c-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="dff6c-112">EXAMPLES</span></span>

### <span data-ttu-id="dff6c-113">Exempel 1: ta bort en anslutning till en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="dff6c-113">Example 1: Delete a connection to a remote computer</span></span>

```
PS C:\> Disconnect-WSMan -computer server01
PS C:\> cd WSMan:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
```

<span data-ttu-id="dff6c-114">Det här kommandot tar bort anslutningen till fjärrdatorn med namnet Server01.</span><span class="sxs-lookup"><span data-stu-id="dff6c-114">This command deletes the connection to the remote computer named server01.</span></span>

<span data-ttu-id="dff6c-115">Denna cmdlet används vanligt vis inom kontexten för WSMan-providern för att koppla från en fjärrdator, i det här fallet Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="dff6c-115">This cmdlet is generally used within the context of the WSMan provider to disconnect from a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="dff6c-116">Du kan dock också använda **Koppla från-WSMan** för att ta bort anslutningar till fjärrdatorer innan du byter till WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="dff6c-116">However, you can also use **Disconnect-WSMan** to remove connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="dff6c-117">Dessa anslutningar visas inte i listan dator namn.</span><span class="sxs-lookup"><span data-stu-id="dff6c-117">Those connections do not appear in the ComputerName list.</span></span>

## <span data-ttu-id="dff6c-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="dff6c-118">PARAMETERS</span></span>

### <span data-ttu-id="dff6c-119">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="dff6c-119">-ComputerName</span></span>
<span data-ttu-id="dff6c-120">Anger den dator som hanterings åtgärden ska köras mot.</span><span class="sxs-lookup"><span data-stu-id="dff6c-120">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="dff6c-121">Värdet kan vara ett fullständigt kvalificerat domän namn, ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="dff6c-121">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="dff6c-122">Använd namnet på den lokala datorn, Använd localhost eller Använd en punkt (.) för att ange den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="dff6c-122">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="dff6c-123">Den lokala datorn är standard.</span><span class="sxs-lookup"><span data-stu-id="dff6c-123">The local computer is the default.</span></span>
<span data-ttu-id="dff6c-124">Om fjärrdatorn finns i en annan domän än användaren måste du använda ett fullständigt kvalificerat domän namn.</span><span class="sxs-lookup"><span data-stu-id="dff6c-124">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="dff6c-125">Du kan skicka ett värde för den här parametern till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="dff6c-125">You can pipe a value for this parameter to the cmdlet.</span></span>

<span data-ttu-id="dff6c-126">Det går inte att koppla från den lokala värden.</span><span class="sxs-lookup"><span data-stu-id="dff6c-126">You cannot disconnect from the local host.</span></span>
<span data-ttu-id="dff6c-127">Det går inte att koppla från standard anslutningen till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="dff6c-127">That is, you cannot disconnect the default connection to the local computer.</span></span>
<span data-ttu-id="dff6c-128">Men om du skapar en separat anslutning till den lokala datorn, till exempel, med hjälp av dator namnet.</span><span class="sxs-lookup"><span data-stu-id="dff6c-128">However, if you create a separate connection to the local computer, for example, by using the computer name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dff6c-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dff6c-129">CommonParameters</span></span>
<span data-ttu-id="dff6c-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dff6c-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dff6c-131">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="dff6c-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dff6c-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="dff6c-132">INPUTS</span></span>

### <span data-ttu-id="dff6c-133">Inga</span><span class="sxs-lookup"><span data-stu-id="dff6c-133">None</span></span>
<span data-ttu-id="dff6c-134">Denna cmdlet accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="dff6c-134">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="dff6c-135">UTDATA</span><span class="sxs-lookup"><span data-stu-id="dff6c-135">OUTPUTS</span></span>

### <span data-ttu-id="dff6c-136">Inga</span><span class="sxs-lookup"><span data-stu-id="dff6c-136">None</span></span>
<span data-ttu-id="dff6c-137">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="dff6c-137">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="dff6c-138">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="dff6c-138">NOTES</span></span>

## <span data-ttu-id="dff6c-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="dff6c-139">RELATED LINKS</span></span>

[<span data-ttu-id="dff6c-140">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="dff6c-140">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="dff6c-141">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="dff6c-141">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="dff6c-142">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="dff6c-142">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="dff6c-143">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="dff6c-143">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="dff6c-144">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="dff6c-144">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="dff6c-145">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="dff6c-145">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="dff6c-146">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="dff6c-146">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="dff6c-147">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="dff6c-147">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="dff6c-148">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="dff6c-148">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="dff6c-149">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="dff6c-149">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="dff6c-150">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="dff6c-150">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="dff6c-151">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="dff6c-151">Test-WSMan</span></span>](Test-WSMan.md)

