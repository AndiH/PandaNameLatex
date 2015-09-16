# »PANDA« for LaTeX
A LaTeX package, providing a nicely-set, customizable »PANDA« name, with the antiparticle bar on top of the p. For https://panda.gsi.de/.

## Purpose
The PANDA experiment is an experiment, currently being built for the FAIR facility in Darmstadt, Germany. Actually, the acronym stands for Antiproton Annihilation in Darmstadt. Why is it not AANDA, you ask? I'm glad you ask! Because someone clever decided to abbreviate antiproton with a capital P with a bar on top – just like we physicists like to do with antiparticles.

While this surely is quite clever, it's also super hard to type in documents. The least hard it is in LaTeX, where one can basically configure everything. Since you can basically configure everything, you can also basically misconfigure everything. To provide a default, but also visually pleasing PANDA name experience, this package was born.

The Anti-P in this package is typeset using features of the original P of the currently chosen font face. It also automatically adapts to bold or italic font. Great, right? The bar is slightly longer than the `\bar` and slightly shorter than `\overline`.

![PANDA with P!](https://raw.githubusercontent.com/AndiH/PandaNameLatex/pandabar.png)
To see it in action you can jump over to [ShareLaTeX](https://www.sharelatex.com/project/5437dda89196212f7b9c5332), as long the page is up…
## Usage
```LaTeX
\usepackage{panda}

\panda{}!
And also \textbf{\panda}!
```

Easy. You can also include `\panda` in a glossaries definition, e.g. 
```LaTeX
\newacronym{panda}{\panda}{Antiproton Annihilation at Darmstadt}
```
so you may call it like `\gls{panda}`. Pro-Tipp:
```LaTeX
\newacronym[sort=PANDA, %
    first={the \glstext*{panda} experiment (\glsdesc*{panda})}, %
    plural={\panda}, %
    firstplural={\panda}]%
{panda}{\panda}{Antiproton Annihilation at Darmstadt}
```
## Modification
The package provides a few ways to style the PANDA to your likings. All are documented in the first few lines of the `.sty` file – and in the following.

### On-load Modifications
The package accepts optional arguments when loading (which can also be combined in a list):
* `scaledistance`: Scales the vertical distance between the bar and the P. `=1` means the pre-chosen distance (i.e. 100 %). Example: `\usepackage[scaledistance=2]{panda} ` will double the distance.
* `scaleregular`: Changes the thickness of the bar for regular-faced fonts (i.e. non-italic, non-bold). `=1` means the pre-chosen scale (i.e. 100 %). Example: ` \usepackage[scaleregular=2]{panda}` will double the regular thickness.
* `scalebold`: Same as before, but for the bold version of the bar. Example: `\usepackage[scalebold=2]{panda}`.

### Modifications in Document
Additionally, the horizontal position of the bar can be tweaked using the `setlength` macro. I consider this quasi-internal functionality and made the lengths only available by `@` characters (so, use `\makeatletter`). Available lengths are:
* `\panda@additionalleftkerning`: The added distance where the left border of the bar starts. Lengths can be given in whatever dimension you desire, I suggest `em`, since we're talking about character width. Example: `\makeatletter\setlength{\panda@additionalleftkerning}{0.05em}\makeatother`
* `\panda@additionalrightkerning`: The same as before, but for the right side. Example: `\makeatletter\setlength{\panda@additionalrightkerning}{-0.02em}\makeatother`

You can return to the original values with setting the values to 0.

## Thanks
The core basic for the package was created by Enrico Gregorio (egreg) at StackExchange: http://tex.stackexchange.com/a/188725/56326
