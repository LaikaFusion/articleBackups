
# Previews and Meta Tags&#58; A Short Guide

## Photo by Brett Jordan on Unsplash

You may have noticed that when you share a site on Facebook, Twitter, or a chat client that it will have a preview stating the site’s name and page, as well as an image and a few other tidbits. Your own site won’t have this by default but they are pretty easy to add in.

![An example in Slack](1*HqIAEGeCt0WbDr7l9Q3bbQ.png)*An example in Slack*

So where does that come from? The answer is `meta` tags put into your page. A tag that only goes into the head of the HTML document and is never seen by the user. These come in handy for more than link previews. Your description on the Google listing comes from these as well for example.

When searching for details about these you will be bombarded by Search Engine Optimization information. This is because if those blogs were not ranked that way, you would not want to be taking advice from them. Most of the advice concerns a specific meta tag, `&lt;meta name="keywords" content="your keywords"&gt;` . The short of it is [Google does not actually use these](https://webmasters.googleblog.com/2009/09/google-does-not-use-keywords-meta-tag.html) to determine what to categorize your website under or page rankings.

To get the best results with social media tags you need to use a combination of different tags and standards. The basic ones are:

`&lt;title&gt; Your websites page title &lt;/title&gt;
&lt;meta name="description" content="A short description of your website" /&gt;
&lt;meta name=viewport content="width=device-width, initial-scale=1"/&gt;`

See not that hard. Yes `&lt;title&gt;` is not a meta tag in the sense it is tagged as such. It however a very good idea to have for obvious reasons. It is recommended to make this different per page. A trick on how to do this with React will be discussed later on. It is also import that each of your pages has a unique meta description though I would worry less about that until later.

I have already described above why not to use the keywords meta tag. But others like author I have not. This is just not used for anything. A few are situational. If your site is targeting an international audience the language tag will be helpful. If you do not want your site indexed by google you can specify that with the robots tag.

But how could things be this simple? Where are the images? What if I want to give the price of an item on the page? Facebook has got you there. They created a specification called [Open Graph protocol](http://ogp.me/). While this was originally a Facebook specific thing it seems that many companies including Slack, and Google will read them. Twitter has their own standard we will get to in a bit. It should be clear that you should not expect anyone but Facebook to use this but they do.

The basic tags are pretty clear and easy to follow. All should be assumed typed as `&lt;meta property="ThePropertyBeingDiscussed" content="ContentForThatProperty" /&gt;` . The more observant might have noticed I switched from name to property. This is what the OG spec says to do. You can have both a property and name on the same meta tag, useful in the case of description.

Tags: 
`og:title` — This is the title of your page as it appears when linked to. It does not have to match your `&lt;title /&gt;` 
`og:type` — A very powerful tag. There is a full list of types [here](http://ogp.me/#types). At that link you will also find sub values of each type that allow more specific details to be passed in
`og:image` — This is the image that appears next to the content when it is linked. It has to be specified as an image file located on the server 
`og:url` — This is the link that will be used when shared. This can be different from the current page URL

That is a list of the required tags on every page. There are some optional ones that may be useful: 
`og:description` — A short description of the page, like above. This is the text that appears under the shared URL. If you want to make it the same you can set the property to this, and the name to `description` to avoid the duplication 
`og:locale` — Defaults to en_US, but can be useful if your page is not in US English 
`og_site_name` — The name of your site. This is more useful on a larger site. The is the difference between “Article Title — Medium” and just “Medium”

That is it for the OG set of tags. But that is not it for meta tags. Twitter also has their own standard known as [Twitter Card](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/abouts-cards). It is similar to OG but with some extra props added. For example Medium uses: 
`&lt;meta name="twitter:label1" value="Reading time"&gt;
&lt;meta name="twitter:data1" value="5 min read"&gt;`

This displays the read time being displayed on Twitter and other places like Slack. There is another standard for all this called [schema ](https://schema.org/docs/gs.html)though it is primarily used for SEO. There is also [oEmbed](https://oembed.com/), which is very far outside of the scope of the article since it needs a custom route set up on your webserver.

Earlier I mentioned you should change the title should be changed on every page. The easiest way to change a React page title is via the public/index.html file.

To do so per page can be done with `[react-helmet`](https://github.com/nfl/react-helmet) which ammusingly is made by the National Football League. This allows both the setting of per page titles, a handy feature if you’re using React Router but also the various meta tags discussed here.

Where does all this leave you? Well if you have your standard, Open Graph, and Twitter Card tags filled out it should give you the great looking share preview I originally showed above. This is easy to do through [templates](https://moz.com/blog/meta-data-templates-123) or [generators](https://megatags.co/) and to test through [Meta Tags](https://metatags.io/).

Further reading:
 [https://medium.com/slack-developer-blog/everything-you-ever-wanted-to-know-about-unfurling-but-were-afraid-to-ask-or-how-to-make-your-e64b4bb9254](https://medium.com/slack-developer-blog/everything-you-ever-wanted-to-know-about-unfurling-but-were-afraid-to-ask-or-how-to-make-your-e64b4bb9254) — Fantastic pictures. I was going to make similar ones before I found this article, no point when they have already done such a good job

[https://css-tricks.com/essential-meta-tags-social-media/](https://css-tricks.com/essential-meta-tags-social-media/) — Always a good source, especially for things like recommended image sizes and ratios