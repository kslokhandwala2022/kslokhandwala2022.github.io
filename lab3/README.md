
# Lab 3:  Forms

In this lab we will continue to develop our web app. You will learn to:

- Create and style HTML 5 forms
- Use JavaScript to validate your forms

**Note:** Teaching staff will evaluate your lab using Chrome Developer tools configured for an iPhone 6/7/8, so this is what you should be testing with. In Chrome, go to View -> Developer tools, and then make sure iPhone 6/7/8 is listed.
![](https://github.com/cs3041-hci-D20/lab3/blob/master/img/image1.png)

## Task

Create a registration form with validation similar to the following form (use iOS mobile device or simulator to open):
https://users.wpi.edu/~esolovey/cs3041/lab3/location.html

## Step-by-Step Tutorial

**Step 0:** Fork this repository ([Help](https://help.github.com/en/github/getting-started-with-github/fork-a-repo)) so that you have a copy of if in your Github account. 

**More Step 0:** Clone your *lab3* repository so that you have a local copy on your computer

**Step 1:** 
- Create a new HTML 5 file called register.html. 
- Create a new CSS file called forms.css

Before we start designing our registration form, it is worthwhile thinking more broadly about the design of sign-up forms. Is there anything to design in a minimalistic sign-up form? Isn’t it too simple to focus on? Read this thoughtful discussion of the [UX design of sign-up forms](https://designmodo.com/ux-sign-up-form/).
 
*Step 2:* Working in register.html, create an empty registration form:
```
<!DOCTYPE html> 
<html>   
<head>     
	<meta name="apple-mobile-web-app-capable" content="yes">    
	<meta name="apple-mobile-webapp-status-bar-style" content="black">
	<meta name="viewport" content="width=device-width, user-scalable=no" >     <title>Register</title>     
	<link rel="stylesheet" href="forms.css">
	<link rel="stylesheet" href="style.css">
</head>   
<body> 	
	<header class="secondary"> Sign up! </header>     
	<button class="back" onclick="location.href='index.html';">Back</button>     
	<div class="info">     
		<p>Register now to take advantage of this site. </p>    
		<form method="post" id="register" >             
			<!-- FORM FIELDS GO HERE -->       
			<br />       
			<input type="submit" value="Sign up">       
			<a href="index.html">Nevermind</a>      
		</form>          
	</div> 
	<script src="stay_standalone.js"></script>         
</body> 
</html>
```
**Step 3:** Now add form fields (study and then copy the code below) to your document inside the form tags (in the HTML code there is a comment that specifies where to add the code). 

HTML5 introduces a number of new input types. These new input types give hints to the browser about what type of keyboard layout to display for on-screen keyboards. This tutorial provides a detailed summary of all new HTML 5 input types and their support by various browsers.

Note that in the code below we add a label and an error message for each form field. Next we will style  the form so that the error message is hidden and the labels appear above the form fields.

```
<label for="name">Your Name:</label>
<div class="error" id="name-error">Name is a required field.</div>
<input type="text" name="name" id="name">

	<label for="email">Email:</label>
	<div class="error" id="email-error">Email is a required field.</div>
	<input type="email" name="email" id="email">
	<label for="dob">Date of Birth:</label>

	<div class="error" id="dob-error">Date of birth is a required field.</div>
		<input type="date" name="dob" id="dob">  
		<label for="pwd">Password:</label>
	<div class="error" id="pwd-error">Password is a required field.</div>       
<input type="password" name="pwd" id="pwd">
```

✔️ **Checkpoint:** For now, here’s what your register.html file should look like in a browser window. 
Test your form and observe the different on-device keyboards that are displayed for each input type.
![](https://github.com/cs3041-hci-D20/lab3/blob/master/img/image3.png) 

**Note:** Check this [quick tuto from Lab0](https://github.com/cs3041-hci-D20/lab0#4-create-your-gh-pages-branch) on how you can test your app online or offline

**Step 4:** Now let’s add some style. Switch to forms.css, and add a few rules. 

**Note** that since we linked our register.html file to style.css all the global rules defined in style.css are applied in register.html. In addition, in forms.css we add rules specific to forms.

First let’s add a rule to make the labels appear above the input fields.
```
label {
	display: block;
}
```
**Step 5:** And, adjust the size of the input fields. Use height, font-size, and margin as needed. Write your rules within the input selector.
```
input {

}
```
**Step 6:** Finally, style the form itself as well as the surrounding `<div>` tag. Add your definitions within the form selector. Use padding, margin, border etc. as needed
```
form {

} 
```

✔️ Checkpoint: Here’s what things could look like now: 
![](https://github.com/cs3041-hci-D20/lab3/blob/master/img/image2.png)

**Step 7:** Ok. Time to style the error messages. We want these to float to the right of their corresponding fields, which we can do with the position: absolute property.
```
.error {
	background-color: LightYellow;
	color: DarkRed;
	width: 160px;
	padding: 10px;
	border: 1px solid gray;
	position: absolute;
	left: 120px;
	box-shadow: 3px 3px 3px #999999;
	border-radius: 7px;
}
```
Take a look in the browser. If all goes well, these should look something like post-it notes stuck on the right side of the form. 

**Step 8:** When things look right, add a rule that changes the visibility property in .error to hidden. We’ll use JavaScript to make these error messages appear when they’re needed.

**Step 9:** Finally, we need to fix the Submit button. Here we’re using a special CSS attribute selector to apply a rule only to input elements with the “submit” type.  We will add an image to the button (see below). Also add rules for `width`, `height`, `margin`, and `font-size: 16px;`
```
input[type='submit'] {
	
/* Add more rules here */
	
-webkit-border-image: url("blueButton.png") 0 14 0 14 stretch;
} 
```

## Form Validation

HTML5 offers automatic validation of required fields, and of valid email and web addresses. HTML 5 also validates numbers based on min and max attributes. Automatic validation is supported in Safari version 10.1. To learn more about HTML 5 form validation read [this tutorial](http://diveintohtml5.info/forms.html).

**Step 10:** Next we add a check that a value for a field has been provided.

For each input field in the form, add the required tag.

✔️ Checkpoint: Try it out. If you leave any fields blank, you should see an error message when you press Submit.  

**Step 11:** We will now add styling to the fields, based on the validation and required states. In forms.css, add rules for the required, valid and invalid input. For more info, see this link: https://www.w3schools.com/cssref/sel_valid.asp
```
input:required {
  /* insert your own style to indicate a required form input */
}

input:invalid {
  /* insert your own styles for invalid form input */
 
}

input:valid {
  /* insert your own styles for valid form input */
}
```
**Note:** The order that fields are listed in the CSS file matter, since the stylesheet “cascades”. You can play around with reordering these fields and see how it changes the behavior.

### Submit your work
On Canvas, submit the following: 
- a link to your Github repository
- a link to your Web page (check this quick tuto on [how to create your webpage](https://github.com/cs3041-hci-D20/lab0#4-create-your-gh-pages-branch)).
