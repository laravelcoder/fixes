<?php/** * * Template header * **/// create an access to the template main objectglobal $dynamo_tpl;?>
<?php do_action( 'dynamowp_doctype' ); ?>
<html <?php do_action( 'dynamowp_html_attributes' ); ?>><head>    
	<title><?php wp_title( '|', 1, 'right' ); ?>
	<?php bloginfo( 'name' ); ?></title>	
	<?php do_action( 'dynamowp_metatags' ); ?>    
	<link rel="profile" href="http://gmpg.org/xfn/11"/>    
	<link rel="shortcut icon" href="<?php get_stylesheet_directory_uri(); ?>/favicon.ico"/>    
	<link rel="pingback" href="<?php bloginfo( 'pingback_url' ); ?>"/>	
	<?php do_action( 'dynamowp_fonts' ); ?>	<?php dp_head_config(); ?>	
	<?php if ( is_singular() && get_option( 'thread_comments' ) ) {		wp_enqueue_script( 'comment-reply' );	} ?>	
	<?php do_action( 'dynamowp_ie_scripts' ); ?>	<?php dp_head_style_pages(); ?>	<?php echo $assets_output; ?>	
	<?php dp_thickbox_load(); ?>	
	<?php echo stripslashes(htmlspecialchars_decode(str_replace('&#039;', "'", get_option($dynamo_tpl->name . '_head_code', '')))); ?>    
	<?php dp_load('responsive_css'); ?>
	<?php wp_head(); ?>    
 

	<?php 
	if (is_user_logged_in()): $user = wp_get_current_user();
		if (current_user_can('manage_options')):
			echo "<!-- You are viewing as an administrator so this is the disabled cache for viewing updated styles while working on them. -->";
			echo '<link rel="stylesheet" media="all and (orientation:portrait)" href="' . get_stylesheet_directory_uri(). '/portrait.css?' . time(). '">'; 
			echo '<link rel="stylesheet" media="all and (orientation:landscape)" href="' . get_stylesheet_directory_uri(). '/landscape.css?' . time(). '">';
		else:
			echo '<link rel="stylesheet" media="all and (orientation:portrait)" href="' . get_stylesheet_directory_uri(). '/portrait.css">'; 
			echo '<link rel="stylesheet" media="all and (orientation:landscape)" href="' . get_stylesheet_directory_uri(). '/landscape.css">';	
		endif;
	endif;
	?>
	<?php if (is_page(['12778', '12779'])): ?>
	<style>
		.woocommerce .button, table.shop_table thead th {background: #5BC500!important; color: #ffffff!important; }
		.woocommerce-info {background: #5BC500!important; color: #ffffff!important; }
		.page-numbers li .current, .page-numbers a:hover, .widget_price_filter .ui-slider .ui-slider-range, .woocommerce-main-image.zoom .dp-wc-zoom > span > span, .wc-product-overlay .dp-wc-view > span > span, .woocommerce-main-image.zoom .dp-wc-zoom > span > span, .woocommerce-message, .woocommerce-error, .woocommerce-info, #payment div.payment_box, ul.products li.product .onsale, span.onsale {background: #5BC500!important; color: #ffffff!important; }
	</style>
	<?php endif;?>
	<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>


	<script src="<?php echo get_template_directory_uri(); ?>-Child/js/tooltip.js" type="text/javascript"></script>    
	<script src="https://use.fontawesome.com/d774ac0cb5.js"></script>
	<script type='text/javascript' src='<?php echo site_url(); ?>/wp-includes/js/jquery/ui/core.min.js?ver=1.11.4'></script>    
	<script type='text/javascript' src='<?php echo site_url(); ?>/wp-includes/js/jquery/ui/datepicker.min.js?ver=1.11.4'></script>    
	<script>
			jQuery(document).ready(function() {
			    jQuery(".odd-btn").click(function() {
			        jQuery(".locate-me").slideToggle('slow');
			    });
			    jQuery(".show-locator").click(function() {
			        jQuery(".store-locator").show(1000);
			    });
			    jQuery('.vp-a').click(function() {
			        console.log(jQuery('button.fullscreen'));
			        console.log('clicked1');
			        console.log(jQuery('button.fullscreen'));
			        jQuery('button.fullscreen').each(function() {
			            jQuery(this).click(function() {
			                console.log(jQuery(this));
			                console.log('clicked2');
			                console.log('dp-page-box',
			                    jQuery('#dp-page-box').find('section'));
			                jQuery('#dp-page-box').find('section').each(function() {
			                    jQuery(this).css('visibility', 'hidden');
			                });
			            });
			        });
			    });
			});
	</script>    
	<meta name="msvalidate.01" content="43F2391151BB4C6569AA734A940BCF79"/>    
	<meta name="google-site-verification" content="wkSnR4qmF2F7STI2w3GyFMoxUazjEgdeHY23Mrpjlkw"/>
</head>