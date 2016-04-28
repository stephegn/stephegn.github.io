---
layout: post
title:  "[3] Custom Post Types on WordPress (Why, Where, How)"
date:   2012-03-05 22:20:00 +0000
categories: wordpress series
---

##Customising the custom posts editor

So now you have your custom post types from here the next step is to customise it so you can start adding other values. Lets take my example of microsites, I want to associate a contact email with the post type. First we need to add the text field into our edit post page.

    add_action(“admin_init”, “admin_init”);

First we define the box that it lives in. This is called a meta box, this one will appear in the sidebar.

    function admin_init()
    {
      add_meta_box(“contact_details”, “Contact Details”, “contact”, “microsite”, “side”, “low”);
    }

Here “contact_details” is the id of the meta box.

“Contact Details” is the title of the box which will appear on the edit post page.

“contact” is the name of the function which defines it

“microsite” is the name of the post type

“side” means the box will appear in the sidebar of the edit post page

“low” is the priority in which it should appear


Next we write the function that defines how the meta box is displayed. This is pretty simple.
We get the custom fields from the post using the ‘get_post_custom()’ method using the postID, then we save the field we need to a variable. This means we have the previous saved value of that field to display so the user can edit. We finally display this with normal HTML with a label and a text box.

    function contact() {
    global $post;
    $custom = get_post_custom($post->ID);
    $contact_email = $custom[“contact_email”][0];
    ?>
    <p><label>Contact Email (default:info@whichplm.com):</label><br />
    <input name=”contact_email” value=”<?php echo $contact_email; ?>” />
    <?php
    }


Finally, all we have to do is save the field again. This save_details function will do it, using the update_post_meta() method. just give it the postID, the name of the field and the value

    add_action(‘save_post’, ‘save_details’);

    function save_details()
    {
      global $post;
      update_post_meta($post->ID, “contact_email”, $_POST[“contact_email”]);
    }

And that’s it.

You can use these functions to define more than one field, more than one meta box in fact you can pretty much define exactly how you want the editor to appear. In my next blog I'll show how you can easily define how the post looks.
