# Digital Clock

Here the time updates in every second.

## The HTML code goes below
### Code
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Project 3</title>
    <link rel="stylesheet" href="fun.css">
</head>
<body style="background-color: grey;">
    <div class="container">
        <div id="banner"><span>Your Local Time</span></div>
        <div id="clock"></div>
    </div>
</body>
<script>
    const clock = document.getElementById('clock')

    setInterval(function(){
        let date = new Date()
        clock.innerHTML = date.toLocaleTimeString()
    },1000) 
</script>
</html>
```
In the js part a function is used named 'setInterval()'.This function is used when a certain part of code is being called in time interval. 
Remember the foramt of the function that is:
```javascript
    setInterval(function(){
        //Code
    },1000) 
```
In this function another function has been written, and afterthat a 1000 is the time interval which is in miliseconds(1ms = 1sec).It can be 2000 also.

## The CSS Code goes below
### Code
```css
.container{
    text-align: center;
    margin-top: 20%;
}
#clock{
    padding: 15px;
    background-color: yellow;
    margin-left: 40%;
    margin-right: 40%;
    border-radius: 5px;
    font-size: x-large;
}
span{
    font-weight: bolder;
    font-size: larger;
}
```