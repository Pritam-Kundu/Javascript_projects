# BMI Calculator
Input your height and weight and then click on the 'calculate' button to calculate your BMI & it also says whether its normal or not

## HTML & JS code is written below

### Code
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Project 2</title>
    <link rel="stylesheet" href="fun.css">
</head>
<body>
    <div class="container">
        <h1><u>BMI Calculator</u></h1>
        <form action="">
            <p><label for="height">Height in cm: <input type="text" name="" id="height"></label></p>
            <p><label for="weight">Weight in kg: <input type="text" name="" id="weight"></label></p>
            <button>Calculate</button>
            <br>
            <br>
            <div id="result"></div>
            <br>
            <br>
            <div id="weight-guide">
                <h2>BMI Weight Guide</h2>
                <p>Under Weight: Less than 18.6</p>
                <p>Normal Weight: 18.6 to 24.9</p>
                <p>Over Weight: More than 24.9</p>
            </div>
        </form>
    </div>
</body>
<script>
    const form = document.querySelector('form')

    // If we will take height before eventListener() then it will take empty values ,, which is not expected
    // const height = parseInt(document.querySelector('#height').value)

    form.addEventListener('submit',function (e){
        e.preventDefault()

        const height = parseInt(document.querySelector('#height').value)
        const weight = parseInt(document.querySelector('#weight').value)
        const result = document.querySelector('#result')

        if(height < 0 || height === '' || isNaN(height)){
            result.innerHTML = `${height} not expected, Enter a valid height`
        }else if(weight < 0 || weight === '' || isNaN(weight)){
            result.innerHTML = `${weight} not expected, Enter a valid weight`
        }else{
            const bmi = (weight / ((height * height)/10000)).toFixed(2)

            if(bmi < 18.6){
                result.innerHTML = `<span>Your BMI is: ${bmi}, and this is under weight</span>`
                result.style.backgroundColor = 'blue';
                result.style.padding = '10px';
                result.style.color = 'white';
            }else if(bmi >= 18.6 && bmi <=24.9){
                result.innerHTML = `<span>Your BMI is: ${bmi}, and this is normal weight</span>`
                result.style.backgroundColor = 'green';
                result.style.padding = '10px';
                result.style.color = 'white';
            }else{
                result.innerHTML = `<span>Your BMI is: ${bmi}, and this is over weight</span>`
                result.style.backgroundColor = 'red';
                result.style.padding = '10px';
                result.style.color = 'white';
            }
        }
    })
</script>
</html>
```
The 'label' tag just expands the mouse clicking area nothing else

## CSS code goes here

### Code
```
h1{
    text-align: center;
    padding: 12px;
}
p{
    text-align: center;
    font-size: 20px;
}
button{
    height: 40px;
    border: 2px solid black;
    border-radius: 10px;
    margin-left: 50%;
}
#result{
    font-size: 16px;
    padding: 10px;
    font-weight: bolder;
    text-align: center;
    margin-left: 20%;
    margin-right: 20%;
}
#weight-guide{
    background-color: grey;
    padding: 16px;
    border-radius: 10px;
}
h2{
    text-align: center;
    padding: 12px;
    background-color: yellow;
}
```