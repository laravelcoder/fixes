

<?php if(is_shop()): ?>
    <h1>THIS IS is_shop()</h1>
<?php endif; ?>
<?php if(is_cart()): ?>
    <h1>THIS IS is_cart()</h1>
<?php endif; ?>
 <?php if(is_checkout()): ?>
    <h1>THIS IS is_checkout()</h1>
<?php endif; ?>


<?php if(function_exists('is_woocommerce') && ( is_shop()||is_cart()||is_checkout())){ ?>
<style>
.woocommerce [class*="button"], table.shop_table thead th { background: #5BC500 !important;  color:#ffffff !important;}
p.stock, span.price, p.price, table.group_table td.price span.amount, .woocommerce.box ins, .woocommerce.box span.amount, .woocommerce .star-rating span, .woocommerce-page .star-rating span { color: #5BC500; }
.woocommerce .button, table.shop_table thead th { background: #5BC500 !important; color: #ffffff !important; }
.page-numbers li .current, .page-numbers a:hover, .widget_price_filter .ui-slider .ui-slider-range, .woocommerce-main-image.zoom .dp-wc-zoom > span > span, .wc-product-overlay .dp-wc-view > span > span, .woocommerce-main-image.zoom .dp-wc-zoom > span > span, .woocommerce-message, .woocommerce-error, .woocommerce-info, #payment div.payment_box, ul.products li.product .onsale, span.onsale { background-color: #5BC500; color: #ffffff !important; }
.woocommerce .button:hover, table.cart a.remove, #content table.cart a.remove { background-color: #5BC500 !important; color: #ffffff !important; }
.product-subtotal span.amount { color: #5BC500; }
table.shop_table th { background: #fff; color: #000; }
    .woocommerce .button, table.shop_table thead th {background: #5BC500!important; color: #ffffff!important; }
    .woocommerce-info {background: #5BC500!important; color: #ffffff!important; }
    .page-numbers li .current, .page-numbers a:hover, .widget_price_filter .ui-slider .ui-slider-range, .woocommerce-main-image.zoom .dp-wc-zoom > span > span, .wc-product-overlay .dp-wc-view > span > span, .woocommerce-main-image.zoom .dp-wc-zoom > span > span, .woocommerce-message, .woocommerce-error, .woocommerce-info, #payment div.payment_box, ul.products li.product .onsale, span.onsale {background: #5BC500!important; color: #ffffff!important; }
</style>
<?php } ?>