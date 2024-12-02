This creates a button (typically at bottom right of page) that brings you back to the top of the page when you scroll down. This is typically done to reduce the amount of scrolling a user would need to do to go back to the top of the page.

## The Script
Using this script, either on the page you want it to be used on, or within a script sheet (JavaScript and enqueued to run) which would allow the button to be visible on all pages on the site.

<script>  
window.onscroll = function() {
	scrollFunction()
};

function scrollFunction() {  
  if (document.body.scrollTop > 20 || document.documentElement.scrollTop > 20) {  
    document.getElementById("bktop").style.bottom = "20px";  
  } else {  
    document.getElementById("bktop").style.bottom = "-100px";  
  }  
}  
</script>

This script (remove the script tags if within a script sheet) uses the .onscroll event on the window (object) which then triggers a unnamed function. Within this function is a named function "scrollFunction".

This function has an if statement that targets the body of the document (webpage) if you scroll 20px away from the top of the page or the documentElement which is a read-only property of the Document, the root of the page essentially, which is at the top of the page. See [mdn web docs](https://developer.mozilla.org/en-US/docs/Web/API/Document/documentElement) for more information.

So if you've scrolled 20px from the top, the button is triggered to appear 20px from the bottom of the page and if clicked, would scroll you back to the top of the page where the element with the id of "bktop" exists. You'll also see an else statement within the if statement that says that if you're not 20px away from the top, to make the button 100px below the bottom of the page.

## The Outcome
