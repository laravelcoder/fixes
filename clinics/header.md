<?php
if (!defined('ABSPATH')) {die();}

global $avia_config;

$style = $avia_config['box_class'];
$responsive = avia_get_option('responsive_active') != "disabled" ? "responsive" : "fixed_layout";
$blank = isset($avia_config['template']) ? $avia_config['template'] : "";
$av_lightbox = avia_get_option('lightbox_active') != "disabled" ? 'av-default-lightbox' : 'av-custom-lightbox';
$preloader = avia_get_option('preloader') == "preloader" ? 'av-preloader-active av-preloader-enabled' : 'av-preloader-disabled';
$sidebar_styling = avia_get_option('sidebar_styling');
$filterable_classes = avia_header_class_filter(avia_header_class_string());
$av_classes_manually = "av-no-preview"; /*required for live previews*/
$av_classes_manually .= avia_is_burger_menu() ? " html_burger_menu_active" : " html_text_menu_active";

?><!DOCTYPE html>
<html <?php language_attributes();?> class="<?php echo "html_{$style} " . $responsive . " " . $preloader . " " . $av_lightbox . " " . $filterable_classes . " " . $av_classes_manually ?> ">
<head>
	<meta charset="<?php bloginfo('charset');?>" />
	<?php
/*
 * outputs a rel=follow or nofollow tag to circumvent google duplicate content for archives
 * located in framework/php/function-set-avia-frontend.php
 */
if (function_exists('avia_set_follow')) {echo avia_set_follow();}

?>

	<!-- mobile setting -->
	<?php

if (strpos($responsive, 'responsive') !== false) {
	echo '<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">';
}

?>

	<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
	<!-- Scripts/CSS and wp_head hook -->
	<?php wp_head();?>

	<?php if (is_user_logged_in()): ?>
	<link rel="stylesheet" media="all" href="<?php echo get_stylesheet_directory_uri(); ?>/clinic-custom.css?<?php echo time(); ?>">
	<?php else: ?>
		<link rel="stylesheet" media="all" href="<?php echo get_stylesheet_directory_uri(); ?>/clinic-custom.css">
	<?php endif; ?>

	<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>

</head>


<body id="top" <?php body_class($style . " " . $avia_config['font_stack'] . " " . $blank . " " . $sidebar_styling);
avia_markup_helper(array('context' => 'body'));?>>

	<?php

if ("av-preloader-active av-preloader-enabled" === $preloader) {
	echo avia_preload_screen();
}

?>

	<div id='wrap_all'>

	<?php
if (!$blank) //blank templates dont display header nor footer
{
	//fetch the template file that holds the main menu, located in includes/helper-menu-main.php
	get_template_part('includes/helper', 'main-menu');

}?>

	<div id='main' class='all_colors' data-scroll-offset='<?php echo avia_header_setting('header_scroll_offset'); ?>'>

	<?php

if (isset($avia_config['temp_logo_container'])) {
	echo $avia_config['temp_logo_container'];
}

do_action('ava_after_main_container');

?>
