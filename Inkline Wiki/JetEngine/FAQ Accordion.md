To create a clean functional accordion style FAQ section on a page you will need the following: [[Elementor]], [[JetEngine]] and [[JetTabs]] installed.

## Creating FAQ Custom Post Type (CPT)
First a Custom Post Type (CPT) must be created to hold all FAQ questions/answers neatly and allows for content to be updated easily and all at once if FAQ sections are in multiple spots on a website.

To create a CPT, you go to [[JetEngine]] > [[Post Types]] and create a new post type by clicking "Add New" button at the top of the page. 

Here you'll name the post type in "Post Type Name", adjust the slug (if needed) and create the labels by filling in the "Singular name" and tabbing through the remaining fields. 

If nothing else is needed for your FAQ you can click "Add Post Type", or if more fields are needed, either for images or other text fields, you can add them within the "Meta fields" section.

When the new CPT is created, you'll want to create some placeholder posts to make sure your FAQ widget works when we add it later.

## Creating a Query for the Accordion Widget
Next we'll want to create a query within the [[JetEngine]] [[Query Builder]] so the widget knows content to use and how to display it on the page.

To create a query go to [[JetEngine]] > [[Query Builder]] and create a new query by clicking "Add New" button at the top of the page.

In the "General Settings" section you'll name the query, following [[Best Practices]], you'll want to name the query something that matches what you'd like to do with it, for example "FAQ Content Query".

Under "Query Type" we'll select "Posts Query" from the drop down menu. We'll keep "Cache Query" enabled and we're done with this section.

![[Pasted image 20240704105427.png]]

Under "Posts Query" section, within the "General" tab, we'll select the correct "Post Type" which we created earlier and choose "Published (publish)" for the "Post Status". After this, you add the query by clicking "Add Query". If your FAQ needs to be in a certain order, you can add that here under "Order & Order By" section within the "General" tab.

![[Pasted image 20240704105751.png]]

## Adding JetTabs for Classic Accordion widget
Next we'll want to enable [[JetTabs]] to have access to the "Classic Accordion" widget within [[Elementor]]. 

Head to [[Crocoblock]] > Update & Installation and within the "More included JetPlugins with your licence" section, install [[JetTabs]] and then activate in the section above once installed. 

![[Pasted image 20240704110046.png]]

## Adding Classic Accordion to page
Within the [[Page]] where you'd like to have the FAQ Accordion, enter the [[Elementor]] editor. 

Here you'll search for [[Classic Accordion]] and add it to the page. 

Once the widget is added and selected in your navigator window, on the left side of the screen under "Items" you'll enable "Use JetEngine query". You'll select the query you created earlier and remove all items but one.

Within the remaining item, for label you'll press "Dynamic Tags" and select "Current Object Field" at the bottom of the selector. Clicking on the wrench will open a new popup and under "Settings" for "Field" you'll select "Title" under "Post". For "Content Type" select "editor". If you have a specific design to follow with additional fields such images or buttons you would select [[Template]], which you'll have to create as well.

For "Content" you'll press "Dynamic Tags" and select "Current Object Field" again. Clicking on the wrench you'll then select "Content" for the "Field".

![[Pasted image 20240704111002.png]]

## Styling Accordion and Publishing/Updating page
Once you've styled the widget to the design, you can publish/update the page.