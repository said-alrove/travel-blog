# [travel-blog](https://said-alrove.github.io/travel-blog/)
The second project from Juan Pablo's course of CSS Grid and Flexbox.

This site was a combination of two of the projects from that course (they were both related, same colors, same logo etc, but the instructor didn't connect both pages to create a site, actually I think each project was on one different section of the course). I combined them mainly due to what I mentioned before, but also because it was going to be a great opportunity to create a "medium" project that could teach me about how to maintain a site correctly (name classes efficiently and reuse components), plus it was going to be the ideal project to practice the SMACSS architecture one more time before starting to use another methodology.

The design of the blog post page was inspired by the [Holy Grail](https://en.wikipedia.org/wiki/Holy_grail_(web_design)) layout (I used the sidebar to create a table of contents very nice :D!).

I have to remark that this project will grow in the future because I'd like to add more pages (like the about, contact, and sections ones) to see how far I can get with this project, therefore this repository will be updated a couple of times more :D.

## Project's preview

### Index
![](readme/screenshot(1).png)

### Blogpost
![](readme/screenshot(2).png)

## What I Learned
For this project, I decided to use SMACSS once again to master it, and I made some things different from the last project (made with SMACSS).

First, I'd like to mention that thanks to [this video](https://www.youtube.com/watch?v=FkhSdKAxEbM&list=LL&index=25) (It's in Spanish) I saw that I should add a prefix to the SASS modules according to where the styles belong. In my case I used two prefixes: 
        
   1.- layout/_layout-footer.scss

   2.- layout/_layout_inderx.scss
   
In both cases, the prefix starts with "layout" to show to what folder it belongs to, but something dissimilar in the two examples is that one has a middle dash after "layout" and the other one has an underscore. that's because the middle dash means that's a reusable component like, in the example above, the footer; and the underscore means that the module is a stylesheet for a specific HTML document (that's due to there'll always be components or elements that are different from page to page, therefore looking for them in their specific module is more efficient from my perspective; although another thing I could've done is to create a different SASS module for each component and specify if the element it's reusable or if it belongs to a specific page with another prefix such as "...footer-about.scss", there, I'm specifying that the element is a footer located in the "about" HTML document. I'll reconsider this in future projects). 

Disclaimer: I separated the modules according to where it belongs to, and added the prefix to identify them, only with the layout folder due to in the other parts of the project such as the "state" there weren't many things to consider for separate to obtain more organization, in other words...It was unnecessary.

I've used the SMACSS methodology at least a couple of times, and now I feel confident enough to jump onto another kinda CSS architecture in the next projects such as [ITCSS](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/), or [7-1](https://www.learnhowtoprogram.com/user-interfaces/building-layouts-preprocessors/7-1-sass-architecture).

I'd like to remark the fact that I've used my own kinda library with mixins that I created such as mixins for flexbox, grid, and media queries just to name some, if you'd like to check it out, [go here](https://github.com/said-alrove/mixins-sass).

Another important thing I did was to create local variables in some parts of the modules with values that I saw were too many times in the same stylesheet, for instance, let's imagine we have a section in our module specifically for the footer component, and there we have the value "2rem" repeated several times for paddings and margins; so in that case, something that could be useful (I say "could be" because maybe some values have nothing to do with others, therefore using the same value for all of them will be useless due to if I want to change one of them because they're not related, I'll have to change that unique value manually, in other words...there could have values that might not be related thus using variables for maintaining consistency where there's not it's at least useless) is create a variable with that value, and that would help me in the future if I'd like to change that value because I'd had just to change that unique variable's value.

I figured out how to use the images in the web correctly by using things like the srcset attribute in either the img or source elements, and in like manner now I know that I was doing the fallback for images with different formats wrongly due to I was using the same image with different formats in the same srcset element (that makes that the browser would only read the first image in the source element, and if it's supported it'd use it, if not, the fallback would have failed), for instance:

        <picture>
            <source srcset="01.webp, 01.avif,">
            <img src="01.webp" alt="">
        </picture>
        
When I should've been specifying the image formats separately, like this:

        <picture>
            <source type="image/webp" srcset="02.webp">
            <source type="image/avif" srcset="02.avif">
            <img src="02.webp" alt="">
        </picture>
        
That way the browser can perfectly understand the whole fallback. If the browser doesn't support the first image format, it goes to the second format if it's possible, if not, it returns to the img original source. If you want more information you can check the following links that helped me to understand this whole idea:

   1.- [Srcset and sizes attributes](https://www.youtube.com/watch?v=2QYpkrX2N48&t=1s). 
  
   2.- [When to use .jpg or .png? the answer is WebP... sort of](https://www.youtube.com/watch?v=Z_28syzkv-0).
  
   3.- [The HTML picture element explained](https://www.youtube.com/watch?v=Rik3gHT24AM&t=1025s). 
 
I have to mention that I've already talked about these videos in the [easy recipe](https://github.com/said-alrove/easy-recipe) project, but there was something left, and that's the type attribute to specify the format of the set of images, and for that, [this other video](https://www.youtube.com/watch?v=rO6rvbN37ZA) and [this article](https://css-tricks.com/avif-has-landed/) gave me a hand for something I took for granted. 

I'd like to add something anyway, this time I had more images what allowed me to create different versions of the same image, not just related to the format, but also to the size because that way the browser can download the ideal image according to the device that the user is using (that depending in two factors, the DPR or density pixel ratio, and the size of the screen, again, if you want more information, check the videos above!). I only created two versions of the image both in format (.webp, and .avif), and size (@1x, and @2x), but in the next project I'd like to get until the @4x version of the image to optimize even more the loaded performance (the reason why I didn't do it with this project was that the images were 800px width and to create 4 versions of them would've been useless, this because the savings would've been minimal, creating 4 or more versions of the same image only makes sense when they have a considerable definition that by loading a smaller version allows better performance on a large scale).

But, why .avif and not other formats? Well that's because what I'm looking for, is a better performance for the users, and the images play a huge role when loading a site, therefore I obviously decided to use the .webp format as always, but furthermore, I figured out that there was a lighter format with great quality too, unfortunately, it doesn't have enough support yet (60-70 percent maybe) so I thought It'd be a great opportunity for using both formats by creating fallbacks, which was a little hard because how I mentioned before, I didn't know how to make the fallback correctly.

If you want to learn more about what's the .avif format check these videos out:

   1.- [¿Qué es AVIF?](https://www.youtube.com/watch?v=32cDac99c04) - It's in Spanish.
   
   2.- [The AVIF Image Format by Kornel Lesiński [ IMAGE READY ]](https://www.youtube.com/watch?v=VHm5Ql33JYw).
   
One thing else I'd like to say is that when I was trying to use JPG as the image format for the Open Graph tags, the card debuggers didn't recognize the image and I don't know why, I'm not completely sure about what was the mistake, maybe the Open Graph tags don't support JPG file formats? I doubt it. I'll continue looking for information, but I wanted to say it because that way I'll remember this the next time with other projects and I'll be able to test JPG file formats with Open Graph tags again to see if It was an external bug or one mine that I didn't notice.

As the last comment, I have to mention that I got an 89 score in the accessibility section in the lighthouse report due to I didn't contrast good enough the secondary color (yellow) with the letters (white) and that's due to that if I'd have given a darker color, the design would've looked weird for that unbalance between the light of the colors (the colors are in their darkest version, if I add darker to any of them, they're gonna look ugly), so I decided to leave it like that. Furthermore, also because the social media menu didn't have "some descriptive text" in it (the menu was made with icons, thus I didn't use text in the links).

That'd be everything for this project :D.

Update: Something that I forgot to mention was that I had noticed that using the fonts from Google by calling it with a link element made the site a little bit slower (was something that always was present in the lighthouse report), thus I decided to download the fonts I was gonna use to get better performance when charging the site (and it worked perfectly :D). To import the fonts in the project I used the @font-face rule, [this video](https://www.youtube.com/watch?v=KzqQXDbDvus) gave me a hand (the @font-face rule works the same in SASS as in CSS so I didn't really deal with anything).

Furthermore, something cool I added almost at the end, was the table of contents for the blog post page with an anchor to the different parts of the post that bring you until those sections in a smooth way thanks to the [scroll-behavior](https://css-tricks.com/almanac/properties/s/scroll-behavior/).

### Lighthouse

#### Index
![](readme/lighthouse(1).png)

#### Blogpost
![](readme/lighthouse(2).png)

### Facebook

#### Index
![](readme/facebook(1).png)

#### Blogpost
![](readme/facebook(2).png)


### Twitter

#### Index
![](readme/twitter(1).png)

#### Blogpost
![](readme/twitter(2).png)
