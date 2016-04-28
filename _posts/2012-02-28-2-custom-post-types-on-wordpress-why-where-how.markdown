---
layout: post
title:  "[2] Custom Post Types on WordPress (Why, Where, How)"
date:   2012-02-28 12:05:00 +0000
categories: wordpress series
---

## How to create custom post types : The Basics

Custom post types sound really difficult be they are actually very simple.
This one function is all it takes for a basic custom post type:

    <?php //Register the custom post type in wordpress

    add_action(‘init’, ‘post-type_register’);
    function post-type_register()
    {

    //Define the labels so we know it’s a custom post type
    //These will show in the admin dashboard, similar to pages

    $labels = array(
    ‘name’ => _x(‘Custom Posts’, ‘post type general name’),
    ‘singular_name’ => _x(‘Custom Post’, ‘post type singular name’),
    ‘add_new’ => _x(‘Add New’, ‘custom_post’),
    ‘add_new_item’ => __(‘Add New Custom Post’),
    ‘edit_item’ => __(‘Edit Custom Post’),
    ‘new_item’ => __(‘New Custom Post’),
    ‘view_item’ => __(‘View Custom Post’),
    ‘search_items’ => __(‘Search Custom Posts’),
    ‘not_found’ => __(‘Nothing found’),
    ‘not_found_in_trash’ => __(‘Nothing found in Trash’),
    ‘parent_item_colon’ => ”
    );

    $args = array(

    ‘labels’ => $labels,
    ‘public’ => true,
    ‘publicly_queryable’ => true,
    ‘show_ui’ => true,
    ‘query_var’ => true,
    ‘rewrite’ => array(‘slug’=>’my-post’),
    ‘capability_type’ => ‘post’,
    ‘hierarchical’ => false,
    ‘menu_position’ => null,
    ‘supports’ => array(‘title’, ‘thumbnail’, ‘revisions’, ‘editor’)
    );
    register_post_type( ‘custom_post’ , $args );

    }

Just add that code into your functions.php (or an included file) and when you log into wp-admin you will see your new post type in the left hand menu. You can even use it! (if you have supported the editor ect)

Let’s look at exactly what’s going on here…

## Labels
Customise these to separate posts and custom posts in the menu

* name -> This is the general name of your custom post type
* singular_name -> This is the singular version
* add_new -> This is the text for add new shown in the menu on the left on the admin dashboard
* edit_item -> This is shown in the wp bar when a user has permission to edit the custom post they are viewing
* view_item -> This is shown when editing the post
* search_items -> This is the text in the search button on the custom posts page
* not_found -> Text shown when search returns nothing
* not_found_in_trash -> Text shown when trash search returns nothing

## Arguments
The basics we need to define a custom post type

* labels -> This is just they array above
* rewrite -> This defines how the slugs work, this can be true, false or an array containing the desired slug. If you change this make sure you refresh your permalinks
* supports -> This defines what part of the default posts you want to include. Choice of title, thumbnail, revisions and editor. By using these most of the work is done for you and keeps everything neat.

You can now get really excited about your new custom post!

However, this doesn't really give you many benefits, it just separates your posts out. Custom posts can do a lot more.

*In my next blog I'll explain in more detail how to use custom taxonomies and some adjustments to the post edit page.*
