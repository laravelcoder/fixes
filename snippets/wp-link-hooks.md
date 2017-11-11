

get_stylesheet_uri()           = http://example.com/wp-content/themes/example-child/style.css
get_template_directory_uri()   = http://example.com/wp-content/themes/example-parent
get_stylesheet_directory_uri() = http://example.com/wp-content/themes/example-child


<?php get_stylesheet_directory_uri(); ?>

get_stylesheet_uri()           = http://example.com/wp-content/themes/example-child/style.css
get_template_directory_uri()   = http://example.com/wp-content/themes/example-parent
get_stylesheet_directory_uri() = http://example.com/wp-content/themes/example-child

wp_enqueue_style('custom', get_stylesheet_directory_uri() . '/custom.css', 100);
  <style type="text/css" media="screen">
                @import url( <?php bloginfo('stylesheet_url'); ?>?<?php echo time(); ?> );
        </style>

<link rel="stylesheet" media="all" href="<?php echo get_stylesheet_directory_uri(); ?>/custom.css?<?php echo time(); ?>">
<link rel="stylesheet" media="all and (orientation:portrait)" href="<?php echo get_stylesheet_directory_uri(); ?>/portrait.css?<?php echo time(); ?>">
<link rel="stylesheet" media="all and (orientation:landscape)" href="<?php echo get_stylesheet_directory_uri(); ?>/landscape.css?<?php echo time(); ?>">



is_page();
// When any single Page is being displayed. is_page(42);
// When Page 42 (ID) is being displayed. is_page('Contact');
// When the Page with a post_title of "Contact" is being displayed. is_page('about-me');
// When the Page with a post_name (slug) of "about-me" is being displayed. is_page(array(42,'about-me','Contact'));
// Returns true when the Pages displayed is either post ID 42.