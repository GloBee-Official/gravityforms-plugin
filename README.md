Gravity Forms BitPay Payment Gateway
=====================

# Brief Description

Add the ability to accept bitcoin in Gravity Forms via BitPay.

# Detail Description

Bitcoin is a powerful new peer-to-peer platform for the next generation of
financial technology. The decentralized nature of the Bitcoin network allows
for a highly resilient value transfer infrastructure, and this allows merchants
to gain greater profits.

This is because there are little to no fees for transferring Bitcoins from one
person to another. Unlike other payment methods, Bitcoin payments cannot be
reversed, so once you are paid you can ship! No waiting days for a payment to
clear.

# Requirements

* [Wordpress](https://wordpress.org/about/requirements/) >= 3.9 (Older versions may work, but we do not test against those)
* [GMP](http://php.net/manual/en/book.gmp.php) or [BCMath](http://php.net/manual/en/book.bc.php) You may have to install GMP as most servers do not come with it, but generally BCMath is already included.
* [GravityForms](http://www.gravityhelp.com/) >= 1.8.4 
* [mcrypt](http://us2.php.net/mcrypt)
* [OpenSSL](http://us2.php.net/openssl) Must be compiled with PHP
* PHP >= 5.4

# Installation

## From Downloadable Archive

Visit the [Releases](https://github.com/bitpay/gravityforms-plugin/releases/latest) page of
this repository and download the latest version. Once this is done, you can just
go to Wordpress's Adminstration Panels > Plugins > Add New > Upload Plugin, select the downloaded archive and click Install Now.
After the plugin is installed, click on Activate.

***WARNING*** It is good practice to backup your database before installing
plugins. Please make sure you create backups.

***NOTE*** Your Maximum File Upload Size located inside your php.ini may prevent you from uploading the plugin if it is less than 2MB. If this is the case just extract the contents of the Release into your Wordpress's wp-content/plugins folder.

## From source code

Run the following command to build the plugin folder:
```
./setup
```
Copy and paste the bitpay-gravityforms-plugin folder into your Wordpress's wp-content/plugins folder

# Configuration

Configuration can be done using the Administrator section of Wordpress.
Once Logged in, you will find the configuration settings under **Forms > Settings > BitPay Payments**.
Alternatively, you can also get to the configuration settings via Plugins and clicking the Settings link for this plugin.

![BitPay Settings](https://raw.githubusercontent.com/aleitner/aleitner.github.io/master/gravityforms/fullSettings2.png "BitPay Settings")

Here your will need to create a [pairing code](https://bitpay.com/api-tokens) using
your BitPay merchant account. Once you have a Pairing Code, put the code in the
Pairing Code field:

![Pairing Code field](https://raw.githubusercontent.com/aleitner/aleitner.github.io/master/gravityforms/pairingCode2.png "Pairing Code field")

On success, you'll receive a token:

![BitPay Token](https://raw.githubusercontent.com/aleitner/aleitner.github.io/master/gravityforms/paired2.png "Bitpay Token")

***NOTE*** Pairing Codes are only valid for a short period of time. If it expires
before you get to use it, you can always create a new one and pair with it.

***NOTE*** You will only need to do this once since each time you do this, the
extension will generate public and private keys that are used to identify you
when using the API.

You are also able to configure how BitPay's IPN (Instant Payment Notifications)
changes the order in your Gravity Forms store.

![Invoice Settings](https://raw.githubusercontent.com/aleitner/aleitner.github.io/master/gravityforms/transactionSpeed.png "Invoice Settings")

When an invoice is paid this is the URL that your customers are taken to.

![Redirect URL](https://raw.githubusercontent.com/aleitner/aleitner.github.io/master/gravityforms/redirectUrl.png "Redirect URL")

Save your changes and you're good to go!

# Usage

Once enabled, your customers will be able to pay with Bitcoins. Once
they checkout they are redirected to a full screen BitPay invoice to pay for
the order.

As a merchant, the orders in your Gravity Forms store can be treated as any other
order. You may need to adjust the Invoice Settings depending on your order
fulfillment.

# GMP Installation

It is highly recommended you install GMP for this plugin to acheive maximum performance.

## Compile PHP with GMP
[http://php.net/manual/en/gmp.installation.php](http://php.net/manual/en/gmp.installation.php)

## Enable Extension
If the extension has been included with your PHP install, you only need to uncomment the line in the PHP ini configuration file.

On Windows:
```ini
; From
;extension=php_gmp.dll
; To
extension=php_gmp.dll
```

On Linux:
```ini
; From
;extension=gmp.so
; To
extension=gmp.so
```

## Ubuntu
```bash
$ sudo apt-get update
$ sudo apt-get install php5-gmp
$ sudo php5enmod gmp

# Restart your server
```


# Support

## BitPay Support

* [GitHub Issues](https://github.com/bitpay/gravityforms-plugin/issues)
  * Open an issue if you are having issues with this plugin.
* [Support](https://support.bitpay.com)
  * BitPay merchant support documentation

## Gravity Forms Support

* [Homepage](http://www.gravityforms.com/)
* [Documentation](http://www.gravityhelp.com/documentation/page/Gravity_Forms_Documentation)
* [Support](http://www.gravityhelp.com/support/)

# Troubleshooting

1. Ensure a valid SSL certificate is installed on your server. Also ensure your
   root CA cert is updated. If your CA cert is not current, you will see curl
   SSL verification errors.
2. Verify that your web server is not blocking POSTs from servers it may not
   recognize. Double check this on your firewall as well, if one is being used.
3. Check the version of this plugin against the official plugin repository to
   ensure you are using the latest version. Your issue might have been
   addressed in a newer version! See the [Releases](https://github.com/bitpay/gravityforms-plugin/releases)
   page for the latest.
4. If all else fails, send an email describing your issue **in detail** to
   support@bitpay.com

***TIP***: When contacting support it will help us is you provide:

* WordPress and Gravity Forms Version
* Other plugins you have installed
  * Some plugins do not play nice
* Configuration settings for the plugin (Most merchants take screen grabs)
* Any log files that will help
  * Web server error logs
* Screen grabs of error message if applicable.

# Contribute

To contribute to this project, please fork and submit a pull request.

# License

The MIT License (MIT)

Copyright (c) 2011-2015 BitPay, Inc.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
