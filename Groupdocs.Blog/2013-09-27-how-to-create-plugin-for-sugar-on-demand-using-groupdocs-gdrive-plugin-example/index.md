---
title: 'How to Сreate a Plugin for Sugar On-Demand Using GroupDocs GDrive Plugin Example'
date: Fri, 27 Sep 2013 11:18:14 +0000
draft: false
url: /2013/09/27/how-to-create-plugin-for-sugar-on-demand-using-groupdocs-gdrive-plugin-example/
author: 'Pavel Teplitsky'
summary: ''
tags: ['GroupDocs plugin', 'Sugar On-Demand', 'SugarCRM plugin', 'zArchive']
---

SugarCRM is an open-platform web-based customer relationship management system which has an on-demand cloud platform, Sugar On-Demand. In a previous article, we discussed [how to create and use a plugin for SugarCRM](https://blog.groupdocs.com/sugarcrm-plugin-tutorial-using-groupdocs-viewer-api), now we will discuss Sugar On-Demand's features. We will use the GroupDocs GDrive plugin as an example. \[caption id="attachment\_3933" align="alignnone" width="600" caption="How to Сreate a Custom GroupDocs Plugin for Sugar On-Demand"\]![How to Сreate a Plugin for Sugar On-Demand Using GroupDocs GDrive Plugin Example](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/GD_Blog_Sugar_02.png "How to Сreate a Plugin for Sugar On-Demand Using GroupDocs GDrive Plugin Example")\[/caption\]

## Requirements

*   PHP 5.3
*   SugarCRM On-Demand account
*   SugarCRM On-Demand application
*   GroupDocs account

## Development of GroupDocs GDriveTwo main features of Sugar On-Demand are:

1.  All functions relating to the file system are denied.
2.  Sugar On-Demand is a cloud service so all plugin files must be installed from a single package because you will not be able to override deleted files during deployment.

## Using the JavaScript SDKOn the on-demand version of SugarCRM we can't use our PHP SDK because all functions that work with file system are **prohibited.** Also it's impossible to override installed files which is why we have to use only one package for the installation, and the installed plugin doesn't need to deploy. In the Gdrive plugin we use the JavaScript SDK which is minimized and located in the **plugin root folder/\_Dashlets/gd\_GroupDocsDashlet/\_gd\_GroupDocsDashletLibs.tpl** file. You can view and download GroupDocs JavaScript SDK [from GitHub](https://github.com/groupdocs). In this file we have also minimized CSS styles for the plugin UI. In the **\_plugin root folder/Dashlets/gd\_GroupDocsDashlet/\_gd\_GroupDocsDashletScript.tpl** we have all the JavaScript functions that provide the plugin UI's connectivity to the JavaScript SDK. For the on-demand version of the plugin we don't use Dashlet: the entire user-side UI is in the Module detail view page (if a user clicks on GroupDocs in the main menu, they will see the user side UI). ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/1.png "1")

## Minimized Template FileFor this reason we have the minimized template file **\_plugin root folder/views/gd\_GroupDocsEditView.tpl**.```
<div> <!-- GroupDocs plugin: begin HTML --> <div id="gd-logo"></div> <div id="gd-widget-container"> <h4>My GroupDocs</h4> <div id="gd-widget-wrapper">
<div id="currentPath" style="margin: 10px 0px 0px 50px; font-size: 14px; color: blue;">/</div> <div class="gd-widget"> <div class="GroupDocsWidget"> <!-- Folders -->
<h5>Folders:</h5> <div class="itemList" id="foldersContainer"> </div> <h5>Files:</h5> <!-- Files --> <div class="itemList" id="filesContainer"> </div> <h5>Download/Delete file:</h5>
<div> <form name="delete" action="index.php?module=gd\_GroupDocs&amp;action=delete" method="post"> <input type="hidden" name="deleteGuid" id="deleteGuid">
<input class="gd-rmv-btn" type="button" id="deleteBtn"> </form> </div> <div> <form name="download" action="index.php?module=gd\_GroupDocs&amp;action=download" method="post">
 <input type="hidden" name="fileGuid" id="downloadGuid"> <input class="gd-dl-btn" type="button" id="downloadBtn"> </form> </div> <h5>Copy/Move file:</h5> <div>
<form name="copy" action="index.php?module=gd\_GroupDocs&amp;action=copy" method="post"> <label for="destPath">Folder in which you want to copy file</label> <br>
<input type="text" id="destPath" name="destPath" class="gd-custom-input-text"> <input type="hidden" id="srcPath" name="srcPath"> <input type="hidden" name="copyGuid">
<input type="hidden" name="do"> <input class="gd-custom-btn-gray" name="copyButton" type="button" value="Copy" id="copyBtn">
<input class="gd-custom-btn-gray" name="moveButton" type="button" value="Move" id="moveBtn"> </form> </div> <!-- start email -->
 <div> <form action="/index.php?module=gd\_GroupDocs&amp;action=sendEmail" method="post" id="sendForm" name="sendForm"> <h5>Choose receivers:</h5> <div>
 <select multiple="" id="emailList" name="emailList\[\]" class="gd-email-receivers"> <!-- Add items in JavaScript -->
</select> <input class="gd-custom-btn-gray" type="button" value="Add receiver" id="addEmail"> <label for="neverExp" style="display: block">
 <input type="checkbox" id="neverExp" name="neverExp" checked=""> Never expires </label> <label for="datePicker" style="display: block">
Expiration date: <input type="text" id="datePicker" name="datePicker"> <img src="modules/gd\_GroupDocs/images/cal.gif" id="date"/> </label>
<input type="button" value="Send emails" id="sendEmail" class="gd-custom-btn-orange gd-email-receivers-btn"> <input type="hidden" value="" name="attach" id="attach">
</div> </form> </div> <!-- end email --> </div> <div class="gd-widget"> <h5>Create new folder:</h5> <div>
<input class="gd-custom-input-text" placeholder="Enter folder name" type="text" id="folderInput">
 <input class="gd-custom-btn-gray" name="create" type="button" value="Create folder" id="createBtn"> </div> <h5>Upload local file:</h5> <label class="filebutton gd-custom-btn-gray">
 Browse <input type="file" id="uploadfile"> </label> <input type="text" id="filefield-text" value="No file selected"> </div> </div> <div></div> </div> </div>
<!-- GroupDocs plugin: end HTML --></div>
```  This file contains simple HTML which generates the UI. To override the standard view of the plugin's edit list and edit view pages, we use the **plugin root folder/views/edit.view.php** and **plugin root folder/views/edit.list.php** files.

## The Edit Plugin Page - Admin OnlyThe edit plugin page is the **plugin root folder/views/view.edit.php**. This is the admin side of the plugin and only admins have access to it.

```
<?php

if (!defined('sugarEntry') || !sugarEntry)
    die('Not A Valid Entry Point');
/\* \* \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
 \* SugarCRM Community Edition is a customer relationship management program developed by
 \* SugarCRM, Inc. Copyright (C) 2004-2012 SugarCRM Inc.
 \*
 \* This program is free software; you can redistribute it and/or modify it under
 \* the terms of the GNU Affero General Public License version 3 as published by the
 \* Free Software Foundation with the addition of the following permission added
 \* to Section 15 as permitted in Section 7(a): FOR ANY PART OF THE COVERED WORK
 \* IN WHICH THE COPYRIGHT IS OWNED BY SUGARCRM, SUGARCRM DISCLAIMS THE WARRANTY
 \* OF NON INFRINGEMENT OF THIRD PARTY RIGHTS.
 \*
 \* This program is distributed in the hope that it will be useful, but WITHOUT
 \* ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
 \* FOR A PARTICULAR PURPOSE.  See the GNU Affero General Public License for more
 \* details.
 \*
 \* You should have received a copy of the GNU Affero General Public License along with
 \* this program; if not, see http://www.gnu.org/licenses/ or write to the Free
 \* Software Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA
 \* 02110-1301 USA.
 \*
 \* You can contact SugarCRM, Inc. headquarters at 10050 North Wolfe Road,
 \* SW2-130, Cupertino, CA 95014, USA. or at email address contact@sugarcrm.com.
 \*
 \* The interactive user interfaces in modified source and object code versions
 \* of this program must display Appropriate Legal Notices, as required under
 \* Section 5 of the GNU Affero General Public License version 3.
 \*
 \* In accordance with Section 7(b) of the GNU Affero General Public License version 3,
 \* these Appropriate Legal Notices must retain the display of the "Powered by
 \* SugarCRM" logo. If the display of the logo is not reasonably feasible for
 \* technical reasons, the Appropriate Legal Notices must display the words
 \* "Powered by SugarCRM".
 \* \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* \*/

/\* \* \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

 \* Portions created by SugarCRM are Copyright (C) SugarCRM, Inc.
 \* All Rights Reserved.
 \* Contributor(s): \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_..
 \* \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* \*/

class gd\_GroupDocsViewEdit extends ViewEdit {

    function gd\_GroupDocsViewEdit() {

        parent::ViewEdit();
    }

    /\*\*
     \* This method will handle the actual display logic of the view.
     \*/
    function display() {
        global $current\_user;
        if ($current\_user->is\_admin == "1") {

            $ss = new Sugar\_Smarty();
            $ss->assign('savedText', SugarCleaner::cleanHtml($this->savedText));
            $ss->assign('saving', $this->dashletStrings\['LBL\_SAVING'\]);
            $ss->assign('saved', $this->dashletStrings\['LBL\_SAVED'\]);
            $ss->assign('id', $this->id);
            $ss->assign('height', $this->height);
            $gd = BeanFactory::getBean('gd\_GroupDocs');
            $config = $gd->retrieve\_by\_string\_fields(array('deleted' => '0')); // TODO: If user is not admin??
            $cid = $config->fetched\_row\['cid'\];
            $pkey = $config->fetched\_row\['pkey'\];
            $bpath = $config->fetched\_row\['bpath'\];
            $str = $ss->fetch('modules/gd\_GroupDocs/views/gd\_GroupDocsEditView.tpl');
            $libs = new Sugar\_Smarty();
            $libsStr = $libs->fetch('modules/gd\_GroupDocs/Dashlets/gd\_GroupDocsDashlet/gd\_GroupDocsDashletLibs.tpl');
            $script = new Sugar\_Smarty();
            $script->assign('moduleName', 'gd\_GroupDocs');
            if (isset($cid) && !empty($cid) && $cid != null && isset($pkey) && !empty($pkey) && $pkey != null && isset($bpath) && !empty($bpath) && $bpath != null) {
                $script->assign('cid', $cid);
                $script->assign('pkey', $pkey);
                $script->assign('bpath', $bpath);
            } else {
                $script->assign('error', 'Error! Please enter credentials in GroupDocs settings!');
            }
            $scriptStr = $script->fetch('modules/gd\_GroupDocs/Dashlets/gd\_GroupDocsDashlet/gd\_GroupDocsDashletScript.tpl');
            $content = $str;
            $js = $libsStr;
            $js .= $scriptStr;
            print '<script>';
            // delay cos 'sugarcrm form' is actualy builded by js
            print 'setTimeout(function(){';
            // create node, there will be the list
            print 'var content = \\'' . $content . '\\';';
            print '$("#detailpanel\_1").append(content);';
            print '},1500);';
            print '</script>';
            print $js;
            parent::display();
        } else {
            print '<script>';
//             delay cos 'sugarcrm form' is actualy builded by js
            print 'setTimeout(function(){';
//             create node, there will be the list
            print '$("#content").append(\\'Only administrator can see this block\\');';
            print '},1500);';
            print '</script>';
            parent::display();
        }

    }

}
```

## View List Page - User ViewThe view list page is the **plugin root folder/views/view.list.php** file. All users can access this page where they will see folders and files which are shared for this user.

```
<?php
/\*\*
 \* Created by JetBrains PhpStorm.
 \* User: liosha
 \* Date: 12.09.13
 \* Time: 17:45
 \*/
if(!defined('sugarEntry') || !sugarEntry) die('Not A Valid Entry Point');

class gd\_GroupDocsViewList extends SugarView{
     function gd\_GroupDocsViewList() {

        parent::SugarView();
    }
    public function display()
    {
        $libs = new Sugar\_Smarty();
        $libsStr = $libs->fetch('modules/gd\_GroupDocs/Dashlets/gd\_GroupDocsDashlet/gd\_GroupDocsDashletLibs.tpl');
        $script = new Sugar\_Smarty();
        $script->assign('moduleName', 'gd\_GroupDocs');
        $gd = BeanFactory::getBean('gd\_GroupDocs');
        $config = $gd->retrieve\_by\_string\_fields(array('deleted' => '0')); // TODO: If user is not admin??
        $cid = $config->fetched\_row\['cid'\];
        $pkey = $config->fetched\_row\['pkey'\];
        $bpath = $config->fetched\_row\['bpath'\];
        if (isset($cid) && !empty($cid) && $cid != null && isset($pkey) && !empty($pkey) && $pkey != null && isset($bpath) && !empty($bpath) && $bpath != null) {
            $script->assign('cid', $cid);
            $script->assign('pkey', $pkey);
            $script->assign('bpath', $bpath);
        } else {
            $script->assign('error', 'Error! Please enter credentials in GroupDocs settings!');
        }
        $scriptStr = $script->fetch('modules/gd\_GroupDocs/Dashlets/gd\_GroupDocsDashlet/gd\_GroupDocsDashletScript.tpl');
        $js = $libsStr;
        $js .= $scriptStr;
        $ss = new Sugar\_Smarty();
        $str = $ss->fetch('modules/gd\_GroupDocs/views/gd\_GroupDocsEditView.tpl');
        $content = $str;
        print '<script>';
        // delay cos 'sugarcrm form' is actualy builded by js
        print 'setTimeout(function(){';
        // create node, there will be the list
        print 'var content = \\'' . $content . '\\';';
        print '$("#content").append(content);';
        print '},1500);';
        print '</script>';
        print $js;
        parent::display();

    }
}
```

## Sharing - Admin OnlyFor sharing functionality we created a separate bin which generates one more table in the database - "gd\_groupdocs\_shared" - and a separate module which provides only sharing functionality. Only admins can access the module. The gd\_GroupDocs\_Sharing module is almost the same as gd\_GroupDocs but doesn't have the user side UI or the different admin side UI. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/2.png "2") That's all: the plugin's created. This plugin can be installed as a common plugin for other versions of SugarCRM.




