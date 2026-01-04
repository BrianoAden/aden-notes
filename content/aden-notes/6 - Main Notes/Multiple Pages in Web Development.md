---
publish: "true"
---
2025-08-24 17:12

Status: 

Tags: [[Web Development]] [[React]]

# How to Use React JS to Create Multiple Pages

This note page is meant to document how to create multiple, separate pages for any website. 

First thing to do is go to your tab page, where there should exist an *index.html* file. This is your home page. Your other pages will also be .html files, with any name you like.

In my case, I used React JS to create my portfolio. So we will be using React for this tutorial. First thing you need to do is run 

```javascript
npm i react-router-dom
```

npm is the node package manager we are using to manage packages, i stands for install, and react-router-dom is the library we are pulling the router from. This allows for you to route pages together! 

Good practice is to have two separate folders *Components* and *Pages* to separate component and page .jsx files. *Components* houses buttons, and other javascript interactive elements. *Pages* is where your pages will go. App.jsx goes outside of your *Pages* folder, but should be treated as the page that houses *all of your other* pages. In your other pages, you will need a base function that returns a header tag. This looks like 

```javascript
export function Page() {
	return (
		<>
			<h1> This is Page </h1>
		</>
	)
}
```

Now, in our App.jsx file, we need to create the routes to our pages. First, make the following imports

```javascript
import { BrowserRouter, Routes, Route } from 'react-router-dom'
```

You will also need to import any pages you create routes to. This might look like 

```javascript
import { Page } from ./Pages/page
```

BrowserRouter is our Router component. Routes is a component where we can specify all the potential routes of our router. Route is the component we use for each individual page. Your App() function should look like 

```javascript
function App() {
	return(
		<BrowserRouter>
			<Routes>
				<Route path="/" element={<Home/>}/>
				<Route path="/page1" element={<Page1/>}/>
				<Route path="/page2" element={<Page2/>}/>
			</Routes>
		</BrowserRouter>
	)
}
```

The first route is our default route. This is typically our landing page.*path* is the path to the page. *element* is where we pass our components of our page, which allows us to render the page. 

To create links that link the pages together and allow for quick and easy traversal, you will need to use a component called Link. In our home.jsx file in *Pages*, do the following

```javascript
import { Link } from "react-router-dom"
	
	export function Home() {
	return (
		<>
			<h1> This is the home page </h1>
			<Link to="/"> Home </Link>
			<Link to="/page1"> Page 1 </Link>
			<Link to="/page2"> Page 2 </Link>
		</>
	)
}
```

*to* needs to map to the exact path of the page specified in the Route component. You can add these links to all pages, or build a Navbar.jsx component! This will house the links to all of your pages.  

**NOTE:** You can use *href* to link to your pages, however it will not work when you deploy the website. You will need to use the *Link* component from *react-router-dom*.

You also need to create a *vercel.json* file in your root directory. In this file you will add

```javascript
{
	"rewrites": [
		{"source": "/(.*)", "destination": "/" }
	]
}
```
	
This will redirect all subpages to the index page and get rid of your 404 Error (which you will have if you do not do this).
# References
[React JS Tutorial #7 - Multiple Pages](https://www.youtube.com/watch?v=qi32YwjoN2U&ab_channel=AustinDavis)
[SPA Routing](https://medium.com/today-i-solved/deploy-spa-with-react-router-to-vercel-d10a6b2bfde8)