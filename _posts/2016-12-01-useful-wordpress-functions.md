---
layout: post
title:  "Useful WordPress Functions"
author: vijayan
categories: [ WordPress ]
tags: [ WordPress, WP Function ]
image: assets/images/2016/12/Useful-WordPress-Functions.png
description: "This is a list of useful WordPress functions that I often reference to enhance or clean up my sites. Please be careful and make backups."
---
<h2>WordPress Functions</h2>
This is a list of useful WordPress functions that I often reference to enhance or clean up my sites. Please be careful and make backups.
<h2>Hide WordPress Update Nag to All But Admins</h2>
<pre class="lang:default decode:true " title="Hide WordPress Update Nag to All But Admins">// Hide WordPress Update Nag to All But Admins
function hide_update_notice_to_all_but_admin() {
    if ( !current_user_can( 'update_core' ) ) {
        remove_action( 'admin_notices', 'update_nag', 3 );
    }
}
add_action( 'admin_head', 'hide_update_notice_to_all_but_admin', 1 );</pre>
<h2>Create Proper WordPress Titles</h2>
<em>Update</em>: As of WP 4.1, the long version is no longer required - simply add the following to functions.php and remove the <code>&lt;title&gt;</code> tag from your header.
<pre class="lang:default decode:true" title="Create Proper WordPress Titles">// Create Proper WordPress Titles
add_theme_support( 'title-tag' );</pre>
<h2>Create Custom WordPress Dashboard Widget</h2>
<pre class="lang:default decode:true " title="Create Custom WordPress Dashboard Widget">// Create Custom WordPress Dashboard Widget
function dashboard_widget_function() {
    echo '
        &lt;h2&gt;Custom Dashboard Widget&lt;/h2&gt;
        &lt;p&gt;Custom content here&lt;/p&gt;
    ';
}

function add_dashboard_widgets() {
    wp_add_dashboard_widget( 'custom_dashboard_widget', 'Custom Dashoard Widget', 'dashboard_widget_function' );
}
add_action( 'wp_dashboard_setup', 'add_dashboard_widgets' );</pre>
<h2>Remove All Dashboard Widgets</h2>
<pre class="lang:default decode:true " title="Remove All Dashboard Widgets">// Remove All Dashboard Widgets
function remove_dashboard_widgets() {
    global $wp_meta_boxes;
    unset( $wp_meta_boxes['dashboard']['side']['core']['dashboard_quick_press'] );
    unset( $wp_meta_boxes['dashboard']['normal']['core']['dashboard_incoming_links'] );
    unset( $wp_meta_boxes['dashboard']['normal']['core']['dashboard_right_now'] );
    unset( $wp_meta_boxes['dashboard']['normal']['core']['dashboard_plugins'] );
    unset( $wp_meta_boxes['dashboard']['normal']['core']['dashboard_recent_drafts'] );
    unset( $wp_meta_boxes['dashboard']['normal']['core']['dashboard_recent_comments'] );
    unset( $wp_meta_boxes['dashboard']['side']['core']['dashboard_primary'] );
    unset( $wp_meta_boxes['dashboard']['side']['core']['dashboard_secondary'] );
    remove_meta_box( 'dashboard_activity', 'dashboard', 'normal' );
}
add_action( 'wp_dashboard_setup', 'remove_dashboard_widgets' );</pre>
<h2>Insert Custom Login Logo</h2>
<pre class="lang:default decode:true " title="Insert Custom Login Logo">// Insert Custom Login Logo
function custom_login_logo() {
    echo '
        &lt;style&gt;
            .login h1 a { background-image: url(image.jpg) !important; background-size: 234px 67px; width:234px; height:67px; display:block; }
        &lt;/style&gt;
    ';
}
add_action( 'login_head', 'custom_login_logo' );</pre>
<h2>Modify Admin Footer Text</h2>
<pre class="lang:default decode:true " title="Modify Admin Footer Text">// Modify Admin Footer Text
function modify_footer() {
    echo 'Created by &lt;a href="https://www.techpulsetoday.com/" target=_blank&gt;TechPulseToday&lt;/a&gt;.';
}
add_filter( 'admin_footer_text', 'modify_footer' );</pre>
<h2>Enqueue Styles and Scripts</h2>
<pre class="lang:default decode:true " title="Enqueue Styles and Scripts">// Enqueue Styles and Scripts
function custom_scripts() {
    wp_enqueue_style( 'bootstrap', get_template_directory_uri() . '/css/bootstrap.min.css', array(), '3.3.6' );
    wp_enqueue_style( 'style', get_template_directory_uri() . '/css/style.css' );
    wp_enqueue_script( 'bootstrap', get_template_directory_uri() . '/js/bootstrap.min.js', array('jquery'), '3.3.6', true );
    wp_enqueue_script( 'script', get_template_directory_uri() . '/js/script.js' );
}

add_action( 'wp_enqueue_scripts', 'custom_scripts' );</pre>
<h2>Enqueue Google Fonts</h2>
<pre class="lang:default decode:true " title="Enqueue Google Fonts">// Enqueue Google Fonts
function google_fonts() {
                wp_register_style( 'OpenSans', '//fonts.googleapis.com/css?family=Open+Sans:400,600,700,800' );
                wp_enqueue_style( 'OpenSans' );
        }
    wp_register_style( 'OpenSans', 'http://fonts.googleapis.com/css?family=Open+Sans:400,600,700,800' );
    wp_enqueue_style( 'OpenSans' );
}

add_action( 'wp_print_styles', 'google_fonts' );</pre>
<h2>Modify Excerpt Length</h2>
<pre class="lang:default decode:true " title="Modify Excerpt Length">// Modify Excerpt Length
function custom_excerpt_length( $length ) {
    return 25;
}
add_filter( 'excerpt_length', 'custom_excerpt_length', 999 );</pre>
<h2>Change Read More Link</h2>
<pre class="lang:default decode:true " title="Change Read More Link">// Change Read More Link
function custom_read_more_link() {
    return '&lt;a href="' . get_permalink() . '"&gt;Read More&lt;/a&gt;';
}
add_filter( 'the_content_more_link', 'custom_read_more_link' );</pre>
<h2>Change More Excerpt</h2>
<pre class="lang:default decode:true " title="Change More Excerpt">// Change More Excerpt
function custom_more_excerpt( $more ) {
    return '...';
}
add_filter( 'excerpt_more', 'custom_more_excerpt' );</pre>
<h2>Disable Emoji Mess</h2>
<pre class="lang:default decode:true " title="Disable Emoji Mess">// Disable Emoji Mess
function disable_wp_emojicons() {
    remove_action( 'admin_print_styles', 'print_emoji_styles' );
    remove_action( 'wp_head', 'print_emoji_detection_script', 7 );
    remove_action( 'admin_print_scripts', 'print_emoji_detection_script' );
    remove_action( 'wp_print_styles', 'print_emoji_styles' );
    remove_filter( 'wp_mail', 'wp_staticize_emoji_for_email' );
    remove_filter( 'the_content_feed', 'wp_staticize_emoji' );
    remove_filter( 'comment_text_rss', 'wp_staticize_emoji' );
    add_filter( 'tiny_mce_plugins', 'disable_emojicons_tinymce' );
}
add_action( 'init', 'disable_wp_emojicons' );
function disable_emojicons_tinymce( $plugins ) {
    if ( is_array( $plugins ) ) {
        return array_diff( $plugins, array( 'wpemoji' ) );
    } else {
        return array();
    }
}</pre>
<h2>Remove Comments</h2>
<pre class="lang:default decode:true " title="Remove Comments">// Removes from admin menu
add_action( 'admin_menu', 'my_remove_admin_menus' );
function my_remove_admin_menus() {
    remove_menu_page( 'edit-comments.php' );
}
// Removes from post and pages
add_action( 'init', 'remove_comment_support', 100 );
function remove_comment_support() {
    remove_post_type_support( 'post', 'comments' );
    remove_post_type_support( 'page', 'comments' );
}
// Removes from admin bar
function mytheme_admin_bar_render() {
    global $wp_admin_bar;
    $wp_admin_bar-&gt;remove_menu( 'comments' );
}
add_action( 'wp_before_admin_bar_render', 'mytheme_admin_bar_render' );</pre>
<h2>Change Media Gallery URL</h2>
<pre class="lang:default decode:true " title="Change Media Gallery URL&#96;">// Change Media Gallery URL
update_option( 'upload_url_path', 'http://s3.website.com/wp-content/uploads' );</pre>
<h2>Create Custom Thumbnail Size</h2>
<pre class="lang:default decode:true" title="Create Custom Thumbnail Size">// Add 250 x 250 Custom Thumbnail Size
add_image_size( 'custom-thumbnail', 250, 250, true );</pre>
<strong>Retrieve Thumbnail</strong>
<pre class="lang:default decode:true" title="Retrieve Thumbnail">&lt;?php $thumb = wp_get_attachment_image_src( get_post_thumbnail_id($post-&gt;ID), 'custom-thumbnail' );

 echo $thumb[0]; ?&gt;</pre>
Since WordPress 4.4.0 you can use:
<pre class="lang:default decode:true ">the_post_thumbnail_url( $size );</pre>
<h2>Add Categories for Attachments</h2>
<pre class="lang:default decode:true " title="Add Categories for Attachments">// Add Categories for Attachments
function add_categories_for_attachments() {
    register_taxonomy_for_object_type( 'category', 'attachment' );
}
add_action( 'init' , 'add_categories_for_attachments' );</pre>
<h2>Add Tags for Attachments</h2>
<pre class="lang:default decode:true " title="Add Tags for Attachments">// Add Tags for Attachments
function add_tags_for_attachments() {
    register_taxonomy_for_object_type( 'post_tag', 'attachment' );
}
add_action( 'init' , 'add_tags_for_attachments' );</pre>
<h2>Add Custom Excerpt to Pages</h2>
<pre class="lang:default decode:true " title="Add Custom Excerpt to Pages">// Add Custom Excerpt to Pages
function add_page_excerpt() {
    add_post_type_support( 'page', array( 'excerpt' ) );
}
add_action( 'init', 'add_page_excerpt' );</pre>
<h2>Create a Global String</h2>
<pre class="lang:default decode:true " title="Create a Global String">// Create a Global String
function global_string() {
    return 'String';
}</pre>
<strong>Retrieve Field</strong>
<pre class="lang:default decode:true " title="Retrieve Field">&lt;?php echo global_string(); ?&gt;</pre>
<h2>Support Featured Images</h2>
<pre class="lang:default decode:true " title="Support Featured Images">// Support Featured Images
add_theme_support( 'post-thumbnails' );</pre>
<h2>Support Search Form</h2>
<pre class="lang:default decode:true " title="Support Search Form">// Support Search Form
add_theme_support( 'html5', array( 'search-form' ) );</pre>
<h2>Excluding pages from search</h2>
<pre class="lang:default decode:true " title="Excluding pages from search">// Excluding pages from search
function exclude_pages_from_search() {
    global $wp_post_types;
    $wp_post_types['page']-&gt;exclude_from_search = true;
}
add_action( 'init', 'exclude_pages_from_search' );</pre>
<h2>Disable xmlrpc.php</h2>
<pre class="lang:default decode:true " title="Disable xmlrpc.php">// Disable XML RPC
add_filter( 'xmlrpc_enabled', '__return_false' );
remove_action( 'wp_head', 'rsd_link' );
remove_action( 'wp_head', 'wlwmanifest_link' );</pre>
<h2>Escape HTML in Posts</h2>
<pre class="lang:default decode:true " title="Escape HTML in Posts">// Escape HTML in &lt;code&gt; or &lt;pre&gt;&lt;code&gt; tags.
function escapeHTML($arr) {
    if (version_compare(PHP_VERSION, '5.2.3') &gt;= 0) {
        $output = htmlspecialchars($arr[2], ENT_NOQUOTES, get_bloginfo('charset'), false);
    }
    else {
        $specialChars = array(
            '&amp;' =&gt; '&amp;amp;',
            '&lt;' =&gt; '&amp;lt;',
            '&gt;' =&gt; '&amp;gt;'
        );

        // decode already converted data
        $data = htmlspecialchars_decode( $arr[2] );
        // escapse all data inside &lt;pre&gt;
        $output = strtr( $data, $specialChars );
    }
    if (! empty($output)) {
        return  $arr[1] . $output . $arr[3];
    }   else    {
        return  $arr[1] . $arr[2] . $arr[3];
    }
}
function filterCode($data) { // Uncomment if you want to escape anything within a &lt;pre&gt; tag
    //$modifiedData = preg_replace_callback( '@(&lt;pre.*&gt;)(.*)(&lt;\/pre&gt;)@isU', 'escapeHTML', $data );
    $modifiedData = preg_replace_callback( '@(&lt;code.*&gt;)(.*)(&lt;\/code&gt;)@isU', 'escapeHTML', $data );
    $modifiedData = preg_replace_callback( '@(&lt;tt.*&gt;)(.*)(&lt;\/tt&gt;)@isU', 'escapeHTML', $modifiedData );

    return $modifiedData;
}
add_filter( 'content_save_pre', 'filterCode', 9 );
add_filter( 'excerpt_save_pre', 'filterCode', 9 );</pre>
Modified from <a href="https://wordpress.org/plugins/escape-html/">Escape HTML</a>.
<h2>Create Custom Global Settings</h2>
<pre class="lang:default decode:true " title="Create Custom Global Settings">// Create Custom Global Settings
function custom_settings_page() { ?&gt;
    &lt;div class="wrap"&gt;
    &lt;h1&gt;Custom Settings&lt;/h1&gt;
    &lt;form method="post" action="options.php"&gt;
        &lt;?php
            settings_fields( 'section' );
            do_settings_sections( 'theme-options' );
            submit_button();
        ?&gt;
    &lt;/form&gt;
    &lt;/div&gt;
&lt;?php }

function custom_settings_add_menu() {
    add_theme_page( 'Custom Settings', 'Custom Settings', 'manage_options', 'custom-settings', 'custom_settings_page', null, 99 );
}
add_action( 'admin_menu', 'custom_settings_add_menu' );

// Example setting
function setting_twitter() { ?&gt;
    &lt;input type="text" name="twitter" id="twitter" value="&lt;?php echo get_option('twitter'); ?&gt;" /&gt;
&lt;?php }

function custom_settings_page_setup() {
    add_settings_section( 'section', 'All Settings', null, 'theme-options' );
    add_settings_field( 'twitter', 'Twitter Username', 'setting_twitter', 'theme-options', 'section' );
    register_setting( 'section', 'twitter' );
}
add_action( 'admin_init', 'custom_settings_page_setup' );</pre>
<strong>Retrieve Field</strong>
<pre class="lang:default decode:true ">&lt;?php echo get_option( 'twitter' ); ?&gt;</pre>
Modified from <a href="http://www.sitepoint.com/create-a-wordpress-theme-settings-page-with-the-settings-api/">Create a WordPress Theme Settings Page with the Settings API</a>.
<h2>Remove WordPress Admin Bar</h2>
<pre class="lang:default decode:true " title="Remove WordPress Admin Bar">function remove_admin_bar() {
    remove_action( 'wp_head', '_admin_bar_bump_cb' );
}
add_action( 'get_header', 'remove_admin_bar' );</pre>
<h2>Add Open Graph Meta Tags</h2>
<pre class="lang:default decode:true " title="Add Open Graph Meta Tags">// Add Open Graph Meta Tags
function meta_og() {
    global $post;
    if ( is_single() ) {
        if(has_post_thumbnail($post-&gt;ID)) {
            $img_src = wp_get_attachment_image_src(get_post_thumbnail_id( $post-&gt;ID ), 'thumbnail');
        } 
        $excerpt = strip_tags($post-&gt;post_content);
        $excerpt_more = '';
        if (strlen($excerpt) &gt; 155) {
            $excerpt = substr($excerpt,0,155);
            $excerpt_more = ' ...';
        }
        $excerpt = str_replace('"', '', $excerpt);
        $excerpt = str_replace("'", '', $excerpt);
        $excerptwords = preg_split('/[\n\r\t ]+/', $excerpt, -1, PREG_SPLIT_NO_EMPTY);
        array_pop($excerptwords);
        $excerpt = implode(' ', $excerptwords) . $excerpt_more;
        ?&gt;
&lt;meta name="author" content="Your Name"&gt;
&lt;meta name="description" content="&lt;?php echo $excerpt; ?&gt;"&gt;
&lt;meta property="og:title" content="&lt;?php echo the_title(); ?&gt;"&gt;
&lt;meta property="og:description" content="&lt;?php echo $excerpt; ?&gt;"&gt;
&lt;meta property="og:type" content="article"&gt;
&lt;meta property="og:url" content="&lt;?php echo the_permalink(); ?&gt;"&gt;
&lt;meta property="og:site_name" content="Your Site Name"&gt;
&lt;meta property="og:image" content="&lt;?php echo $img_src[0]; ?&gt;"&gt;
&lt;?php
    } else {
            return;
    }
}
add_action('wp_head', 'meta_og', 5);</pre>
<h2>Add Custom Post Type</h2>
<pre class="lang:default decode:true " title="Add Custom Post Type">// Create Custom Post Type
function create_custom_post() {
    register_post_type('custom-post', // slug for custom post type
        array(
        'labels' =&gt; array(
            'name' =&gt; __('Custom Post'),
        ),
        'public' =&gt; true,
        'hierarchical' =&gt; true, 
        'has_archive' =&gt; true,
        'supports' =&gt; array(
            'title',
            'editor',
            'excerpt',
            'thumbnail'
        ), 
        'can_export' =&gt; true,
        'taxonomies' =&gt; array(
                'post_tag',
                'category'
        )
    ));
}
add_action('init', 'create_custom_post');</pre>
<h2>Implement Preconnect to Google Fonts in Themes</h2>
<pre class="lang:default decode:true " title="Implement Preconnect to Google Fonts in Themes">function twentyfifteen_resource_hints( $urls, $relation_type ) {
    // Checks whether the subject is carrying the source of fonts google and the `$relation_type` equals preconnect.
    // Replace `enqueue_font_id` the `ID` used in loading the source.
    if ( wp_style_is( 'enqueue_font_id', 'queue' ) &amp;&amp; 'preconnect' === $relation_type ) {
        // Checks whether the version of WordPress is greater than or equal to 4.7
        // to ensure conmpatibilidade with older versions
        // because the 4.7 has become necessary to return an array instead of string
        if ( version_compare( $GLOBALS['wp_version'], '4.7-alpha', '&gt;=' ) ) {
            // Array with url google fonts and crossorigin
            $urls[] = array(
                'href' =&gt; 'https://fonts.gstatic.com',
                'crossorigin',
            );
        } else {
            // String with url google fonts
            $urls[] = 'https://fonts.gstatic.com';
        }
    }
    return $urls;
}
add_filter( 'wp_resource_hints', 'twentyfifteen_resource_hints', 10, 2 );</pre>
<h2>Add Thumbnail Column to Post Listing</h2>
<pre class="lang:default decode:true " title="Add Thumbnail Column to Post Listing">add_image_size( 'admin-list-thumb', 80, 80, false );

function wpcs_add_thumbnail_columns( $columns ) {

    if ( !is_array( $columns ) )
        $columns = array();
    $new = array();

    foreach( $columns as $key =&gt; $title ) {
        if ( $key == 'title' ) // Put the Thumbnail column before the Title column
            $new['featured_thumb'] = __( 'Image');
        $new[$key] = $title;
    }
    return $new;
}

function wpcs_add_thumbnail_columns_data( $column, $post_id ) {
    switch ( $column ) {
    case 'featured_thumb':
        echo '&lt;a href="' . $post_id . '"&gt;';
        echo the_post_thumbnail( 'admin-list-thumb' );
        echo '&lt;/a&gt;';
        break;
    }
}

if ( function_exists( 'add_theme_support' ) ) {
    add_filter( 'manage_posts_columns' , 'wpcs_add_thumbnail_columns' );
    add_action( 'manage_posts_custom_column' , 'wpcs_add_thumbnail_columns_data', 10, 2 );
}</pre>
<h2>Add Lead Class to First Paragraph</h2>
<pre class="lang:default decode:true" title="Add Lead Class to First Paragraph">// Add Lead Class to First Paragraph
function first_paragraph( $content ) {
    return preg_replace('/&lt;p([^&gt;]+)?&gt;/', '&lt;p$1 class="lead"&gt;', $content, 1);
}
add_filter( 'the_content', 'first_paragraph' );</pre>
Adds a <code>lead</code> class to the first paragraph in <a href="https://developer.wordpress.org/reference/functions/the_content/">the_content</a>.

<a href="https://github.com/taniarascia/wp-functions#hide-wordpress-update-nag-to-all-but-admins">Source</a>