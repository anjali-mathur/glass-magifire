##maginifire glass oom and fancy box on product page

        <div class="product-single__photos grid pull-grid">
          {% assign featured_image = current_variant.featured_image | default: product.featured_image %}
          {% comment %}
          Display current variant image, or default first
          {% endcomment %}
          <div class="product-single__photo-wrapper grid__item large--ten-twelfths">

            <img class="product-single__photo img1 fancybox"rel="gallery1"
                 id="ProductPhotoImg"
                 src="{{ featured_image | img_url: 'original' }}"
                 alt="{{ featured_image.alt | escape }}" data-image-id="{{ featured_image.id }}" data-zoom-image="{{ featured_image | img_url: 'master' }}">

          </div>
          <div class="grid__item large--two-twelfths">
            <ul class="thumbnails" id="gallery_01">
              {% comment %}
              Display rest of product images, not repeating the featured one
              {% endcomment %}
              {% for image in product.images %}
              {% unless image contains featured_image %}
              <li class="product-single__photo-wrapper">
                <a class="active fancybox" rel="gallery1" href="{{ image.src | img_url: 'original' }}" data-image="{{ image.src | img_url: 'original' }}" data-zoom-image="{{ image.src | img_url: 'master' }}" >
                  <img class="product-single__photo" src="{{ image.src | img_url: 'compact' }}"
                       alt="{{ image.alt | escape }}"
                       data-image-id="{{ image.id }}">
                </a>
              </li>
              {% endunless %}
              {% endfor %}
            </ul>
          </div>
        </div>
 

       
                <script>
                  jQuery(window).load(function() { 
                    jQuery('.thumbnails .owl-wrapper .owl-item').first().find('a').addClass('zoomGalleryActive');


                    jQuery(".thumbnails").owlCarousel({
                      itemsCustom : [
                        [320, 3],
                        [767, 3],
                        [768, 3],
                        [992, 3],
                        [1024, 3],
                        [1025, 4],
                        [1600, 4]
                      ],
                      pagination : true,
                      navigation : true,
                      navigationText : ['<i class="cs-font clever-icon-prev"></i>','<i class="cs-font clever-icon-next"></i>']
                    });
                  });
                </script>
