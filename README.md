Software
1. wampserver/xamp 
2. wordpress download 
Theme=>new folder(no space) => index.php => style.css=> screenshot.png(1200*900) 
**add in style.css 
/*===== (no space) 
    Theme Name:RaddP 
    Theme URI:# 
    Version:1.0.0 
    Author:Raihan Hossain 
    Author URI:raihandevzone.com 
    Text Domain:RaihanHossain 
    Description:Raihan bla bla bla 
    Tags:one,two,three 
    License:GNU General Public License v2 or later 
    License URI:http://www.gnu.org/licenses/gpl-2.0.html 
    Requires at least:4.9.6 
    Requires PHP:5.2.4 
    Tested up to:5.8 
    =====*/ 
**add in index.php 
        <?php 
          /* 
          * This template for displaying the header 
          */ 
          ?> 
          <!DOCTYPE html> 
          <html lang="<php echo language_attributes();?>" class="no-js"> 
          <head> 
            <meta charset = "<?php bloginfo('charset')?>"> 
            <meta http-equiv="X-UA-Compatible" content = "IE-edge"> 
            <meta name="viewport" content="width=device-width,initial-scale=1.0"> 
          </head>  
  ** add in functions.php
            <?php
            /*php
            * My theme function
            // Theme Title
            add_theme_support('title-tag');
  **continue in index.php:
           <?php wp_head();?>
           </head>
           <body <?php body-class();?>>
           <php get_header();?>
           <?php the_content();?>
           <?php get_footer();?>
           <?php wp_footer();?>
           </body>
           </html>
   ** VS Extension
       1. Wordpress development
       2. Wordpress development toolbox
       3. php intelephense
       4. woocommerce-snippets & auto complete
       5. autocomplete wordpress hooks
   ** css & js file calling
       ** in functions.php
             //Theme css & js file calling
               function css_js_file_calling(){
               wp_enqueue_style('ali_style',get_stylesheet_uric()); //default style.css calling
               wp_register_style('bootstrap',get_template_directory_uri().'/css/bootstrap.css',array(),'5.0.2','all');
               wp_enqueue_style('bootstrap');
             // Jquery
               wp_enqueue_script('jquery');
             // js
               wp_enqueue_script('bootstrap',get_template_directory_uri().'/js/bootstrap.js',array().'5.0.2','true');
             }
             add_action('wp_enqueue_scripts','css_js_file_calling');
   **img in body:
         <img src="<?php echo get_template_directory_uri();?>/img/logo.phg">
   ** custom login page
         *in functions.php
             include_once('inc/login_enqueue.php');
         *in login_enqueue.php
             <?php
               function login_enqueue_register(){
                   wp_enqueue_style('login_enqueue',get_stylesheet_directory_uri()./css/login_enqueue.css',array(),'1.0.0','all';
               }
                 add_action('login_enqueue_scripts','login_enqueue_register');
         *login_enqueue.css:
           body.login{background:red;}
         *inc/login_enqueue.php:
             //changing logo of wordpress
               function logo_change(){
             ?>
               <style>
                   #login h1 a,.login h1 a{
                     background_image:url(<?php print get_stylesheet_directory_uri();?>../img/logo-small.png);
                   }
               </style>
               <?php
               add_action('login_enqueue_scripts','login_logo_change'); 
   ** custom login Page create 
       **in custom-login-page.php
                   <?php
            /**
            * Template Name: Custom Login Page
            */
            get_header();
            if ( ! is_user_logged_in() ) {
                $args = array
                    'redirect' => admin_url(), // redirect to admin dashboard.
                    'form_id' => 'custom_loginform',
                    'label_username' => __( 'Username:' ),
                    'label_password' => __( 'Password:' ),
                    'label_remember' => __( 'Remember Me' ),
                    'label_log_in' => __( 'Log Me In' ),
                     'remember' => true
                );
            wp_login_form( $args );
            }
            get_footer();
   ***edirect wp-login.php to Custom Login Page
 ** in functions.php
       function redirect_login_page() {
        $login_url  = home_url( '/login' );
        $url = basename($_SERVER['REQUEST_URI']); // get requested URL
        isset( $_REQUEST['redirect_to'] ) ? ( $url   = "wp-login.php" ): 0; // if users ssend request to wp-admin
        if( $url  == "wp-login.php" && $_SERVER['REQUEST_METHOD'] == 'GET')  {
            wp_redirect( $login_url );
            exit;
        }
    }
    add_action('init','redirect_login_page');
   function error_handler() {
    $login_page  = home_url( '/login' );
    global $errors;
    $err_codes = $errors->get_error_codes(); // get WordPress built-in error codes
    $_SESSION["err_codes"] =  $err_codes;
    wp_redirect( $login_page ); // keep users on the same page
    exit;
    }
    add_filter( 'login_errors', 'error_handler');
** in custom_login_page.php
   $err_codes = isset( $_SESSION["err_codes"] )? $_SESSION["err_codes"] : 0;
    if( $err_codes !== 0 ){
        echo display_error_message(  $err_codes );
}
function display_error_message( $err_code ){
    // Invalid username.
    if ( in_array( 'invalid_username', $err_code ) ) {
        $error = '<strong>ERROR</strong>: Invalid username.';
    }
    // Incorrect password.
    if ( in_array( 'incorrect_password', $err_code ) ) {
        $error = '<strong>ERROR</strong>: The password you entered is incorrect.';
    }
    // Empty username.
    if ( in_array( 'empty_username', $err_code ) ) {
        $error = '<strong>ERROR</strong>: The username field is empty.';
    }
    // Empty password.
    if ( in_array( 'empty_password', $err_code ) ) {
        $error = '<strong>ERROR</strong>: The password field is empty.';
    }
    // Empty username and empty password.
    if( in_array( 'empty_username', $err_code )  &&  in_array( 'empty_password', $err_code )){
        $error = '<strong>ERROR</strong>: The username and password are empty.';
    }
    return $error;
    }
   

   
           

         
         
  
