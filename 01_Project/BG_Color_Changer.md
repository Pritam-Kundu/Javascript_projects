# Background Color Changer

## This is the html part for the project
### Code:

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Project 1</title>
    <link rel="stylesheet" href="fun.css">
    
</head>
<body style="background-color: black; color: aliceblue;">
    <h1><u>Backgroud Color Changer</u></h1>
    <span class="button" id="grey">Grey</span>
    <span class="button" id="white">White</span>
    <span class="button" id="yellow">Yellow</span>
    <span class="button" id="red">Red</span>
    <br>
    <br>
    <br>
    <p><i>Click on a color to change the background color of the page</i></p>
</body>
<script>
    const buttons = document.querySelectorAll('.button')
        const body = document.querySelector('body')

    buttons.forEach(function (button){
        button.addEventListener('click',function (e){
            if(e.target.id === 'grey'){
                body.style.backgroundColor = e.target.id;
            }
            else if(e.target.id === 'white'){
                body.style.backgroundColor = e.target.id;
            }
            else if(e.target.id === 'yellow'){
                body.style.backgroundColor = e.target.id;
            }
            else if(e.target.id === 'red'){
                body.style.backgroundColor = e.target.id;
            }
            
        })
    
    })
</script>
</html>

```

## This is the css part for the project

### Code:

```
h1{
    text-align: center;
    padding: 12px;
}
.button{
    border-radius: 100%;
    padding: 30px;
    border: dashed rgb(21, 0, 255);
}
#grey{
    background-color: grey;
    color: black;
}
#white{
    background-color: whitesmoke;
    color: black;
}
#yellow{
    background-color: yellow;
    color: black;
}
#red{
    background-color: red;
    color: black;
}
p{
    text-align: center;
    font-size: 20px;
}
```