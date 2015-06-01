# Class_WP_ezClasses_Menu_Walker_Social_Share_1
A product of WPezClasses (https://github.com/WPezClasses)

##### Use wp_nav_menu() to generate a simple list of Share To icons / links. Adds a handful of custom ez_args because that's The ezWay.


=======================================================================================

#### WPezClasses: Getting Started
- https://github.com/WPezClasses/wp-ezclasses-docs-getting-started

Note: Social Share 1 doesn't extend the standard ez parent class. But the Getting Start is still worth reviewing.

=======================================================================================


#### Overview

Uses Font Awesome (http://fortawesome.github.io/Font-Awesome/icons/) for the icons (but is coded in such a way to make using other icons sets ez, if you're so inclined).

When adding links to this menu please use the WP Admin > Menus > Custom Links. The URL for each menu item will be parsed to identify its host. If the host (domain) is in the (supported) Share To list, this class will generate a share to icon / link.

There are plenty of opportunities (read: args and methods) for customization.



#### Supports Share To:

Facebook

Twitter

LinkedIn

Google Plus

Email (aka Email to a Friend)


TODO: Other networks.


=======================================================================================

#### See Also

https://codex.wordpress.org/Class_Reference/Walker

https://codex.wordpress.org/Class_Reference/Walker_Nav_Menu

=======================================================================================


#### The ez_args

Doin' it...The ezWay.

These are the additional args unique to Walker Nav Menu: Social Share 1. They can be changed by extending this class (see method: ez_args_defaults()) or just pass them in (as an array with key 'ez_args') as part of the standard array of args for your wp_nav_menu().

###### 'item_tag'
 - What HTML tag will rap a given item. See also method: valid_item_tags() for the other values currently allowed.
 - Default: 'li'

###### 'item_id_slug'
 - What slug should be used to create the item id. The actual item (post) id will be append to the end of the slug.
 - Default: 'simple-list-item-'
 - Note: It's '...item-" (item hyphen) and not just '...item' (no hyphen).
 - Note: Setting this to false prevents the item id from being added. That is, there will be no item id="..." at all.
 - Note: If you use Simple List 1 for more than one menu on a given page you'll want to make the item_id_slug unique for each if a menu item can be in multiple menus. The resulting CSS ids should be unique.

###### 'item_class'
 - What class should be assigned to each item
 - Default: 'simple-list-1-item'
 - Note: This is in addition to the item's class(es) as defined via Admin > Menu.

###### 'parent'
 - A given list item can be assigned parent and child CSS classes in case you desire a bit more styling control than uber simple.
 - Default: 'is-parent'

###### 'not_parent'
 - Default: 'not-parent'

###### 'child'
 - Default: 'is-child'

###### 'child_of'
 - Default: 'is-child-of-'
 - Note: It's '...of-" (of hyphen) and not just '...of' (no hyphen).

###### 'not_child'
 - Default: 'not-child'

###### 'fw_class'
 - Add what class to the icon for fixed width
 - Default: 'fa-fw'

###### 'stack_tag'
 - In the case of stack icons, what tag wraps them
 - Default: 'span'

###### 'stack_wrap_class'
 - Add what class to the stack wrapper
 - Default: 'fa-stack',

###### 'stack_back_class'
 - Add what class to the icon at the back of an icon stack
 - Default: 'fa-stack-2x',

###### 'stack_front_class'
 - Add what class to the icon at the front of an icon stack
 - default: 'fa-stack-1x'

###### 'inverse_class'
 - If 'inverse' is true / 'true' what class to add
 - Default: 'fa-inverse',

###### 'title_prefix'
 - For example, "Share to: "
 - Default: ''

###### 'target_default'
 - Target of the share link
 - Default: '_blank',

###### 'icon'
 - Of the host's icons (see method: social_share_to()) which key?
 - Default is: 'a'
 - Note: False will prevent an icon(s) from being used. For example, perhaps you'd prefer to use a CSS sprite instead.

###### 'fw'
 - fw stands for fixed width, which is a font Awesome option (that may or may not apply to other icon sets).
 - Default: true,

###### 'stack'
 - Another Font Awesome option for stacking two icons (http://fortawesome.github.io/Font-Awesome/examples/#stacked). false, else the key of the back icon (see method: stack_icons()).
 - Default false,

###### 'inverse'
 - Apply the inverse_class
 - Default: false
 - Note: In a stack, inverse will only apply to the front icon

###### 'msg'
 - Add a brand or menu item-centric "message"
 - Default: ''
 - For example, a #hashtag and/or the brand's @handle can be added at the args level or menu item level (as explained next).


#####In addition, the following args can also be passed via a query string appended to the URL of individual menu items when they're entered via Admin > Menus > Custom Links.

'icon'

'fw'

'stack'

'inverse'

'msg'


Example: https://twitter.com?icon=b&msg=#WPdev @WPezClasses

=======================================================================================

#### Example / Sample

```
$arr_menu_args = array(

  'description'     => 'Social Share',  // key => description is used for register_nav_menus()
  'theme_location'  => 'menu_social_share',
  'menu'            => 'menu_social_share',
  'container'       => false,
  //  'container_class' => 'container_class--carousel slide',
  //  'container_id' => 'container_id--carousel-example-generic', // TODO
  'menu_id'         => 'social-share-list',
  'menu_class'      => 'blog-menu-ul social-share-ul',
  'items_wrap'      => '<ul id="%1$s" class="%2$s" role="listbox">%3$s</ul>',
  'echo'            => false,
  'fallback_cb'     => false,
  'walker'          => new Class_WP_ezClasses_Menu_Walker_Social_Share_1(),

  'ez_args'         => array(
    'fw'            => false
    'item_tag'      => 'li',
    'item_id_slug'  => 'blog-menu-social-id-',
    'item_class'          => 'blog-menu-item',
    )

);

```

=======================================================================================

#### Other WPezClasses you might be interested in

 TODO