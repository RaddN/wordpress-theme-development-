**in functions.php
  function site_custo_register($wp_customize){
    // add a new button in site customize section
    $wp_customize->add_section('raddp_header_area', // this the section id
      array(
      'title'=>__('Header Area','raddp'),//raddp for translate & Header area is menu title
      'description'=>'customize header here','priority' => 30,));

    //Show default logo
    $wp_customize->add_setting('raddp_logo',
      array(
       'default' =>get_bloginfo('template_directory').'/img/logo/png'));
    //add upload new image section
    $wp_customize->add_control(new WP_Customize_Image_Control($wp_customize,'raddp_logo',array('label'=>'Logo Upload',
        'description'=>'You can update logo here',
        'setting'=>'raddp_logo',
        'section'=>'raddp_header_area',
        )));

    // Add a color picker control
    $wp_customize->add_setting('raddp_primary_color', array(
        'default' => '#ffffff',
        'sanitize_callback' => 'sanitize_hex_color',
    ));

    //Color change
    $wp_customize->add_control( new WP_Customize_Color_Control($wp_customize,'raddp_primary_color',array('label'=>'Site Color',
      'description'=>'You can update color here',
      'setting'=>'raddp_primary_color',
      'section'=>'raddp_header_area'
   )));

  // Add a text input control
    $wp_customize->add_setting('custom_theme_text', array(
        'default' => '',
        'sanitize_callback' => 'sanitize_text_field',
    ));
     $wp_customize->add_control(new WP_Customize_Control(
        $wp_customize,
        'custom_theme_text_control',
        array(
            'label' => 'Custom Text',
            'section' => 'raddp_header_area',
            'settings' => 'custom_theme_text',
            'type' => 'text',
        )
    ));
}
add_action('customize_register','site_custo_register');


// use cutomize inputs
   <img src="<?php echo get_theme_mod('raddp_logo');?>">




















