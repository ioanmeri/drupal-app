# Drupal 7 Tutorials
###Video series on [youtube](https://www.youtube.com/watch?v=-cUWFLBZU5I&list=PL15BE2E8313A4E809&index=2) by Scott Tolinski

* Install Drupal 7 Locally
	* touch settings.php and /files in /sites/default dir

* Admin Bar Review

* Themes
	* Install
		* download [omega theme](https://www.drupal.org/project/omega) and move to /sites/all/themes
	* Create subtheme
		* copy /sites/all/themes/omega/starterkits/omega-html5 to /sites/all/themes
		* rename folder, change css file names YOURTHEME to subtheme folder name

* Create Content Types
	* Basic Page
	* Article
	* Custom Content Type: Project
		* Create a Project and set basic fields
		* Add an Image from existing field
			* Manage display: order, format, style

* URL Aliases
	* Alias 1 page link from node/3 to scott/alias 
		* About Page -> Edit -> URL path settings
	* Set a pattern with the module [Pathauto](https://www.drupal.org/project/pathauto)
		* copy folder to /sites/all/modules
		* install required modules: Token
		* Admin Bar -> Modules (Check and Save Configuration)
		* Admin Bar -> Configuration -> URL Aliases
			* Set Default Path pattern: [node:title]
			* Pattern for Projects: projects/[node:title]
			* _Update old urls: Find Content-> Check all -> Update Options(Update URL alias)_	

* Blocks
	* rearange navbar, search and footer blocks
	* Create a Basic Block (Text)

* Menus
	* Rearange menu items
	* Create a menu (as footer nav, from Blocks)

* Custom Homepage
	* Create a Basic page
	* Configuration -> Site information -> Default front page (home)

* Update Module
	* Modules -> Update (don't update in production, backup!)
	* /update.php to update the DB

----------------------------------
* Custom Image Styles
	* Configuration -> Media -> Image Styles
	* Add new effect: Scale (height: 500) and Crop 500x500


## Contact forms

* Contact Form (Core Module), simple not configurable
	* Modules -> Check Contact and Save
	* Configure -> Add another Category (Contact)
	* Modify Menus to include Contact (Check Enable)

* Webform
	* Install module
	* Configure (Create custom fields)

## Wysiwg

* Install Wysiwyg Text Editor
	* Download [module](https://www.drupal.org/project/wysiwyg)
	* copy in /sites/all/modules
	* Admin Bar -> Modules -> Check Wysiwyg -> Save -> Configure -> Download CKEditor and follow instructions where to copy
	* Refresh configuration page, Select Text Format: Filtered HTML, Editor: CKEditor
	* Add Buttons

* Insert an Image in Wysiwyg with Insert
	* Install Insert module
	* Structrure -> Content Types -> Article -> Manage Fields -> Add a new Field (insert_image)
	* Select Insert -> Enable insert Button

* Insert Image with IMCE * IMCE Wysiwyg Bridge
	* Install imce, imce_wysiwyg
	* Configure imce
		* Edit User-1
		* create img dir in root (where files will be uploaded to)
		* Directores set path to <root>/img
		* Create Full Html profile (Configuration » Content authoring » Wysiwyg profiles)
		* In Buttons and plugins check Image and IMCE

---------------------

## Views
_A way to control displaying your content_

_Can set various filters, relationships_

_Display content based on page_

### Create a block View 
* Install ctools(required) and views
* Structure -> Views -> Add new view
	* Add View name (Test View)
	* add description
	* Uncheck Create a Page
	* Check Create a block
* View appears under Structure -> Blocks (View: Test View: Test)

* Filters
	* (Structure -> Views -> Filter Criteria)
	* Add Content: Type (= Article) Filter
	* Add Content: Promoted to front page status (Yes)

* Fields
	* Configure the fields that appear for each Article in that View
	* Reposition the View (Gear icon -> Configure Block)


* Formats & Pagers
	* Format as Table (enable Title to be sortable)
	* Format as HTML unorder list
	* Format as Grid
	* Use a Pager 
		* Full, mini and Num of items
		* Use AJAX (link doesn't change). Advanced -> Use AJAX: Yes

### Create a Page View 