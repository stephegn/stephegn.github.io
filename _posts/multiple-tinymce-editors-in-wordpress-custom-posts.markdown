---
layout: post
title:  "Multiple TinyMCE Editors in WordPress Custom Posts"
date:   2012-05-21 16:29:46 +0000
categories: wordpress
---

This is a small update to my Custom Posts series which explained how to create your own custom posts.

For my custom posts I needed multiple editor boxes as there are different large areas of text to fill. Pre WordPress 3.3 I had to do this in a really clunky way with the addition of another plugin and I just wasn’t happy with it.

However, there is a massive big gleaming light at the end of the tunnel as WordPress 3.3 supports multiple instances of its default editor (TinyMCE) on the same page. All it takes are a few lines of code.

 1. We need to preload (simple one liner)
{% highlight php %}
    add_action( 'admin_print_footer_scripts', 'wp_preload_dialogs');
{% endhighlight %}

 2. We need to load tinyMCE
{% highlight php %}
    function pluginLoadTinyMCE {
        wp_tiny_mce();
    }
{% endhighlight %}
 3. Call the editor (another simple one liner)
{% highlight php %}
    <?php wp_editor( $value, 'name', $settings = array() );?>
{% endhighlight %}
Just surround this editor in whatever html you need and grab the POST['name'] variable. The editor will appear just like any other editor in default WordPress pages.

Useful Links
[wp_editor function reference](http://codex.wordpress.org/Function_Reference/wp_editor)
