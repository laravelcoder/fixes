

<?php
if ( is_user_logged_in() ) {
    echo 'Welcome, registered user!';
} else {
    echo 'Welcome, visitor!';
}
?>

<?php if ( is_user_logged_in() ) { ?>
    <a href="<?php echo wp_logout_url(); ?>">Logout</a>
<?php } else { ?>
    <a href="/wp-login.php" title="Members Area Login" rel="home">Members Area</a>
<?php } ?>


<?php if ( ! is_admin() ) {
     echo "You are viewing the theme";
} else {
     echo "You are viewing the WordPress Administration Panels";
} ?>




<?php if (!is_admin()) {
    echo "You are viewing the theme";
} else {
    echo "You are viewing the WordPress Administration Panels";
}?>
if ( ! current_user_can( 'manage_options' ) ):
    show_admin_bar( false );
endif;

<?php
if(is_user_logged_in()):
    $user = wp_get_current_user();
    if (current_user_can( 'manage_options' )):
     echo "You are viewing as an administrator";
    else:
     echo "You are not viewing as an administrator";
    endif;
endif;
?>


     <?php if (is_user_logged_in()):
    $user = wp_get_current_user();
    if (current_user_can('manage_options')):
        echo "You are viewing as an administrator";
        //else:
        //echo "You are not viewing as an administrator";
    endif;
endif;
?>

