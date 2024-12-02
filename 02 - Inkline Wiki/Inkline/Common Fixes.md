## Native WordPress Menu Widget
If using the native "WordPress Menu" widget within [[Elementor]] with sub-menu items, the drop down icon can be turned off, but still might have left/right spacing issues. 

If the design does not have icons for the menu items to indicate sub-menu, first turn off the icon within the widget. Within the "Content" tab of the "WordPress Menu" widget, select "None" for "Submenu Indicator".

If this does not resolve the left/right spacing issues, custom CSS is required.

Within the appropriate style sheet, in this case the "Hello Elementor Child" theme, in the "style.css" file which you select on the right hand sidebar, following [[Best Practices]] use the following classes to remove the padding for the menu items:

.elementor-nav-menu--main li .sub-arrow { padding: 0; }
![[WordPress Menu Sub-Menu Fix.png]]

This will remove the padding around the sub-menu icon and cause even spacing left/right for the menu item.