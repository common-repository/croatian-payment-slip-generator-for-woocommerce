=== Croatian payment slip generator for WooCommerce ===
Contributors: zeko868, marlevak, ipomper, media-x
Tags: croatian payment slip, woocommerce, croatia, general payment, hrvatska, uplatnica, virman, opća uplatnica, mobilno bankarstvo
Requires PHP: 5.6
Tested up to: 5.8.3
WC requires at least: 2.6
WC tested up to: 6.3.1
Stable tag: 1.7.1
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

Make it easy for your customers from Croatia to perform direct bank transfer with generated payment slip, along with barcode for mBanking.

== Description ==

Make it easy for your customers from Croatia to perform direct bank transfer with generated payment slip, along with barcode for mBanking.

This plugin adds to the WooCommerce new payment gateway which is actually customization of Direct Bank Transfer payment option applicable for customers from the Republic of Croatia.
By installing, activating and enabling this payment gateway users are able to select payment options that offers them following:

 - generated and pre-filled payment slip document which can be downloaded and printed, and then brought to any bank or post-office for making payment
 - aforementioned payment slip also contains barcode which can be scanned through many apps for mobile banking in Croatia, thus making the payment process much faster and easier

Translations:

 - Croatian
 - English


== Requirements ==
The following PHP modules have to be installed and enabled:
 - bcmath
 - fileinfo
 - gd
 - mbstring


== Installation ==

This section describes how to install the plugin and get it working.


1. Install the plugin using WordPress plugin search under WordPress admin area or upload it manually to the `/wp-content/plugins/` directory
2. Activate the plugin through the 'Plugins' menu in WordPress admin area


== Screenshots ==

1. Additional payment option is displayed on the checkout page and can be selected.
2. After user selects that option and proceeds to the payment, image of the payment slip, filled with previously-entered customer's data, is being shown and is available for download in various formats. The same image is also sent to the customer via Email.
3. All fields (along with various other properties) can be set through settings page of this payment gateway that is located within WooCommerce Admin Dashboard.
4. All fields (along with various other properties) can be set through settings page of this payment gateway that is located within WooCommerce Admin Dashboard.
5. All fields (along with various other properties) can be set through settings page of this payment gateway that is located within WooCommerce Admin Dashboard.


== Frequently Asked Questions ==

= Where can I report bugs or contribute to the project?

Report bugs on the [issue tracker of this plugin on GitHub](https://github.com/marlevak/croatian-payment-slip-generator-for-woocommerce/issues). You can also report them in [support forum](https://wordpress.org/support/plugin/croatian-payment-slip-generator-for-woocommerce).
You can follow and join the development process of this plugin on [its GitHub repository](https://github.com/marlevak/croatian-payment-slip-generator-for-woocommerce/).

= Why aren't customers receiving e-mail messages with order details?

In case you are encountering this issue, potential cause could be because you are using some plugin that is changing default behaviour of SMTP client. If you don't want to sacrifice that plugin, the solution is to deselect the option "Display image(s) inline in e-mail message body" in the settings page of this plugin which will be cause that e-mail messages won't be sent using _PHPMailer_ module, but using alternative way. By using this approach the images won't be displayed inline in e-mail message body, yet they will be treated as regular attachments, although at least the e-mail messages will be delivered to the customers.

= How to handle order prices in different currency, so they could be converted to the prices corresponding to the currency on the payment slip?

In your `functions.php` file you should add function to the filter 'wooplatnica-croatia_order' that would perform conversion of the order price (which could be extracted from the object of class WC_Order passed as a first/only function argument) and would return instance of WC_Order class with updated field values.

== Special thanks to ==

- [Webmonster](https://webmonster.rs/) - team that developed plugin [Wooplatnica (Serbian payment slip generator for WooCommerce)](https://wordpress.org/plugins/wooplatnica/)
- [Ivan Habunek](https://github.com/ihabunek) - author of [PDF 417 barcode generator for PHP](https://github.com/ihabunek/pdf417-php)

== Changelog ==

= 1.7 =
* Add option to send e-mail messages without PHPMailer module by unselecting newly-added settings option "Display image(s) inline in e-mail message body". This could help when e-mail messages with order details aren't delivered to customers and when there are some plugins in use that are changing default behaviour of SMTP client.
* Register uninstall hook to remove plugin data and settings
* Add an action link to plugin Settings page from list of plugins
* Display translations of installed plugin info even when it's disabled

= 1.6 =
* Add selection of payment slip file formats to be available for the download. The following options are available both for e-mail attachments as well as for image displayed on the page with order details:
    * print version in PDF document
    * normal version in PDF document
    * print version as an image file
    * normal version as an image file
* Show in plugin settings only image types supported by active PHP version
* Group plugin assets by file type into corresponding subdirectories
* Fix bug with wrong price on payment slip when no decimal places
* Include codes in the text of payment intention options

= 1.5 =
* Fix preview of payment slip image on the checkout page
* Fix bug causing missing payment slip image in the e-mail message
* Fix inability to download payment slip image on Internet Explorer & Edge
* Add selection of image type for generated payment slip image
* Fix bug causing previous image from session to be attached in e-mail when custom ThankYou page is used
* Remove previous images from session which were not removed in case custom ThankYou page is used
* Update plugin dependencies to ensure compatibility with PHP version 7.3 and newer

= 1.4 =
* Add select options representing all payment models from HR00 to HR99
* Add header above group of form elements independent to any payment slip type
* Add payment slip insertion when order status is changed to the initial state

= 1.3 =
* Add more whitespace between barcode and borders of the barcode area on payment slip so laser barcode scanners can successfully load its data
* Change payment slip template image size so the payment slip when printed is of actual size as the original one
* Add option to select between national and universal payment slip type
* Add option to exclude confirmation part from payment slip
* Fix division of address components for displaying on payment slip when customer selects R1 invoice and when enters address containing ordinal number. At example, when address was "Ulica 7. gardijske brigade 4 Zagreb", that was until now split to:
	```
	Ulica 7
	. gardijske brigade 4 Zagreb
	```
	and actually it should be:
	```
	Ulica 7. gardijske brigade 4
	Zagreb
	```

= 1.2 =
* Replace order id with custom order number for payment reference number
* Display payment slip for order in order history
* Use instructions in order page instead of payment gateway description
* Display company info on payment slip when specified (if plugin for R1 invoices is installed)
* Improve performance when loading order page

= 1.1 =
* Fix value interpolation of date placeholders in callout/reference number
* Allow using placeholders like %order% in Payment description field
* Fix bug causing that the downloaded image does not have valid filetype
* Add font selection for text that won't be displayed in fields with grid

= 1.0 =
* Initial upload
