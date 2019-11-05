# Push button game

## Introduction @unplugged

Let's make a push button game

![picture of microbit](https://raw.githubusercontent.com/BrightWearables/pxt-microbit-push-button-game/master/docs/static/PushButtonMicrobitImage.png)

## Step 1: Create a variable named "pushed" @fullscreen

In the ``||variables:Variables||`` menu click "Make a Variable".
When asked, name it ``||variables:pushed||`` 
Drag the new ``||variables:set pushed to 0||`` block into ``||basic:on start||``, then change the value of ``||variables:pushed||`` to 1.

![create a variable](https://raw.githubusercontent.com/BrightWearables/pxt-microbit-push-button-game/master/docs/static/makeVariableMakeCode.gif)

After you make the new variable ``||variables:pushed||``, set its value to 1:

```blocks
let pushed = 0
pushed = 1
```

## Step 2: Start the game when you shake the micro:bit

Add the ``||input:on shake||`` code block to the editor.
Add the ``||basic:show string||`` block inside the ``||input:on shake||``block and set it
to say "wait" when you shake the micro:bit. This tells players the game is starting.

```blocks
input.onGesture(Gesture.Shake, function () {
    basic.showString("wait")
})
let pushed = 0
pushed=1
```
## Step 3: Add a random wait time

Add a ``||basic:pause||`` block inside the ``||input:onShake||`` block.
Then take the ``||math:random from 0 to 10||`` block from the ``||math:Math||`` menu 
and place it inside the ``||basic:pause||`` block. 
Change the minimum and maximum wait times to 1000 and 5000 milliseconds:

```blocks
input.onGesture(Gesture.Shake, function () {
    basic.showString("wait")
    basic.pause(Math.randomRange(1000, 5000))
})
let pushed = 0
pushed=1
```
## Step 4: Enable button pushing

Inside ``||input:onShake||``, after the ``||basic:pause||`` block, add a 
block to set the value of ``||Variables:pushed||`` to 0.
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
Move an ``||input:on button A pressed||`` code block into the editor window.
From the ``||logic:Logic||`` menu, take the top ``||logic:if||`` block and 
place it inside the ``||input:on button pressed||`` block.

```blocks
input.onButtonPressed(Button.A, function () {
    if (true) {
    }
})

input.onGesture(Gesture.Shake, function () {
    basic.showString("wait")
    basic.pause(Math.randomRange(1000, 5000))
    pushed = 0
    basic.showIcon(IconNames.Yes)
})
let pushed = 0
pushed = 1
```

## Step 6: Check if player A pushed first

Inside the ``||logic:if||`` block we'll check if we were first.
Get the first comparison block from the ``||logic:Logic||`` menu, and place it inside the ``||logic:if||`` block. 
Then check if the value of ``||variables:pushed||`` is zero by taking it from the ``||variables:Variables||`` menu, 
and place it inside the comparison block.

![compare a variable](https://raw.githubusercontent.com/BrightWearables/pxt-microbit-push-button-game/master/docs/static/compareVariable.gif)

## Step 7: Lock out the other player

If the value of ``||variables:pushed||``
is 0, we'll lock the other player out by setting ``||variables:pushed||`` to 1. 
We'll also write the letter "A" to the screen to show who won (check the hint if you're not sure how)
  
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
    basic.showIcon(IconNames.Yes)
})
let pushed = 0
pushed = 1
```
## Step 7: Check if player B won

Copy the same code that checks if player A won in ``||input:on button A pressed||`` into a new block
that responds to button B being pressed. Don't forget to show the letter "B" if B wins

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
    basic.showIcon(IconNames.Yes)
})
let pushed = 0
pushed = 1
```
## Step 8: Download and test your code

Pair your micro:bit. Download your code. Play the game against a friend and 
test your reaction time. When you're sure it's working, do the next tutorial.