---
title: Development Environments
date: "2021-11-19T20:00:00Z"
description: On development tools and Memo-to-Self on config hacks.
---
Development environments are personal.  I've burned up too
much good will trying to convince people of "the right way" to work. Everyone
needs to figure that out for themselves.

Here are a few things I've figured out about "the right way" for *me* to work:

* **I generally prefer typing over mousing**
  ...I'd like to keep my hands on the keyboard
  as much as possible and not have to break flow to mouse around, click buttons,
  and -- god forbid -- hunt around menus. That said, I'm also not a fan of
  memorizing a bazillion key-combinations: They don't always translate well
  between different OSes and keyboard types -- especially Apple vs non-Apple.
  So I usually want to have the mouse available as an emergency exit. Also, the
  Macbook Pro's touchpad is nice as: I do need to move my hand a bit to mouse,
  I don't need to move it far.
* **I'm love-hate with the Mac**
  ...I find their devices to be built from high quality components and their
  designs to be very kind to the senses. Also that their OS is built on BSD
  means they're on stable ground. However the keyboard is cultish maddening.
  It's a huge productivity killer.
* **I love UNIX Family OSes**
  ...I think about the creation of the UNIX kernel, the command shell,
  the basic commands like `cat`, `grep`, `awk`, `sed`, etc., and the internet
  protocol like the High Renaissance. While other modes of commanding a
  computer have come along, the UNIX Philosophy has withstood the test of time.
* **Good Languages. Simple Tools.**
  ...I'm pretty allergic to VisualStudio and the whole Microsoft approach of
  "You click, drag, and drop, and we'll let the IDE write the code." It's not
  just the mousey-ness. If I want a high-level mode of expression, I'd prefer to
  use a high-level *language*, not a high-level *tool*.  A language
  (at it's best) is a rigorously design and logically consistent system
  of abstractions that, once I get it into my head, is mine. I don't
  need *any* specific tools: A pen and napkin will often do fine. The design
  of a tool, on the other hand, can be less rigorous, less standardized,
  more ephemeral, and
  thus less worthy of the time I'd need to spend to learn it.  
  If I need a complicated
  tool to be productive in a language, then maybe the language sucks.
    * **I spend almost all my coding time in Python these days**
    ...I am very productive in Python. The community is super-impressive:
    It skews towards scientists and engineers -- so lots of really
    smart people. The language itself is elegant, expressive, easy on the eyes,
    and -- above all -- *fun.*   

      ...That said, I sometimes find myself yearning to build
      something with static-typing, low-level programming, functional programming,
      etc. Time permitting I'll revisit some of my old languages like Java and
      C++, and learn some new languages too.
    * **I used to favor Emacs but now I favor Atom**
    ...I love that emacs is dead-simple. It's a raw-text editor implemented
    to run on a text-only terminal in curses. Yet it is infinitely hackable and
    extensible. However it does feel a little quirky and anachronistic lately,
    and when Atom came along I really liked it because it seemed to embrace
    the same ethos as emacs. Earlier versions of Atom were pretty sluggish,
    but I'm pretty happy with 1.58 running on my 2019 MacBookPro.
      * *Why not PyCharm?* I have respect for its "Python-smarts"
        and enjoy its decent docker-integration.
        That's all a bit lacking in Atom.
        I have a pro license and do use it sometimes, but PyCharm suffers
        from the menu/configuration opaqueness hell
        that makes Eclipse so unenjoyable. So, on balance, I think I still
        lean to Atom over PyCharm.
      * *Why not VSCode?* Culture over features. It has that VisualStudio
        mindset that makes me pukey. I realize it's and open source juggernaut
        with huge numbers of people and dollars behind it. I hope it doesn't
        squelch out all alternatives.
      * *I sometimes use vim* Start-up time is zero. Hardware requirements are
        zero. The key commands are a bit anachronistic, but it's elegant like
        so much of the UNIX-era toolset -- even more so than emacs.
  * **I Often Start in a Jupyter Notebook.**
    ...If I just need to get a number or a plot, it's super productive.  
    Back pre-GFC when I worked on a structured credit desk
    I would reflexively open
    Excel as a scratch-pad if I needed to figure out anything quantitative.
    These days I *sometimes* open Excel -- or more likely a Google Sheet --
    but I am *way more likely* to open a
    Collab notebook: I can pull in any type of data, get it
    into pandas, and trounce a spreadsheet's capabilities in a minute or two.
    Especially if I need anything to be repeatable.
    The one big exception: If lots of manually inputted data is required.
    Then a spreadsheet still
    wins. Though once I get the data in, I'm often just loading it into
    pandas anyway.
  * **Conda for Python Environments**
    ...It's not perfect. Nothing in package management is -- especially in Python
    land.  But Conda solves the binary install problem, and let's you use pip
    as much as you want.
    * **I like to deploy software via push-to-deploy CI/CD using Git+Docker.**
      Why do it any other way? GitLab + Docker has been a power-duo for me. And
      if we're deploying Docker, I'm pro Kubernetes. It's pretty complicated
      which is a downside, but it appears to be winning the game.
  * **I'd do it all in browser if I could**
    ...JupyterLab is a great demonstration of how a really productive coding
    environment implemented entirely in a browser. If there was a
    server-side Atom, I'd use that in minute!  I would
    run it in a Docker container! (...like I often do with JupyterLab.)



# Customizations
Over the decades I've built muscle memory around using a
computer.  When computers don't behave like my muscle memory expects, it can
be maddening.  Sometimes the right answer is to retrain my muscle memory.
That's better for my brain-plasticity and requires less configuration baggage.  

...But other times the right answer is to just reconfigure.

This is my memo-to-self about the various configurations I've found helpful.


## Atom

### Problem: Atom isn't so good at English
It's English-word autocomplete is super-broken.  Always trying to replace
"with" with "width"!

The fix: Disable **autocomplete-plus**   

(not spell-checker as I would have expected.)



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
I see no benefit to learning Mac's version of Home/End behavior as it's
completely different than all other computers and offers me no perceivable
advantage.

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
