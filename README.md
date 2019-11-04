# Push button game

## Introduction @unplugged

Let's make a push button game

![picture of microbit](https://raw.githubusercontent.com/BrightWearables/pxt-microbit-push-button-game/master/docs/static/PushButtonMicrobitImage.png)

## Step 1: Create a variable named "pushed" @fullscreen

In the ``||variables:Variables||`` menu click "Make a Variable".
When asked, name it ``||variables:pushed||`` 
Drag the new ``||variables:set pushed to 0||`` block into ``||basic:on start||``, then change the value of ``||variables:pushed||`` to 1.

Do this:
![create a variable](https://raw.githubusercontent.com/BrightWearables/pxt-microbit-push-button-game/master/docs/static/makeVariableMakeCodeSmaller.gif)

To end up with this code:
```blocks
pushed = 1
```

## Step 2: Start the game when you shake the micro:bit

Add the ``||input:on shake||`` code block to the editor.
Add the ``||basic:show string||`` block inside the ``||input:on shake||``block and set it
to say "wait" when you shake the micro:bit. This tells players the game is starting

```blocks
input.onGesture(Gesture.Shake, function () {
    basic.showString("wait")
})
pushed=1
```
## Step 3: Add a random wait time

Add a ``||basic:pause||`` block inside the ``||input:onShake||`` block.
Then take the ``||math:random from 0 to 10||`` block from the ``||Math||`` menu and place it inside the ``||basic:pause||`` block. 
Change the minimum and maximum wait times to 1000 and 5000 milliseconds:
```blocks
input.onGesture(Gesture.Shake, function () {
    basic.showString("wait")
    basic.pause(Math.randomRange(1000, 5000))
})
pushed=0
```
## Step 4: Enable button pushing

After the ``||basic:pause||``, add a block to set the value of ``||Variables:pushed||`` to 0.
This tells the micro:bit it's ok to respond to button presses.
Add a ``||basic:show icon||`` block to let the players know to press the buttons.

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
## Step 5: Check putton pushes
Move an ``||input:on button pressed||`` code block into the editor window.
From the ``||logic:Logic||`` menu, take the first ``||logic:if||`` block and 
place it inside the ``||input:on button pressed||`` block.

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

## Step 6: See if we're the first to push the button

We'll use the ``||logic:if||`` block to check if we're the first person to push the button. 
Get the first comparison block from the ``||logic:Logic||`` menu, and add it inside the ``||logic:if||`` block.
Check if the value of ``||variables:pushed||`` is zero by taking it from the ``||variables:Variables||`` menu, 
and place it inside the comparison block.


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
