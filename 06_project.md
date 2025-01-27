# Pressed Key Identifier
It identifies the key pressed by you in the keyboard and also displays the keycode and code for that key

## Here is the HTML and JS part
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pressed Key Identifier</title>
    <link rel="stylesheet" href="fun.css">
</head>
<body style="background-color: black; color: thistle;">
    <p id="text">
        <h2>Press any key to see the key code and the key itself.</h2>
    </p>
    <div id="insert">
    </div>
</body>
<script>
    const insert = document.getElementById("insert");

    window.addEventListener("keydown", (e) => {
        insert.innerHTML = `
        <div>
            <table>
                <tr>
                    <th>Key</th>
                    <th>Key Code</th>
                    <th>Code</th>
                </tr>
                <tr>
                    <td>${e.key === " " ? "Space" : e.key}</td>             
                    <td>${e.keyCode}</td>
                    <td>${e.code}</td>
                </tr>
            </table>
        </div>
        `;
    });
</script>
</html>

```

## CSS part goes here
```css
h2{
    text-align: center;
    font-style: italic;
}
#insert{
    margin-top: 15%;
    margin-left: 40%;
    color: seashell;
}
tr,th,td{
    border: 1px solid white;
    font-size: x-large;
}
```
