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
