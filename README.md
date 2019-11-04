# Push button game

## Introduction @fullscreen

Let's make a push button game

![picture of microbit](https://raw.githubusercontent.com/BrightWearables/pxt-microbit-push-button-game/master/docs/static/PushButtonMicrobitImage.png)

## Step 1: Create a variable named "pushed"

In the ``||variables:Variables||`` menu click "Make a Variable".
When asked, name it ``||variables:pushed||`` 
Drag the new ``||bariables:set pushed to 0||`` block into ``||basic:on start||``, then change the value of pushed to 1 as shown below:

![create a variable](https://raw.githubusercontent.com/BrightWearables/pxt-microbit-push-button-game/master/docs/static/makeVariableMakeCode.gif)

```blocks
pushed = 1
```

## Step 2: Start the game when you shake the micro:bit

Add the ``||input:on shake||`` code block to the editor.
Use the ``||basic:show string||`` to say "wait" when you shake the micro:bit. This means the game is starting..

```blocks
input.onGesture(Gesture.Shake, function () {
    basic.showString("wait")
})
pushed=0
```
## Step 3: Add a random wait time

Add a ``||basic:pause||`` block inside the ``||input:onShake||`` block. Don't set the time for the pause. 
Instead take the ``||math:random from 0 to 10||`` block from the ``||Math||`` menu and place it inside the ``||basic.pause||`` block. Change
the minimum and maximum wait times to 1000 and 5000 milliseconds:
```blocks
input.onGesture(Gesture.Shake, function () {
    basic.showString("wait")
    basic.pause(Math.randomRange(1000, 5000))
})
pushed=0
```
## Step 4: Enable button pushing

Once the wait is over, set the value of ``||Variables:pushed||`` to 0. We'll use this value to let the players push buttons A and B.
Add a ``||basic:show icon||`` block to let the players know it's ok to push the buttons:

```blocks
input.onGesture(Gesture.Shake, function () {
    basic.showString("wait")
    basic.pause(Math.randomRange(1000, 5000))
    pushed = 0
    basic.showIcon(IconNames.Yes)
})
let pushed = 0
pushed = 1
```
## Step 5: Code a response to button pushing
Move an ``||input:on button pressed||`` code block into the editor window.
Place the ``||logic:if||`` block inside it:

```blocks
input.onButtonPressed(Button.A, function () {
    if (0==0) {
    }
})

input.onGesture(Gesture.Shake, function () {
    basic.showString("wait")
    basic.pause(Math.randomRange(1000, 5000))
    pushed = 0
    basic.showLeds(`
        . . . . .
        . # . # .
        # # # # #
        . # . # .
        . . . . .
        `)
})
let pushed = 0
pushed = 1
```

## Step 6: Check if player "A" won
We'll use the "if" block to check if we're the first person to push the button. 
Get the comparison block from the ``||logic||`` menu, and add it inside the "if" block. Grab ``||variables:pushed||``
from the ``||variables||`` menu, and place it in the comparison block to check if the value is zero.
If the value of ``||variables:pushed||``
is 0, and we'll block the other player out by setting ``||variables:pushed||`` to 1. 
We'll also write the name of our button to the screen so we can see who won using the ``||basic:show string||`` block:
  
```blocks
input.onButtonPressed(Button.A, function () {
    if (pushed == 0) {
        pushed = 1
        basic.showString("A")
    }
})

input.onGesture(Gesture.Shake, function () {
    basic.showString("wait")
    basic.pause(Math.randomRange(1000, 5000))
    pushed = 0
    basic.showLeds(`
        . . . . .
        . # . # .
        # # # # #
        . # . # .
        . . . . .
        `)
})
let pushed = 0
pushed = 1
```
## Step 7: Check if player B won

Add the exact same On button pressed code block for button B. The only difference is we'll change the value


## Discard This Later
```blocks
input.onButtonPressed(Button.A, function () {
    if (pushed == 0) {
        pushed = 1
        basic.showString("A")
    }
})
input.onButtonPressed(Button.B, function () {
    if (pushed == 0) {
        pushed = 1
        basic.showString("B")
    }
})
input.onGesture(Gesture.Shake, function () {
    basic.showString("wait")
    basic.pause(Math.randomRange(1000, 5000))
    pushed = 0
    basic.showLeds(`
        . . . . .
        . # . # .
        # # # # #
        . # . # .
        . . . . .
        `)
})
let pushed = 0
pushed = 1
```
