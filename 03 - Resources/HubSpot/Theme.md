A theme is a portable and self-contained package of developer assets designed to work together to enable a flexible content editing experience. These assets might include templates, modules, CSS files, JavaScript files, images, and more. Themes allow developers to create a set of theme fields, similar to module fields, which allow content creators to control global website styles without having to edit CSS.

You can use HubL to access the values of theme fields throughout the theme's CSS. Content creators can then use the theme editor to modify theme fields, preview those changes against existing templates within a theme, and publish their changes.

## [1. Start a boilerplate theme project](https://developers.hubspot.com/beta-docs/guides/cms/content/themes/getting-started#1.-start-a-boilerplate-theme-project)

Run `hs create website-theme my-website-theme` to create a `my-website-theme` directory populated with files from the [CMS theme boilerplate](https://github.com/HubSpot/cms-theme-boilerplate).

## [2. Upload the CMS Boilerplate to your HubSpot account](https://developers.hubspot.com/beta-docs/guides/cms/content/themes/getting-started#2.-upload-the-cms-boilerplate-to-your-hubspot-account)

Run `hs upload my-website-theme my-website-theme`. This will upload the boilerplate to your account’s design manager, in a folder titled _my-website-theme_.

## [3. Create a page](https://developers.hubspot.com/beta-docs/guides/cms/content/themes/getting-started#3.-create-a-page)

To create a page from the uploaded theme:

- In your HubSpot account, navigate to **Marketing** > **Website** > **Website Pages.**
- In the upper right, click **Create**, then select **Website page**.
- In the dialog box, select the **domain** that the page will be published to, then enter a **page name**. Then, click **Create page**.

![create-page-from-dashboard](https://www.hubspot.com/hubfs/Knowledge_Base_2023/create-page-from-dashboard.gif)

- On the template selection screen, templates from your [active theme](https://knowledge.hubspot.com/website-pages/use-themes#use-an-active-theme) will appear at the top of the page.
    - If you haven’t selected an active theme, hover over **CMS theme boilerplate** and click **Set as active theme**.
    - If you've already set an active theme, select your new theme by clicking the **theme selector** dropdown menu, then selecting **Change theme**. Then, hover over **CMS theme boilerplate** and click **Set as active theme**. On the next screen, select a **template**.

![theme-selector](https://www.hubspot.com/hubfs/Knowledge_Base_2023/theme-selector.gif)

You'll then be brought to the page editor where you can edit the theme's fields.

## [4. Edit theme fields](https://developers.hubspot.com/beta-docs/guides/cms/content/themes/getting-started#4.-edit-theme-fields)

- In the left sidebar of the page editor, click the **Themes** tab.
- On the _Themes_ tab, click **Edit theme settings**. This is where you can modify your existing theme settings. Publishing changes to theme settings will update the styles across your pages using this theme that was updated.

![edit-theme-settings](https://www.hubspot.com/hubfs/Knowledge_Base_2023/edit-theme-settings.gif)

## [5. Prepare to make local changes](https://developers.hubspot.com/beta-docs/guides/cms/content/themes/getting-started#5.-prepare-to-make-local-changes)

Return to your terminal, then run `hs watch my-website-theme my-website-theme`. This [command](https://developers.hubspot.com/beta-docs/guides/cms/setup/getting-started-with-local-development) watches your local directory and automatically uploads the following changes to your HubSpot account on file saves.

## [6. Add a theme field](https://developers.hubspot.com/beta-docs/guides/cms/content/themes/getting-started#6.-add-a-theme-field)

Now that we're listening for local changes, add a new theme field:

- Open `fields.json` file in your editor. This file controls the available fields in the theme editor sidebar. We’ll be adding a new [field](https://developers.hubspot.com/beta-docs/guides/cms/content/themes/overview#fields-json) to specify the height of the footer.
- Near the bottom of the file, locate the `footer` group.
- Copy the code below and paste the JSON into the file above the first item in the children array for the footer group.

```
1 // fields.json
2      {
3      "id" : "",
4      "name" : "height",
5      "label" : "Footer height",
6      "required" : false,
7      "locked" : false,
8      "display" : "text",
9      "step" : 1,
10      "type" : "number",
11      "min" : 10,
12      "max" : 900,
13      "help_text":"This footer will expand in height to accomodate any content           added to the footer. You are setting the minimum height in px",
14      "default" : 100
15      },
```

- Save `fields.json`, and refresh the theme previewer in HubSpot. Your new field should display in the left-hand sidebar.

## [7. Reference the field in your CSS](https://developers.hubspot.com/beta-docs/guides/cms/content/themes/getting-started#7.-reference-the-field-in-your-css)

- In your code editor, open the `theme-overrides.css` file. Then locate the css selector for `.footer`. We're now going to add a `min-height` to this selector.
- To access a value in a theme, use the `theme` object. For example, you would use `{{ theme.footer.height }}` to access the height value set in our height field.
- Replace the `.footer` declaration in theme-overrides.css with the following:

```
1 .footer {
2  background-color: {{ footer_bg_color }};
3  min-height: {{theme.footer.height}}px;
4
}
```

- Save `theme-overrides.css` to upload it to your HubSpot account.

## [8. Test changes](https://developers.hubspot.com/beta-docs/guides/cms/content/themes/getting-started#8.-test-changes)

Return to the theme editor, and refresh the page to see your new field appear under footer. Update the height value to have it reflected immediately in the preview. It might be helpful to set a background color for the footer so you can see the change more easily.

## [Next Steps](https://developers.hubspot.com/beta-docs/guides/cms/content/themes/getting-started#next-steps)

Now that you've created and updated your theme, you can now create more theme fields and customize them for your projects. For more customization options, check out the [themes overview](https://developers.hubspot.com/beta-docs/guides/cms/content/themes/overview). While building out your theme, it might be helpful to view the best practices for [optimizing websites on the HubSpot CMS](https://developers.hubspot.com/beta-docs/guides/cms/content/performance/speed).

HubSpot has several [default themes](https://developers.hubspot.com/beta-docs/guides/cms/content/themes/default-themes) that come with CMS Hub. These themes are available for you to view, clone, and update, to learn how you might use a theme in a real-world scenario.

Once you've got a handle on themes, [learn how to build your first custom module](https://developers.hubspot.com/beta-docs/guides/cms/content/modules/quickstart).