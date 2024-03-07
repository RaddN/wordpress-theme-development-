Software
1. wampserver/xamp /n
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

         
         
  
