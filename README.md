# Barebones.CSS Documentation
- - - -
## ABOUT

This is a project I used to gain a better understanding of CSS including grid, flexbox, and transitions. It is also aimed to save myself some time when creating sites without unnecessary features or downloads. I will probably end up using another existing framework for most of my sites, but this has certainly been fun for educational purposes.

I realize that most developers have already created a library or framework for themselves, but it is my hope in sharing this that aspiring developers like myself can use it to learn CSS without a large framework. I plan to update this and refactor as I learn more, but I am proud of the way it has turned out in just a few hours. (Writing this documentation is taking almost as long as creating this project.)

Barebones will require you to think about your design. You will deal with specificity, and can make changes without using the !important tag. I have labeled the sections in the CSS file, and tried to keep a logical enough order that anyone could use barebones and modify it easily to meet their design needs. My goal was to avoid the bloated, ready made nature of a tool like bootstrap, where several color classes are available for each element. I have managed to keep a commented, un-minified stylesheet to < 500 lines, that still provides template classes for grid, and flexbox, — as well as a responsive nav with a hamburger dropdown menu that does not require glyphs or javascript. If desired, javascript can be added or the nav could be completely reworked.

I make heavy use of the REM measurement and set just one root font-size for the whole html document. This allows my size classes to work predictably.



## CSS Reset
- - - -
I used a common css reset and modified it slightly to keep default styles for <em> and <strong>. At the end of the reset, I define a base font-size for the whole document, and then set the h1 - h6 tags to the following (note that markdown will give them its own default styles here)


## HEADINGS
- - - -

# H1 - 3 REM
## H2 - 2.3 REM
### H3 - 1.75 REM
#### H4 - 1.4 REM
##### H5 - 1.3 REM
###### H6 - 1.1 REM

I did not add any heading font or styles. This is so Barebones can be used easily with a wide variety of templates. I follow this design pattern throughout, allowing for easy modification and not much magic.


## COLORS
- - - -
I added some default color classes and background color classes that override some browser defaults. This is simply because I liked these colors better and found it useful to be able to quickly add colors via class assignment in my html. In many cases you will still want or even need to define your own colors inside a custom class to adjust the scope or specificity of the color's application.
```
.black{color:black;}
.white{color:white;}
.silver{color:#afafaf;}
.gray{color:#8e8e8e;}
.darkgray{color:#565656;}
.navy{color:#212e59;}
.blue{color:#3b5199;}
.red{color:#963333;}
.maroon{color:#561d1d;}
.orange{color:orange;}
.tangerine{color:#f78c4f;}
.yellow{ color:#f7dd4f;}
.aqua{ color:#7de8f2;}
.teal{ color: #5fc5ce;}
.green{color:#5fce8d;}
.lime{color:#55f45d;}
.purple{color:#49349b;}
.fuchsia{color:#654ebf;}

.bg-black{background-color:black;}
.bg-white{background-color:white;}
.bg-silver{background-color:#afafaf;}
.bg-gray{background-color:#8e8e8e;}
.bg-darkgray{background-color:#565656;}
.bg-navy{background-color:#212e59;}
.bg-blue{background-color:#3b5199;}
.bg-red{background-color:#963333;}
.bg-maroon{background-color:#561d1d;}
.bg-orange{background-color:orange;}
.bg-tangerine{background-color:#f78c4f;}
.bg-yellow{ background-color:#f7dd4f;}
.bg-aqua{ background-color:#7de8f2;}
.bg-teal{ background-color: #5fc5ce;}
.bg-green{background-color:#5fce8d;}
.bg-lime{background-color:#55f45d;}
.bg-purple{background-color:#49349b;}
.bg-fuchsia{background-color:#654ebf;}
```


## MARGIN AND PADDING
- - - -
Similar to colors, many times margins/padding will need to be defined within a custom class.  For elements that do not change state, like a "<p>" or "<span>", these classes can be used and modified. I have capitalized them here to explain them, but the classes are all lowercase in the CSS file. 

P = padding
M = margin
L = left
R = right
1 = 1rem
2 = 2rem
3 = 3rem
half = .5rem
*letters are all lowercase, then hyphen, then the number (or half)*

example
```
<div class=“content”>
	<p class=“**pl-1**”>Padding left 1 rem</p>
	<div class=“box **p-half**”>Box with .5rem padding on all sides</p>
</div>
```

## BIGGER / SMALLER TEXT
- - - -
This class could be quickly added to a paragraph or span to make the text either **.bigger-text** of 1.25 REM or **.smaller-text** of  .75 REM. This feature has a limited use case in responsive design, but was easy to include with minimal overhead.


## BOX
- - - -
This class should be used on a div that contains other elements to give it a semi-transparent background with a rounded border. All properties can be found in the .box class.  I like to design with a background color/pattern and overlay these boxes for my text.


## BANNER
- - - -
Just a simple class to set a height of 6rem on a div with centered element. Use this class to make a header banner photo and set a bg color class on the same div.

## NAV-WRAPPER
- - - -
Some may call this a “hack” and it is certainly not the cleanest way to achieve a functional menu, but doing this without any reliance on Javascript was my goal. The .nav-wrapper class is built mobile first, and made responsive by media queries. It starts out as a centered logo and a hamburger menu (I just use a span with unicode  &#x2630;).  I used the :checked pseudoclass and hid the checkbox, leaving the label for the checkbox (the unicode span) as a clickable object. I used some transitions to animate the opening and closing of the menu, and transform to create a dropdown slide effect.  See the code in the NAV-LINKS section for clarification.
 *I really wanted to push the rest of the content down instead of rolling over it with the nav, but I haven’t found a way without javascript or the mythical parent selector.*

## NAV-LINKS
- - - -
The nav links class is supposed to be included on the div that contains the. navigation items. I prefer to code this as follows:
```
<nav class=“nav-wrapper”>
	<h1 class=“logo pb-1”>LOGO</h1>
	<input type="checkbox" id="hamburger-toggle" class="hamburger-toggle">
	<div class=“nav-links mb-3”>
		<ul>
			<li>item 1</li>
			<li>item 2</li>
			<li>item  3</li>
		</ul>
	</div>
	<label for="hamburger-toggle" class="ml-1 hamburger-toggle-label">
        	<span class="white">&#x2630;</span>
      	</label>
</nav>
```
Notice the additional classes **“.hamburger-toggle”** and **“.hamburger-toggle-label”**. If you want to use the checkbox method for a dropdown nav, you will need to label them with these classes.

## CONTENT
- - - -
I use this class to wrap the main part of the body, excluding the nav and footer. It is used to make content stay out of these areas since they are positioned absolutely. You should only have one content div. I would probably use it as a class for ```<main>```


## GRID & GRID-ITEM
- - - -
A template for your grid/grids that appears in the base css and the media queries to make the site fluid. Use this as a class for a div that will be your grid “container”. Fill it with .grid-item1, .grid-item2, etc.
My layout leaves the grid-items blank so each grid-item fills the viewport until the second media query.  I started out  with 1 column and 1 row, then went to 2 columns / 2 rows, then 6 col / 3 rows, and finally 12 col / 3 rows for the desktop breakpoint.


## MEDIA QUERIES
- - - -
Include a meta tag for the viewport with width=device-width in your html files. I included 4 breakpoints in the CSS because I don't like to have a ton of them. Feel free to add more as needed. All breakpoints are min-width since the design is mobile first. I believe this is the best practice these days. 


## OTHER NOTES
- - - -
This framework is only a CSS file and a demo html file showing the concepts. Dig into the CSS and make it work for your style preferences. Maybe you have better ways to do things, or maybe you will learn something new. I've tried to emphasize that this is more a learning tool for new developers than a rapid prototyping framework like bootstrap. It only includes the “bare bones" that you will likely use in every site design. Enjoy!


## ABOUT ME
- - - -
I am a new developer (~1 year ago I started learning html in the evenings and branched out from there.) I want to get a better grasp on design concepts and best practices instead of limiting myself to using standard templates or bootstrap for my projects. I am currently looking for a position in the web development industry. As a new developer, I am constantly learning and am very passionate about writing code.  My experience so far has been mostly with Django and PHP, I am of course familiar with HTML and CSS, but always trying to dig deeper. Recently I completed a certificate program in Web development and earned a 4.0 GPA. If your team could benefit from my current skills, and are willing to help me take the next step on my coding journey, please reach out to me through my website at rltomlinson.com.
