<?php
// From your functions file, this code displays a personal message for logged in users.
function wpdocs_personal_message_when_logged_in() {
    if ( is_user_logged_in() ) {
        $current_user = wp_get_current_user();
        printf( 'Personal Message For %s!', esc_html( $current_user->user_firstname ) );
    } else {
        echo( 'Non-Personalized Message!' );
    }
}
add_action( 'loop_start', 'wpdocs_personal_message_when_logged_in' );



<?php
function phillips_custom_setup() {

    add_theme_support('post-thumbnails');

    // add_action('template_redirect', 'trash_redirect');
    // function trash_redirect(){
    //  if (is_404()){
    //      global $wp_query, $wpdb;
    //      $page_id = $wpdb->get_var( $wp_query->request );
    //      $post_status = get_post_status( $page_id );
    //      if($post_status == 'trash'){
    //          wp_redirect(home_url(), 301);
    //          die();
    //      }
    //  }
    // }
    // add_filter( 'woocommerce_get_availability', 'custom_override_get_availability', 1, 2);



    add_theme_support('woocommerce');






    function disableAutoSave()
    {
        wp_deregister_script('autosave');
    }
    add_action('wp_print_scripts', 'disableAutoSave');


    function scripts_styles_print_frontend() {
        global $loader;
        if ( ! is_admin() ) :
            wp_register_style('parent_main', get_template_directory_uri() . '/style.css', false);
        wp_register_style('fjalla', 'http://fonts.googleapis.com/css?family=Fjalla+One');
        wp_register_style('child_main', get_stylesheet_directory_uri() . '/style.css', array( 'parent_main','fjalla'));
        wp_enqueue_style('child_main');
        if ( is_page ( '1533' ) ):
            wp_register_style('specs', get_stylesheet_directory_uri() . '/lib/css/specs.css', array( 'parent_main'),  false, 'all');
        wp_enqueue_style('specs');
        endif;
        if ( is_page ( '1568' ) ):
            wp_register_style('features', get_stylesheet_directory_uri() . '/lib/css/features.css', array( 'parent_main'),  false, 'all');
        wp_enqueue_style('features');
        endif;
        if ( is_page ( '1148' ) ):
            wp_register_style('contact', get_stylesheet_directory_uri() . '/lib/css/contact.css', array( 'parent_main'),  false, 'all');
        wp_enqueue_style('contact');
        endif;
        if ( is_page ( '662' ) ):
            wp_register_style('responsive-home', get_stylesheet_directory_uri() . '/lib/css/responsive-home.css', array( 'parent_main', 'child_main'),  false, 'all');
        wp_enqueue_style('responsive-home');
        endif;
        wp_enqueue_style('custom', get_stylesheet_directory_uri() . '/custom.css', 20);
        endif;
        wp_enqueue_script( 'fade', get_stylesheet_directory_uri() . '/lib/js/fade.js', array('jquery' ), false, true);
        $browser = $_SERVER['HTTP_USER_AGENT'];
        global $variable_array;
        if(strpos($browser, 'MSIE') !== false) {
            wp_register_script('html5', 'http://html5shiv.googlecode.com/svn/trunk/html5.js', false, false, false );
            wp_register_script('respond', get_stylesheet_directory_uri().'/lib/js/respond.js', false, false, false );
            wp_register_script('selectivizr', get_stylesheet_directory_uri().'/lib/js/selectivizr.js', false, false, false );
            wp_enqueue_script('html5');
            wp_enqueue_script('respond');
            wp_enqueue_script('selectivizr');
        }
    }
    add_action( 'wp_enqueue_scripts','scripts_styles_print_frontend', 99 );



    function child_theme_head_script_html() { ?>
    <link href="https://plus.google.com/103254379638581092910?rel=publisher" rel="publisher" />
    <link href="https://plus.google.com/u/1/103688104445020169312?rel=author" rel="author" />
    <meta name="p:domain_verify" content="27ad1047f66fc82673d4ce92985e6739"/>

    <script src="https://apis.google.com/js/platform.js" async defer></script>

    <?php }
    add_action( 'wp_head', 'child_theme_head_script_html' );


    if (!function_exists('phillips_navigation_menus')) {
        function phillips_navigation_menus() {
            $locations = array(
                'footer' => __('Footer Menu', 'text_domain'),
                'disclosures' => __('Disclosures Menu', 'text_domain'),
                );
            register_nav_menus($locations);
        }
        add_action('init', 'phillips_navigation_menus', '999');
    }


    // function remove_footer_admin () {
    //  echo 'Fueled by <a href="http://www.qniquequilter.com" target="_blank">Qnique/a> | Designed by <a href="http://www.affordableprogrammer.com" target="_blank">Phillip Madsen</a> | Products by <a href="http://www.graceframe.com" target="_blank">The Grace Company</a></p>';
    // }
    // add_filter('admin_footer_text', 'remove_footer_admin');

    function html_tag_schema() {
        $schema = 'http://schema.org/';
        if (is_product_category()){
            $type = 'ItemPage, https://schema.org/WebPageElement, https://schema.org/ItemList';
        }
        elseif( is_singular( array( 'product' ) )  ){
            $type = 'WebPage, https://schema.org/ItemPage, https://schema.org/WebPageElement, https://www.schema.org/Product';
        }
        elseif (is_singular()) {
            $type = 'WebPage, https://schema.org/WebPageElement, https://www.schema.org/Article';
        }
        elseif (is_page(1148)) {
            $type = 'ContactPage';
        }
        elseif ( is_page ( '1370' )){
            $type = 'Place';
        }
        elseif (is_page(1457)) {
            $type = 'Place';
        }
        elseif (is_page(1456)) {
            $type = 'Place';
        }
        elseif (is_page(1454)) {
            $type = 'Place';
        }
        elseif (is_author()) {
            $type = 'ProfilePage';
        }
        elseif (is_search()) {
            $type = 'SearchResultsPage';
        }else{
            $type = 'WebPage';
        }
        echo 'itemscope="itemscope" itemtype="' . $schema . $type . '"';
    }


    function wc_rrp_product_field() {
        woocommerce_wp_text_input( array( 'id' => 'model', 'class' => 'wc_input_model short', 'label' => __( 'Model:', 'woocommerce' ) . ' ' ) );
        woocommerce_wp_text_input( array( 'id' => 'mpn', 'class' => 'wc_input_mpn short', 'label' => __( 'MPN:', 'woocommerce' ) . ' ' ) );
        woocommerce_wp_text_input( array( 'id' => 'rrp_price', 'class' => 'wc_input_price short', 'label' => __( 'MSRP', 'woocommerce' ) . ' (' . get_woocommerce_currency_symbol() . ')' ) );
        woocommerce_wp_text_input( array( 'id' => 'UPC', 'class' => 'wc_input_upc short', 'label' => __( 'UPC:', 'woocommerce' ) . ' ' ) );
    }

    function wc_rrp_save_product( $product_id ) {

        if ( defined( 'DOING_AUTOSAVE' ) && DOING_AUTOSAVE )
            return;
        if ( isset( $_POST['mpn'] ) ) {
            if ( !empty( $_POST['mpn'] ) )
                update_post_meta( $product_id, 'mpn', $_POST['mpn'] );
        } else delete_post_meta( $product_id, 'mpn' );
        if ( isset( $_POST['model'] ) ) {
            if ( !empty( $_POST['model'] ) )
                update_post_meta( $product_id, 'model', $_POST['model'] );
        } else delete_post_meta( $product_id, 'model' );
        if ( isset( $_POST['rrp_price'] ) ) {
            if ( is_numeric( $_POST['rrp_price'] ) )
                update_post_meta( $product_id, 'rrp_price', $_POST['rrp_price'] );
        } else delete_post_meta( $product_id, 'rrp_price' );
        if ( isset( $_POST['UPC'] ) ) {
            if ( is_numeric( $_POST['UPC'] ) )
                update_post_meta( $product_id, 'UPC', $_POST['UPC'] );
        } else delete_post_meta( $product_id, 'UPC' );
    }
    add_action( 'save_post', 'wc_rrp_save_product' );


    function wc_rrp_show() {
        global $product;
        if ( $product->product_type <> 'variable' ) {
            $rrp = get_post_meta( $product->id, 'rrp_price', true );
            echo '<div class="singleline woocommerce_msrp">';
            _e( 'MSRP: ', 'woocommerce' );
            echo '<span class="woocommerce-rrp-price">' . woocommerce_price( $rrp ) . '</span>';
            echo '</div>';
        }
        if ( $product->product_type <> 'variable' ) {
            $UPC = get_post_meta( $product->id, 'UPC', true );
            echo '<div itemprop="gtin13" class="singleline woocommerce_upc">';
            _e( 'UPC: ', 'woocommerce' );
            echo '<span class="woocommerce-upc-price">' . $UPC . '</span>';
            echo '</div>';
        }
        if ( $product->product_type <> 'variable' ) {
            $model = get_post_meta( $product->id, 'model', true );
            echo '<div itemscope itemtype="http://schema.org/ProductModel" class="singleline woocommerce_model">';
            _e( 'MODEL: ', 'woocommerce' );
            echo '<span itemprop="name" class="woocommerce-model-price">' . $model . '</span>';
            echo '</div>';
        }
        if ( $product->product_type <> 'variable' ) {
            $mpn = get_post_meta( $product->id, 'mpn', true );
            _e( '<span class="mpncont singleline woocommerce-mpn-price">MPN: ', 'woocommerce' );
            echo '<span itemprop="" class="hasMPN mpncont woocommerce-mpn-price">' . $mpn . '</span></span>';
        }
    }

    add_action( 'woocommerce_single_product_summary', 'wc_rrp_show', 5 );

    remove_filter("the_content", "wptexturize");
    remove_filter("the_content", "convert_chars");
















}
add_action('after_setup_theme', 'phillips_custom_setup', 30);

