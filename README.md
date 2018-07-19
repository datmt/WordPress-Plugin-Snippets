# WordPress-Plugin-Snippets
useful wordpress plugin snippets

## Register a menu in Wordpress Admin
`
add_action('admin_menu', 'core37_lp_form_add_menu');

function core37_lp_form_add_menu()
{
	add_menu_page('WP Lead Plus X', 'WP Lead Plus X', 'edit_posts', C37_LP_FORM_MENU_SLUG, 'core37_lp_form_ui_main');
	add_submenu_page(C37_LP_FORM_MENU_SLUG, 'Make Pages', 'Make Pages', 'edit_posts', C37_LP_FORM_MENU_SLUG . '-make', 'core37_lp_form_ui_make_form');
	if (c37LpNangCap)
	{
		add_submenu_page(C37_LP_FORM_MENU_SLUG, 'Popups', 'Popups', 'edit_posts', C37_LP_FORM_MENU_SLUG . '-popup', 'core37_lp_ui_popup_manager');
		add_submenu_page(C37_LP_FORM_MENU_SLUG, 'Widgets', 'Widgets', 'edit_posts', C37_LP_FORM_MENU_SLUG . '-widget', 'core37_lp_ui_widget_manager');
	}

}
`
