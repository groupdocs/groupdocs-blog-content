---
title: 'How to Create GroupDocs Viewer Plugin for Contao CMS'
date: Wed, 10 Apr 2013 09:28:42 +0000
draft: false
url: /2013/04/10/how-to-create-groupdocs-plugin-for-cms/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'GroupDocs Viewer', 'GroupDocs Viewer Plugin', 'online document viewer', 'View documents online', 'zArchive']
---

This article explains the basics of creating a plugin for the Contao CMS using the Contao Viewer plugin as an example. You can download the completed plugin [from Contao](https://contao.org/en/extension-list/view/groupdocs_viewer.10000099.en.html).

## Requirements

*   Contao CMS
*   PHP 5.3
*   JavaScript

## PreparationTo create a GroupDocs Viewer plugin for Contao CMS:

1.  Install [Contao CMS](https://contao.org/en/). The installation of this CMS is a simple.
2.  Allow GroupDocs <iframe> to appear go to **Admin** > **Setting** > **Security settings** > **Allowed HTML tags** and just add **<iframe>** at the end.
3.  Create a folder to hold future plugin files in the **root/system/modules** directory of the Contao CMS installation and name it **groupdocs\_viewer**.

## Creating the PluginThis plugin adds a button to the Admin side of the CMS above the editing block of any article. When users click the button a dialog appears. Here, users enter the file GUID from their [GroupDocs](http://groupdocs.com) account to embed and iframe with this file. OK. Let's start creating a Viewer plugin. All operations are in the **groupdocs\_viewer** folder. First of all, create a **ModuleGroupdocsViewer.php** file. This file will contain the plugin's installation and uninstallation logic. Enter this code into the file:```
<?php if (!defined('TL\_ROOT')) die('You can not access this file directly!');

/\*\*
 \* GroupDocs
 \*
 \* This program is free software: you can redistribute it and/or
 \* modify it under the terms of the GNU Lesser General Public
 \* License as published by the Free Software Foundation, either
 \* version 2.1 of the License, or (at your option) any later version.
 \*
 \* This program is distributed in the hope that it will be useful,
 \* but WITHOUT ANY WARRANTY; without even the implied warranty of
 \* MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
 \* Lesser General Public License for more details.
 \*
 \* You should have received a copy of the GNU Lesser General Public
 \* License along with this program. If not, please visit the Free
 \* Software Foundation website at http://www.gnu.org/licenses/.
 \*
 \* PHP version 5
 \* @copyright  2012
 \* @author     sales@groupdocs.com
 \* @license    GPL
 \*/

 /\*\*
 \* @package    Controller
 \*/
class ModuleGroupdocsViewer extends Module
{

	/\*\*
	 \* Template
	 \* @var string
	 \*/
	protected $strTemplate = 'mod\_groupdocsviewer';

	/\*\*
	 \* Display a wildcard in the back end
	 \* @return string
	 \*/
	public function generate()
	{
		if (TL\_MODE == 'BE')
		{
			$objTemplate = new BackendTemplate('be\_wildcard');

			$objTemplate->wildcard = '### GROUPDOCS VIEWER LIST ###';
			$objTemplate->title = $this->headline;
			$objTemplate->id = $this->id;
			$objTemplate->link = $this->name;
			$objTemplate->href = 'contao/main.php?do=themes&amp;table=tl\_module&amp;act=edit&amp;id=' . $this->id;

			return $objTemplate->parse();
		}

		return parent::generate();
	}

	/\*\*
	 \* Generate module
	 \*/
	protected function compile()
	{

/\*
		$this->Template->gdv = $arrGdv;
		$this->Template->width = $objCategory->width;
		$this->Template->height = $objCategory->height;
		$this->Template->categories = $arrCategories;
\*/
	}

}

?>
```

### The Code Line by LineLet's take a look at the code we inserted. The first line

```
if (!defined('TL\_ROOT')) die('You can not access this file directly!');
```

says that if TL\_ROOT has not been defined, the user can't access the file. This line must be in all plugin files as first line. The next, commented, block contains information about the plugin. Now create a basic class of our plugin which will extend the Contao CMS's **Module** class. This is necessary for Contao to understand that this is a module and give us access to the CMS's functions.

```
class ModuleGroupdocsViewer extends Module
```

That creates the class. Then we have the magic that installs and uninstalls the plugin. For this purpose we create some functions. All code explanations are on the same lines of the code in the section below.

```
protected $strTemplate = 'mod\_groupdocsviewer'; // Creation of the protected variable which declare a template with module name

	/\*\*
	 \* Display a wildcard in the back end
	 \* @return string
	 \*/
	public function generate() //This function is describe an insertion of plugin info to the CMS.
                                  //For this purpose we use a variables of the basic Module class which we expanded by our class
	{
		if (TL\_MODE == 'BE')
		{
			$objTemplate = new BackendTemplate('be\_wildcard');

			$objTemplate->wildcard = '### GROUPDOCS VIEWER LIST ###';
			$objTemplate->title = $this->headline;
			$objTemplate->id = $this->id;
			$objTemplate->link = $this->name;
			$objTemplate->href = 'contao/main.php?do=themes&amp;table=tl\_module&amp;act=edit&amp;id=' . $this->id;

			return $objTemplate->parse();
		}

		return parent::generate();
	}

	/\*\*
	 \* Generate module
	 \*/
	protected function compile() //In this function we transfer our plugin data to the template such as button position and in which area to insert our button.
	{

/\*
		$this->Template->gdv = $arrGdv;
		$this->Template->width = $objCategory->width;
		$this->Template->height = $objCategory->height;
		$this->Template->categories = $arrCategories;
\*/
	}
```

So far, we've created the basic plugin file but the plugin doesn't do anything yet. So let's add some functionality.

### Completing the Plugin DeclarationBefore adding functionality to the plugin, we need to set up some files and file structures.

1.  First, create a **Template** folder and add an empty template file to it. The Contao CMS will write data that we declare for the template to this file. The file name for is **mod\_groupdocsviewer** - the same that we called our protected variable.
2.  Create a **languages** folder in the plugin's root folder and, in this folder, create one an **en** folder. In the **en**folder, create two files which will contain a string declaration of all titles and messages for our plugin.![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/04/Image-1-GD-Viewer-tree-structure.png "Image 1 - GD Viewer tree structure")

#### modules.phpThe first file is named **modules.php** and contain basic data such as the plugin name:

```
<?php if (!defined('TL\_ROOT')) die('You can not access this file directly!');

/\*\*
 \* GroupDocs
 \*
 \* This program is free software: you can redistribute it and/or
 \* modify it under the terms of the GNU Lesser General Public
 \* License as published by the Free Software Foundation, either
 \* version 2.1 of the License, or (at your option) any later version.
 \*
 \* This program is distributed in the hope that it will be useful,
 \* but WITHOUT ANY WARRANTY; without even the implied warranty of
 \* MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
 \* Lesser General Public License for more details.
 \*
 \* You should have received a copy of the GNU Lesser General Public
 \* License along with this program. If not, please visit the Free
 \* Software Foundation website at http://www.gnu.org/licenses/.
 \*
 \* PHP version 5
 \* @copyright  2012
 \* @author     sales@groupdocs.com
 \* @license    GPL
 \*/

/\*\*
 \* Back end modules
 \*/
$GLOBALS\['TL\_LANG'\]\['MOD'\]\['groupdocs\_viewer'\] = array('GroupDocs Viewer', 'Module name');

/\*\*
 \* Front end modules
 \*/
//$GLOBALS\['TL\_LANG'\]\['FMD'\]\['groupdocs\_viewer'\] = array('GDV List', 'Module list');

?>
```

As you can see, even in language files there has to be a plugin info block and a line of code that limits access. So in this file we have only one line of code which declares an array with the plugin name and transfers it to the CMS's global data.

#### tl\_gdv.phpThe second language file is named **tl\_gdv.php** and contains all local names, titles and messages for our plugin:

```
<?php if (!defined('TL\_ROOT')) die('You can not access this file directly!');

/\*\*
 \* GroupDocs
 \*
 \* This program is free software: you can redistribute it and/or
 \* modify it under the terms of the GNU Lesser General Public
 \* License as published by the Free Software Foundation, either
 \* version 2.1 of the License, or (at your option) any later version.
 \*
 \* This program is distributed in the hope that it will be useful,
 \* but WITHOUT ANY WARRANTY; without even the implied warranty of
 \* MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
 \* Lesser General Public License for more details.
 \*
 \* You should have received a copy of the GNU Lesser General Public
 \* License along with this program. If not, please visit the Free
 \* Software Foundation website at http://www.gnu.org/licenses/.
 \*
 \* PHP version 5
 \* @copyright  2012
 \* @author     sales@groupdocs.com
 \* @license    GPL
 \*/

/\*\*
 \* Table tl\_gdv
 \*/
$GLOBALS\['TL\_DCA'\]\['tl\_gdv'\] = array
(

	// Config
	'config' => array
	(
		'dataContainer'               => 'Table',
		//'ptable'                      => 'tl\_gdv',
	),

	// List
	'list' => array
	(
		'global\_operations' => array
		(
			'all' => array
			(
				'label'               => &$GLOBALS\['TL\_LANG'\]\['MSC'\]\['all'\],
				'href'                => 'act=select',
				'class'               => 'header\_edit\_all',
				'attributes'          => 'onclick="Backend.getScrollOffset();"',
				'button\_callback'			=> array('GrouDocs\_Details', 'groupdocs\_owner'),
			)
		),
		'operations' => array
        (
            'edit' => array
            (
                'label'               => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['edit'\],
                'href'                => 'act=edit',
                'icon'                => 'edit.gif'
            ),
            'copy' => array
            (
                'label'               => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['copy'\],
                'href'                => 'act=copy',
                'icon'                => 'copy.gif'
            ),
            'delete' => array
            (
                'label'               => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['delete'\],
                'href'                => 'act=delete',
                'icon'                => 'delete.gif',
                'attributes'          => 'onclick="if (!confirm(\\'' . $GLOBALS\['TL\_LANG'\]\['MSC'\]\['deleteConfirm'\] . '\\')) return false; Backend.getScrollOffset();"'
            ),
            'show' => array
            (
                'label'               => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['show'\],
                'href'                => 'act=show',
                'icon'                => 'show.gif'
            )
        )

	),

	// Palettes
	'palettes' => array
	(
		'default'                     => '{title\_legend},apiKey,clientId,width,height;'
	),

	// Fields
	'fields' => array
	(
        'id' => array
        (
            'label'                   => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['id'\],
            'inputType'               => 'text',
            'search'                  => false,
            'eval'                    => array('mandatory'=>true)
        ),
        'apiKey' => array
        (
            'label'                   => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['apiKey'\],
            'inputType'               => 'text',
            'search'                  => false,
            'eval'                    => array('mandatory'=>true, 'maxlength'=>128, 'tl\_class'=>'w50')
        ),
        'clientId' => array
        (
            'label'                   => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['clientId'\],
            'inputType'               => 'text',
            'search'                  => false,
            'eval'                    => array('mandatory'=>true, 'maxlength'=>128, 'tl\_class'=>'w50')
        ),
        'width' => array
        (
            'label'                   => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['width'\],
            'inputType'               => 'text',
            'search'                  => false,
            'eval'                    => array('mandatory'=>true, 'maxlength'=>4, 'tl\_class'=>'w50')
        ),
        'height' => array
        (
            'label'                   => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['height'\],
            'inputType'               => 'text',
            'search'                  => false,
            'eval'                    => array('mandatory'=>true, 'maxlength'=>4, 'tl\_class'=>'w50')
        ),
		/\*
        'image' => array
        (
            'label'                   => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['image'\],
            'inputType'               => 'fileTree',
            'eval'                    => array('files'=>true, 'filesOnly'=>true, 'fieldType'=>'radio')
        ),\*/
	)
);

/\*\*
 @calss GrouDocs\_Details
 groupdocs\_owner() - method manipulate
\*/
class GrouDocs\_Details{
	function groupdocs\_owner(){
	print "<script>";
	// admin interface
	echo "
	setTimeout(function(){
			var GroupDocsAcc = document.getElementsByClassName('tl\_file\_list');
			GroupDocsAcc\[0\].innerHTML = 'GroupDocs Details';
	},500);
		 ";
	print "</script>";
}}

?>
```

Remember that all data is declared as arrays and transferred to the CMS's Global arrays. Also in this file we have JavaScript code which gets a list of sidebar elements and adds links to our plugin details:

```
class GrouDocs\_Details{
	function groupdocs\_owner(){
	print "<script>";
	// admin interface
	echo "
	setTimeout(function(){
			var GroupDocsAcc = document.getElementsByClassName('tl\_file\_list');
			GroupDocsAcc\[0\].innerHTML = 'GroupDocs Details';
	},500);
		 ";
	print "</script>";
}}
```

You must write the JavaScript code as a simple text by using the 'echo' command. Also in this language file we declare all dependences and includes such as icons etc. That's the last step of the plugin declaration. Now we will add some useful functionality.

### Adding Functionality

1.  Create three folders: **html**, **config** and **dca**.
2.  Place an icon .gif file, 16x16 pixels, in the **html** folder. That's all we need to do with the **html** folder.
3.  In the **dca**folder, create two files:
    
    1.  .htaccess
    2.  tl\_gdv.php
    

#### htaccess

```
order deny,allow
deny from all
```

That's all. This code gave access to this folder from ather web pages of Admin side where user can bee.

#### tl\_gdv.phpThe code for the second file:

```
<?php if (!defined('TL\_ROOT')) die('You can not access this file directly!');

/\*\*
 \* GroupDocs
 \*
 \* This program is free software: you can redistribute it and/or
 \* modify it under the terms of the GNU Lesser General Public
 \* License as published by the Free Software Foundation, either
 \* version 2.1 of the License, or (at your option) any later version.
 \*
 \* This program is distributed in the hope that it will be useful,
 \* but WITHOUT ANY WARRANTY; without even the implied warranty of
 \* MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
 \* Lesser General Public License for more details.
 \*
 \* You should have received a copy of the GNU Lesser General Public
 \* License along with this program. If not, please visit the Free
 \* Software Foundation website at http://www.gnu.org/licenses/.
 \*
 \* PHP version 5
 \* @copyright  2012
 \* @author     sales@groupdocs.com
 \* @license    GPL
 \*/

/\*\*
 \* Table tl\_gdv
 \*/
$GLOBALS\['TL\_DCA'\]\['tl\_gdv'\] = array
(

	// Config
	'config' => array
	(
		'dataContainer'               => 'Table',
		//'ptable'                      => 'tl\_gdv',
	),

	// List
	'list' => array
	(
		'global\_operations' => array
		(
			'all' => array
			(
				'label'               => &$GLOBALS\['TL\_LANG'\]\['MSC'\]\['all'\],
				'href'                => 'act=select',
				'class'               => 'header\_edit\_all',
				'attributes'          => 'onclick="Backend.getScrollOffset();"',
				'button\_callback'			=> array('GrouDocs\_Details', 'groupdocs\_owner'),
			)
		),
		'operations' => array
        (
            'edit' => array
            (
                'label'               => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['edit'\],
                'href'                => 'act=edit',
                'icon'                => 'edit.gif'
            ),
            'copy' => array
            (
                'label'               => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['copy'\],
                'href'                => 'act=copy',
                'icon'                => 'copy.gif'
            ),
            'delete' => array
            (
                'label'               => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['delete'\],
                'href'                => 'act=delete',
                'icon'                => 'delete.gif',
                'attributes'          => 'onclick="if (!confirm(\\'' . $GLOBALS\['TL\_LANG'\]\['MSC'\]\['deleteConfirm'\] . '\\')) return false; Backend.getScrollOffset();"'
            ),
            'show' => array
            (
                'label'               => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['show'\],
                'href'                => 'act=show',
                'icon'                => 'show.gif'
            )
        )

	),

	// Palettes
	'palettes' => array
	(
		'default'                     => '{title\_legend},apiKey,clientId,width,height;'
	),

	// Fields
	'fields' => array
	(
        'id' => array
        (
            'label'                   => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['id'\],
            'inputType'               => 'text',
            'search'                  => false,
            'eval'                    => array('mandatory'=>true)
        ),
        'apiKey' => array
        (
            'label'                   => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['apiKey'\],
            'inputType'               => 'text',
            'search'                  => false,
            'eval'                    => array('mandatory'=>true, 'maxlength'=>128, 'tl\_class'=>'w50')
        ),
        'clientId' => array
        (
            'label'                   => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['clientId'\],
            'inputType'               => 'text',
            'search'                  => false,
            'eval'                    => array('mandatory'=>true, 'maxlength'=>128, 'tl\_class'=>'w50')
        ),
        'width' => array
        (
            'label'                   => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['width'\],
            'inputType'               => 'text',
            'search'                  => false,
            'eval'                    => array('mandatory'=>true, 'maxlength'=>4, 'tl\_class'=>'w50')
        ),
        'height' => array
        (
            'label'                   => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['height'\],
            'inputType'               => 'text',
            'search'                  => false,
            'eval'                    => array('mandatory'=>true, 'maxlength'=>4, 'tl\_class'=>'w50')
        ),
		/\*
        'image' => array
        (
            'label'                   => &$GLOBALS\['TL\_LANG'\]\['tl\_gdv'\]\['image'\],
            'inputType'               => 'fileTree',
            'eval'                    => array('files'=>true, 'filesOnly'=>true, 'fieldType'=>'radio')
        ),\*/
	)
);

/\*\*
 @calss GrouDocs\_Details
 groupdocs\_owner() - method manipulate
\*/
class GrouDocs\_Details{
	function groupdocs\_owner(){
	print "<script>";
	// admin interface
	echo "
	setTimeout(function(){
			var GroupDocsAcc = document.getElementsByClassName('tl\_file\_list');
			GroupDocsAcc\[0\].innerHTML = 'GroupDocs Details';
	},500);
		 ";
	print "</script>";
}}

?>
```This second file is a copy of the language file with the same name - **tl\_gdv.php**. We do this in order that Contao CMS will have access to this file from any Admin side page where user edit the content of this page.

#### The Config FolderThe most important and interesting files are placed in the **Config** folder:

*   **.htaccess**
*   **config.php**
*   **database.sql**

1.  Create these three files in the **config** folder.
2.  The **.htaccess** file is a copy of **.htaccess** file created in the **dca** folder. We need this file here for the same purposes.
3.  The **config.php** file contains all the plugin's usefull logic. You'll find the code below.

```
<?php if (!defined('TL\_ROOT')) die('You can not access this file directly!');

/\*\*
 \* GroupDocs
 \*
 \* This program is free software: you can redistribute it and/or
 \* modify it under the terms of the GNU Lesser General Public
 \* License as published by the Free Software Foundation, either
 \* version 2.1 of the License, or (at your option) any later version.
 \*
 \* This program is distributed in the hope that it will be useful,
 \* but WITHOUT ANY WARRANTY; without even the implied warranty of
 \* MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
 \* Lesser General Public License for more details.
 \*
 \* You should have received a copy of the GNU Lesser General Public
 \* License along with this program. If not, please visit the Free
 \* Software Foundation website at http://www.gnu.org/licenses/.
 \*
 \* PHP version 5
 \* @copyright  2012
 \* @author     sales@groupdocs.com
 \* @license    GPL
 \*/

array\_insert($GLOBALS\['BE\_MOD'\]\['content'\], 3, array
(
	'groupdocs\_viewer' => array
	(
		'tables' => array('tl\_gdv'),
		'icon'   => 'system/modules/groupdocs\_viewer/html/groupdocs.gif'
	)
));

// Just add JS to Back End where using TinyMCE
$GLOBALS\['TL\_HOOKS'\]\['outputBackendTemplate'\]\[\] = array('ArticleAddGroupDocs', 'javaScriptFileID');
class ArticleAddGroupDocs{
public function javaScriptFileID($strContent, $strTemplate)
{
    if ($strTemplate == 'be\_main')
    {
		if($\_GET\['do'\]=='article' && $\_GET\['act'\]=='edit')
			print "<script>
					//build GroupDocs Button just above Text Editor
				setTimeout(function(){
					var place\_for\_but = document.getElementById('pal\_text\_legend');
					var leg = place\_for\_but.getElementsByTagName('legend')\[0\];
					var btn=document.createElement('input');
					btn.type = 'button';
					btn.id = 'groupdocsv'
					btn.value = 'Embed GroupDocs Viewer';
					btn.onclick = function() { insertGroupDocsIframe(); };
					insertAfter(leg, btn);
				},500);

				function insertGroupDocsIframe(){
						// Enter GroupDocs File ID
						var ans=prompt('Enter GroupDocs File ID:','');
						if(ans.length<50) { alert('Sorry, but this File ID is too short'); return false; }
						if(ans.length>70) { alert('Sorry, but this File ID is too big'); return false; }
						// all good continue
                        var CMSNAME = 'Contao'
                        var CMSVERSION = '2.11.6'
						var iframe = '<iframe src=\\"https://apps.groupdocs.com/document-viewer/embed/'+ans+'?&referer='+CMSNAME+'/'+CMSVERSION+'\\" frameborder=\\"0\\" width=\\"600\\" height=\\"400\\"></iframe>';
						var tinyMceContent = tinyMCE.activeEditor.getContent();
						// set content
						tinyMCE.activeEditor.setContent(tinyMceContent+iframe);
				}
				// as in jquery .after()
				function insertAfter(referenceNode, newNode) {
					referenceNode.parentNode.insertBefore(newNode, referenceNode.nextSibling);
				}
			</script>";
    }

}

}
?>
```

As you already know, we have the basic plugin info block. Then let's take a look at the code. This block inserts the icon file:

```
array\_insert($GLOBALS\['BE\_MOD'\]\['content'\], 3, array
(
	'groupdocs\_viewer' => array
	(
		'tables' => array('tl\_gdv'),
		'icon'   => 'system/modules/groupdocs\_viewer/html/groupdocs.gif'
	)
));
```

Contao uses the TinyMCE editor so we can use this as the starting point to get the position for where to place our button, and recognize if a user turns on page editing or not. Here is the code:

```
// Just add JS to Back End where using TinyMCE
$GLOBALS\['TL\_HOOKS'\]\['outputBackendTemplate'\]\[\] = array('ArticleAddGroupDocs', 'javaScriptFileID');
class ArticleAddGroupDocs{
public function javaScriptFileID($strContent, $strTemplate)
{
    if ($strTemplate == 'be\_main')
    {
		if($\_GET\['do'\]=='article' && $\_GET\['act'\]=='edit')
			print "<script>
					//build GroupDocs Button just above Text Editor
				setTimeout(function(){
					var place\_for\_but = document.getElementById('pal\_text\_legend');
					var leg = place\_for\_but.getElementsByTagName('legend')\[0\];
					var btn=document.createElement('input');
					btn.type = 'button';
					btn.id = 'groupdocsv'
					btn.value = 'Embed GroupDocs Viewer';
					btn.onclick = function() { insertGroupDocsIframe(); };
					insertAfter(leg, btn);
				},500);

				function insertGroupDocsIframe(){
						// Enter GroupDocs File ID
						var ans=prompt('Enter GroupDocs File ID:','');
						if(ans.length<50) { alert('Sorry, but this File ID is too short'); return false; }
						if(ans.length>70) { alert('Sorry, but this File ID is too big'); return false; }
						// all good continue
                        var CMSNAME = 'Contao'
                        var CMSVERSION = '2.11.6'
						var iframe = '<iframe src=\\"https://apps.groupdocs.com/document-viewer/embed/'+ans+'?&referer='+CMSNAME+'/'+CMSVERSION+'\\" frameborder=\\"0\\" width=\\"600\\" height=\\"400\\"></iframe>';
						var tinyMceContent = tinyMCE.activeEditor.getContent();
						// set content
						tinyMCE.activeEditor.setContent(tinyMceContent+iframe);
				}
				// as in jquery .after()
				function insertAfter(referenceNode, newNode) {
					referenceNode.parentNode.insertBefore(newNode, referenceNode.nextSibling);
				}
			</script>";
    }

}
```

As I mentioned, we must use JavaScript as simple text and include it to the page by using **echo** or **print** commands. This JavaScript receives the button position and creates the button:

```
//build GroupDocs Button just above Text Editor
				setTimeout(function(){                                                  //Set timeout that the page would be loaded completely
					var place\_for\_but = document.getElementById('pal\_text\_legend'); //Get element to place our button to him
					var leg = place\_for\_but.getElementsByTagName('legend')\[0\];      //Get legend element
					var btn=document.createElement('input');                        //Creation of button
					btn.type = 'button';                                            //Declare button type as 'button'
					btn.id = 'groupdocsv'                                           //Declare button id as 'groupdocsv'
					btn.value = 'Embed GroupDocs Viewer';                           //Declare button value
					btn.onclick = function() { insertGroupDocsIframe(); };          //Declare function which will be executed on click
					insertAfter(leg, btn);                                         //Inserting button above legend
				},500);
```We've created a button and added its function. Then we have a function that generates a dialog window and places an iframe in the editor.

```
function insertGroupDocsIframe(){
						// Enter GroupDocs File ID
						var ans=prompt('Enter GroupDocs File ID:','');                                      //Genaretion of dialog window
						if(ans.length<50) { alert('Sorry, but this File ID is too short'); return false; } //Check entered by user data lenght
						if(ans.length>70) { alert('Sorry, but this File ID is too big'); return false; }
						// all good continue
                        var CMSNAME = 'Contao'
                        var CMSVERSION = '2.11.6'
                                                //Next long line of code it's our iframe to which we transfer entered by user File GUID
                                                var iframe = '<iframe src=\\"https://apps.groupdocs.com/document-viewer/embed/'+ans+'?&referer='+CMSNAME+'/'+CMSVERSION+'\\" frameborder=\\"0\\" width=\\"600\\" height=\\"400\\"></iframe>';
						var tinyMceContent = tinyMCE.activeEditor.getContent(); //This line get editor content

						tinyMCE.activeEditor.setContent(tinyMceContent+iframe); //Here we add our iframe to editor
				}
				// as in jquery .after()
				function insertAfter(referenceNode, newNode) {
					referenceNode.parentNode.insertBefore(newNode, referenceNode.nextSibling);
				}
```That's it. We created a GroupDocs Viewer plugin for Contao CMS.

## The Final PluginThis is the plugin in action: \[caption id="attachment\_1841" align="alignnone" width="600" caption="Plugin structure"\]![Plugin structure](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/04/Plugin-structure1.png "Plugin structure")\[/caption\] \[caption id="attachment\_1842" align="alignnone" width="600" caption="Button"\]![Button](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/04/Button.png "Button")\[/caption\] \[caption id="attachment\_1843" align="alignnone" width="602" caption="Dialog"\]![Dialog](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/04/Dialog.png "Dialog")\[/caption\] \[caption id="attachment\_1844" align="alignnone" width="598" caption="Iframe"\]![Iframe](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/04/Iframe.png "Iframe")\[/caption\] That's all for today. See you in the next article.




