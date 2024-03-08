** add menu
  * in functions.php
    register_nav_menu('main_menu',
    __('Main Menu',"RaddP"))'//raddp is text domain from css
  * Show or use menu
    <header>
      <?php wp_nav_menu(array('theme_location'=>'main_menu','menu_id'=>'nav'));?>
    </header>
