---
layout: post
title:  "Finally some meta data!"
date:   2012-05-18 16:12:46 +0000
categories: flex
---

You may recall in a previous post I told of my trouble when trying to add XMP data into files. Well, I have finally implemented it and wanted to share the problems I had and how to overcome them.

I ended up using [this](http://en.alexander-block.net/Business/eZ-Systems/XMP-extension-for-PHP) php extension. I can't thank Alex enough who was able to give me a hand with it even though he wrote it over 2 years ago!

To install the extension there is a great tutorial [here](http://mattiasgeniar.be/2008/09/14/how-to-compile-and-install-php-extensions-from-source/).

The extension itself is very simple to use the documentation on it’s website. I did find however that it will only run in command line. Once I had worked that out it was pretty easy to pull everything together.

So here are the steps to pull an image (in my case an AI file) from the database, dynamically add XMP data to it and then send it to the user.

1. Create a temporary name for our file. I just keep producing random names until I find a free one. I will delete this file after use.

{% highlight php %}
    global $server;
    $fileExists = true;
    while ($fileExists)
    {
      $tempName = uniqid();
      $fileExists = file_exists($server['FILES_PUBLIC_DIRECTORY'] . "/" . $tempName . ".ai");
    }
{% endhighlight %}

2. Write our image to this file

{% highlight php %}
    $filePath = $server['FILES_PUBLIC_DIRECTORY'] . "/" . $tempName . ".ai";
    $fh = fopen($filePath, 'w');
    fwrite($fh, $productImage['ai']);
    fclose($fh);
{% endhighlight %}

3. Create somewhere to store the XMP data and store it

{% highlight php %}
    $xmpFilePath = $server['FILES_PUBLIC_DIRECTORY'] . "/" . $tempName . ".xml";
    $fh = fopen($xmpFilePath, 'w');
    fwrite($fh, $this->createXMP());
    fclose($fh);
{% endhighlight %}

(This is what my createXMP() function looks like)

{% highlight php %}
    private function createXMP()
     {
      $imageAccessor = new imageFields();
      $fieldArray = $imageAccessor->getData($id);
      foreach ($fieldArray as $field)
      {
        switch ($field->id)
        {
          case 8:
            $shortDesc = $field->data;
            break;
          case 9:
            $longDesc = $field->data;
        break;
        }
      }
      return '<x:xmpmeta xmlns:x="adobe:ns:meta/" x:xmptk="Exempi + XMP Core 4.4.0">
     <rdf:RDF xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#">
     <rdf:Description rdf:about="" xmlns:myNS="http://ns.stephcook.me">
      <myNS:ShortDesc>'.$shortDesc.'</myNS:ShortDesc>
      <myNS:LongDesc>'.$longDesc.'</myNS:LongDesc>
     </rdf:Description>
      <rdf:Description rdf:about=""
        xmlns:xmp="http://ns.adobe.com/xap/1.0/">
       <xmp:MetadataDate>2008-01-29T10:55:40-08:00</xmp:MetadataDate>
        </rdf:Description>
     </rdf:RDF>
    </x:xmpmeta>';
    }
{% endhighlight %}

It is important to note here that the bottom section of the XMP which is hardcoded here is required for this to work.

4. Now all we need to do is attach this XMP data to the file. We do this by running a unix command (because this only works in command line).

{% highlight php %}
    $xmpresult = exec('php '.$libraryAddress.'xmp_write.php '.$xmpFilePath.' '.$filePath);
{% endhighlight %}

5. This command will run a file called xmp_write.php using php. With our XMP file and the image file as arguments. This xmp_write.php file will simply run the following from the extension:

{% highlight php %}
    $xmp = file_get_contents( $argv[1] );
    xmp_can_write( $argv[2], $xmp );
    xmp_write( $argv[2], $xmp );
{% endhighlight %}

6. Now I just send the address of this file to my user, and delete the file when I'm finished. Easy!
