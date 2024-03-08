** woocommerce-setup-in-theme
in functions.php
    check woocommerce is active or not
    if(class_exists('Woocommerce')){
    include_once 'inc/wc-setup.php';
    }
inc/wc-setup.php
function woocommerce_setup(){
  add_theme_support('woocommerce',
      array(
        'thumbnail_image_width'=>150,
        'single_image_width'=>200,
        //product show in grid style
        'product_grid'=>array(
          'default_columns'=>10,
          'min_columns'=>2,
          'max_columns'=>3
        )
        ));
    add_theme_support("wc_product_gallery_zoom");
    add_theme_support("wc_product_gallery_lightbox");
    add_theme_support("wc_product_gallery_slider");
  }
  add_action("after_setup_theme','woocommerce_setup');
  root->woocommerce->archive-product.php
  also create single-product.php
**in archive-product.php
  get all file and copy past from template woocommerce archive-product.php

  
