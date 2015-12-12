# CI3 Fire Starter (ci3-fire-starter)

<a name="toc"></a>
## TABLE OF CONTENTS
* [Introduction](#introduction)
* [(Not) Modular](#not-modular)
* [Base Classes](#base-classes)
  * [MY\_controller](#my-controller)
  * [Public\_controller](#public-controller)
  * [Private\_controller](#private-controller)
  * [Admin\_controller](#admin-controller)
  * [API\_controller](#api-controller)
  * [Understanding Includes](#understanding-includes)
* [Core Files](#core-files)
  * [Core Config](#core-config)
  * [Core Language](#core-language)
  * [Core Helper](#core-helper)
* [Libraries](#libraries)
  * [JSi18n](#jsi18n-library)
* [User Management](#user-management)
* [Settings](#settings)
* [Themes](#themes)
  * [Theme Functions](#theme-functions)
* [APIs](#apis)
* [System Requirements](#system-requirements)
* [Installation](#installation)
* [Conclusion](#conclusion)
* [What's New](#whats-new)
* [Fork It!](#forkit)

<a name="introduction"></a>
## INTRODUCTION

CI3 Fire Starter is a CodeIgniter3 skeleton application that includes [jQuery](https://jquery.com/) and
[Twitter Bootstrap](http://getbootstrap.com/). It is intended to be light weight, minimalistic and not
get in your way of building great CodeIgniter 3 applications. It is also intended for newbies who want
a simple, easy platform for learning CodeIgniter.

* CodeIgniter 3.x
* Base controllers for Public, Private, Admin and API classes
* JSi18n Library to support internationalization in your JS files
* The latest version of [jQuery](https://jquery.com/)
* The latest version of [Twitter Bootstrap](http://getbootstrap.com/)
* The latest version of [Font Awesome](https://fortawesome.github.io/Font-Awesome/)
* Independent responsive admin and frontend themes
* [Summernote](http://summernote.org/ "Summernote") WYSIWYG editor
* Auto-loaded core config file
* Auto-loaded core language file
* Auto-loaded core helper files
    + Human-readable JSON string output for API functions
    + Array to CSV exporting
    + Enhanced CAPTCHA
    + Random password generator
* Simple user authentication with registration, forgot password and profile editor
* Contact Us page with enhanced CAPTCHA
* Basic admin tool with dashboard, user management, settings and Contact Us message list
* File-based sessions

That should be all you need to kickstart many CodeIgniter projects. While there are many great
CodeIgniter CMS applications ([see below](#conclusion)), sometimes you don't need a full CMS, or you need
something much simpler than what's available, or you need a completely customizable solution. That's
why I created CI3 Fire Starter. I was tired of always having to do the same things over and over again.
So I took some best practices, included all the addons and functions I most commonly use, and this
was the end result, which I now use to start the majority of my projects.

I hope you find it useful. **Please [fork it on Github](https://github.com/JasonBaier/ci3-fire-starter/fork "Fork It")
and help make it better!**

NOTE: This documentation assumes you are already familiar with PHP and CodeIgniter. To learn more about PHP,
visit [php.net](http://php.net/). If you need to learn more about CodeIgniter, visit the
[CodeIgniter User Guide](http://www.codeigniter.com/userguide3/index.html).

![Welcome Screen](http://s3.postimg.org/7vxaw3b2b/ci3_fire_starter_welcome_screen.png?raw=true)

<a name="not-modular"></a>
## (NOT) MODULAR

The former versions of CI Fire Starter (prior to v3.0.0) used to utilize wiredesign's
[Modular Extensions](https://bitbucket.org/wiredesignz/codeigniter-modular-extensions-hmvc). At this
time I have opted not to include it, however, if you have an argument in support of reimplementing it,
I'm all ears... just let me know.

<a name="base-classes"></a>
## BASE CLASSES

Phil Sturgeon wrote a very helpful blog post years ago called
["CodeIgniter Base Classes: Keeping it DRY"](http://philsturgeon.co.uk/blog/2010/02/CodeIgniter-Base-Classes-Keeping-it-DRY).
The methods he described in that article have been implemented in CI3 Fire Starter. All base classes
are located in the /application/core folder.

<a name="my-controller"></a>
#### MY_Controller

This is the main core class used for loading settings, defining includes that get passed to the views,
loading logged-in user data, setting the configured timezone, and turning the profiler on or off. All
other classes extend this class.

<a name="public-controller"></a>
#### Public_Controller

This extends MY\_Controller and drives all your public pages (home page, etc). Any controller that
extends Public\_Controller will be open for the whole world to see.

<a name="private-controller"></a>
#### Private_Controller

This extends MY\_Controller and drives all your private pages (user profile, etc). Any controller that
extends Private\_Controller will require authentication. Specific page requests are stored in session
and will redirect upon successful authentication.

![Profile Screen](http://s8.postimg.org/xpcn4kuud/ci3_fire_starter_profile_screen.png?raw=true)

<a name="admin-controller"></a>
#### Admin_Controller

This extends MY\_Controller and drives all your administration pages. Any controller that extends
Admin\_Controller will require authentication from a user with administration privileges. Specific
page requests are stored in session and will redirect upon successful authentication.

<a name="api-controller"></a>
#### API_Controller

This extends MY\_Controller and drives all your API functions. Any controller that extends
API\_Controller will be open for the whole world to see ([see below for details](#apis)).

<a name="understanding-includes"></a>
#### Understanding Includes

* page\_title    : the title of the page which gets inserted into the document head
* css\_files     : an array of css files to insert into the document head
* js\_files      : an array of javascript libraries to insert into the document body
* js\_files\_i18n : an array of javascript files with internationalization to insert into the document body (see more about these below)

Includes can be appended and/or overwritten from any controller function.

<a name="core-files"></a>
## CORE FILES

Several core files have been included to simplify customizations:

<a name="core-config"></a>
#### Core Config

In /application/config there is a file core.php. This file allows you to set site-wide variables. It
is set up with site version, default templates, pagination settings, enable/disable the profiler and
default form validation error delimiters.

<a name="core-language"></a>
#### Core Language

In /application/language/english is a file core\_lang.php. This file allows you to set language
variables that could be used throughout the entire site (such as the words Home or Logout).

In addition to English, the following languages have been contributed by the community:

* Dutch
* Indonesian
* Turkish
* Spanish
* Simplified Chinese

<a name="core-helper"></a>
#### Core Helper

In /application/helper is a file core\_helper.php. This includes the following useful functions:

* display\_json($array) - used to output an array as JSON in a human-readable format - used by the API
* json\_indent($array) - this is the function that actually creates the human-readable JSON string
* array\_to\_csv($array, $filename) - exports an array into a CSV file (see admin user list)
* generate\_random\_pasword() - used to reset password for users who forgot password

<a name="libraries"></a>
## LIBRARIES

The following libraries have been included in /application/libraries:

<a name="jsi18n-library"></a>
#### JSi18n

This library allows you to internationalize your JavaScript files through CI language files and was
inspired by Alexandros D on [coderwall.com](https://coderwall.com/p/j88iog).

Load this library in the autoload.php file or manually in your controller:

    $this->load->library('jsi18n');

In your language file:

    $lang['alert_message'] = "This is my alert message!";

In your JS files, place your language key inside double braces:

    function myFunction() {
        alert("{{alert_message}}");
    }

Render the Javascript file in your template file:

    <script type="text/javascript"><?php echo $this->jsi18n->translate("/themes/admin/js/my_javascript_i18n.js"); ?></script>

OR in your includes array:

    $this->includes = array_merge_recursive($this->includes, array(
        'js_files_i18n' => array(
            $this->jsi18n->translate("/themes/admin/js/my_javascript_i18n.js")
        )
    ));

<a name="user-management"></a>
## USER MANAGEMENT

CI3 Fire Starter comes with a simple user management tool in the administration tool. It uses a database
table called 'users'. This tool demonstrates a lot of basic but important functionality:

* Sortable list columns
* Search filters
* Pagination with user-changeable items/page
* Exporting lists to CSV
* Form validation
* Harnessing the power of Twitter Bootstrap to accelerate development

![User Administration](http://s27.postimg.org/udwfwrtqb/ci3_fire_starter_user_list.png?raw=true)

IMPORTANT NOTE: user id 1 is the main administrator - DO NOT MANUALLY DELETE. You can not delete this
user from within the admin tool.

<a name="settings"></a>
## SETTINGS

Adding additional setting fields couldn't be any easier. Simply add a new entry in the 'settings'
table of the database with the information below. The script then does all the work and adds the
setting fields to the form automatically. There's no need to modify the form yourself!

* name: this will be the actual input name in the settings form (Ex: site\_name)
* input\_type: type of input to use - options are: input, textarea, radio, dropdown, timezones
* options: optional field for declaring radio and dropdown values - key/value pair - each on its own line
* is\_numeric: 0 or 1 - forces numeric keypad on mobile devices and validates numbers only on form submission
* show\_editor: 0 or 1 - use only on textarea field types to utilize the WYSIWYG editor
* input\_size: use to specify width of input field - options are: small, medium, large
* help\_text: optional field for displaying help/info about the input
* validation: specifies how to validate the input values - uses the pipe-delimited rules from CI's Form
Validation Library - see [Rule Reference](https://codeigniter.com/user_guide/libraries/form_validation.html#rule-reference)
* sort\_order: use to sort the order of input fields
* label: text to display as the input's label
* value: this is the actual value stored for this setting - be sure to set something as the default value
* last\_update: datetimestamp of when the settings field was updated
* updated\_by: reference to the 'users'.'id'

Settings are loaded in MY_Controller and are accessible in every controller, model and view file. 

Example: $this->settings->site_version

![Settings Screen](http://s4.postimg.org/3ltmgpt5p/ci3_fire_starter_setttings_screen.png?raw=true)

<a name="themes"></a>
## THEMES

There are 2 responsive themes provided with CI3 Fire Starter: 'admin' and 'default'. There is also a
'core' theme for global assets. To keep the application light-weight, I did not include a templating
library, such as Smarty, nor did I utilize CI's built-in parser. If you really wanted to include one,
you could check out Phil Sturgeon's [CI-Dwoo extension](https://github.com/philsturgeon/codeigniter-dwoo).

<a name="theme-functions"></a>
#### Theme Functions

***add_css_theme($css_files)***

This function is used to easily add css files to be included in a template. With this function, you
can just add the css file name as a parameter and it will use the default css path for the active theme.
You can add one or more css files as the parameter, either as a string or an array. If using parameter
as a string, it must use comma separation between each css file name.

	 1. Using string as parameter
	     $this->add_css_theme("bootstrap.min.css, style.css, admin.css");

	 2. Using array as parameter
	     $this->add_css_theme(array("bootstrap.min.css", "style.css", "admin.css"));

***add_js_theme($js_files, $is_i18n)***

This function is used to easily add Javascript files to be included in a template. With this function,
you can just add the js file name as a parameter and it will use the default js path for the active theme.
You can add one or more js files as the parameter, either as a string or an array. If using the parameter
as a string, it must use comma separation between each js file name.

The second parameter is used to indicate that the js file supports internationalization using the i18n library. Default is FALSE.

	 1. Using string as parameter
	     $this->add_js_theme("jquery-1.11.1.min.js, bootstrap.min.js, another.js");

	 2. Using array as parameter
	     $this->add_js_theme(array("jquery-1.11.1.min.js", "bootstrap.min.js,", "another.js"));


***add_jsi18n_theme($js_files)***

This function is used to easily add Javascript files that support internationalization to be included
in a template. With this function, you can just add the js file name as the parameter and it will use
the default js path for the active theme. You also can add one or more js files as the parameter,
either as a string or an array. If using the parameter as a string, it must use comma separation
between each js file name.

    1. Using string as parameter
	    $this->add_jsi18n_theme("dahboard_i18n.js, contact_i18n.js");

	2. Using array as parameter
	    $this->add_jsi18n_theme(array("dahboard_i18n.js", "contact_i18n.js"));

	3. Or we can use add_js_theme function, and add TRUE for second parameter
	    $this->add_js_theme("dahboard_i18n.js, contact_i18n.js", TRUE);
	    	- or -
	    $this->add_js_theme(array("dahboard_i18n.js", "contact_i18n.js"), TRUE);

***add_external_css($css_files, $path)***

This function is used to easily add css files from external sources or outside the theme folder to be
included in a template. With this function, you can just add the css file name and their external path
as the parameter, or add css complete with path. See example below:

    1. Using string as first parameter
	    $this->add_external_css("global.css, color.css", "http://example.com/assets/css/");
	 	- or -
	    $this->add_external_css("http://example.com/assets/css/global.css, http://example.com/assets/css/color.css");

	2. Using array as first parameter
	    $this->add_external_css(array("global.css", "color.css"), "http://example.com/assets/css/");
		- or -
	    $this->add_external_css(array("http://example.com/assets/css/global.css", "http://example.com/assets/css/color.css"));

***add_external_js($js_files, $path)***

This function is used to easily add js files from external sources or outside the theme folder to be
included in a template. With this function, you can just add the js file name and their external path
as the parameter, or add js complete with path. See example below:

    1. Using string as first parameter
	    $this->add_external_js("global.js, color.js", "http://example.com/assets/js/");
	 	- or -
	    $this->add_external_js("http://example.com/assets/js/global.js, http://example.com/assets/js/color.js");

	2. Using array as first parameter
	    $this->add_external_js(array("global.js", "color.js"), "http://example.com/assets/js/");
		- or -
	    $this->add_external_js(array("http://example.com/assets/js/global.js", "http://example.com/assets/js/color.js"));

***Chaining***

These methods can also be chained like this:

    $this
        ->add_css_theme("bootstrap.min.css, style.css, admin.css")
		->add_external_css("global.css, color.css", "http://example.com/assets/css/")
        ->add_js_theme("jquery-1.11.1.min.js, bootstrap.min.js, another.js")
		->add_js_theme("dahboard_i18n.js, contact_i18n.js", TRUE)
		->add_external_js("global.js, color.js", "http://example.com/assets/js/");

***set_template($template_file)***

Sometimes you might want to use a different template for different pages, for example, 404 template,
login template, full-width template, sidebar template, etc. You can simply load a different template
using this function.

<a name="apis"></a>
## APIS

With the API class, you can easily create API functions for external applications. There is no
security on these, so if you need a more robust solution, such as authentication and API keys, check
out Phil Sturgeon's [CI Rest Server](https://github.com/philsturgeon/codeigniter-restserver). You
could also just set your own request authentication headers to the code that's already there.

![Sample JSON String](http://s8.postimg.org/nx4x1tdlx/ci3_fire_starter_sample_api.png?raw=true)

<a name="system-requirements"></a>
## SYSTEM REQUIREMENTS

* PHP version 5.4+
* MySQL 5.1+
* PHP GD extension for CAPTCHA to work
* PHP Mcrypt extension if you want to use the Encryption class

See CodeIgniter's [Server Requirements](https://codeigniter.com/user_guide/general/requirements.html)
for the complete list.

<a name="installation"></a>
## INSTALLATION

* Create a new database and import the included sql file from the /assets folder
    + default administrator username/password is **admin/admin**
* Modify the /application/config/config.php
    + line 26: set your base site URL (new requirement as of CI v3.0.3)
    + line 220: set your log threshold - I usually set it to 1 for production environments
    + line 314: set your encryption key using the [recommended method](http://www.codeigniter.com/user_guide/libraries/encryption.html#setting-your-encryption-key "Encryption Library: Setting your encryption key")
* Modify /application/config/database.php and connect to your database
* Upload all files to your server
* Make sure the /captcha folder has write permission
* Set /application/sessions permission to 0600
* Configure your path to use /htdocs
* Visit your new URL
* The default welcome page includes links to the admin tool and the private user profile page
* Make sure you log in to admin and change the administrator password!

<a name="conclusion"></a>
##CONCLUSION

As I said before, CI3 Fire Starter does not attempt to be a full-blown CMS. You would need
to build that functionality yourself. If you're looking for a great CMS built on CodeIgniter,
or need a more robust starting point, then check out one of these awesome applications:

* [HeroFramework](https://github.com/electricfunction/hero/): this was my favorite, but sadly, this
project appears to no longer be active since their website went down - but the source is still available
* [Halogy](http://www.halogy.com/): not sure if development is still active on this project
* [Expression Engine](http://ellislab.com/expressionengine/): from the original creators of CodeIgniter
* [GoCart](http://gocartdv.com/): shopping cart
* [Open-Blog](http://www.open-blog.org/): this is another one of my opensource projects - currently
working on a complete rewrite, but it's been slow going
* [Bonfire](http://cibonfire.com/): this is more of an application builder than a full CMS
* [FuelCMS](http://getfuelcms.com/)
* [CMS Canvas](http://www.cmscanvas.com/)

<a name="whats-new"></a>
## WHAT'S NEW

#### Version 3.1.6
12/11/2015

Thanks [TowerX](https://github.com/TowerX "TowerX") for your Spanish translation.
Thanks [yinlianwei](https://github.com/yinlianwei "yinlianwei") for your Simplified Chinese translation.

* Included pull requests
    + Spanish translation
    + Simplified Chinese translation

#### Version 3.1.5
11/10/2015

* Moved CAPTCHA font, Bromine, to core theme folder

#### Version 3.1.4
11/09/2015

* Moved the base classes into their own files
* Added [Table of Contents](#toc) to README.md
* Added new section for [Settings](#settings) in README.md

#### Version 3.1.3
11/02/2015

* Upgraded to CI 3.0.3
    + Requires you to now set your base URL in config.php
* Upgraded jQuery to 1.11.3
* Upgraded Font Awesome to 4.4.0

#### Version 3.1.2
08/25/2015

Thanks [DeeJaVu](https://github.com/DeeJaVu "DeeJaVu") for your Turkish and Dutch translations.

* Included pull requests
    + Turkish translation
    + Dutch translation
* Upgraded to CI 3.0.1

#### Version 3.1.1
06/16/2015

Thanks [arif-rh](https://github.com/arif-rh "Arif RH") and [simogeo](https://github.com/simogeo "Simon Georget")
for your contributions.

* Included pull requests
    + Added base\_url to links
    + Improved theme functions
    + Indonesian translation
    + Repeat Password error fix
* Fixed email validation check during account registration
* Links to this Github page in theme footers

#### Version 3.1.0
04/15/2015

* Upgraded to CI 3.0.0

#### Version 3.0.5
03/11/2015

* Upgraded to CI 3.0rc3

#### Version 3.0.4
02/17/2015

* Upgraded to CI 3.0rc2

#### Version 3.0.3
01/31/2015

* Added missing glyphicon halfling fonts
* Added favicon transparency
* Fixed favicon bug in main template files

#### Version 3.0.2
01/31/2015

* Updated site name in footers

#### Version 3.0.1
01/31/2015

* Upgraded to CI 3.0rc

#### Version 3.0.0
01/31/2015

* Started as a whole new repository (retiring former repo)
* Upgraded to CI 3.0dev
* Stripped out HMVC pattern
* Removed database navigation
* Replaced TinyMCE with Summernote WYSIWYG editor
* Lots of code cleanup and other improvements

#### Version 2.0.0
05/06/2014

Too many to list them all, but here are some of the major changes:

* Added database-driven settings administration
* Included TinyMCE WYSIWYG editor
* Included Bootstrap DatePicker and modified to work with Bootstrap 3.x
* Removed separate auth module and merged into user module
* Added user self-registration and forgot password functionality to the user module
* Removed separate login template
* Added database-driven menus with sub-menu capabilities and built-in Bootstrap formatting
* Added a CAPTCHA-protected contact page with an admin tool to view messages
* Enabled CSRF protection on all forms
* Enabled database session handling
* Tons of code cleanup and miscellaneous improvements

#### Version 1.0.1
10/10/2013

* Removed admin template includes
* Made login more secure using salt
* Modified users table to handle the login change
    + password field is now char(128)
    + added salt field char(128)

#### Version 1.0.0
10/08/2013

* Initial version

<a name="forkit"></a>
## FORK IT!

**Please [fork CI3 Fire Starter on Github](https://github.com/JasonBaier/ci3-fire-starter/fork "Fork It")
and help make it better!**
