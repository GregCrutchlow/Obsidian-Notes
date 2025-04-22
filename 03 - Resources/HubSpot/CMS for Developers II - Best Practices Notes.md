Web Content Accessibility Guidelines (WCAG) is gold standard, which are a set of recommendations.

The principles are represented by the acronym POUR, Perceivable, Operable, Understandable and Robust. 

### Perceivable:
Users must be able to perceive the information using one of their senses.

### Operable: 
A user must be able to perform any interaction that the website requires, regardless of how they're accessing the website.

### Understandable:
The text content on the page is easily readable and the user interface is consistent across pages and provides the user with appropriate cues.

### Robust: 
The content must be developed using well-adopted web standards that will work across different browsers and assistive technologies, now and in the future.

Improving accessibility solves other priorities as a developer such as user experience, performance and SEO. 

Coding accessible websites also produces cleaner code which is easier to read and to code.

### WebAIM Million:
96.7% of the errors fell into six categories:
1. Low contrast text
2. Missing alternative text for images
3. Missing form input labels
4. Empty Links
5. Missing document language
6. Empty buttons

## Automated testing

WebAIM colour contrast checker is a good tool to use to test colour contrast for text on a site.

#### Landmarks
Landmarks refer to the major sections of a webpage, like the header, main content, navigation, and footer areas.
Adding landmarks will make it easier for individuals using assistive technology to navigate your page.

Add HTML semantic elements to make it easier for someone using assistive technologies to navigate your site.

#### Skip to Content Link
Allows a user using assistive technology to skip to the main content of your page.
Without it, navigation is much less efficient for these users.

To add a "Skip to Content Link" use the following code at the top of your page, making sure to add a corresponding id to the main html element on the page.
```
<a href="#main" class="skip-to-main-content">
	Skip to Main content
</a>
```

Style: 
```
.skip-to-main-content {
	background: [color of choice];
	padding: [padding of choice];
	left: 0;
	color: white;
	position: absolute;
	transform: translateY(-100%);
	transition: transform 0.3s;
}
.skip-to-main-content:focus {
	transform: translateY(0%);
}
```

# Performance

## Loading Performance
Refers to how long it takes for the server to transfer all of your site's files to the browser.

## Rendering Performance
Refers to how long it takes the browser to take your site's files and eventually paint the pixels to the page.

## Time to Interactive (TTI)
Refers to how long it takes for a page to become fully interactive.
## Performance Optimizations
Performance optimizations that we make aim to improve each of these elements of website performance: loading performance, rendering performance, and Time to Interactive.

# The Critical Rendering Path (CRP)
The five steps a browser takes to render a web page.

Document Object Model (DOM) is the browser's representation of all of the content on the page, organized into a tree structure.

Example of what happens when the browser receives HTML
1. **Parse HTML** > **Construct DOM** > **Load Resources** > **Preload Scanner**
   **Note**: When the parser encounters JS, the browser has to pause construction of the DOM.
   JS is said to be both **parser-blocking** and **render-blocking**
2. **Construct CSSOM (CSS Object Model)**
   **Note**: CSSOM is the browser's representation of the page's styles, organized into a tree structure.
3. **Create Render Tree**
   **Note**: A combination of both the DOM and CSSOM containing the visible nodes in the DOM along with the CSS styles applied to each **node** 
4. **Layout**
   **Note**: During layout, the browser calculates the position, width, and height of all the nodes in the render tree.
5. **Paint**
   **Note**: During this step, the browser paints all of the visual elements to the page. The painting of the page marks the end of the Critical Rendering Path.
6. Finally remaining JS work and interactivity is added.

# Common Page Optimization
Main areas for optimization are images, videos, JS and CSS.

## Images
Optimization of images is the best thing to do for site optimization, doing things like Lazy loading, is quite important. Adding width and height attributes to images allows HubSpot to add a source set and reduce cumulative layout shift. 

Using resize_image_url HubL function to lower an images resolution.

## Videos
Best to avoid auto play videos. Make sure to compress auto play videos to allow faster loading.

## HTML, CSS and JS
Minification, compression and caching are always necessary.

Minification is a process through which all unnecessary characters are removed from a file. This includes removing spaces and comments.

Compression occurs at the server level and reduces the size of the file that is delivered to the browser, improving loading performance.

Caching occurs at both the browser and server levels. 

Browser caching refers to the temporary storage of files by the browser. When the browser caches a file, it doesn't have to re-request that file each time a user visits a page that requires it. This improves loading performance.

Server caching refers to when server caching is active, the server keeps a pre-built copy of a page's HTML ready so that it can be delivered to a user's browser as soon as it's requested.

#### CSS
The require_css HubL function enqueues a CSS file to be rendered in the head element. All CSS link tags are grouped together and rendered before any JS tags.
#### JS
Parser-blocking and render-blocking, common performance bottleneck. Adding async, or defer attribute tags allows for faster loading. Without async/defer, parser pauses while script is fetched and executed, script is parser-blocking. 

The async attribute allows for the script file to be loaded asynchronously, which allows the parser to work while the file is being retrieved. Once the script is downloaded, the parser halts while the script is executed.

The defer attribute allows for the script to be loaded asynchronously and the script is only executed after the parser is done constructing the DOM. The script is not parser-blocking with the defer attribute.
   
The require_js HubL function specifies whether a script should be enqueued to render in the head or footer of a page (footer being the default).
# Testing
Using Google Lighthouse we can measure performance of a page to see where we can make optimizations.

Largest Contentful Paint (LCP) is a measurement of loading performance and refers to the amount of time it takes for the browser to load and render the largest image or text block that is visible in the viewport. Good is within 2.5s, Needs Improvement within 4s and Poor is anything beyond 4s.

Total Blocking Time (TBT) is a measurement of interactivity and refers to the amount of time between the Largest Contentful Paint and page interactivity. TBT is a proxy for another measurement, First Input Delay (FID). FID is measured similarly to LCP where Good is within 100ms, Needs Improvement within 300ms and Poor anything beyond that.

Cumulative Layout Shift (CLS) is a measurement of visual stability and refers to the movements of elements that can happen on page load. Measured as Good which is within 0.1, Needs Improvement 0.25 and Poor which is anything beyond that.

LCP, FID and CLS are Googles Core Web Vitals and factor greatly in the Lighthouse score. 

# Creating base.html Template
Within the "Templates" folder of the custom theme within HubSpot, create a folder named "layout". Within this folder create a file named "base.html".

Within this file, the "templateType" is none and remove "isAvailableForNewContent". Remove the default content of this file and replace it with this:

```
<!doctype html>
<html>
	<head>
		<meta charset="utf-8">
		<title>{{ content.html_title }}</title>
		<meta name="description" content="{{ content.meta_description }}>
		{{ standard_header_includes }}
	</head>
	<body>
	
		{% block header %}
		{% global_partial path="./partials/header.html" %}
		{% endblock header%}
		
		<!-- Main Content -->
		<main id="main">
			<div class="container">
				{% block body %}
				{% endblock body %}
			</div>
		</main>

		{% block footer %}
		{% global_partial path="./partials/footer.html" %}
		{% endblock footer %}
		
	</body>
</html>
```

Within the "home.html" template, remove the html and add: 
```
{% extends './layout/base.html' %}
```

Then add:
```
{% block body %}
{% dnd_area 'dnd_area' label='Main Content' %}
	{% dnd_section %}
		{% dnd_module "Name of Module" path="./path_to_module" label="Label of Module" %}
		{% end_dnd_module %}
	{% end_dnd_section %}
{% end_dnd_area %}
{% endblock body %}
```

# SEO

Search Engine Optimization (SEO) is the practice of increasing the quantity and quality of traffic to a website through organize search engine results. 

Google's main web crawler is known as Googlebot. Google maintains both mobile and desktop versions of its main crawler, known as Googlebot Smartphone and Googlebot Desktop.

### How Google Search Works
What Google Search does can be broken up into 3 main stages: 
Crawling which includes rendering
	In the crawling stage, Google downloads the text, images, and videos on your page. As part of crawling, Google also renders the page and runs any JavaScript it finds.	

Indexing
	Google processes and analyzes the page and stores it in the Google index, which is Google's database used to serve search results.

Serving search results (ranking)
	This stage occurs when a user actually performs a Google search. At this stage, Google searches its index and returns what it believes are the highest quality and most relevant results.

Categories of SEO fall into 3 categories
1. Off-page
	1. Things you can do off of your website to improve SEO
2. On-page
	1. Things that you can do on your website to improve its ranking
	2. Examples: including an optimized title tag and including alt text on images
3. Technical
	1. Other things you can do to improve the ranking of your site
	2. Examples: ensuring your site is mobile-friendly, creating and maintaining a sitemap, or improving site speed

Many SEO recommendations are easily measurable and straightforward to implement.

Technical SEO includes things like: creating and editing sitemaps, using URL redirects, using structured data and optimizing for site speed.

Developers & On-Page SEO include using meta titles and meta descriptions, using canonical links correctly and using descriptive text in links.

Meta Title is implemented as a < title> tag in HTML, provides a concise and accurate description of the page's content and should be 55 characters or less.

Meta Description is implemented as a < meta> tag with name and content attributes in HTML, and should tell a user what your page is about and should be 155 characters or less.

Example of a meta description
```
<meta name="description" content="HubSpot Academy is the worldwide leader in inbound marketing, sales, and customer service/support training.">
```

Using Descriptive Link Text
 - Don't:
	 - use generic link text
	 - "click here" or "learn more"	 
- Do:
	- use specific descriptions that describe the content on the hyperlinked page.
	- "sign up for free courses"

## Prioritizing Mobile-Friendly Web
According to Statista mobile web usage was responsible for 59% of global website traffic in the second quarter of 2022.

Google has implemented Mobile-First Indexing. Google primarily uses it's smartphone agent to crawl and index pages. Thus, the mobile version of your site is what is appearing in search results. 

### Responsive Design
Responsive design includes things like using media queries, responsive text sizes and responsive images to change the appearance of your site based on the device of your users.

Including Viewport meta tag
```
<meta name='viewport' content='width=device-width, initial-scale=1.0'>
```
This tag is automatically included within HubSpot when creating a page. This is included within the:
```
{{ standard_header_includes }}
```

Using Legible Font Sizes, Google recommends using a font size of a least 12px on at least 60% of the text on your page. 

Using appropriately sized tap targets, Google recommends tag targets (buttons for touch devices for example) at least 48px wide and 48px tall, and to be at least 8px apart from each other.

Mobile-First Indexing Best practices:
Google also provides these general guidelines when creating a mobile site: 
- Use the same content on your mobile site as on your desktop site
- Make sure you're using the same meta tags on both the desktop and mobile versions of your sites.

### Structured Data
A standardized format for providing information about a page and classifying the page content.

#### Schema.org
Schema.org is the organization that creates the standardized language and rules used for structured data.

#### JSON-LD
JSON-LD is a script that can be placed within a web page to communicate structured data to search engines.

#### Three Main Ways to Implement Structed Data: 
- Work with a dev
- Use a plugin
- Add it manually

#### Steps to add structed data to a page:
1. In the head HTML of your web page, add a script element to set to JSON-LD
2. Inside the script element, tell Google you're using Schema.org structured data.
3. Based on the type of content you're describing, tell Google which kind of structured data you're using.
4. Add all the required and recommended properties to give Google more information about the content being described.

### Redirects
Flexible Redirects Example: End-of-URL Redirect
Original: 
```
https://example.com/posts/*rest-of-url
```
New URL:
```
https://blog.example.com/posts/{rest-of-url}
```


# Accessibility
## The Web Content Accessibility Guidelines (WCAG):
- Include 78 success criteria
- List issues that people with disabilities face
- Detail ways to remediate these issues
