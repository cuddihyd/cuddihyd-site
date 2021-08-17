---
title: Customizations
date: "2021-08-17T15:50:00Z"
description: A reminder various customizations
---

## Overview
Over the decades I've built up all sorts of muscle memory around using a
computer.  When computers don't behave like my muscle memory expects, it can
be maddening.  Sometimes the right answer is to retrain those muscle memories:
Better for my brain-plasticity and less configuration baggage.  

...But sometimes the right answer is to just reconfigure.

This is my memo-to-self about the various configurations I've found helpful.


## My Mac External Keyboard
I've been using an Apple external keyboard with my workplace-provided PC for
a few years now.  That's pretty straightforward: Option means Alt, Command
means Windows-key. Control and Shift are Control and Shift.

Recently I bought an Apple USB-C to USB-old and  and hooked my Apple keyboard
to a MacBook Pro.

### First problem. It didn't work at all.  

The fix turned out to be completely insane:  Purchase a
short USB-extension-cable and interject that between the adapter and the
keyboard.

#### Second problem: Home and End Keys
I see no benefit to learning Mac's verysion of Home/End behavior as it's
completely different than all other computers and offers me no perceivable
advanged.

The Fix: I create file `~/Library/KeyBindings/DefaultKeyBinding.dict`
with the contents:

```
{
  "\UF729"  = moveToBeginningOfParagraph:; // home
  "\UF72B"  = moveToEndOfParagraph:; // end
  "$\UF729" = moveToBeginningOfParagraphAndModifySelection:; // shift-home
  "$\UF72B" = moveToEndOfParagraphAndModifySelection:; // shift-end
  "^\UF729" = moveToBeginningOfDocument:; // ctrl-home
  "^\UF72B" = moveToEndOfDocument:; // ctrl-end
  "^$\UF729" = moveToBeginningOfDocumentAndModifySelection:; // ctrl-shift-home
  "^$\UF72B" = moveToEndOfDocumentAndModifySelection:; // ctrl-shift-end
}
```
...as suggested by [this article](https://damieng.com/blog/2015/04/24/make-home-end-keys-behave-like-windows-on-mac-os-x).



## Atom


### Problem: Atom isn't so good at English
It's English-word autocomplete is super-broken.  Always trying to replace
"with" with "width"!

The fix: Disable **autocomplete-plus**   

(not spell-checker as I would have expected.)
