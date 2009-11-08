Not ready for production use!
=============================

Based on:

- [Priminister's API presentation during CakeFest #03, Berlin][http://www.cake-toppings.com/2009/07/15/cakefest-berlin/]
- [Forked XML Serialization helper by rodrigorm][http://github.com/rodrigorm/rest]
- [REST documentation][http://book.cakephp.org/view/476/REST]
- [CakeDC article][http://cakedc.com/eng/developer/mark_story/2008/12/02/nate-abele-restful-cakephp]

License: BSD-style

Installation
=============================

As a git submodule
------------------

    git submodule add git://github.com/kvz/cakephp-rest-plugin.git app/plugins/rest
    git submodule update --init

Other
-----
Just place the files directly under: `app/plugins/rest`

Implementation
==============

Controller
-----------
    class ClustersController extends AppController {
        public $components = array(
            'RequestHandler',
            'Rest.Rest' => array(
                'debug' => 0,
                'index' => array(
                    'restVars' => array(
                        'rows' => 'servers'
                    ),
                ),
            ),
        );
    }

`restVars` makes variables you have in: `$this->viewVars` available in the
resulting XML or json under the name you specify in the value part

Router
------
    // Add an element for each controller that you want to open up
    // in the REST API
    Router::mapResources(array('clusters'));  

    // Add xml + json to your parseExtensions
    Router::parseExtensions('rss', 'json', 'xml', 'json', 'pdf'); 

