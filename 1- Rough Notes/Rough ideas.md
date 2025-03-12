
HTML & CSS - The languages that we use to describe the structure and style of the webpage

HTML & CSS:-
	HTML5 and CSS3
	- It is helpful to think about the webpage as a tree like structure. We call this tree like structure as DOM. 
Good html tags:
	- ol, ul, li
	- IMG tag does not have a closing tag. It is a single html tag that can not have anything inside of it. That's why it is a self-closing tag.
	- `<img src="cat.jpg" alt="cat" width="300px">` when we control the width, it automatically scales down the height, to keep the image proportional.
	- Using `href` attributes we can provide link to other html pages inside our own website too.
	- use `<thead>`tag, and `<th>` for representing each header column in the table. It will make the columns as bold 
	- `<tbody>` tag to write about the table body, and `<tr>` tag to write about each table row. and `<td>` tag to write about each of the individual cell data
	- Any place where user can provide some input in html webpage, is considered as a `form` in HTML. (Ex, in google, we can provide our input inside the search bar)
	- form tag:
	```
	
```
        <form>

            <input type="text" placeholder="Full Name" name="name">

            <input type="submit">

        </form>
```

- Other various `form` tags in use:
	- userid and password 
		- `<input name="name" placeholder="userid" type="text">`
		- `<input name="name" placeholder="password" type="password">`
	- radio buttons
		- `<input name="color" type="radio" value="red"> Red`
	- datalist
		- User chooses from a dropdown listing various options. We want to very quickly filter down the options as we start to type.


CSS: Styling the webpage
	- We can give html elements individual CSS properties. where property is sth like color of the element or the alignment of the element. Each of these propery already has a default value, but we can change these values to our needs.
	- `<h1 style="color: blue;"> Welcome to my web page</h1>`
	- HTML elements can also get their styling details from their parent element as well. Remember it follows the DOM structure.
	- Inline Styling: Taking the CSS code and placing it directly as an attribute inside the HTML elements.
	- Moving the style code, to a completely new CSS file.
		- Head section is a great place to start keeping the style information for the webpage.
	- Most common CSS properties:
		- background-color
		- width : 200px
		- height : 400px
		- padding:
			- Adding some space in a HTML element, so that the content of the element is not so close to the border of the element itself.
			- padding: 20px;
			- space inside to the border of the element.
		- margin:
			- If we have an HTML element which is too close to the edge of the screen, may be It's too close to the top of the screen. We can also add space around outside the element. We call this space as margin.
			- margin: 20px;
			- space outside to the border of the element.
		- font:
			- Always specify multiple different fonts, so that if a specific font is not supported inside the browser, we fall back to a different font. (sans-serif font is a default font)
			- font-family, font-weight, font-size, border
		- table:
			- border, border-collapse, padding
	- Controlling styling for individual elements:
		- Give that HTML element an `id`, then use that to do the actual styling. `id` are unique in a webpage.
		- We need to style the attribute as: (We use # for it. Only style element with id=foo)
			#<id> { color: red}			
		- Giving name to multiple HTML elements that is not unique: class
			- .<id> { color: red}	
			- (We use `.` for it. Only style element with class=foo)
		- Now we have multiple ways to style the same thing. It comes under CSS Specificity.
		- What is the applicable, if more than 1 selector applies to the same CSS element,
		- inline > id > class > type (Precedence order)
	
	- CSS Selectors:
	![[css_selectors.png]]

- Pseudoclass Selector:
	- use to do some action/feedback, when user perform some action. Example change the color of a HTML element when you hover on it. Check it on Facebook website, what kind of hovering they are doing.
	- button:hover { background-color: orange}

- Responsive Design: (support all types of media which can access the webpage)
	- You can access the webpage on mobile phones too.
	- Ideas:
		- viewport
			- Visual part of the screen that the user can see.
			- `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
			- It is providing some metadata to our webpage and saying that, I would like you to change the viewport to specifically the width of the device.
		- Media Queries
			- Controlling how our page is going to look, depending on what size screen we render the webpage.
			- Example: Changing the color of webpage if it is rendered on mobile device as compare to laptop
			- Any css property can be controlled in media queries.
		- Flexbox
			- these are used to move things around based on the screen size. 
		- Grids
			- Any time you want to arrange some section to be of certain width while other columns could be of variable size.
		- Bootstrap:
			- These are libraries that exist out in open, where people have written a lot of CSS to make our buttons, texts etc look good.
			- One of these libraries is 'Bootstrap'.
			- Bootstrap has a separate mechanism to make webpage to be mobile responsive. It uses a model known as `bootstrap-column-model`
			- Bootstrap divides the webpage into 12 columns
			- Bootstrap columns are also mobile responsive and can do wrap around and stuff.
				- <div class="col-lg-3 col-sm-6"> It means that on large screen this col will take space of 3 units (there by 4 such col cane be present in a row) where as in the smaller screen it will take up 6 unit of space.
			- SAAS language:
				- It allows the use of variables inside the CSS. It's file are named as `variables.scss`
				- All variables begin with a $ sign.
				- Also you can write normal css into this file.
				- We need to compile this file to generate a css out of it. 
				- sass <file_you_want_to_compile>:<file_you_want_to_generate>
				- sass variables.scss:variable.css
				-  It will be cumbersome to keep compiling the new file once we make changes to the scss file.
				- We can use a command
				```shell
					sass --watch variable.scss:variables.css
				```
				- sass gives a better control for nesting elements, styling tasks
				- It allows inheritance feature as well.
		- Python:
			- NoneType signifies - Absence of the value
			- 