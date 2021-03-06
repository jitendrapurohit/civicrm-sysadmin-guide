# Upgrading CiviCRM for Joomla

Use this document to upgrade CiviCRM installations on Joomla to the latest CiviCRM release.

!!! caution "Before upgrading"
    Make sure you have done the steps listed in ["Before upgrading"](/upgrade/index.md#before-upgrading) first.

## Download the latest code

1. Go to [civicrm.org/download](https://civicrm.org/download)
1. Select the latest currently available CiviCRM tarball for Joomla.

    Example: `civicrm-4.7.20-joomla.zip`

    !!! note
        You may notice a file on the named something like `civicrm-4.7.xx-joomla-alt.zip` the `-alt` version does not require `.zip` functions compiled into PHP by your hosting company. If you get errors like _"Your PHP version is missing zip functionality"_, then try the `-alt` version.

1. Save this file in `<joomla_root>/tmp/`. Unzipping will create a directory called: `com_civicrm`.

If using localization, also download the latest version of the localization files. See the [CiviCRM Localisation](http://wiki.civicrm.org/confluence/display/CRMDOC40/CiviCRM+Localisation) page about how to install files for running CiviCRM in languages other than American English.

## Backup your settings files

The ["Before upgrading"](/upgrade/index.md#before-upgrading) steps describe steps for backing _everything_ up in case something goes wrong during the upgrade. In addition to this important safeguard, we also need to actually _use_ these two settings files, as they are, during the upgrade:

* `<joomla_root>/components/com_civicrm/civicrm.settings.php`
* `<joomla_root>/administrator/components/com_civicrm/civicrm.settings.php`
    
Copy these files to a location outside your Joomla project. You will need to restore them after upgrading.

## Install the Extension

1. Login to your Joomla Administrator site.
1. Go to Extensions » Manage
1. Use the **Install from Folder** tab and enter the full path to the un-zipped **com_civicrm** directory, which should be something like **JOOMLA.x_ROOT/tmp/com_civicrm**. If your temp directory is configured correctly you should only need to add "com_civicrm" to the prepopulated path.
1. You should see "CiviCRM successfully installed" message.

The steps above will install CiviCRM directly on top of your existing installation. If you run into any issues, such as the component not appearing to reflect the new version, you may need to first uninstall the existing version and then install the new version. Uninstalling CiviCRM will remove the component files, but will not impact your database in any way.

## Clear the file cache

Delete all cache files in `<joomla_root>/media/civicrm/templates_c` on your server before proceeding with the update script.

## Upgrade the database

**After the component installation completes click the link to run the database upgrade script.** You may also point your web browser to the following URL (you should already be logged in to Joomla with administrator-level permissions):

```
http://<your_joomla_home>/administrator/index.php?option=com_civicrm&task=civicrm/upgrade&reset=1
```

You should see an **Upgrade successful** message when the upgrade completes.

1. If you receive any errors during the process, please note the exact error message and check for solutions on the community support forum.
1. Now click the **Return to CiviCRM home page** link.
1. You should be up and running with the latest CiviCRM version. Confirm by checking the version and revision in the page footer. Note that you may need to refresh the browser screen a couple times to clear out your local cache and ensure the layout loads correctly.
1. Take some time to browse the CiviCRM features that your organization uses. If you notice unexpected behaviors or error messages, refer to the trouble-shooting section below.



## Restore settings file changes

Review the backup versions of the files below and compare them with the new versions just installed. In particular, make sure your site key value was retained and any of the configuration options found in those files are still intact.

1. <joomla_root>/components/com_civicrm/civicrm.settings.php
1. <joomla_root>/administrator/components/com_civicrm/civicrm.settings.php

## Post upgrade

See these steps to take [after upgrading](/upgrade/index.md#after-upgrading).
