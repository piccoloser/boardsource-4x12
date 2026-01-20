# Greigh's 4x12 Ortho Layout
Hello, and welcome to this extremely compact and arguably cursed Dvorak-centric keyboard layout for the Boardsource 4x12 and similar 40% keyboards that support QMK! This README will include a short description of how you're supposed to use this thing as well as explaining the mindset behind each decision I made in the development process.

One very important note to be aware of ahead of time is that my layout, like those of many QMK-compatible keyboards, relies **heavily** on layers to reduce finger movement and strain over time. I type for a living, and even after using this layout all day, every day, while doing typing tests [at considerable speeds](https://monkeytype.com/profile/_piccoloser), my hands are rarely ever tired, let alone uncomfortable thanks to the way I've set things up.

This layout also supports rudimentary one-handed typing, which I'm still adjusting to and rarely make use of, but this is the only area where one may experience strain because I'm not a scientist.

## Building & Flashing
The QMK documentation already has a [super helpful guide](https://docs.qmk.fm/newbs_building_firmware#build-your-firmware) to building and flashing firmware! The only things to be aware of with this layout in particular are the `qmk/rules.mk` and `qmk/handswap.c` files.

Just by having these files in the same directory as your generated `keymap.c`, when you go to compile your firmware (I recommend using the [QMK CLI](https://docs.qmk.fm/cli)), everything should compile without issue. `handswap.c` is just a matrix that describes where the keyboard's keys will be after the layout has been mirrored. By adding the following to `rules.mk`:

```makefile
SWAP_HANDS_ENABLE = yes
SRC += handswap.c
```

We tell the compiler to include the contents of `handswap.c` as if it were part of the generated C code (no copy/pasting needed)!

## Base Layer (0)
![Base Layer](/images/layer0.png)

This is the layer where you'll do most of your typing (unless you're a QWERTY user in which case... no shame, but what are you doing here?).

As you can see, the default layout is a slightly modified version of Dvorak intended to accommodate for the smaller form factor of 40% keebs. There are also some opinionated layout decisions which make it easier for me to type personally, but these can be modified at your discretion.

### Modifier Keys
1. **Caps Lock** now serves as `Ctrl+Shift` when held.
2. **Shift** keys now insert opening and closing parentheses when tapped.
3. **Ctrl** has been placed on a modifier toggle on the third-row pinky keys.
    - Tap for (`;` or `z`), hold for (`L_Ctrl` or `R_Ctrl`)
4. **Browser Navigation** (also useful for other tabbed applications) is made easier using the bottom corner keys.
5. **Esc** is now on the bottom row beneath the left ring finger and switches to the [function layer](#function-layer-3) when held.
6. **Super (GUI)** keys remain in the same location as they would be normally.
7. **Alt** keys now function like the square-bracket version of the shift keys.
    - Tap for (`[` or `]`), hold for (`L_Alt` or `R_Alt`)
8. **Backspace** is now located on the bottom row beneath the pinky finger.
9. **Enter** is located under the left thumb and switches to the [navigation layer](#navigation-layer-4) when held.
    - 40% keyboards don't have keys two-out from the pinky and I was almost never using my left thumb anyway lol.
10. **Space** is located under the right thumb and similarly switches to the [navigation layer](#navigation-layer-4) when held.
    - I noticed I only ever pressed `Space` with my right thumb when typing on a normal keyboard, so I was like "why not make good use of the extra space this 1u "spacebar" provides? Needless to say, keebs with 2u spacebars aren't supported.

## Hand-Swap Layer (1)
![Hand-Swap Layer](/images/layer1.png)

This layer is almost completely transparent, but the bottom row has been modified such that the user can type almost entirely with their left hand.

### Modifier Keys
1. **Backspace** is now on the bottom-row left pinky finger. In exchange, the tilde and backtic key has been moved to the bottom-row right pinky finger.
2. **Space** is now under the left thumb and mirrors the keyboard when held.
    - Every key is flipped symmetrically such that `a` becomes `s` and so on.
    - To return to the base layer without using your right hand, hold the left thumb key and press the key under the bottom-row left middle finger.
3. **Enter** is the only key which fully requires moving the thumb to a different key than it would normally press — the adjacent key, under the  bottom-row right thumb.
4. **Alt** keys remain in the same location and can both be accessed with the same finger whether you hold space or not.
5. **`TO(0)`** is located where the `R_GUI` key used to be, the key under the bottom-row right middle finger.

## QWERTY Layer (2)
![QWERTY Layer](/images/layer2.png)

> "For those who need it. I just use it for gaming and Vim." — Mozart, probably.

This is pretty much a normal QWERTY keyboard except the bottom row and modifier keys are exactly the same as the base layer, with `Enter` under the left thumb, `Space` under the right, layer toggles under the ring and fingers and thumbs, etcetera. It's the base layer's more vanilla sibling.

## Function Layer (3)
![Function Layer](/images/layer3.png)

This layer is where you'll find:
- Special symbols along the top row as they would appear on a regular keyboard
- A `CAPS_WORD` key where `Caps Lock` would normally be
- Function keys in a 4x3 grid beneath the home row
- Conveniently placed repeat keys for repeating the same thing many times quickly
    - You can rapidly flutter your fingers between the second and third rows to repeat an action many times or do this one column to the right to repeat the opposite action, or stim by going back and forth between the same and opposite action when you wanna be silly.
- Windows-centric multi-desktop controls (swap back and forth or use Vim-style down and up arrows respectively to view all desktops or open a new one)
- A **boot** key to quickly prepare the keyboard for flashing
- Layer-switching keys to navigate between the base layer, third layer, and second layer (in that order; `Base -> QWERTY -> Hand-Swap`)
- Some conveniently placed modifiers if you need them, mostly on the right hand because the function keys take up most of the left side

## Navigation Layer (4)
![Navigation Layer](/images/layer4.png)

I refer to this as the **Navigation Layer,** but it's really more of an essential "you will use this constantly" layer. On the left side, it's got `NumLock`, media controls for volume and play/pause toggles, page navigation, quick `Ctrl_L/R` and `Repeat` keys for when you're navigating through text, and on the right side, it's got a numpad.

It's important to note the thumb keys here. They're central to Windows, but these can be modified for your OS pretty easily.
1. Holding the left thumb and pressing the right will activate **Snipping Tool**
2. Holding the right thumb and pressing the left will lock your computer.

As for why there is a numpad but no number row, and why I put the symbols on their own on the previous row, this is a quirk of how I personally think of typing numbers versus symbols. I think of symbols (`!`, `@`, `#`, and so on...) linearly, left to right. On the other hand, when I type numbers, I think of them in a numpad configuration.

---

# Common Issues

If you type quickly enough, layer keys may activate when you don't intend them to. For instance, when I'm doing a typing test, I may type `Z + E` too quickly and the browser (Zen in my case) will interpret this as a navigation key and switch focus to the URL bar. This can be a hangup in the beginning, but you learn to account for these things while still being able to type extremely quickly.

Another common hangup for quick typists is accidentally locking your computer or activating Snipping Tool on Windows because the thumb keys can respond to each other. This, however, is less common because rarely would you be pressing `Enter` and `Space` in rapid succession (at least intentionally). It definitely helps to be accurate with your keypresses because if you press more than one key by mistake these issues can happen pretty easily.