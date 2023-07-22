---
pageName: how-to-optimize-a-website
blogTitle: How to optimize a website's Core Vitals and Page Speed Score
titleTag: How to optimize a website's Core Vitals and Page Speed Score | Alamo
  Web Designs
shortDesc: Google's new Core Vitals metrics are changing how sites get ranked
  based on and optimized mobile experience. I will show you everything you need
  to know about how to satisfy these new metrics and get 95+ scores on speed and
  performance for hand made HTML and CSS websites.
blogDescription: How to optimize your site speed.
author: Cameron Anchondo
date: 2023-07-22T03:17:12.796Z
tags:
  - post
image: https://unsplash.com/photos/hGV2TfOh0ns/download?ixid=M3wxMjA3fDB8MXxzZWFyY2h8Njd8fHdlYnNpdGUlMjBzcGVlZHxlbnwwfDB8fHwxNjg5OTk2MzAzfDA&force=true&w=640
imageAlt: Site Speed
---
A  while back Google announces their [Core Vitals](https://web.dev/vitals/) metrics and how it will be the leading ranking factor going forward. It is basically favoring websites that have the fastest and best mobile experience. And that is what I am going to show you how to do right now.

<h3 class="blog-h3">Asset Optimization</h3>

Generally a lot of it comes down to asset optimization like having images the same size as they are being displayed at. Like not having a 1000px wide image resized in css to be 300px wide on the screen. That’s a waste of space. Also losslessly compressing all your assets can save up to 80% of the file size. I use [Compressor.io](https://compressor.io/) to lossly compress all my images. I pay for the pro subscription so I can upload 100 images to compress at a time. I've been using it for years. I highly reccomend them.

Also, background images. Why have a 2300px wide stock photo loading on a 400px wide phone screen? Resize that sucker to 500px wide and compress it. You go from 2.3MB to like 37k or less. HUGE reduction in size and load times. Then on tablet and desktop you just reset the background image to the larger 2300px image. I saw a website from someone who was loading multiple 4000px wide images as backgrounds and it was slow as all hell. It’s not enough to compress it. Because even if it compresses 70%, 70% of 4MB is still like 1.2MB which is huge for an image to load on mobile. Resize your images and load the smaller ones for mobile and the larger ones for tablet and desktop and compress them.

Then theres picking the right sized images for the right screen size, ad that's what the attribute "srcset" does. You can read about it [here](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images) from Mozilla Developer Network. What it does is you provide a list of different sized images to load at the screen sizes you want them to load, and using "src" as your fallback image. This way, if you have an image that's 700px wide in your html on desktop, you can load a verison of it that's 350px wide on screens under 480px or whatever you want and load a smaller file which in turn improves your laod time.

After you've done all that, make sure you add the proper height and width attributes to your images as Google wants to see those on every one of them. It helps allocate space for the image before it loads and helps reduce content layout shifts.

<h3 class="blog-h3">Lazy Loading</h3>

Then there’s lazy loading, using the loading=“lazy” attribute that is supported by most browsers. This used the browsers built in lazy loading without you having to do a lot of fancy JavaScript. But don’t lazy load any images that are “above the fold” meaning the bottom of the screen when the website loads. If the image will load on the landing page section and in the viewport, don’t lazy load it. It will create content layout shifts. So whatever images are on the screen when your website first loads should not be lazy loaded.

<h3 class="blog-h3">Remove jQuery, Google Fonts, and all other nonessential CDN links</h3>

There's a time and place for everything, and jQuery's time is 5 years ago and it's place in on the bench. Class toggling and all that can be handled within javascript now and there’s really no reason to be using JQuery anymore. It’s bloated and removing it can make your website more secure and load much faster. Remove it! Google's page speed score will label it as something you need to remove to improve your score, so we should all just get used to working without it unless its absolutely necessary.

Then there's your Google Fonts CDN links. Instead of linking to them in your head, download your fonts from them if it’s not a standard font on browsers. I use the @font-face to load my fonts locally. I store all the downloaded files in a fonts folder snd then load them in on my core-styles.css sheet that is shared on all pages of the site. This way I can eliminate using the google fonts cdn which eliminates it as a render blocking resource.

Just copy and paste this code in your CSS sheet that is shared on ALL your pages. Replaces the file path with the file path of your font that you downloaded. The font-family property in here is what YOU name it. So it doesn't have to be "Lobster" like in the example code. It can be called whatever I want it to be and thats what I sue when I declare it in CSS somewhere.



```css
@font-face {
    font-family:'Lobster';
    src: url('/fonts/Lobster-Regular.ttf') format('woff2');
    font-weight: normal;
    font-style: normal;
}
```

By downlaoding and loading your fonts locally you can eliminate the need for using the Google CDN, and load your fonts even faster while also removing a render blocking resource. I highly recommend doing this for all your sites.

<h3 class="blog-h3">Defer your nonessential Javascript</h3>

On all your script tags, add the defer attribute to the opening script tag and this will "defer" its loading until AFTER the website has loaded. This way, the Javascript doesn't interrupt the website from loading it's HTML and CSS first and painting the page. It waits its turn patiently until everyone else is finished.

<h3 class="blog-h3">Use SVG's as often as you can over PNG's</h3>

Use as many svgs as you can over pngs. Svgs are much smaller and load much faster. I use [Flaticon](https://www.flaticon.com/) to get all my svg graphics and icons and I can customize their colors and download the svg. Love it. This also replaces Fontawesome since that’s another cdn link you don’t need to be loading. Rather than using Fontawesome, just load in the icons you need as svgs. It’s much more lightweight than using Fontawesome.

If you can, hire someone off [Fiverr](https://www.fiverr.com/) who is an SVG graphic illustrator to convert your clients logos to svgs and load those into the site instead. Much more optimized and scalable. You can replace a 36k png or more with a 2k svg. It's worth every penny. You can find some affordable options for under $30 per graphic. A fantastic investment.

It’s always a great idea to convert your clients logos into svg format and then give it to them to use for decals, business cards, and t-shirts. They will love you for it.

<h3 class="blog-h3">Google Lighthouse</h3>

When all is said and done check your Google Lighthouse scores in your dev tools inspector and satisfy those as well. Usually you just need to check off some accessibility stuff like adding aria-label attributes to links with no text in them or alt tags on images or contrast issues. Once you have a 96+ page speed score and nearly 100’s across the board on lighthouse, your website is now properly optimized and dressed to impress.

These are the optimzation steps I take everytime I finish a website. I wanted to detail this out for anyone looking for a detailed "prcoess" on what to do and how to do it wihtout all the jargon and over complicated lengthy descriptions. I hope this helps!