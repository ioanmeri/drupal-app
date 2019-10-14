# Drupal 7 Tutorials
### Video series on [youtube](https://www.youtube.com/watch?v=-cUWFLBZU5I&list=PL15BE2E8313A4E809&index=2) by Scott Tolinski

* Install Drupal 7 Locally
	* touch settings.php and /files in /sites/default dir

* Admin Bar Review

* Themes
	* Install
		* download [omega theme](https://www.drupal.org/project/omega) and move to /sites/all/themes
	* Create subtheme
		* copy /sites/all/themes/omega/starterkits/omega-html5 to /sites/all/themes
		* rename folder, change css file names YOURTHEME to subtheme folder name

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

* Custom Image Styles
	* Configuration -> Media -> Image Styles
	* Add new effect: Scale (height: 500) and Crop 500x500

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



## Content Types
### Create
* Basic Page
* Article
* **Custom** Content Type: Project
	* Create a Project and set basic fields
	* Add an Image from existing field
		* Manage display: order, format, style

### Reference other Nodes with References

_reference one content type with other content types_

_e.g One **Course** (Custom Content Type) can have a **Course Category** (Custom Content Type) and many **Course Videos** (Custom Content Type)_

* install [references](https://www.drupal.org/project/references), Modules: Node reference, References
* Add content type (Course)
* Add field to Course: 
	* Label: Topic, Field Type: **Node reference**, Widget: Check boxes/radio 
		* Content types that can be referenced: **Course Category** (Content Type)
	* Label: Course Videos, Field Type: **Node reference**, Widget: Auto Compete text field 
		* Content types that can be referenced: **Course Videos** (Content Type), Number of values: Unlimited

----------------------------------


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

### Replacement Patters
_Customize the Output of fields in Views_

_e.g. 2 fields exists: **team1** and **team2** => Must output **team1 vs team2**_

* Add Field -> Global: Custom text
	* Add fields to be used in replacement pattern
		* Exclude them from display
	* Rearrange custom text to be below them
		* User replacement pattern [field_team1] vs [field_team2] 





### Contextual Filters with Views
_The designer of a project must appear in the left column of a project_

* Add Designer field in Project Content Type
* Create a Block View: Side Info View
	* pager 1 item only
	* Sort Criteria (Post date (desc))
	* show only last piece of content (Sass mastery)
* From Blocks -> show Side Info View in Sidebar first
* Configure block to appear only in projects/* pages
* Now Sass mastery appears in sidebar of every Project 
	* Not what we want!
	* Should say the name of the designer
* Pass Contextual filter (so it knows what content is on & display proper Designer field)
	* Project Side Info: **Block View -> Advanced -> Add Contextual Filter**
	* Provide Default value
		* Contet ID from URL


### Attach view to a View

_e.g. **Only the title fields** of a view must appear **again** before/after that view_

* Edit View -> Displays + Add -> Attachment
* Creates a Duplicate! -> with attachment settings
* Change fields -> For: **This attachment (override)**

### Views with relationships

_e.g **Course** Content Type has a node reference of **Course Videos** Content type_

_A view must have **only items in course videos**_

* Create a block View: Courses
	* Fields: Title, Poster Image
* Advanced Tab
	* Relationships Add -> Content: Course Videos **(Require this relationship)**
* Fields
	* Content: title -> Now Relationship **field course videos** appears
	* Content: Poster Image -> Now Relationship **field course videos** appears


### Exposed Filters

_Expose filters to users_

* Edit Block View
* Filter Criteria
	* Add filter 
	* Content: Project Type 
	* Use AJAX


---------------------------------



## Taxonomy
_Core module_ // _Sort and categorize content_ // _metadata, tags_

_e.g. In **Project** Content Type add the field **Project Type** that can be one of the terms in created **taxonomy**_

* Structure -> Taxonomy
* Create Taxonomy (Vocabulary) for projects (tutorial, development, design)
* Add  -> Project Type -> Add description
* Add Terms (now page available: /project-type/development)
* In Project Content Type -> Add new field -> Widghet (Check boxes)
	* Name: Project Type
	* Field: **Term reference**
	* Vocabulary: **Project Type**


* Add children to Taxonomy terms
	* list terms
	* Add term
	* Relations -> Parent terms (-Drupal)

--------------------------

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

---------------------------

## Responsive Grid with Views
_2 items in md, 1 item in sm_
* Views Format: Semantic Views, Semantic Views fields
* Format Settings
	* No Groups, No List (List type: None)
	* Row (Element: div), class="tut-tease"


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



## Slideshow
### Views slideshow
* install [views_slideshow](https://www.drupal.org/project/views_slideshow) and required modules, libraries
* Add a new Block view
* Display format -> Slideshow -> Continue & Edite
* Add Fields -> project image
* Configure
	* Format -> Settings
	* Can choose effect (Cycle specific)

### Responsive Slideshow
_connect to the same slideshow ^^_
* install [flex_slider](https://www.drupal.org/project/flexslider)
* Add [jQuery library](https://github.com/woocommerce/FlexSlider) in /sites/all/libraries
* Edit previous Slideshow view
* Format -> Settings -> Slides -> Slideshow Type (Flex Slider) -> Flex Slider Options
	* Add Control
* Flex Slider Plugin Configuration
	* Configuration -> Media -> Flex Slider
----------------------------

## Useful Modules

### Google Analytics
* install [module](https://www.drupal.org/project/google_analytics)
* configure web property id

### reCAPTCHA

### module filter 
_modules appear nicer! in administration_

### Quick Tabs
* install module
* Structure -> Quicktabs
* Add Tabs (Can use AJAX)
* Shows up in Blocks -> choose where to show

### Menu Attributes

_additional attributes for menu items such as id, name, class, style.._

* install [module](https://www.drupal.org/project/menu_attributes)
* Structure -> Menus -> Main Menu -> Link (Edit)
* Dropdown Menu Item Attributes
	* title
	* id
	* classes...

### Better Exposed Filters
* install [module](https://www.drupal.org/project/better_exposed_filters)
* Edit view
* Advanced Tab -> Exposed Form -> Better Exposed options
	* Autosubmit
* Can have multiple selections

### Semantic Views
_removes unnecessary divs etc => better semantics_

_controls semantics of a view_

* install [module](https://www.drupal.org/project/semanticviews)
* Edit a view -> Format
	* Change to Sematic Views
	* Show: Change to Semantic Views Fields




## Update Drupal Core
_e.g. 7.12 -> 7.14_

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


## Host Drupal App
* Clear Cache (Performance)
* Export DB from phpMyAdmin gzip
* Compress all files (drupalapp dir)
* Login to Host
* Create test subdomain
	* Create DB
	* Add DB user
	* Import previous DB in newly created
* ssh upload compressed files 
* uncompress the files from server

* Browse to test.sitename.com (DB credentials error)
	* server/sites/default/settings.php
	* change database information $databases
		* database
		* username 
		* password
* Reports
	* /sites/default/files must be writable (cached public files)
		* change permissions to 777



## Feeds

_parses feeds (csv, rss, xml) and creates content_

* install [feeds](https://www.drupal.org/project/feeds) and required [job_scheduler](https://www.drupal.org/project/job_scheduler)
* Structure -> **Feed Importers**
	* Create feed importer (Simple CSV)
	* Browse to /import and run feed

### Create content with CSV files
* Create Content Type: Feed
	* Title, Body
* Configure the Feed (Structure -> Feed Importers) to parse imported CSV file
* Browse to /import/simple_csv and import local csv


### Import from RSS feed
* Create New Feed Importer (RSS)
* Configure **Structure -> Feed Importers**
* /import -> RSS -> paste link

### Feeds Tamper
_modify data before it gets saved_

* install [module](https://www.drupal.org/project/feeds_tamper)
* Structure -> Feed Importers -> Tamper (New operation)