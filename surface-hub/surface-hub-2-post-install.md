---
title: Configure Windows 10 Pro or Enterprise on Surface Hub 2
description: This article includes recommendations to ensure the best experience when using a personalized large screen touch and pen computer.
keywords: Surface Hub, Windows 10, desktop, install, configuration
ms.prod: surface-hub
ms.mktglfcycl: deploy
ms.localizationpriority: low
ms.sitesec: library
ms.pagetype: deploy
audience: admin
manager: laurawi
ms.audience: itpro
author: greg-lindsay
ms.author: greglin
ms.collection: M365-modern-desktop
ms.topic: article
ms.date: 10/01/2020
appliesto:
- Surface Hub 2S
ms.openlocfilehash: 68f3fe1eb2fba0673444510fc77d3f41e09144af
ms.sourcegitcommit: e0047f07c42b1e3cbd074b66a4704ea72e9d7bae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2020
ms.locfileid: "11093897"
---
# <span data-ttu-id="03ab8-104">Configure Windows 10 Pro or Enterprise on Surface Hub 2</span><span class="sxs-lookup"><span data-stu-id="03ab8-104">Configure Windows 10 Pro or Enterprise on Surface Hub 2</span></span>

<span data-ttu-id="03ab8-105">After you have completed the installation process of migrating to Windows 10 Pro or Enterprise, you can perform the following steps to configure apps and settings on your Surface Hub 2.</span><span class="sxs-lookup"><span data-stu-id="03ab8-105">After you have completed the installation process of migrating to Windows 10 Pro or Enterprise, you can perform the following steps to configure apps and settings on your Surface Hub 2.</span></span> <span data-ttu-id="03ab8-106">These steps are recommended to ensure the best experience when using this personalized large screen touch and pen computer.</span><span class="sxs-lookup"><span data-stu-id="03ab8-106">These steps are recommended to ensure the best experience when using this personalized large screen touch and pen computer.</span></span>

<span data-ttu-id="03ab8-107">When performing these steps, you might find it useful to use a wired or wireless keyboard and mouse.</span><span class="sxs-lookup"><span data-stu-id="03ab8-107">When performing these steps, you might find it useful to use a wired or wireless keyboard and mouse.</span></span>

## <span data-ttu-id="03ab8-108">Configure system settings</span><span class="sxs-lookup"><span data-stu-id="03ab8-108">Configure system settings</span></span>

1. <span data-ttu-id="03ab8-109">Sign in with an account that has local administrator privileges on the device.</span><span class="sxs-lookup"><span data-stu-id="03ab8-109">Sign in with an account that has local administrator privileges on the device.</span></span>  
    - <span data-ttu-id="03ab8-110">On Azure AD joined devices, the user that performs the Azure AD join is automatically added to the local administrator group.</span><span class="sxs-lookup"><span data-stu-id="03ab8-110">On Azure AD joined devices, the user that performs the Azure AD join is automatically added to the local administrator group.</span></span> <span data-ttu-id="03ab8-111">Azure AD global administrators and Azure AD devices administrators are [also local administrators](https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin).</span><span class="sxs-lookup"><span data-stu-id="03ab8-111">Azure AD global administrators and Azure AD devices administrators are [also local administrators](https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin).</span></span> 
    - <span data-ttu-id="03ab8-112">You can type **net localgroup administrators** at a command prompt to list the accounts that have local administrator rights.</span><span class="sxs-lookup"><span data-stu-id="03ab8-112">You can type **net localgroup administrators** at a command prompt to list the accounts that have local administrator rights.</span></span>
2. <span data-ttu-id="03ab8-113">Rename the device using a friendly name, for example: **username-SHub-Desktop**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-113">Rename the device using a friendly name, for example: **username-SHub-Desktop**.</span></span>
3. <span data-ttu-id="03ab8-114">Select **Start** > **Settings** > **Accounts** > **Sync your settings** and turn **Sync settings** off.</span><span class="sxs-lookup"><span data-stu-id="03ab8-114">Select **Start** > **Settings** > **Accounts** > **Sync your settings** and turn **Sync settings** off.</span></span> 
    - <span data-ttu-id="03ab8-115">The settings used here are intended to enable the best large-screen touch experience, and therefore you may not want to sync other devices.</span><span class="sxs-lookup"><span data-stu-id="03ab8-115">The settings used here are intended to enable the best large-screen touch experience, and therefore you may not want to sync other devices.</span></span>
4. <span data-ttu-id="03ab8-116">Reboot the device.</span><span class="sxs-lookup"><span data-stu-id="03ab8-116">Reboot the device.</span></span>

## <span data-ttu-id="03ab8-117">Enable the touch keyboard and touchpad</span><span class="sxs-lookup"><span data-stu-id="03ab8-117">Enable the touch keyboard and touchpad</span></span>

1. <span data-ttu-id="03ab8-118">Tap and hold or right-click the taskbar and then select **Show touch keyboard button** and **Show touchpad button**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-118">Tap and hold or right-click the taskbar and then select **Show touch keyboard button** and **Show touchpad button**.</span></span> 
    - <span data-ttu-id="03ab8-119">The touch keyboard is helpful for direct user input, and the virtual touchpad helps with precise selections, hovering screen tips, or as an alternative to tap and hold for right-click.</span><span class="sxs-lookup"><span data-stu-id="03ab8-119">The touch keyboard is helpful for direct user input, and the virtual touchpad helps with precise selections, hovering screen tips, or as an alternative to tap and hold for right-click.</span></span> 
    - <span data-ttu-id="03ab8-120">See the following example.</span><span class="sxs-lookup"><span data-stu-id="03ab8-120">See the following example.</span></span>

     ![Touch settings](images/touch.png)

2. <span data-ttu-id="03ab8-122">Configure the touch keyboard to QWERTY and floating.</span><span class="sxs-lookup"><span data-stu-id="03ab8-122">Configure the touch keyboard to QWERTY and floating.</span></span>
    1. <span data-ttu-id="03ab8-123">Select the keyboard icon on the taskbar to show the touch keyboard.</span><span class="sxs-lookup"><span data-stu-id="03ab8-123">Select the keyboard icon on the taskbar to show the touch keyboard.</span></span>
    2. <span data-ttu-id="03ab8-124">On the touch keyboard, select the keyboard icon in the upper left corner to open keyboard settings.</span><span class="sxs-lookup"><span data-stu-id="03ab8-124">On the touch keyboard, select the keyboard icon in the upper left corner to open keyboard settings.</span></span>
    3. <span data-ttu-id="03ab8-125">Select the next to last keyboard type on the top row to enable QWERTY, and the last option on the second row to enable floating, which is very helpful on this large screen.</span><span class="sxs-lookup"><span data-stu-id="03ab8-125">Select the next to last keyboard type on the top row to enable QWERTY, and the last option on the second row to enable floating, which is very helpful on this large screen.</span></span> <span data-ttu-id="03ab8-126">See the following examples.</span><span class="sxs-lookup"><span data-stu-id="03ab8-126">See the following examples.</span></span>

     ![Keyboard settings](images/kbd.png)

3. <span data-ttu-id="03ab8-128">Configure the soft keyboard settings.</span><span class="sxs-lookup"><span data-stu-id="03ab8-128">Configure the soft keyboard settings.</span></span>
    1. <span data-ttu-id="03ab8-129">Search for and open **Typing settings**</span><span class="sxs-lookup"><span data-stu-id="03ab8-129">Search for and open **Typing settings**</span></span> 
    2. <span data-ttu-id="03ab8-130">Enable all the options under Spelling, Typing, and Touch keyboard.</span><span class="sxs-lookup"><span data-stu-id="03ab8-130">Enable all the options under Spelling, Typing, and Touch keyboard.</span></span>


<span data-ttu-id="03ab8-131">The following example shows the trackpad, which is useful to navigate and select options.</span><span class="sxs-lookup"><span data-stu-id="03ab8-131">The following example shows the trackpad, which is useful to navigate and select options.</span></span> <span data-ttu-id="03ab8-132">The onscreen keyboard is being used to search the Microsoft Store:</span><span class="sxs-lookup"><span data-stu-id="03ab8-132">The onscreen keyboard is being used to search the Microsoft Store:</span></span>

![Using the trackpad](images/store.png)

## <span data-ttu-id="03ab8-134">Configure bluetooth keyboard and mouse (optional)</span><span class="sxs-lookup"><span data-stu-id="03ab8-134">Configure bluetooth keyboard and mouse (optional)</span></span>

<span data-ttu-id="03ab8-135">Connect a keyboard and mouse if you are using the device as your primary Windows device, or you use it often for typing or precision work.</span><span class="sxs-lookup"><span data-stu-id="03ab8-135">Connect a keyboard and mouse if you are using the device as your primary Windows device, or you use it often for typing or precision work.</span></span>

<span data-ttu-id="03ab8-136">If your Surface Hub device is near to a PC, you can use [Mouse without Borders](https://aka.ms/mm) to move seamlessly between the Surface Hub and the PC.</span><span class="sxs-lookup"><span data-stu-id="03ab8-136">If your Surface Hub device is near to a PC, you can use [Mouse without Borders](https://aka.ms/mm) to move seamlessly between the Surface Hub and the PC.</span></span> <span data-ttu-id="03ab8-137">For more information, see [Microsoft download from The Garage: Mouse without Borders](https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/).</span><span class="sxs-lookup"><span data-stu-id="03ab8-137">For more information, see [Microsoft download from The Garage: Mouse without Borders](https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/).</span></span>

## <span data-ttu-id="03ab8-138">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="03ab8-138">OneDrive for Business</span></span>

<span data-ttu-id="03ab8-139">Use [OneDrive for Business](https://docs.microsoft.com/onedrive/onedrive) to easily share tools, logs, and other files between all your work devices.</span><span class="sxs-lookup"><span data-stu-id="03ab8-139">Use [OneDrive for Business](https://docs.microsoft.com/onedrive/onedrive) to easily share tools, logs, and other files between all your work devices.</span></span>

- <span data-ttu-id="03ab8-140">OneDrive enables you to share your work files between your laptops, Surface Hub Desktop, and your Intune-managed mobile devices.</span><span class="sxs-lookup"><span data-stu-id="03ab8-140">OneDrive enables you to share your work files between your laptops, Surface Hub Desktop, and your Intune-managed mobile devices.</span></span> <span data-ttu-id="03ab8-141">Files can be edited on any device, and all network connected devices will be updated with the changes.</span><span class="sxs-lookup"><span data-stu-id="03ab8-141">Files can be edited on any device, and all network connected devices will be updated with the changes.</span></span>
- <span data-ttu-id="03ab8-142">Considering the size of the Surface Hub SSD (128GB), if you configure OneDrive on your Surface Hub Desktop device, make sure the default configuration is to keep the files online and download files as you use them.</span><span class="sxs-lookup"><span data-stu-id="03ab8-142">Considering the size of the Surface Hub SSD (128GB), if you configure OneDrive on your Surface Hub Desktop device, make sure the default configuration is to keep the files online and download files as you use them.</span></span>

<span data-ttu-id="03ab8-143">To configure OneDrive to download files only when needed, set the **Files On-Demand** setting to **Save space and download files as you use them**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-143">To configure OneDrive to download files only when needed, set the **Files On-Demand** setting to **Save space and download files as you use them**.</span></span> <span data-ttu-id="03ab8-144">For more information, see [Query and set Files On-Demand states in Windows](https://docs.microsoft.com/onedrive/files-on-demand-windows).</span><span class="sxs-lookup"><span data-stu-id="03ab8-144">For more information, see [Query and set Files On-Demand states in Windows](https://docs.microsoft.com/onedrive/files-on-demand-windows).</span></span>

![OneDrive settings](images/onedrive.png)

> [!NOTE]
> <span data-ttu-id="03ab8-146">You can also repeat these steps to configure a personal OneDrive but be sure to conserve drive space and only download files as you need them.</span><span class="sxs-lookup"><span data-stu-id="03ab8-146">You can also repeat these steps to configure a personal OneDrive but be sure to conserve drive space and only download files as you need them.</span></span>

## <span data-ttu-id="03ab8-147">SharePoint and Teams</span><span class="sxs-lookup"><span data-stu-id="03ab8-147">SharePoint and Teams</span></span>

<span data-ttu-id="03ab8-148">SharePoint and Teams Channel files can also sync locally to your desktop devices, such as laptops and Surface Hubs, using the OneDrive sync engine.</span><span class="sxs-lookup"><span data-stu-id="03ab8-148">SharePoint and Teams Channel files can also sync locally to your desktop devices, such as laptops and Surface Hubs, using the OneDrive sync engine.</span></span>

<span data-ttu-id="03ab8-149">To sync internal corporate files to your local drive with the OneDrive sync app:</span><span class="sxs-lookup"><span data-stu-id="03ab8-149">To sync internal corporate files to your local drive with the OneDrive sync app:</span></span>

1. <span data-ttu-id="03ab8-150">Go to a SharePoint site and navigate to the top-level document directory for files that you are interested in viewing or editing from your local device.</span><span class="sxs-lookup"><span data-stu-id="03ab8-150">Go to a SharePoint site and navigate to the top-level document directory for files that you are interested in viewing or editing from your local device.</span></span>
2. <span data-ttu-id="03ab8-151">Select on the **Sync** button on the top of the SharePoint ribbon.</span><span class="sxs-lookup"><span data-stu-id="03ab8-151">Select on the **Sync** button on the top of the SharePoint ribbon.</span></span>
3. <span data-ttu-id="03ab8-152">Select on **Open** on the popup **This site is trying to open Microsoft OneDrive**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-152">Select on **Open** on the popup **This site is trying to open Microsoft OneDrive**.</span></span>
4. <span data-ttu-id="03ab8-153">Verify that the SharePoint files are synchronizing to your local drive by selecting on the OneDrive icon at the bottom right of the taskbar.</span><span class="sxs-lookup"><span data-stu-id="03ab8-153">Verify that the SharePoint files are synchronizing to your local drive by selecting on the OneDrive icon at the bottom right of the taskbar.</span></span>
5. <span data-ttu-id="03ab8-154">Verify the configuration is set to keep the files online and download the files only as you use them:</span><span class="sxs-lookup"><span data-stu-id="03ab8-154">Verify the configuration is set to keep the files online and download the files only as you use them:</span></span>
    1. <span data-ttu-id="03ab8-155">Open file explorer.</span><span class="sxs-lookup"><span data-stu-id="03ab8-155">Open file explorer.</span></span>
    2. <span data-ttu-id="03ab8-156">Navigate to and right select on the **Microsoft \ \<SharePoint Document Folder Name\>**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-156">Navigate to and right select on the **Microsoft \ \<SharePoint Document Folder Name\>**.</span></span>
    3. <span data-ttu-id="03ab8-157">Select **Free up space**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-157">Select **Free up space**.</span></span>
    4. <span data-ttu-id="03ab8-158">The Status column will display the status of files and folders.</span><span class="sxs-lookup"><span data-stu-id="03ab8-158">The Status column will display the status of files and folders.</span></span> <span data-ttu-id="03ab8-159">For more information, see [Sync SharePoint files with the OneDrive sync client](https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd).</span><span class="sxs-lookup"><span data-stu-id="03ab8-159">For more information, see [Sync SharePoint files with the OneDrive sync client](https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd).</span></span>
6. <span data-ttu-id="03ab8-160">Teams Channel files are stored in SharePoint sites, with all of the same SharePoint document functionality, including version history and synchronizing to your local desktop devices.</span><span class="sxs-lookup"><span data-stu-id="03ab8-160">Teams Channel files are stored in SharePoint sites, with all of the same SharePoint document functionality, including version history and synchronizing to your local desktop devices.</span></span> <span data-ttu-id="03ab8-161">To sync Teams Channel files:</span><span class="sxs-lookup"><span data-stu-id="03ab8-161">To sync Teams Channel files:</span></span>
    1. <span data-ttu-id="03ab8-162">Navigate to the Teams Channel of interest and select on the **Files** tab at the top.</span><span class="sxs-lookup"><span data-stu-id="03ab8-162">Navigate to the Teams Channel of interest and select on the **Files** tab at the top.</span></span> <span data-ttu-id="03ab8-163">Then select **Sync**. The files will start synchronizing and will be visible in File Explorer at **Desktop \ Microsoft \ \<name of the Teams Channel\>**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-163">Then select **Sync**. The files will start synchronizing and will be visible in File Explorer at **Desktop \ Microsoft \ \<name of the Teams Channel\>**.</span></span>
    2. <span data-ttu-id="03ab8-164">Use the same procedure that you used for synchronizing SharePoint sites to keep the files in the cloud and only download them when you use them, by tap and hold or right-click in File Explorer on the Teams Channel name, and then selecting **Free up space**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-164">Use the same procedure that you used for synchronizing SharePoint sites to keep the files in the cloud and only download them when you use them, by tap and hold or right-click in File Explorer on the Teams Channel name, and then selecting **Free up space**.</span></span>

## <span data-ttu-id="03ab8-165">Surface Hub pen settings</span><span class="sxs-lookup"><span data-stu-id="03ab8-165">Surface Hub pen settings</span></span>

**<span data-ttu-id="03ab8-166">Pair the Bluetooth Surface Hub Pen</span><span class="sxs-lookup"><span data-stu-id="03ab8-166">Pair the Bluetooth Surface Hub Pen</span></span>**

<span data-ttu-id="03ab8-167">Pair the pen to keep the pen firmware up to date and get battery charge information on the Bluetooth device settings page, or in the Surface app:</span><span class="sxs-lookup"><span data-stu-id="03ab8-167">Pair the pen to keep the pen firmware up to date and get battery charge information on the Bluetooth device settings page, or in the Surface app:</span></span>

1. <span data-ttu-id="03ab8-168">Select **Start** > **Settings** > **Devices**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-168">Select **Start** > **Settings** > **Devices**.</span></span>
2. <span data-ttu-id="03ab8-169">Select **Add Bluetooth or other device**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-169">Select **Add Bluetooth or other device**.</span></span>
3. <span data-ttu-id="03ab8-170">Choose **Bluetooth**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-170">Choose **Bluetooth**.</span></span>
4. <span data-ttu-id="03ab8-171">Remove the pen tail button and shake to disconnect the battery connection.</span><span class="sxs-lookup"><span data-stu-id="03ab8-171">Remove the pen tail button and shake to disconnect the battery connection.</span></span>
5. <span data-ttu-id="03ab8-172">Put the cap back on and press and hold the cap until the pairing LED flashes.</span><span class="sxs-lookup"><span data-stu-id="03ab8-172">Put the cap back on and press and hold the cap until the pairing LED flashes.</span></span>
6. <span data-ttu-id="03ab8-173">On the Surface Hub Bluetooth settings, choose **Surface Hub 2 Pen**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-173">On the Surface Hub Bluetooth settings, choose **Surface Hub 2 Pen**.</span></span>
7. <span data-ttu-id="03ab8-174">Complete the pairing operation.</span><span class="sxs-lookup"><span data-stu-id="03ab8-174">Complete the pairing operation.</span></span> 
8. <span data-ttu-id="03ab8-175">If the pairing is not successful, attempt to pair the pen again.</span><span class="sxs-lookup"><span data-stu-id="03ab8-175">If the pairing is not successful, attempt to pair the pen again.</span></span> <span data-ttu-id="03ab8-176">If necessary, reboot the device and then try again.</span><span class="sxs-lookup"><span data-stu-id="03ab8-176">If necessary, reboot the device and then try again.</span></span>

## <span data-ttu-id="03ab8-177">Camera configuration</span><span class="sxs-lookup"><span data-stu-id="03ab8-177">Camera configuration</span></span>

<span data-ttu-id="03ab8-178">You can mount the camera on the top or on either side of the device.</span><span class="sxs-lookup"><span data-stu-id="03ab8-178">You can mount the camera on the top or on either side of the device.</span></span> <span data-ttu-id="03ab8-179">Mount the camera in a position to optimize the camera angle if you are using the Hub with a desktop stand instead of a cart, or are in close proximity to the Hub.</span><span class="sxs-lookup"><span data-stu-id="03ab8-179">Mount the camera in a position to optimize the camera angle if you are using the Hub with a desktop stand instead of a cart, or are in close proximity to the Hub.</span></span> <span data-ttu-id="03ab8-180">The camera does not auto-rotate, so you need to have a 2mm hex key to manually rotate the camera.</span><span class="sxs-lookup"><span data-stu-id="03ab8-180">The camera does not auto-rotate, so you need to have a 2mm hex key to manually rotate the camera.</span></span> 

<span data-ttu-id="03ab8-181">For more information on how to side-mount the camera and rotate the camera manually, see [Surface Hub 2S camera lens orientation](https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation).</span><span class="sxs-lookup"><span data-stu-id="03ab8-181">For more information on how to side-mount the camera and rotate the camera manually, see [Surface Hub 2S camera lens orientation](https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation).</span></span>

## <span data-ttu-id="03ab8-182">Windows Hello configuration</span><span class="sxs-lookup"><span data-stu-id="03ab8-182">Windows Hello configuration</span></span>

<span data-ttu-id="03ab8-183">Surface Hub 2S running Windows 10 Enterprise allows the full suite of Win32 desktop applications as well as biometric Windows Hello options.</span><span class="sxs-lookup"><span data-stu-id="03ab8-183">Surface Hub 2S running Windows 10 Enterprise allows the full suite of Win32 desktop applications as well as biometric Windows Hello options.</span></span> <span data-ttu-id="03ab8-184">The Surface Hub 2 Fingerprint Reader accessory can be plugged into any USB-C port on the device.</span><span class="sxs-lookup"><span data-stu-id="03ab8-184">The Surface Hub 2 Fingerprint Reader accessory can be plugged into any USB-C port on the device.</span></span> 

<span data-ttu-id="03ab8-185">To order a Surface Hub 2 Fingerprint Reader or view technical specs, see [Essential add-ons for Windows 10 Pro and Enterprise on Surface Hub 2](surface-hub-2-essential-add-ons.md).</span><span class="sxs-lookup"><span data-stu-id="03ab8-185">To order a Surface Hub 2 Fingerprint Reader or view technical specs, see [Essential add-ons for Windows 10 Pro and Enterprise on Surface Hub 2](surface-hub-2-essential-add-ons.md).</span></span> 

<span data-ttu-id="03ab8-186">After inserting the fingerprint reader, select **Start** > **Settings** > **Accounts** > **Sign-in options** > **Windows Hello Fingerprint** to enroll your fingerprint.</span><span class="sxs-lookup"><span data-stu-id="03ab8-186">After inserting the fingerprint reader, select **Start** > **Settings** > **Accounts** > **Sign-in options** > **Windows Hello Fingerprint** to enroll your fingerprint.</span></span>

<span data-ttu-id="03ab8-187">Use a Windows Hello certified device for face recognition.</span><span class="sxs-lookup"><span data-stu-id="03ab8-187">Use a Windows Hello certified device for face recognition.</span></span> <span data-ttu-id="03ab8-188">The Surface Hub 2S camera does not support Windows Hello face recognition.</span><span class="sxs-lookup"><span data-stu-id="03ab8-188">The Surface Hub 2S camera does not support Windows Hello face recognition.</span></span>

## <span data-ttu-id="03ab8-189">Enable a Lock Screen shortcut icon on the taskbar</span><span class="sxs-lookup"><span data-stu-id="03ab8-189">Enable a Lock Screen shortcut icon on the taskbar</span></span>

<span data-ttu-id="03ab8-190">To add an icon to the taskbar that enables one-touch screen lock similar to the Windows-L keyboard shortcut:</span><span class="sxs-lookup"><span data-stu-id="03ab8-190">To add an icon to the taskbar that enables one-touch screen lock similar to the Windows-L keyboard shortcut:</span></span> 

1.  <span data-ttu-id="03ab8-191">Tap and hold or right-click on the desktop, select **New** > **Shortcut** > **Browse** > **Desktop** > **OK** > **Next**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-191">Tap and hold or right-click on the desktop, select **New** > **Shortcut** > **Browse** > **Desktop** > **OK** > **Next**.</span></span>

1.  <span data-ttu-id="03ab8-192">Provide a name for the shortcut such as **Lock my PC**, and then select **Finish**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-192">Provide a name for the shortcut such as **Lock my PC**, and then select **Finish**.</span></span>

1.  <span data-ttu-id="03ab8-193">Right-click or tap and hold the newly created shortcut on the desktop, and select **Properties**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-193">Right-click or tap and hold the newly created shortcut on the desktop, and select **Properties**.</span></span> <span data-ttu-id="03ab8-194">On the **Shortcut** tab, enter the following in the **Target** field: **Rundll32.exe User32.dll,LockWorkStation**</span><span class="sxs-lookup"><span data-stu-id="03ab8-194">On the **Shortcut** tab, enter the following in the **Target** field: **Rundll32.exe User32.dll,LockWorkStation**</span></span>

1.  <span data-ttu-id="03ab8-195">Select the **Change Icon** button and browse to **C:\Windows\System32\imageres.dll** and select an icon to use.</span><span class="sxs-lookup"><span data-stu-id="03ab8-195">Select the **Change Icon** button and browse to **C:\Windows\System32\imageres.dll** and select an icon to use.</span></span> 

    <span data-ttu-id="03ab8-196">See the following example:</span><span class="sxs-lookup"><span data-stu-id="03ab8-196">See the following example:</span></span>

    ![Choose an icon](images/lock.png)
    
1.  <span data-ttu-id="03ab8-198">Select **OK** to save the shortcut.</span><span class="sxs-lookup"><span data-stu-id="03ab8-198">Select **OK** to save the shortcut.</span></span>

1.  <span data-ttu-id="03ab8-199">Right-click or tap and hold the shortcut and select **Pin to taskbar**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-199">Right-click or tap and hold the shortcut and select **Pin to taskbar**.</span></span>

1. <span data-ttu-id="03ab8-200">After you have pinned the lock shortcut to the taskbar, you can delete it from the desktop.</span><span class="sxs-lookup"><span data-stu-id="03ab8-200">After you have pinned the lock shortcut to the taskbar, you can delete it from the desktop.</span></span>

## <span data-ttu-id="03ab8-201">Applications</span><span class="sxs-lookup"><span data-stu-id="03ab8-201">Applications</span></span>

### <span data-ttu-id="03ab8-202">Update installed apps</span><span class="sxs-lookup"><span data-stu-id="03ab8-202">Update installed apps</span></span>

<span data-ttu-id="03ab8-203">To update all installed Store apps:</span><span class="sxs-lookup"><span data-stu-id="03ab8-203">To update all installed Store apps:</span></span>

1. <span data-ttu-id="03ab8-204">Open Microsoft Store app and select the **See more** ellipsis in the top-right corner.</span><span class="sxs-lookup"><span data-stu-id="03ab8-204">Open Microsoft Store app and select the **See more** ellipsis in the top-right corner.</span></span>
2. <span data-ttu-id="03ab8-205">Select **Downloads and updates**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-205">Select **Downloads and updates**.</span></span>
2. <span data-ttu-id="03ab8-206">Select **Get updates**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-206">Select **Get updates**.</span></span>

### <span data-ttu-id="03ab8-207">Microsoft Whiteboard</span><span class="sxs-lookup"><span data-stu-id="03ab8-207">Microsoft Whiteboard</span></span>

<span data-ttu-id="03ab8-208">To install the Microsoft Whiteboard:</span><span class="sxs-lookup"><span data-stu-id="03ab8-208">To install the Microsoft Whiteboard:</span></span>

 - <span data-ttu-id="03ab8-209">Select the **Windows Ink Workspace** icon on the lower right of the taskbar and download **Whiteboard**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-209">Select the **Windows Ink Workspace** icon on the lower right of the taskbar and download **Whiteboard**.</span></span>
 
   ![Ink workspace](images/ink.png) 

<span data-ttu-id="03ab8-211">Alternatively, you can install Whiteboard from the Microsoft Store:</span><span class="sxs-lookup"><span data-stu-id="03ab8-211">Alternatively, you can install Whiteboard from the Microsoft Store:</span></span>

1. <span data-ttu-id="03ab8-212">Open Microsoft Store app and search for **Whiteboard**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-212">Open Microsoft Store app and search for **Whiteboard**.</span></span>
2. <span data-ttu-id="03ab8-213">Choose **No thanks** to sign in and use across devices.</span><span class="sxs-lookup"><span data-stu-id="03ab8-213">Choose **No thanks** to sign in and use across devices.</span></span>
3. <span data-ttu-id="03ab8-214">Pin Whiteboard to the taskbar.</span><span class="sxs-lookup"><span data-stu-id="03ab8-214">Pin Whiteboard to the taskbar.</span></span>

### <span data-ttu-id="03ab8-215">Surface app</span><span class="sxs-lookup"><span data-stu-id="03ab8-215">Surface app</span></span>

1. <span data-ttu-id="03ab8-216">In the Microsoft Store, search for **Surface**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-216">In the Microsoft Store, search for **Surface**.</span></span>
2. <span data-ttu-id="03ab8-217">Set the **Available on** filter to **All devices**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-217">Set the **Available on** filter to **All devices**.</span></span>
3. <span data-ttu-id="03ab8-218">Install the **Surface** app.</span><span class="sxs-lookup"><span data-stu-id="03ab8-218">Install the **Surface** app.</span></span> <span data-ttu-id="03ab8-219">This should be the first app listed.</span><span class="sxs-lookup"><span data-stu-id="03ab8-219">This should be the first app listed.</span></span> <span data-ttu-id="03ab8-220">You might need to associate your MSA to the Store in order to install the app.</span><span class="sxs-lookup"><span data-stu-id="03ab8-220">You might need to associate your MSA to the Store in order to install the app.</span></span>
4. <span data-ttu-id="03ab8-221">Pin the **Surface** app to taskbar.</span><span class="sxs-lookup"><span data-stu-id="03ab8-221">Pin the **Surface** app to taskbar.</span></span>

### <span data-ttu-id="03ab8-222">Snip & Sketch</span><span class="sxs-lookup"><span data-stu-id="03ab8-222">Snip & Sketch</span></span>

1. <span data-ttu-id="03ab8-223">Open the **Snip & Sketch** app and pin it to the taskbar.</span><span class="sxs-lookup"><span data-stu-id="03ab8-223">Open the **Snip & Sketch** app and pin it to the taskbar.</span></span>
2. <span data-ttu-id="03ab8-224">Select the ellipsis in the upper right corner and then select **Settings**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-224">Select the ellipsis in the upper right corner and then select **Settings**.</span></span>
3. <span data-ttu-id="03ab8-225">In **Settings**, turn on **Auto copy to clipboard**, **Save snips**, and **Multiple windows** (optional).</span><span class="sxs-lookup"><span data-stu-id="03ab8-225">In **Settings**, turn on **Auto copy to clipboard**, **Save snips**, and **Multiple windows** (optional).</span></span>

### <span data-ttu-id="03ab8-226">Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="03ab8-226">Microsoft Office</span></span>

1. <span data-ttu-id="03ab8-227">Open the [Office Portal](https://portal.office.com/account#installs) and install your desired applications.</span><span class="sxs-lookup"><span data-stu-id="03ab8-227">Open the [Office Portal](https://portal.office.com/account#installs) and install your desired applications.</span></span>
2. <span data-ttu-id="03ab8-228">Pin desired Office applications to the taskbar.</span><span class="sxs-lookup"><span data-stu-id="03ab8-228">Pin desired Office applications to the taskbar.</span></span>
3. <span data-ttu-id="03ab8-229">If Outlook is installed, be sure to set the Outlook OST to only save last two weeks cache.</span><span class="sxs-lookup"><span data-stu-id="03ab8-229">If Outlook is installed, be sure to set the Outlook OST to only save last two weeks cache.</span></span> <span data-ttu-id="03ab8-230">This will vastly reduce disk usage and setup time.</span><span class="sxs-lookup"><span data-stu-id="03ab8-230">This will vastly reduce disk usage and setup time.</span></span>
    - <span data-ttu-id="03ab8-231">Select **File** > **Account Settings** and select your account.</span><span class="sxs-lookup"><span data-stu-id="03ab8-231">Select **File** > **Account Settings** and select your account.</span></span>
    - <span data-ttu-id="03ab8-232">Select **Change** and set the slider for **Use Cached Exchange Mode** to 14 days.</span><span class="sxs-lookup"><span data-stu-id="03ab8-232">Select **Change** and set the slider for **Use Cached Exchange Mode** to 14 days.</span></span>

### <span data-ttu-id="03ab8-233">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="03ab8-233">Microsoft Teams</span></span>

1. <span data-ttu-id="03ab8-234">Download and install [Microsoft Teams](https://teams.microsoft.com/downloads).</span><span class="sxs-lookup"><span data-stu-id="03ab8-234">Download and install [Microsoft Teams](https://teams.microsoft.com/downloads).</span></span>
2. <span data-ttu-id="03ab8-235">Configure settings to Auto-start application (optional).</span><span class="sxs-lookup"><span data-stu-id="03ab8-235">Configure settings to Auto-start application (optional).</span></span>
3. <span data-ttu-id="03ab8-236">Pin Teams to the taskbar.</span><span class="sxs-lookup"><span data-stu-id="03ab8-236">Pin Teams to the taskbar.</span></span>
4. <span data-ttu-id="03ab8-237">Consider reducing Teams notifications on the device to avoid distractions (optional).</span><span class="sxs-lookup"><span data-stu-id="03ab8-237">Consider reducing Teams notifications on the device to avoid distractions (optional).</span></span>

  ![Teams notifications](images/teams.png)

### <span data-ttu-id="03ab8-239">Connect app</span><span class="sxs-lookup"><span data-stu-id="03ab8-239">Connect app</span></span>

> [!IMPORTANT]
> <span data-ttu-id="03ab8-240">In Windows 10, version 2004 and later, the Connect app for wireless projection using Miracast is not installed by default, but is available as an optional feature.</span><span class="sxs-lookup"><span data-stu-id="03ab8-240">In Windows 10, version 2004 and later, the Connect app for wireless projection using Miracast is not installed by default, but is available as an optional feature.</span></span> <span data-ttu-id="03ab8-241">To install the app, select on **Settings** > **Apps** > **Optional features** > **Add a feature** and then install the **Wireless Display** app.</span><span class="sxs-lookup"><span data-stu-id="03ab8-241">To install the app, select on **Settings** > **Apps** > **Optional features** > **Add a feature** and then install the **Wireless Display** app.</span></span>

1. <span data-ttu-id="03ab8-242">Search for **Connect**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-242">Search for **Connect**.</span></span>
2. <span data-ttu-id="03ab8-243">Open the app and then close it (**Project to this PC** might not work unless the app has been run at least once).</span><span class="sxs-lookup"><span data-stu-id="03ab8-243">Open the app and then close it (**Project to this PC** might not work unless the app has been run at least once).</span></span>
3. <span data-ttu-id="03ab8-244">Tap and hold or right-click to pin to taskbar.</span><span class="sxs-lookup"><span data-stu-id="03ab8-244">Tap and hold or right-click to pin to taskbar.</span></span>
4. <span data-ttu-id="03ab8-245">Search for **Projection settings**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-245">Search for **Projection settings**.</span></span>
5. <span data-ttu-id="03ab8-246">Under **Some Windows and Android devices can project to this PC when you say it's OK**, choose **Available everywhere** if the device is not on a corporate network.</span><span class="sxs-lookup"><span data-stu-id="03ab8-246">Under **Some Windows and Android devices can project to this PC when you say it's OK**, choose **Available everywhere** if the device is not on a corporate network.</span></span> <span data-ttu-id="03ab8-247">Otherwise, you can choose **Available everywhere on secure networks**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-247">Otherwise, you can choose **Available everywhere on secure networks**.</span></span>
6. <span data-ttu-id="03ab8-248">Under **Ask to project to this PC**, choose **First time only**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-248">Under **Ask to project to this PC**, choose **First time only**.</span></span>
7. <span data-ttu-id="03ab8-249">Under **Require PIN for pairing**, choose **Never**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-249">Under **Require PIN for pairing**, choose **Never**.</span></span>

<span data-ttu-id="03ab8-250">Recommended configuration when not on the corporate network:</span><span class="sxs-lookup"><span data-stu-id="03ab8-250">Recommended configuration when not on the corporate network:</span></span>

  ![Settings at home](images/project1.png)

<span data-ttu-id="03ab8-252">Recommended configuration on the corporate network:</span><span class="sxs-lookup"><span data-stu-id="03ab8-252">Recommended configuration on the corporate network:</span></span>

  ![Settings at work](images/project2.png)

### <span data-ttu-id="03ab8-254">Your Phone</span><span class="sxs-lookup"><span data-stu-id="03ab8-254">Your Phone</span></span>

<span data-ttu-id="03ab8-255">The **Your Phone** app is installed by default on Windows 10.</span><span class="sxs-lookup"><span data-stu-id="03ab8-255">The **Your Phone** app is installed by default on Windows 10.</span></span> <span data-ttu-id="03ab8-256">If it is not present, you can also install it from the Windows Store.</span><span class="sxs-lookup"><span data-stu-id="03ab8-256">If it is not present, you can also install it from the Windows Store.</span></span>

<span data-ttu-id="03ab8-257">For information about setting up the app, see [How to set up Your Phone on Windows 10 and sync data between your PC and phone](https://www.windowscentral.com/how-set-your-phone-windows-10).</span><span class="sxs-lookup"><span data-stu-id="03ab8-257">For information about setting up the app, see [How to set up Your Phone on Windows 10 and sync data between your PC and phone](https://www.windowscentral.com/how-set-your-phone-windows-10).</span></span> <span data-ttu-id="03ab8-258">Also see [How to fix common problems with Your Phone app on Windows 10](https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10).</span><span class="sxs-lookup"><span data-stu-id="03ab8-258">Also see [How to fix common problems with Your Phone app on Windows 10](https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10).</span></span>

### <span data-ttu-id="03ab8-259">Super Fancy Zones</span><span class="sxs-lookup"><span data-stu-id="03ab8-259">Super Fancy Zones</span></span>

<span data-ttu-id="03ab8-260">**Super Fancy Zones** helps users arrange windows to maximize screen real estate.</span><span class="sxs-lookup"><span data-stu-id="03ab8-260">**Super Fancy Zones** helps users arrange windows to maximize screen real estate.</span></span> <span data-ttu-id="03ab8-261">It is now included in [PowerToys](https://github.com/microsoft/PowerToys/releases) on GitHub.</span><span class="sxs-lookup"><span data-stu-id="03ab8-261">It is now included in [PowerToys](https://github.com/microsoft/PowerToys/releases) on GitHub.</span></span>

### <span data-ttu-id="03ab8-262">Edge Chromium browser</span><span class="sxs-lookup"><span data-stu-id="03ab8-262">Edge Chromium browser</span></span>

<span data-ttu-id="03ab8-263">Download and install the new [Edge Chromium browser](https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL).</span><span class="sxs-lookup"><span data-stu-id="03ab8-263">Download and install the new [Edge Chromium browser](https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL).</span></span>

## <span data-ttu-id="03ab8-264">Additional settings</span><span class="sxs-lookup"><span data-stu-id="03ab8-264">Additional settings</span></span>

### <span data-ttu-id="03ab8-265">Pen tail select to launch Whiteboard</span><span class="sxs-lookup"><span data-stu-id="03ab8-265">Pen tail select to launch Whiteboard</span></span>

1. <span data-ttu-id="03ab8-266">Search for **Pen** and select **Pen & Windows Ink settings**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-266">Search for **Pen** and select **Pen & Windows Ink settings**.</span></span>
2. <span data-ttu-id="03ab8-267">Near the bottom of the page, under **Pen shortcuts** set **Select once** to **Microsoft Whiteboard**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-267">Near the bottom of the page, under **Pen shortcuts** set **Select once** to **Microsoft Whiteboard**.</span></span> 

### <span data-ttu-id="03ab8-268">Power management</span><span class="sxs-lookup"><span data-stu-id="03ab8-268">Power management</span></span>

<span data-ttu-id="03ab8-269">There are several power settings available to get the best experience using Windows 10 Pro or Enterprise on Surface Hub 2.</span><span class="sxs-lookup"><span data-stu-id="03ab8-269">There are several power settings available to get the best experience using Windows 10 Pro or Enterprise on Surface Hub 2.</span></span> <span data-ttu-id="03ab8-270">This includes screen and pc timeouts and how they interact with the built-in human presence detection (Doppler), the screen saver and password protection, and then if appropriate how to by-pass group policy power settings intended for laptop / desktop users.</span><span class="sxs-lookup"><span data-stu-id="03ab8-270">This includes screen and pc timeouts and how they interact with the built-in human presence detection (Doppler), the screen saver and password protection, and then if appropriate how to by-pass group policy power settings intended for laptop / desktop users.</span></span>

<span data-ttu-id="03ab8-271">Windows 10 Pro or Enterprise on Surface Hub 2 keeps the screen from going to sleep by touch, mouse, and keyboard actions, as well as the built-in human occupancy detection (Doppler).</span><span class="sxs-lookup"><span data-stu-id="03ab8-271">Windows 10 Pro or Enterprise on Surface Hub 2 keeps the screen from going to sleep by touch, mouse, and keyboard actions, as well as the built-in human occupancy detection (Doppler).</span></span> <span data-ttu-id="03ab8-272">Human occupancy detection is enabled by default, but if desired it can be disabled in UEFI by toggling the device option in the Surface UEFI Configurator tool either as part of the initial migration, or by building and applying a later UEFI configuration package.</span><span class="sxs-lookup"><span data-stu-id="03ab8-272">Human occupancy detection is enabled by default, but if desired it can be disabled in UEFI by toggling the device option in the Surface UEFI Configurator tool either as part of the initial migration, or by building and applying a later UEFI configuration package.</span></span> 

**<span data-ttu-id="03ab8-273">Power Management: Screen and PC sleep settings</span><span class="sxs-lookup"><span data-stu-id="03ab8-273">Power Management: Screen and PC sleep settings</span></span>**

1. <span data-ttu-id="03ab8-274">Select **Start** > **Settings** > **System** > **Power & sleep**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-274">Select **Start** > **Settings** > **System** > **Power & sleep**.</span></span>
2. <span data-ttu-id="03ab8-275">Set the power mode slider to **Best performance**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-275">Set the power mode slider to **Best performance**.</span></span>
3. <span data-ttu-id="03ab8-276">Configure screen and sleep values to your preference while also accounting for Doppler presence detection that wakes up the device when movement is detected.</span><span class="sxs-lookup"><span data-stu-id="03ab8-276">Configure screen and sleep values to your preference while also accounting for Doppler presence detection that wakes up the device when movement is detected.</span></span> <span data-ttu-id="03ab8-277">Accordingly, as a best practice, it's recommended to set Screen to **Turn off after 2 hours** and the PC to **Turn off after 4 hours.**</span><span class="sxs-lookup"><span data-stu-id="03ab8-277">Accordingly, as a best practice, it's recommended to set Screen to **Turn off after 2 hours** and the PC to **Turn off after 4 hours.**</span></span>

**<span data-ttu-id="03ab8-278">Power Management: Screen saver</span><span class="sxs-lookup"><span data-stu-id="03ab8-278">Power Management: Screen saver</span></span>**

1. <span data-ttu-id="03ab8-279">Search for **Lock Screen** and open **Lock screen settings**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-279">Search for **Lock Screen** and open **Lock screen settings**.</span></span>
2. <span data-ttu-id="03ab8-280">Configure **Screen timeout settings** and **Screen saver settings** to your preference.</span><span class="sxs-lookup"><span data-stu-id="03ab8-280">Configure **Screen timeout settings** and **Screen saver settings** to your preference.</span></span>

### <span data-ttu-id="03ab8-281">Storage Sense</span><span class="sxs-lookup"><span data-stu-id="03ab8-281">Storage Sense</span></span>

<span data-ttu-id="03ab8-282">The Surface Hub 2 has a 128GB SSD for local storage, so it is necessary to consider the use of storage saving measures during normal usage.</span><span class="sxs-lookup"><span data-stu-id="03ab8-282">The Surface Hub 2 has a 128GB SSD for local storage, so it is necessary to consider the use of storage saving measures during normal usage.</span></span>  <span data-ttu-id="03ab8-283">To configure Storage Sense:</span><span class="sxs-lookup"><span data-stu-id="03ab8-283">To configure Storage Sense:</span></span>

1.  <span data-ttu-id="03ab8-284">Search for **storage settings**, which is found under **System settings**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-284">Search for **storage settings**, which is found under **System settings**.</span></span>
2.  <span data-ttu-id="03ab8-285">Under **Settings**, select **Turn on storage sense** to open the **Storage** settings page.</span><span class="sxs-lookup"><span data-stu-id="03ab8-285">Under **Settings**, select **Turn on storage sense** to open the **Storage** settings page.</span></span>
3.  <span data-ttu-id="03ab8-286">Turn Storage Sense to **On**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-286">Turn Storage Sense to **On**.</span></span>
4.  <span data-ttu-id="03ab8-287">Select **Configure Storage Sense or run it now** and configure settings to keep files online as much as possible (due to limited drive space).</span><span class="sxs-lookup"><span data-stu-id="03ab8-287">Select **Configure Storage Sense or run it now** and configure settings to keep files online as much as possible (due to limited drive space).</span></span>

<span data-ttu-id="03ab8-288">Recommended settings:</span><span class="sxs-lookup"><span data-stu-id="03ab8-288">Recommended settings:</span></span>
- <span data-ttu-id="03ab8-289">Run Storage Sense = Every Day.</span><span class="sxs-lookup"><span data-stu-id="03ab8-289">Run Storage Sense = Every Day.</span></span>
- <span data-ttu-id="03ab8-290">Delete temporary files that my apps aren't using = Every 14 days (at least).</span><span class="sxs-lookup"><span data-stu-id="03ab8-290">Delete temporary files that my apps aren't using = Every 14 days (at least).</span></span>
- <span data-ttu-id="03ab8-291">Delete files in my Downloads folder if they have been there for over = 30 days.</span><span class="sxs-lookup"><span data-stu-id="03ab8-291">Delete files in my Downloads folder if they have been there for over = 30 days.</span></span>
- <span data-ttu-id="03ab8-292">OneDrive: Content will become online-only if not opened for more than = 30 days.</span><span class="sxs-lookup"><span data-stu-id="03ab8-292">OneDrive: Content will become online-only if not opened for more than = 30 days.</span></span>

### <span data-ttu-id="03ab8-293">Tablet mode</span><span class="sxs-lookup"><span data-stu-id="03ab8-293">Tablet mode</span></span>

<span data-ttu-id="03ab8-294">Turn on Tablet mode if desired for accessibility needs.</span><span class="sxs-lookup"><span data-stu-id="03ab8-294">Turn on Tablet mode if desired for accessibility needs.</span></span>

### <span data-ttu-id="03ab8-295">Power management</span><span class="sxs-lookup"><span data-stu-id="03ab8-295">Power management</span></span>

> [!NOTE]
> <span data-ttu-id="03ab8-296">Before performing the following procedure, check with your IT department for approval to exclude a Surface Hub 2S device from global power management policy.</span><span class="sxs-lookup"><span data-stu-id="03ab8-296">Before performing the following procedure, check with your IT department for approval to exclude a Surface Hub 2S device from global power management policy.</span></span> <span data-ttu-id="03ab8-297">Some power management settings can disable the presence detection function.</span><span class="sxs-lookup"><span data-stu-id="03ab8-297">Some power management settings can disable the presence detection function.</span></span>

1. <span data-ttu-id="03ab8-298">Search for **Software Center** and open it.</span><span class="sxs-lookup"><span data-stu-id="03ab8-298">Search for **Software Center** and open it.</span></span>
2. <span data-ttu-id="03ab8-299">Select **Options** in the navigation pane.</span><span class="sxs-lookup"><span data-stu-id="03ab8-299">Select **Options** in the navigation pane.</span></span>
3. <span data-ttu-id="03ab8-300">Expand the **Power management** section and select **Do not apply power settings from my IT department to this computer**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-300">Expand the **Power management** section and select **Do not apply power settings from my IT department to this computer**.</span></span>

   ![Software settings](images/soft-cntr.png)

### <span data-ttu-id="03ab8-302">Sound settings</span><span class="sxs-lookup"><span data-stu-id="03ab8-302">Sound settings</span></span>

1. <span data-ttu-id="03ab8-303">Search for **Sounds settings** and open this page.</span><span class="sxs-lookup"><span data-stu-id="03ab8-303">Search for **Sounds settings** and open this page.</span></span>
2. <span data-ttu-id="03ab8-304">Select **Sound Control Panel** on the right and select the **Sounds** tab.</span><span class="sxs-lookup"><span data-stu-id="03ab8-304">Select **Sound Control Panel** on the right and select the **Sounds** tab.</span></span>
3. <span data-ttu-id="03ab8-305">Under **Program Events** set **Device Connect** and **Device Disconnect** to **None**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-305">Under **Program Events** set **Device Connect** and **Device Disconnect** to **None**.</span></span>

### <span data-ttu-id="03ab8-306">Silence notifications</span><span class="sxs-lookup"><span data-stu-id="03ab8-306">Silence notifications</span></span>

1. <span data-ttu-id="03ab8-307">Search for **Focus assist** and open this page.</span><span class="sxs-lookup"><span data-stu-id="03ab8-307">Search for **Focus assist** and open this page.</span></span>
2. <span data-ttu-id="03ab8-308">Select **Alarms Only**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-308">Select **Alarms Only**.</span></span> <span data-ttu-id="03ab8-309">This will avoid constant notification flyouts.</span><span class="sxs-lookup"><span data-stu-id="03ab8-309">This will avoid constant notification flyouts.</span></span>

### <span data-ttu-id="03ab8-310">Disk Cleanup</span><span class="sxs-lookup"><span data-stu-id="03ab8-310">Disk Cleanup</span></span>

1. <span data-ttu-id="03ab8-311">Search for **Disk Cleanup** and open this app.</span><span class="sxs-lookup"><span data-stu-id="03ab8-311">Search for **Disk Cleanup** and open this app.</span></span>
2. <span data-ttu-id="03ab8-312">Under **Files to delete**, select the files you wish to delete.</span><span class="sxs-lookup"><span data-stu-id="03ab8-312">Under **Files to delete**, select the files you wish to delete.</span></span> 
3. <span data-ttu-id="03ab8-313">Also select **Clean up system files**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-313">Also select **Clean up system files**.</span></span>

## <span data-ttu-id="03ab8-314">Complete and verify</span><span class="sxs-lookup"><span data-stu-id="03ab8-314">Complete and verify</span></span>

1. <span data-ttu-id="03ab8-315">Scan for and install all Windows Updates.</span><span class="sxs-lookup"><span data-stu-id="03ab8-315">Scan for and install all Windows Updates.</span></span>
2. <span data-ttu-id="03ab8-316">Update Group Policy</span><span class="sxs-lookup"><span data-stu-id="03ab8-316">Update Group Policy</span></span>
    1. <span data-ttu-id="03ab8-317">At an elevated command prompt, enter **gpupdate /force /boot /wait:0**.</span><span class="sxs-lookup"><span data-stu-id="03ab8-317">At an elevated command prompt, enter **gpupdate /force /boot /wait:0**.</span></span>
3. <span data-ttu-id="03ab8-318">Reboot the device.</span><span class="sxs-lookup"><span data-stu-id="03ab8-318">Reboot the device.</span></span>
4. <span data-ttu-id="03ab8-319">Verify taskbar apps.</span><span class="sxs-lookup"><span data-stu-id="03ab8-319">Verify taskbar apps.</span></span>
    - <span data-ttu-id="03ab8-320">Connect App</span><span class="sxs-lookup"><span data-stu-id="03ab8-320">Connect App</span></span>
    - <span data-ttu-id="03ab8-321">Lock Icon</span><span class="sxs-lookup"><span data-stu-id="03ab8-321">Lock Icon</span></span>
    - <span data-ttu-id="03ab8-322">Snip & Sketch</span><span class="sxs-lookup"><span data-stu-id="03ab8-322">Snip & Sketch</span></span>
    - <span data-ttu-id="03ab8-323">Teams (if applicable)</span><span class="sxs-lookup"><span data-stu-id="03ab8-323">Teams (if applicable)</span></span>
    - <span data-ttu-id="03ab8-324">Office Apps (if applicable)</span><span class="sxs-lookup"><span data-stu-id="03ab8-324">Office Apps (if applicable)</span></span>
    - <span data-ttu-id="03ab8-325">Surface App</span><span class="sxs-lookup"><span data-stu-id="03ab8-325">Surface App</span></span>
    - <span data-ttu-id="03ab8-326">Whiteboard</span><span class="sxs-lookup"><span data-stu-id="03ab8-326">Whiteboard</span></span>
5. <span data-ttu-id="03ab8-327">Verify presence detection.</span><span class="sxs-lookup"><span data-stu-id="03ab8-327">Verify presence detection.</span></span>
    - <span data-ttu-id="03ab8-328">Presence detection will be a green icon in the system tray</span><span class="sxs-lookup"><span data-stu-id="03ab8-328">Presence detection will be a green icon in the system tray</span></span>
6. <span data-ttu-id="03ab8-329">Verify projecting to this PC is enabled with the Connect App (the application does not need to be running before connecting).</span><span class="sxs-lookup"><span data-stu-id="03ab8-329">Verify projecting to this PC is enabled with the Connect App (the application does not need to be running before connecting).</span></span>
7. <span data-ttu-id="03ab8-330">Verify power and sleep settings.</span><span class="sxs-lookup"><span data-stu-id="03ab8-330">Verify power and sleep settings.</span></span>
    - <span data-ttu-id="03ab8-331">Screen Saver: 15 minutes, set to (none), Mystify or Blank; check box for requiring password is checked</span><span class="sxs-lookup"><span data-stu-id="03ab8-331">Screen Saver: 15 minutes, set to (none), Mystify or Blank; check box for requiring password is checked</span></span>
    - <span data-ttu-id="03ab8-332">Screen: **Turn off after 2 hours.**</span><span class="sxs-lookup"><span data-stu-id="03ab8-332">Screen: **Turn off after 2 hours.**</span></span>
    - <span data-ttu-id="03ab8-333">PC:  **Turn off after 4 hours.**</span><span class="sxs-lookup"><span data-stu-id="03ab8-333">PC:  **Turn off after 4 hours.**</span></span>
8. <span data-ttu-id="03ab8-334">Verify Windows Hello is working.</span><span class="sxs-lookup"><span data-stu-id="03ab8-334">Verify Windows Hello is working.</span></span>
9. <span data-ttu-id="03ab8-335">Verify sync your settings is disabled.</span><span class="sxs-lookup"><span data-stu-id="03ab8-335">Verify sync your settings is disabled.</span></span>
10. <span data-ttu-id="03ab8-336">Verify startup apps.</span><span class="sxs-lookup"><span data-stu-id="03ab8-336">Verify startup apps.</span></span>

> [!TIP]
> <span data-ttu-id="03ab8-337">After installing and configuring Windows 10, the Surface Hub 2S can be managed just like any other Windows 10 device.</span><span class="sxs-lookup"><span data-stu-id="03ab8-337">After installing and configuring Windows 10, the Surface Hub 2S can be managed just like any other Windows 10 device.</span></span>

## <span data-ttu-id="03ab8-338">Related topics</span><span class="sxs-lookup"><span data-stu-id="03ab8-338">Related topics</span></span>

[<span data-ttu-id="03ab8-339">Migrate to Windows 10 Pro or Enterprise on Surface Hub 2</span><span class="sxs-lookup"><span data-stu-id="03ab8-339">Migrate to Windows 10 Pro or Enterprise on Surface Hub 2</span></span>](surface-hub-2s-migrate-os.md)
