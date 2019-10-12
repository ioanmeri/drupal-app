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