To create an icon picker for [[JetFormBuilder]], you need the following installed:
- [[JetEngine]]
- [[JetFormBuilder]]
- [[Elementor]] or Block editor of choice [[Gutenburg]]

## Creating a Taxonomy for Icons
First within [[JetEngine]], Taxonomies then create a new [[Taxonomy]]. Here name the taxonomy which works best for the [[Post Types]] you'll be attaching it to. 

Be sure to follow [[Best Practices]] to maintain consistency throughout the site and other sites.

Make sure to select the appropriate post type under "Post Type" within the "General Settings" when creating the taxonomy. Then create the Labels for the taxonomy by creating a "Singular name" and then "tabbing" through the rest to create all labels (optional but ideal).

Next you'll want to create a [[Meta Field]] with a appropriate label and Name/ID (follow [[Best Practices]]). 

Set the field type to "Media" and "Add Taxonomy".

## Creating Terms for Taxonomy
Next we'll want to create [[Terms]] within the [[Taxonomy]] to be able to attach icons within the media meta field.

Under the post type we've attached our new taxonomy to, you should see the taxonomy while hovering over the post type. Clicking into the taxonomy we can then create the terms. 

Here name a term, example "Support", and attach the appropriate icon to the meta field you created earlier. This can be any image based file already in the [[Media Library]]. 

Then click "Add New" to create the term. 
## Creating a Listing for the Form
Next we'll want to create a [[Listing]] to show the icons for our form. 

Hovering over "JetEngine" and selecting "Listings", we'll be able to create a new [[Listing]] for our icons. Click "Add New" at the top of the page. Within the new popup select "Terms" for "Listing Source", then select the right taxonomy under "From taxonomy". Then name the listing (following [[Best Practices]]), and choosing your choice of editor (we use [[Elementor]]).

Within the editor add a [[Dynamic Image]] widget to the page. Under "Source" within the dynamic image widget, select the appropriate meta field under the taxonomy you created. 

For example we created the "Amenity Icon" taxonomy with a meta field of "Icon". So here we'll select "Icon" for our source.

Change the "Image Resolution" to "Thumbnail" (for optimization) and make any changes for styling under the "Style" tab for the widget. 

Once done, publish the listing.
## Adding Icons to Form
Next we'll want to add a [[Radio Field]] to our [[Form]] within [[JetFormBuilder]]. This allows us to attach the taxonomy we created to the form to list the icons we attached to the taxonomy. 

Create a new field within the form by either clicking on the "+" icon at the top of the form page or the "+" within the form between fields or within a [[Column]] field added to the form. 

Here, you'll name the radio field for the form under "Field Label" making sure to follow [[Best Practices]] for the form field name. Then you'll change "Fill Options From" from "Manual" to "Terms". Then selecting the appropriate taxonomy from the "Taxonomy" drop down. Then for the "Value from Meta Field", put the slug for the meta field within the taxonomy, for example "ai_icon".

Toggle on "Use custom template" and in the select field choose the listing we created earlier which has the [[Dynamic Image]]. 

Be sure to map all fields appropriately when publishing or updating the form under [[Post Submit Actions]] in the "JetForm" tab at top of the right hand sidebar for the form.

## Adding the Form to the Page
Next we'll add the form to the page using our page editor and the "JetForm" widget within the page editor.

Be sure to add the form and make any styling changes you'd like to reflect the style guidelines for the site. 

## Adding Styling to Show Icon Selection
To show our icon picker selections correctly, we'll need to add some custom [[CSS]] rules for our icons so the user can see the icon they've chosen correctly as our listing and radio field within the form won't allow us to show the selection.

Since we're using [[JetFormBuilder]], they have standard naming conventions for their classes. For our example, we want the radio field to be inline along a row instead of in a column. We'll also need to show our selection once we click on an icon, otherwise there will be no visual cue to show what is selected. 

Within the [[Theme File Editor]] under "Appearance" on the left hand sidebar of the dashboard, select "style.css" in the right hand sidebar, making sure you've selected the appropriate theme to edit. Unless a client has requested it, we'll use the [[Hello Elementor Child]] theme.

Within the style.css sheet, add the following rules with these classes:
- .jet-form-builder__fields-group.checkradio-wrap (this selects the radio field within the form to style it)
- .jet-form-builder__field-template--checked img (this selects the image within the radio field once a selection has been made and select the image specifically)

![[Icon Picker Radio Field Style.png]]

To follow the guidelines for our site, we chose an appropriate colour for an outline with a size and radius that follows the styling with the rest of the site.

![[Icon Picker Selected Style.png]]

Update the style sheet and test the form on the front-end of the site.