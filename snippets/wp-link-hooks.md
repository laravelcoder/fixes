

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

F:\1\larada\clinics\lcaSTAGE\wp-content\
F:\1\larada\clinics