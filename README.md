# WordPress-Plugin-Snippets
useful wordpress plugin snippets

## Register a menu in Wordpress Admin
```
add_action('admin_menu', '_prefix_add_menu');

function _prefix_add_menu()
{
	add_menu_page('MENU NAME', 'MENU NAME', 'edit_posts', 'your slug', 'UI_FUNCTION');
}
```
## Set a template file as post/page template
```
add_filter('template_include', 'c37_use_custom_template', 99999999);

function c37_use_custom_template($page_template)
{
	//if the page is created by wp lead plus x, it will have this meta key
	$isC37LP = get_post_meta(get_the_ID(), C37LPManager::C37_LP_META_PAGE_SETTINGS);

	if ($isC37LP != false)
	{
		return plugin_dir_path(__FILE__) .'inc/c37-template.php';
	}
	return $page_template;

}

```

## Enqueue front end scripts and style
```
add_action('wp_enqueue_scripts', 'core37_lp_form_load_frontend_scripts');

function core37_lp_form_load_frontend_scripts()
{
	wp_register_style('c37-lpx-front-styles', plugins_url('bundle/css/front-styles-bundle.css', __FILE__));
	wp_register_script('c37-lpx-front-script', plugins_url('bundle/js/front-bundle.js', __FILE__), array('jquery', 'underscore', 'backbone', 'jquery-ui-core','jquery-ui-datepicker'), false, false);
	
	wp_enqueue_script('c37-lpx-front-script');
	wp_enqueue_style('c37-lpx-front-styles');
}

```


## Enqueue scripts/style for backend
```
add_action('admin_enqueue_scripts', 'core37_lp_form_load_backend_scripts', 1000);

function core37_lp_form_load_backend_scripts()
{
	//you can perform a screen check here to make sure the scripts, styles only available on a specific page
	/*
	$currentScreen = get_current_screen();
	if (stripos($currentScreen->base, 'screen-slug') !== false)
	{
		//register and enqueue styles/scripts here
	}
	
	*/
	//register and enqueue scripts
	wp_register_script( 'script-handler', plugins_url( 'bundle/js/my-bundle.js', __FILE__ ), array(
		'jquery',
		'underscore',
		'backbone'
	), false, true );
	
	wp_enqueue_script('script-handler', '', array(), false, true);
	
	//register and enqueue styles
	wp_register_style('style-handler', plugins_url('bundle/css/editor-bundle.css', __FILE__));
	
	wp_enqueue_style('style-handler');

}

```
