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

### Create a Block View 
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
_It creates a page_

* Title: New page
* Add Fields and Filters
* Browse the page at /new-page


## Contextual Filters with Views
_The designer must appear in the left column of a project_

* Add Designer field in Project Content Type
* Create a Block View: Side Info View
	* pager 1 item only
	* Sort Criteria (Post date (desc))
	* show only last piece of content (Sass mastery)
* From Blocks -> show Side Info View in Sidebar first
* Configure block to appear only in projects/* pages
* Now Sass mastery appears in sidebar of every Project 
	* Not what we want!
	* Should say the name of the developer
* Pass Contextual filter (show it knows what content is on a display proper Designer field)
	* Project Side Info: Block View -> Advanced -> Add Contextual Filter
	* Provide Default value
		* Contet ID from URL


## Taxonomy
_Core module_ // _Sort and categorize content_ // _metadata, tags_

* Structure -> Taxonomy
* Create Taxonomy (Vocabulary) for projects (tutorial, development, design)
* Add  -> Project Type -> Add description
* Add Terms (now page available: /project-type/development)
* In Project Content Type -> Add new field -> Widghet (Check boxes)
	* Name: Project Type
	* Field: Term reference
	* Vocabulary: Project Type created


* Add children to Taxonomy terms
	* list terms
	* Add term
	* Relations -> Parent terms (-Drupal)

## Exposed Filters

_Expose filters to users_

* Edit Block View
* Filter Criteria
	* Add filter 
	* Content: Project Type 
	* Use AJAX




## Create Custom Date Types
* Configuration » Regional and language » Date and time
* Formats Tab
	* Add format 
	* Add Format string -> M d Y (php date time docs)
* Types Tab
	* Add date type
	* Name it and choose the newly created Date format
* In the View
	* you can choose the New Type format for Date format


## Update Drupal Core
* 7.12 -> 7.14
* BackUp all files
* Home » Administration » Configuration » Development » Maintenance mode
	* Check Put site into maintenance mode
* Download latest version
* Delete everything from root folder except /sites!!
* Paste everything from latest version except /sites
* Browse to /update.php
* Update DB
* Configuration -> Clear Cache
* Uncheck maintance mode
* Delete files
	(CHANGELOG.txt, INSTALL.mysql.txt, INSTALL.pgsql.txt, install.php, INSTALL.sqlite.txt, INSTALL.txt, LICENCE.txt, MAINTAINERS.txt, UPGRADE.txt)



## Google Analytics
* install [module](https://www.drupal.org/project/google_analytics)
* configure web property id

## reCAPTCHA

## Quick Tabs
* instal module
* Structure -> Quicktabs
* Add Tabs (Can use AJAX)
* Shows up in Blocks -> choose where to show




