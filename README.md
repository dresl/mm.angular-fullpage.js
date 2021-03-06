# MM Angular fullPage.js
Angular directive for use the [jQuery fullPage.js library](https://github.com/alvarotrigo/fullPage.js) on Angular.js v1.x


---------------------


This code is a completely adapted version of [fullPage.js library developed by Alvaro Trigo](https://github.com/alvarotrigo/fullPage.js) for working with Angular.js v1.X.


---------------------

**Donate for this project!!**


[![Donate](https://www.paypalobjects.com/en_US/GB/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=9MCU8ESDM26KC&lc=ES&item_name=angular%2dfullpage%2ejs&currency_code=EUR&bn=PP%2dDonationsBF%3abtn_donate_LG%2egif%3aNonHosted)

**Donate for original jQuery project (Alvaro Trigo)!!**

[![Donate](https://www.paypalobjects.com/en_US/GB/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=BEK5JQCQMED4J&lc=GB&item_name=fullPage%2ejs&currency_code=USD&bn=PP%2dDonationsBF%3abtn_donateCC_LG%2egif%3aNonHosted)

## Working example ##
You can check a working example on our [company website, http://www.mmautomatizacion.com](http://mmautomatizacion.com)

## Installation ##
This library works with `jQuery`, so we have to include this library.

Then, you have to include the *MM Angular fullPage.js* library into the HTML. Download the last release from github and include the source or minified file like another JS code:

```html
<script type="text/javascript" src="mm.angular-fullpage.min.js"></script>
```

You also have to include the CSS stylesheet
```html
<link type="text/css" rel="stylesheet" href="mm.angular-fullpage.min.css">
```


### Using Bower or NPM ###

You can install MM Angular FullPage.js using Bower or NPM:

**Bower**
> bower install mm.angular-fullpage.js

**NPM**
> npm install mm.angular-fullpage.js


### Inject module ###
For work, you may inject the directive to your angular app. The module name is `fullpage.js`:
```js
(function() {
	'use strict';

	angular
		.module('app', ['fullpage.js']);
})();
```

## First steps ##
The use of the Angular fullPage directive is very similar to the use of [the original jQuery fullPage.js library of Alvaro Trigo](https://github.com/alvarotrigo/fullPage.js). You only have to use the `full-page` attribute into a div, and define sections and slides.

```html
<div full-page>
  <div class='section' data-anchor='section1'></div>
  <div class='section' data-anchor='section2'>
    <div class='slide' data-anchor='slide1'></div>
    <div class='slide' data-anchor='slide2'></div>
  </div>
</div>
```

### Link to sections and slides ###
For linking, we only have to use this href format: `#!SECTION/SLIDE`. I recommend to use the angular `ng-href` instead of original *href*.

```html
<a ng-href='#!firstPage'>
<a ng-href='#!secondPage/2'>
```


## Options. The Angular FullPage Config Provider ##
For configure the behaviour of Angular fullPage.js we can use a config provider, named 'fullPageConfig', and define the options object throw 'setConfig' function. Here's an complete example with all options:
```js
(function() {
	'use strict';

	angular
		.module('app')
		.config(function(fullPageConfigProvider) {
			fullPageConfigProvider.setConfig({
				//Navigation
		        menu: '#menu',
		        lockAnchors: false,
		        anchors:['firstPage', 'secondPage'],
		        navigation: false,
		        navigationPosition: 'right',
		        navigationTooltips: ['firstSlide', 'secondSlide'],
		        showActiveTooltip: false,
		        slidesNavigation: false,
		        slidesNavPosition: 'bottom',

		        //Scrolling
		        css3: true,
		        scrollingSpeed: 700,
		        autoScrolling: true,
		        fitToSection: true,
		        fitToSectionDelay: 1000,
		        scrollBar: false,
		        easing: 'easeInOutCubic',
		        easingcss3: 'ease',
		        loopBottom: false,
		        loopTop: false,
		        loopHorizontal: true,
		        continuousVertical: false,
		        continuousHorizontal: false,
		        scrollHorizontally: false,
		        interlockedSlides: false,
		        dragAndMove: false,
		        offsetSections: false,
		        resetSliders: false,
		        fadingEffect: false,
		        normalScrollElements: '#element1, .element2',
		        scrollOverflow: false,
		        scrollOverflowReset: false,
		        scrollOverflowOptions: null,
		        touchSensitivity: 15,
		        normalScrollElementTouchThreshold: 5,
		        bigSectionsDestination: null,

		        //Accessibility
		        keyboardScrolling: true,
		        animateAnchor: true,
		        recordHistory: true,

		        //Design
		        controlArrows: true,
		        verticalCentered: true,
		        sectionsColor : ['#ccc', '#fff'],
		        paddingTop: '3em',
		        paddingBottom: '10px',
		        fixedElements: '#header, .footer',
		        responsiveWidth: 0,
		        responsiveHeight: 0,
		        responsiveSlides: false,

		        //Custom selectors
		        sectionSelector: '.section',
		        slideSelector: '.slide',

		        lazyLoading: true,
			});
       	});

})();
```

We can also add events in the config object:

```js
(function() {
	'use strict';

	angular
		.module('app')
		.config(function(fullPageConfigProvider) {
			fullPageConfigProvider.setConfig({
				lazyLoading: true,
				onLeave: function(index, nextIndex, direction){},
		        afterLoad: function(anchorLink, index){},
		        afterRender: function(){},
		        afterResize: function(){},
		        afterResponsive: function(isResponsive){},
		        afterSlideLoad: function(anchorLink, index, slideAnchor, slideIndex){},
		        onSlideLeave: function(anchorLink, index, slideIndex, direction, nextSlideIndex){}
			});
       	});

})();
```

You can find complete information about options in the [original jQuery project readme](https://github.com/alvarotrigo/fullPage.js#initialization).


## Methods. The Angular FullPage Service ##
You can interact with Angular FullPage by the Angular FullPage Service. Only you have to do is inject the service "fullPageService" and enjoy. There is an example that move section up on load:
```js
(function() {
	'use strict';

	angular
		.module('app')
		.controller('app.indexCtrl', indexCtrl);


	indexCtrl.$inject = ['fullPageService'];


	function indexCtrl(fullPageService) {
		fullPageService.moveSectionUp();
	}

})();
```

You can find all the possible methods to configure in the [original jQuery project readme](https://github.com/alvarotrigo/fullPage.js/blob/master/README.md#methods).

### Current Section and Slide ###
We have added an additional method to the original project, named "status". This one allow to know which section and slide are on screen.

```js
fullPageService.status.anchorLink; // Current section anchor
fullPageService.status.sectionIndex; // Current section index
fullPageService.status.slideIndex; // Current slide index
fullPageService.status.slideAnchor; // Current slide anchor
```

## Events (callbacks) ##
All the events about Angular Fullpage are emitted by $rootScope. It allow to access this events in any controller of the app. 

- `fp-afterLoad` data => { *anchorLink* , *index* }
- `fp-onLeave` data => { *index* , *nextIndex* , *direction* }
- `fp-afterRender` data => {  }
- `fp-afterResize` data => {  }
- `fp-afterResponsive` data => { *isResponsive* }
- `fp-afterSlideLoad` data => { *anchorLink* , *index* , *slideAnchor* , *slideIndex* }
- `fp-onSlideLeave` data => { *anchorLink* , *index* , *slideIndex* , *direction* , *nextSlideIndex* }

**How to use**
```js
$rootScope.$on('fp-afterLoad', function(event, data) {
	console.log(data);
});
```


## What's next? ##
For further information and complete documentation, you have to access the official site of [the original jQuery fullPage.js library](https://github.com/alvarotrigo/fullPage.js)



## Keep in mind ##
 - This project contains the complete code of the original modified for work with Angular. **Is not necessary (and not recommended) to include the jQuery original library**.
 - Angular fullPage.js is not compatible with Angular routing (ngRoute, uiRoute...).
 - You *can* use **HTML5 mode**.
 - If you have any doubt, contact me.