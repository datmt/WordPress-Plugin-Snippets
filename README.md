# WordPress-Plugin-Snippets
useful wordpress plugin snippets

## Register a menu in Wordpress Admin
```
add_action('admin_menu', 'core37_lp_form_add_menu');

function _prefix_add_menu()
{
	add_menu_page('WP Lead Plus X', 'WP Lead Plus X', 'edit_posts', 'your slug', 'UI_FUNCTION');
}
```
