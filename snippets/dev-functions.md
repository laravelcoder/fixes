
function scripts_styles_print_frontend()
{
    global $loader;
    if (!is_user_logged_in()) :
    wp_enqueue_style('custom-css', get_stylesheet_directory_uri() . '/custom.css?');
    else:
    wp_enqueue_style('custom-css', get_stylesheet_directory_uri() . '/custom.css?'. time());
    endif;
}
add_action( 'wp_enqueue_scripts','scripts_styles_print_frontend', 120 );



function scripts_styles_print_frontend()
{
    global $loader;
    if (!is_user_logged_in()) :
    wp_enqueue_style('custom-css', get_stylesheet_directory_uri() . '/custom.css?');
    wp_enqueue_style('portrait-css', get_stylesheet_directory_uri() . '/portrait.css?');
    wp_enqueue_style('landscape-css', get_stylesheet_directory_uri() . '/landscape.css?');
    else:
    wp_enqueue_style('custom-css', get_stylesheet_directory_uri() . '/custom.css?'. time());
    wp_enqueue_style('portrait-css', get_stylesheet_directory_uri() . '/portrait.css?'. time());
    wp_enqueue_style('landscape-css', get_stylesheet_directory_uri() . '/landscape.css?'. time());
    endif;
}
add_action( 'wp_enqueue_scripts','scripts_styles_print_frontend', 120 );
