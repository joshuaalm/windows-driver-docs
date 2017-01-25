---
title: Test distribution guidance to self-host desktop drivers
description: Test distribution guidance to self-host desktop drivers
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 67E31BC1-6209-4264-B9F4-8CDFE8CE2E65
---

# Test distribution guidance to self-host desktop drivers


Hardware partners can test OS upgrade scenarios by publishing a driver to Windows Update and using test distribution. Once published, IHVs/OEMs can configure their client systems to request these drivers by configuring a predefined registry key value. In addition to receiving drivers distributed for testing, production drivers will still be offered to the same client machine. This adds prerelease drivers to the list of production drivers that will be offered from Windows Update. This method restricts prerelease drivers from being offered to the general public.

Starting with Windows 10, client systems may participate in receiving test distributed drivers throughout the Windows upgrade process. Hardware partners can test OS upgrade scenarios using this test distribution process.

## <span id="What_is_test_distribution__and_why_do_I_need_it_"></span><span id="what_is_test_distribution__and_why_do_i_need_it_"></span><span id="WHAT_IS_TEST_DISTRIBUTION__AND_WHY_DO_I_NEED_IT_"></span>What is test distribution, and why do I need it?


By publishing drivers for test distribution and configuring client systems to receive test distributed drivers, you enable that system to receive all prerelease drivers and firmware content that are published on Windows Update. This allows partners to publish drivers using Windows Update to their test audience without impacting their retail consumer audience.

## <span id="Publishing_drivers_with_test_distribution"></span><span id="publishing_drivers_with_test_distribution"></span><span id="PUBLISHING_DRIVERS_WITH_TEST_DISTRIBUTION"></span>Publishing drivers with test distribution


Publishing drivers for test distribution can be done for Windows 7, Windows 8.x, and Windows 10 systems. To publish a test distribution, simply [create a shipping label](manage-driver-distribution-by-submission.md) as normal and click on the "Test Registry Key" checkbox in the Targeting section.

![an image showing the "test registry key" checkbox](images/test-registry-key-checkbox.png)

## <span id="Removing_drivers_published_for_test_distribution"></span><span id="removing_drivers_published_for_test_distribution"></span><span id="REMOVING_DRIVERS_PUBLISHED_FOR_TEST_DISTRIBUTION"></span>Removing drivers published for test distribution


### <span id="How_do_I_manually_remove_my_driver_published_for_test_distribution_"></span><span id="how_do_i_manually_remove_my_driver_published_for_test_distribution_"></span><span id="HOW_DO_I_MANUALLY_REMOVE_MY_DRIVER_PUBLISHED_FOR_TEST_DISTRIBUTION_"></span>How do I manually remove my driver published for test distribution?

Once a driver has been published for test distribution it can be manually expired or re-published for (normal) distribution.

### <span id="How_long_does_my_driver_published_for_test_distribution_last_"></span><span id="how_long_does_my_driver_published_for_test_distribution_last_"></span><span id="HOW_LONG_DOES_MY_DRIVER_PUBLISHED_FOR_TEST_DISTRIBUTION_LAST_"></span>How long does my driver published for test distribution last?

Once you have published your driver for test distribution, the expiration time is set to 14 days from the time of publication to Windows Update. Once expired, test distributed drivers are removed from the Windows Update server and are no longer available to client machines.

## <span id="Client_PC_configuration"></span><span id="client_pc_configuration"></span><span id="CLIENT_PC_CONFIGURATION"></span>Client PC configuration


### <span id="Test_distribution_client_configuration_for_previous_versions_of_Windows"></span><span id="test_distribution_client_configuration_for_previous_versions_of_windows"></span><span id="TEST_DISTRIBUTION_CLIENT_CONFIGURATION_FOR_PREVIOUS_VERSIONS_OF_WINDOWS"></span>Test distribution client configuration for previous versions of Windows

Prior to Windows 10, a legacy registry key was used to indicate that a client machine is interested in receiving test distribution drivers. Starting with Windows 10, this legacy registry key will be retired and no longer function.

To configure a client machine (Windows 7, Windows 8, or Windows 8.1) for test distribution, you must configure the client machine using the steps outlined in the following section.

### <span id="How_do_I_configure_my_machine_to_receive_test_distribution_drivers_"></span><span id="how_do_i_configure_my_machine_to_receive_test_distribution_drivers_"></span><span id="HOW_DO_I_CONFIGURE_MY_MACHINE_TO_RECEIVE_TEST_DISTRIBUTION_DRIVERS_"></span>How do I configure my machine to receive test distribution drivers?

Configuring a system to receive test distribution updates is easier than ever. Follow these steps on the test machine running Windows 10, or on the source OS (Windows 8.1 or earlier) if you are testing upgrade scenarios to Windows 10.

1.  Open the Windows Registry Editor (regedit.exe)
2.  Go to HKLM\\Software\\Microsoft\\
3.  Create subkeys \\DriverFlighting\\Partner\\
4.  Under the \\Partner subkey, create a string named **TargetRing** and type **Drivers** as the value
5.  Make sure you have the setting as shown below:

    ![an image showing the created string under the partner subkey, within the windows registry editor](images/registry-editor-drivers.png)

6.  Exit Windows Registry Editor. You do not need to restart the computer after this change.
7.  Do one of the following:
    -   Run Windows Update and check for updates.
    -   In Device Manager, right click on the target device and select **Update Device Software**.
8.  Verify that your test driver is offered as expected

    -   If you run into issues, contact Customer Service and Support.

        ![an image showing the button to contact customer service and support](images/dashboard-help-button.png)

### <span id="How_do_I_stop_my_PC_from_receiving_test_distribution_drivers_"></span><span id="how_do_i_stop_my_pc_from_receiving_test_distribution_drivers_"></span><span id="HOW_DO_I_STOP_MY_PC_FROM_RECEIVING_TEST_DISTRIBUTION_DRIVERS_"></span>How do I stop my PC from receiving test distribution drivers?

To stop receiving test distribution drivers, remove the **TargetRing** registry data value you created in the previous section. Double-click on the **Drivers** data value to remove it, and then click **OK**. By doing this, your client system will no longer be offered pre-release drivers.

**Note**  Your system will continue to receive all production drivers from Windows Update.

 

1.  Open the Windows Registry Editor (regedit.exe)
2.  Go to HKLM\\Software\\Microsoft\\DriverFlighting\\Partner. If these keys do not exist then you are done, otherwise continue to the next step.
3.  Under \\Partner subkey, remove the data value for **TargetRing**
4.  Make sure the setting appears as shown below:

    ![an image showing the removed string value under the partner subkey, within the windows registry editor](images/registry-editor-no-drivers.png)

5.  Exit Windows Registry Editor. You do not need to restart the computer after this change.
6.  Do one of the following:
    -   Run Windows Update and check for updates
    -   In Device Manager, right click on the target device, and select **Update Device Software**.

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bhw_dashboard\hw_dashboard%5D:%20Test%20distribution%20guidance%20to%20self-host%20desktop%20drivers%20%20RELEASE:%20%281/3/2017%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



