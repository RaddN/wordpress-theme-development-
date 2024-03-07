Software
1. wampserver/xamp /n
2. wordpress download /n
Theme=>new folder(no space) => index.php => style.css=> screenshot.png(1200*900) /n
**add in style.css /n
/*===== (no space) /n
    Theme Name:RaddP /n
    Theme URI:# /n
    Version:1.0.0 /n
    Author:Raihan Hossain /n
    Author URI:raihandevzone.com /n
    Text Domain:RaihanHossain /n
    Description:Raihan bla bla bla /n
    Tags:one,two,three /n
    License:GNU General Public License v2 or later /n
    License URI:http://www.gnu.org/licenses/gpl-2.0.html /n
    Requires at least:4.9.6 /n
    Requires PHP:5.2.4 /n
    Tested up to:5.8 /n
    =====*/ /n
**add in index.php /n
        <?php /n
          /* /n
          * This template for displaying the header /n
          */ /n
          ?> /n
          <!DOCTYPE html> /n
          <html lang="<php echo language_attributes();?>" class="no-js"> /n
          <head> /n
            <meta charset = "<?php bloginfo('charset')?>"> /n
            <meta http-equiv="X-UA-Compatible" content = "IE-edge"> /n
            <meta name="viewport" content="width=device-width,initial-scale=1.0"> /n
          </head> /n 
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
               add_action('login_enqueue_scripts','login_logo_change'); /n
   ** custom login Page create /n
       **in custom-login-page.php/n
                   <?php/n
            /**/n
            * Template Name: Custom Login Page/n
            *//n
            get_header();/n
            if ( ! is_user_logged_in() ) {/n
                $args = array/n
                    'redirect' => admin_url(), // redirect to admin dashboard./n
                    'form_id' => 'custom_loginform',/n
                    'label_username' => __( 'Username:' ),/n
                    'label_password' => __( 'Password:' ),/n
                    'label_remember' => __( 'Remember Me' ),/n
                    'label_log_in' => __( 'Log Me In' ),/n
                     'remember' => true/n
                );/n
            wp_login_form( $args );/n
            }/n
            get_footer();/n
   ***edirect wp-login.php to Custom Login Page/n
 ** in functions.php/n
       function redirect_login_page() {/n
        $login_url  = home_url( '/login' );/n
        $url = basename($_SERVER['REQUEST_URI']); // get requested URL/n
        isset( $_REQUEST['redirect_to'] ) ? ( $url   = "wp-login.php" ): 0; // if users ssend request to wp-admin/n
        if( $url  == "wp-login.php" && $_SERVER['REQUEST_METHOD'] == 'GET')  {/n
            wp_redirect( $login_url );/n
            exit;/n
        }/n
    }/n
    add_action('init','redirect_login_page');/n
   function error_handler() {/n
    $login_page  = home_url( '/login' );/n
    global $errors;/n
    $err_codes = $errors->get_error_codes(); // get WordPress built-in error codes/n
    $_SESSION["err_codes"] =  $err_codes;/n
    wp_redirect( $login_page ); // keep users on the same page/n
    exit;/n
    }/n
    add_filter( 'login_errors', 'error_handler');/n
** in custom_login_page.php/n
   $err_codes = isset( $_SESSION["err_codes"] )? $_SESSION["err_codes"] : 0;/n
    if( $err_codes !== 0 ){/n
        echo display_error_message(  $err_codes );/n
}/n
function display_error_message( $err_code ){/n
    // Invalid username./n
    if ( in_array( 'invalid_username', $err_code ) ) {/n
        $error = '<strong>ERROR</strong>: Invalid username.';/n
    }/n
    // Incorrect password./n
    if ( in_array( 'incorrect_password', $err_code ) ) {/n
        $error = '<strong>ERROR</strong>: The password you entered is incorrect.';/n
    }/n
    // Empty username./n
    if ( in_array( 'empty_username', $err_code ) ) {/n
        $error = '<strong>ERROR</strong>: The username field is empty.';/n
    }/n
    // Empty password./n
    if ( in_array( 'empty_password', $err_code ) ) {/n
        $error = '<strong>ERROR</strong>: The password field is empty.';/n
    }/n
    // Empty username and empty password./n
    if( in_array( 'empty_username', $err_code )  &&  in_array( 'empty_password', $err_code )){/n
        $error = '<strong>ERROR</strong>: The username and password are empty.';/n
    }/n
    return $error;/n
    }/n
   

   
           

         
         
  
