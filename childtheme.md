**child theme
 folderName(mainthemename-child)->style.css->functions.php
** style.css
    /*
    Theme Name: mainthemename child
    Template: mainthemename
    */
** functions.php
    <?php function childtheme(){
      wp_enqueue_style('child_style', get_stylesheet_uri());
      add_action('wp_enqueue_scripts','childtheme',PHP_INT_MAX);
  
