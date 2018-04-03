## Install wkhtmltopdf on Ubuntu

This was tested on:

- Ubuntu 14.04 x64
- Ubuntu 16.04 x64

#### Installation

```sh
sudo apt-get update
sudo apt-get install xvfb libfontconfig wkhtmltopdf
```

#### For docker 
```
RUN apt-get update && apt-get install xvfb libfontconfig wkhtmltopdf
```

#### Upddate Composer
```
composer require nahidulhasan/html2pdf
```

If laravel version is less than 5.5 , add the ServiceProvider to the providers array in config/app.php

    NahidulHasan\Html2pdf\Html2pdfServiceProvider::class,

You can optionally use the facade for shorter code. Add this to your facades:

    'Pdf'  => NahidulHasan\Html2pdf\Facades\Pdf::class,

## Basic Usage

To create PDF add something like this to one of your controllers.

```php
use NahidulHasan\Html2pdf\Facades\Pdf;

$document = Pdf::generatePdf('<h1>Test</h1>');

```
Now If you want to send mail to your client ataching pdf  then you can follow this code

```php
     /**
     * Build the message.
     *
     * @return $this
     */
    public function build()
    {
        return $this->from('username@gmail.com')
                    ->view('mails.demo')
                    ->attachData($document, ' Invoice.pdf');
    }
  
```
