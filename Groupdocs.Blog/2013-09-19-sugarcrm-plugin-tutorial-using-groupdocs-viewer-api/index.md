---
title: 'SugarCRM Plugin Tutorial Using GroupDocs Viewer API'
date: Thu, 19 Sep 2013 10:50:10 +0000
draft: false
url: /2013/09/19/sugarcrm-plugin-tutorial-using-groupdocs-viewer-api/
author: 'Pavel Teplitsky'
summary: ''
tags: ['GroupDocs API', 'GroupDocs plugin', 'SugarCRM plugin', 'zArchive']
---

GroupDocs offers a full set of document management tools for SugarCRM: we've developed a bunch of [plugins](http://groupdocs.com/marketplace/plugins) which help you use Viewer, Annotation, Assembly, Comparison and Signature apps in SugarCRM. This article gives some recommendations on how to create your own custom plugin for SugarCRM. We will use the [GroupDocs Viewer plugin for SugarCRM](https://github.com/groupdocs) as an example. SugarCRM is an open-platform web-based CRM solution which has an _on-demand cloud platform._ Today we show you how to create an on-site version plugin. Thе next article considers some bottlenecks when creating plugins using the SugarCRM cloud platform. \[caption id="attachment\_3861" align="alignnone" width="600" caption="How to Create a Custom GroupDocs Plugin for SugarCRM"\]![How to Create a Custom GroupDocs Plugin for SugarCRM](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/GD_Blog_Sugar.png "How to Create a Custom GroupDocs Plugin for SugarCRM")\[/caption\]

## Requirements

*   PHP 5.3
*   Installed SugarCRM
*   GroupDocs account

## Plugin CreationBefore you start creating a plugin, keep in mind that all data and all parameters such as displayed fields (including field parameters), relationships etc. are declared as arrays in SugarCRM. Also make sure that your plugin file starts with the following:

```
/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
 \* SugarCRM Community Edition is a customer relationship management program developed by
 \* SugarCRM, Inc. Copyright (C) 2004-2013 SugarCRM Inc.
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
 \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/
```

## Getting Started

1.  First of all, create a **manifest.php** file. This file will contain all information for plugin installation. I'm not showing the **manifest.php** code because of its big size but you can find it on [GitHub](https://github.com/groupdocs-viewer/).
2.  The next step is creating icons: we need to create a folder named **icons** and add all icon files to it. Now let's start creating the plugin functionality. The GroupDocs Viewer plugin embeds files from a GroupDocs account using its GUID.

## Plugin Functionality

1.  Lets start with variables. All variables are specified in **vardefs.php**.
2.  Then create a folder named **shugarModule** which will contain all functionality.
3.  Create a language file:
    *   In the **ShugarModule** folder, create a **language** folder.
    *   In this folder, create an **application** folder with an **en\_us.lang.php** file. You will have the following structure: ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/structure1.png "structure1")
4.  Create a **relationships** folder. This folder will contain all the files that describe relationships for the database tables that will be created for the plugin. In the **./relationships** directory, all the many-to-many relationships are defined and included in the $dictionary array. The files are stored in **./appropriate folder/<relation\_table\_name>MetaData.php**. Tables are generated based on these definitions. These files are included through the **./modules/TableDictionary.php** file. If you create a custom many-to-many relationship, you need to add a reference to the new relationship to the **custom/application/Ext/TableDictionary/tabledictionary.php** file. If the file doesn't exist, create it. These changes take effect after you clear the Sugar cache by running the **Quick Repair and Rebuild** option from the Admin Repair screen. The following are the definitions for $dictionary\[\]. They are similar to the Vardefs. If necessary use that page as a reference. <relationship\_table> : The index for this relationship in the $dictionary array 
    *   table : The name of the table that is created in the database
    *   fields : Array containing arrays for each column definition. The join table must have a field for the primary key of each table to be linked, a primary key for the join table itself, a deleted field for relationship unlinking, and a date\_modified field to track when the relationship changes. Additional fields can be added to track the role played by the relationship
    *   indices : The database indices on the relationship table
    *   relationships : Definitions of the relationships between the two tables
    *   lhs\_modules : The left hand module. Should match $beanList index
    *   lhs\_table : The left hand table name
    *   lhs\_key : The key to use from the left table
    *   rhs\_modules : The right hand module. Should match $beanList index
    *   rhs\_table : The right hand table name
    *   rhs\_key : The key to use from the right table
    *   relationship\_type : Relationship type
    *   join\_table : Join table used to join items
    *   join\_key\_lhs : Left table key. Should exist in table field definitions above
    *   join\_key\_rhs : Right table key. Should exist in table field definitions aboveWe've finished with the basic functions needed to for SugarCRM to install and recognize the plugin. Now we can work directly with the module files which do all magic.
5.  In the **SugarModule** folder, create a **modules** folder, and in this folder create a **gdoc\_GroupDocs** folder. This last folder will be placed in the SugarCRM installation's **modules** folder and will contain all the plugin files.
6.  Place the **vardefs.php** file, which contains an array with all variables, into this folder.
7.  Create a **controller.php** file. This file will do all the work, and will receive all the requests from the form. This is a **controller.php** code: 
    
    ```
    if(!defined('sugarEntry') || !sugarEntry) die('Not A Valid Entry Point');
    
    //require\_once('include/MVC/Controller/SugarController.php');
    
    class Gd\_GroupDocsController extends SugarController {
        var $moduleName = 'gd\_GroupDocs';
    
        public function action\_index()
        {
            return parent::action\_listview();
        }
    ```
    
    Here we can see the following:
    
    *   The first line is standard for SugarCRM.
    *   Then we define a class for the controller which extends the standard SugarCRM controller class.
    *   All action names must start with "action\_" and then the action name. To call an action, simply call "&action=index" in the URL.
    
    Also we need views. To edit the plugin page, we need the **edit.view.php** file.
8.  Create a **views** folder and place **edit.views.php** in it. The following table lists the metadata definition files found in the **modules/module/metadata** directory, and a brief description of their purpose within the system.

File

**Description**

additionalDetails.php

Used to render the Popup information displayed when a user hovers the mouse cursor over a row in the List View.

editviewdefs.php

Used to render a record's EditView.

detailviewdefs.php

Used to render a record's DetailView.

listviewdefs.php

Used to render the List View display for a module.

metafiles.php

Used to override the location of the metadata definition file to be used. The EditView, DetailView, List View, and Popup code check for the presence of these files.

popupdefs.php

Used to render and handle the search form and list view in Popups.

searchdefs.php

Used to render a module's basic and advanced search form displays.

sidecreateviewdefs.php

Used to render a module's quick create form shown in the side shortcut panel.

subpaneldefs.php

Used to render a module's sub-panels shown when viewing a record's DetailView.

  We've finished with the basic files. There can be other files depending on the plugin functionality, but for the purposes of this example, we're done.

## The Final PluginLet's look at the installed module structure: \[caption id="attachment\_3863" align="alignnone" width="600" caption="The installed module structure"\]![The installed module structure](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/Installed-module-structure.png "The installed module structure")\[/caption\] And lets see how our plugin looks like in action. \[caption id="attachment\_3864" align="alignnone" width="600" caption="The plugin edit page"\]![The plugin edit page](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/The-plugin-edit-page.png "The plugin edit page")\[/caption\] An embedded file on the page. \[caption id="attachment\_3865" align="alignnone" width="600" caption="An embedded file on the page"\]![An embedded file on the page](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/An-embedded-file-on-the-page.png "An embedded file on the page")\[/caption\]




