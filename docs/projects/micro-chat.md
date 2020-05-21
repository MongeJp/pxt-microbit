# Micro Chat

## Introduction @unplugged

![Two @boardname@ connected via radio](/static/mb/projects/a9-radio.png)

Use the **radio** to send and receive messages with other @boardname@.

## Sending a message

Use ``||input:on button pressed||`` to send a text message over radio with ``||radio:send string||``.
Every @boardname@ nearby will receive this message.

```blocks
input.onButtonPressed(Button.A, function() {
    radio.sendString(":)");
});
```

## Receiving a message

Add a ``||radio:on received string||`` block to run when a message is received. 

```blocks
radio.onReceivedString(function (receivedString) {
})
```

## Displaying text

Add a ``||basic:show string||`` to display the string on the screen. Pull the ``||variables:receivedString||`` out of ``||radio:on received string||`` and put it into ``||basic:show string||``.

```blocks
radio.onReceivedString(function (receivedString) {
    basic.showString(receivedString);
})
```

## Testing in the simulator

Press button **A** on the simulator, you will notice that a second @boardname@ appears (if your screen is too small, the simulator might decide not to show it). Try pressing **A** again and notice that the ":)" message gets displayed on the other @boardname@.

```blocks
input.onButtonPressed(Button.A, function() {
    radio.sendString(":)");
});
radio.onReceivedString(function (receivedString) {
    basic.showString(receivedString);
})
```

## Try it for real

If you two @boardname@s, download the program to each one. Press button **A** on one and see if the other gets a message.

## Groups

Use the ``||radio:set group||`` block to assign a **group** number to your program. You will only receive messages from @boardname@s within the same group. Use this to avoid receiving messages from every @boardname@ that is transmitting.

```blocks
radio.setGroup(123)
```

```package
radio
```
