
<?php
function users_list()
{
   global $current_user;
   $current_user =  wp_get_current_user();
   echo 'User ID: ' . $current_user->ID ;
   print_r($current_user);

}
?>
<?php users_list(); ?>


    <!-- <?php echo get_current_user_id(); ?> -->

<!-- <?php
$user_id = get_current_user_id();
if ($user_id == 0) {
    echo 'You are currently not logged in.';
} else {
    echo 'You are logged in as user ' . $user_id;
}
?>  -->

<?php if (is_user_logged_in()): ?>

<?php endif;?>

<?php if ( ! current_user_can( 'manage_options' ) ):
    show_admin_bar( false );
 endif;
?>






<!-- <?php echo get_current_user_id(); ?> -->

<!-- <?php
$user_id = get_current_user_id();
if ($user_id == 0) {
echo 'You are currently not logged in.';
} else {
echo 'You are logged in as user ' . $user_id;
}
?>  -->

<!-- <?php
function users_list() {
global $current_user;
$current_user = wp_get_current_user();
echo 'User ID: ' . $current_user->ID;
print_r($current_user);

}
?>
<?php users_list();?> -->