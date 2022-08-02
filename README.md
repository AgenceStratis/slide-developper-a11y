AccesSlide
===========

A HTML5-CSS3-JS framework for accessible keynotes.
[Version française](READMEFR.md)

# Install

Install grunt globally with npm.

```npm
npm install -g grunt
```

Go to your folder where you want to install the project and launch the installation.

```npm
npm install
```

Run the project

```npm
grunt
```

# Structure
Put the slides in the `main` element with `section` elements associated with a `slide` class.
`section` elements can be imbricated in `section` elements.

The first and the last slide need an extra class: respectively a `couv` and `end` class.

## Short example of structure
	<section class="slide">
	 <h2>Heading of the slide</h2>
	 [content]
	</section>
	
	<section class="slide" aria-label="heading of the slide">
	 [content]
	</section>

# Hide elements
Every `html` elements of a slide can be hidden using the `Cmasque` class, they will appear with the action next slide.

# Navigation
The navigation bar has (in order of appearance):

*  a previous button;
*  a selection list: select the number of the slide you want to reach;
*  a next button;
*  a table of contents: reach a slide through its title;
*  a pagination;
*  a configuration button.

## Keyboard navigation

*   `SPACE` or `RIGHT ARROW` or `Click` Next slide
*   `SHIFT` + `SPACE` or `LEFT ARROW` Previous slide
*   `Start` First slide
*   `End` Last slide
*   `ALT + 0 (zero)` Table of contents

To go to the next slide with Jaws: ignore the next keystroke (using INSERT + 3) then press SPACE to make the slideshow scroll.

With NVDA, ignoring the next key is not necessary, the SPACE keystroke works.

## Remote navigation

You can navigate in the slideshow with a remote.
Use the equivalent of `LEFT ARROW` and `RIGHT ARROW`.

#Effects

The available effects can be set in the configuration panel.

Create your own effect:

1.  Create a `class`, for example `.my-effect`.
2.  In the [AccesSlide.js](AccesSlide.js) file, create an entry in the `config` object (see the instructions in the file at the `Effects` section).
3.  In the language file: create an entry for the tag's effect. Warning: the entry in the language file must have the same name than the `config` object.

# CSS

2 CSS files are necessary:

*   [css/style.css](css/style.css) general properties of the slideshow;
*   [css/themes/default.css](css/themes/default.css) theme.

##Themes

Several themes are delivered with AccesSlide in the folder [css/themes](css/themes).

	<!-- Theme stylesheet -->
	<link rel="stylesheet" href="css/themes/default.css" type="text/css" media="all" />

## Post-processor

The CSS is generated by the post-processor [Myth](http://www.myth.io/).

Source files are in the [css/sources](css/sources) folder and in the [css/sources/themes](css/sources/themes) folder for themes.
Compiled files are in the [css/themes](css/themes) folder for themes and in the [css/](css/) folder for the general layout.

Every file is also available in a non-minified version. This lets you change or create your own CSS without using a post-processor.

## Automation with Grunt
A minimal Grunt configuration is also available for CSS compilation. 4 modules are configured in [Gruntfile.js](Gruntfile.js):

*   [grunt-myth](https://www.npmjs.com/package/grunt-myth): to compile CSS;
*   [grunt-contrib-cssmin](https://www.npmjs.com/package/grunt-contrib-cssmin): to minify CSS;
*   [grunt-combine-media-queries](https://www.npmjs.com/package/grunt-combine-media-queries): to combine media queries;
*   [grunt-contrib-watch](https://www.npmjs.com/package/grunt-contrib-watch).

## Responsive design
The slideshow will adapt to the size of the font and the size of the window.

## Print
A [print.css](css/print.css) style sheet provides a layout for printing from the browser (Ctrl + p)

Only some of the styling from the chosen theme is kept on print (property `all` from the theme's CSS). To hide an element or an entire section on print, add a `noprint` class.

    <section class="slide noprint">
     [content]
    </section>

# Customizing the interface

Icons (toolbar, configuration panel) are generated thanks to fontawesome.

If the font is not loading, images in the [img](img/) folder take over. This fallback is provided by the a font garde script from the Filament Group.

AccesSlide CSS files don't include the entire fontawesome library. To edit an icon, check the [fontawesome documentation](http://fortawesome.github.io/Font-Awesome/icons/) and edit the AccesSlide CSS file with the required code.

# Accessibility parameters

You will find these parameters in the configuration panel. The parameters are persistent (use of <code>cookies</code> or of <code>localStorage</code> when possible). Use the <kbd>Default</kbd> button to go back to the default configuration.

* **Slide number** Read the slide number when displayed.
* **Hidden content** Beep when a hidden content appears.
* **Slide** Beep when displaying a slide.
* **First slide** Beep at the first slide.
* **Last slide** Beep at the last slide.
* **Heading** Read the heading of the current slide.
* **Window heading** Update the window heading when a slide is displayed.
* **Next button** Place the focus on the “Next” button when the slideshow is loading.
* **Click** Remove the click action (and the space bar) to display the next slide.


#Other parameters

* **Table of contents**: Chose the behavior of the table of contents (modal or modeless). Slides are resized if the table of contents is modeless.
* **Sweep** : Chose the mode (Javascript or CSS3) for the animations of the sweep panel.
* **Outline view**: Display the slideshow linearly.

Configure these parameters in the configuration panel.

# JavaScript
You can use your own scripts in the html page or in the [slide.js](en/slide.js) file.

# Outline view

The outline view displays the slideshow linearly, allowing you to prepare and check the content of your presentation more quickly.

Use the `configuration panel` to activate the outline view.
The `CSS` styling of the slides is kept, but the effects aren't. The pagination and markers are there to help visualizing the content of each slide.

# Localization

All elements of the interface can be localized using a language file ([lang](lang/) folder).

To use a language file, edit the file path in the `head` of the page. Here is an example for the French file: `<script type="text/javascript" src="lang/lang_fr.js"></script>`.

## Create a language file

* Open the language file with a text editor
* Edit the buttons labels `label`, image alternatives `alt`, options values `value` of the effects list, buttons or windows titles `title` and help messages `help`
* Save your language file using the filename `lang_[language code].js`

Check out the live demo: www.accesslide.net