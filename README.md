# SCSS

# SCSS
SCSS tutorial

### Variables
$fontSize :1.125rem;
$showBgColor : lightgreen;
$hideBgColor : red;
$bgColor : grey;
$font-heightlight : 'Bree serif';
$body: #fefefe;
$header:#226666;
body {
	font-family: sans-serif;
	text-align: center;
	padding: 3rem;
	font-size: $fontSize;
	line-height: 1.5;
	transition: all 725ms ease-in-out;
}

### nesting 

.main{
	background-color: $body;
	//normal nesting
	h1{
		color: $showBgColor;
	}
	
	p{
		color: blue;
		font-style: bold-italics;
	}
	
	.hide{
		background-color: $hideBgColor;
	}

	.show {
		background-color: $showBgColor;
	}
}

#### nesting with &
button {
	cursor: pointer;
	appearance: none;
	border-radius: 4px;
	font-size: 1.25rem;
	padding: 0.75rem 1rem;
	border: 1px solid navy;
	background-color: $bgColor;
	color: white;
	// nesting using &
	&:hover {
    color: black;
		font-size : 2rem;
  }
}

### mixin and include

mixin allow you to create a function construct in SCSS where you can pass parameters to the style.
@inclue is to call the mixin

// mixin
@mixin absolute-center() {
  position:relative;
  left:50%;
  top:50%;
  transform:translate(-50%,-50%);
}
.element-1 {
   // @inclue is to call the mixin
  @include absolute-center();
}
.element-2 {
  @include absolute-center();
  color:blue;
}


### Mixins with content blocks
<TODO>

### @import and @use

The examples below demonstrate how to chunk files and import them into one parent file using @import.

normalize.scss:

body {
  padding:0;
  margin:0;
}
body, html {
  width:100%;
  min-height:100%;
}
styles.scss:

@import 'normalize';

content {
  max-width:660px;
  // and more styles
}

When using @import, all the variables, mixins, etc. become globally accessible, which is a problem when you have complex file structures and use libraries. For this reason, using @importis now officially discouraged.

The solution is @use.

### @use

Files imported with @use are called modules. To use mixins or variables of these modules, we have to call them using namespaces. By default, the namespace is the filename (without the extension).

src/_colors.scss:

$accent-color: #535353;
@mixin dark-background {
  background-color:#000;
  color:#fff;
}

You can also use a custom namespace using as.

@use 'src/colors' as c;
body  {
  color: c.$accent-color;
}

### Flow control rules
There are four types of flow control rules: @if /@else, @each, @for, and @while.

//color pallet using @each
$myColors : black,red,blue,green,violet,indigo,yellow,orange,white;

@each $myColor in $myColors {
  .dynamic-color-#{$myColor} {
    @extend .square;
    background-color: $myColor;
  }
}


