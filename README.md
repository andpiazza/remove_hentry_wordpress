# remove_hentry_wordpress
Removes hentry class entries from Wordpress pages, categories and tags. SEO benefits for the website: eliminate related errors from Google Search Console > Structured Data > hatom (markup: microformats.org)

## Problems this code solves
Wordpress core reports hentries for all pages to search engines. This causes SEO markup errors for non-posts whose authors or creation / update dates are irrelevant.  

## Who's This For
Developers, webmasters, SEO and Content specialists and practioners that want to fix errors found on Google Search Console > Search Appearance > Structured Data: hatom (markup: microformats.org):
* usually, it will list as errors all the pages, category and tag URLs in a Wordpress website

## The Solution
This codes removes hentries from all Wordpress pages, category and tag URLs so in a matter of days Google Search Console no longer reports errors.

## Instructions - How to Apply and Customize this Code to Your Needs
1. Add the code below to your functions.php file
2. Over the next few days, test your pages using the [Google’s Structured Data Testing Tool](http://www.google.com/webmasters/tools/richsnippets) or [Google Search Console](https://www.google.com/webmasters/tools/home?hl=en) on the following path: Search Appearance > Structured Data.

```
function themeslug_remove_hentry( $classes ) {
    if ( is_page() OR is_category() OR is_tag()) {
        $classes = array_diff( $classes, array( 'hentry' ) );
    }
    return $classes;
}
add_filter( 'post_class','themeslug_remove_hentry' );
```

## Sample Results
This [chart](https://swampsidestudio.com/wp-content/uploads/2014/07/hentry-structured-data-errors-google-webmaster-tools.png) shows how Google Search Console processes existing errors in a matter of days: decrease on the next day and full solution in 2-3 weeks typically).  
         
## Credit and References
1. [Remove WordPress hentry Class from Pages](https://swampsidestudio.com/remove-wordpress-hentry-class/) provided the basic code to implement these changes, updated to extend coverage to category and tag pages
2. [Conditional Tags on Wordpress](https://codex.wordpress.org/Conditional_Tags) containing many examples

## Want to provide feedback or contribute?
Leave a comment! Thanks for reading and using this.

## Future Developments
1. Implement schema using Google Tag Manager [Reference](https://moz.com/blog/seo-changes-using-google-tag-manager)
While the code above _removes errors_, it doesn't _improves SEO_. I'll look into it and provide guidance here shortly. 
