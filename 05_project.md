# Automatic Background Color Changer

When you start then the color will start changing randomly after every 1 second and if you hit the stop button then the background color changing will be stopped
## Here is the whole code using HTML, CSS, JS

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Background Color Changer</title>
    <style>
        body{
            background-color: black;
            color: antiquewhite;
        }
        h1{
            text-align: center;
        }
        button{
            padding: 5px;
        }
        
    </style>
</head>
<body>
    <h1>Changing Background Color Randomly</h1>
    <ul>
        <li><h5>Click the start button to start changing of colors</h5></li>
        <li><h5>Click the stop button to stop changing of colors</h5></li>
    </ul>
    <button id="start">Start</button>
    <button id="stop">Stop</button>
</body>
<script>
    let randomColor = function(){
        const hex = "0123456789ABCDEF"
        let color = '#'
        for(i=0; i<6; i++){
            color += hex[Math.floor(Math.random() * 16)]
        }
        return color;
    };

    let randomColorId

    let startChangingColor = function(){
        function bgcolor(){
            document.body.style.backgroundColor = randomColor();
        }
        randomColorId = setInterval(bgcolor,1000)
    }

    let stopChangingColor = function(){
        clearInterval(randomColorId)
    }

    document.querySelector('#start').addEventListener('click', startChangingColor)
    document.querySelector('#stop').addEventListener('click', stopChangingColor)
</script>
</html>
```
