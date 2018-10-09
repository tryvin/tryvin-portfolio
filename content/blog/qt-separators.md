---
title: "Separators"
date: 2018-10-08T21:06:06-03:00
draft: false
icon: "https://icon-icons.com/icons2/159/PNG/256/qtproject_qtcreator_qt_22392.png"
image: "https://icon-icons.com/icons2/159/PNG/256/qtproject_qtcreator_qt_22392.png"
---

One beautiful thing about computer programming are the differences from OS to OS, from Windows, to <whatever>nix, and so on.

When we are writing cross-platform code, as in my case where my dev machine is a Windows 10 machine, and our production servers are all Linux, we have some little things that you need to go on with an IF or some constant from the Programming Language or the toolkit.

Today I was surfing the web, and got into an [article](http://agateau.com/2015/qdir-separator-considered-harmful)&nbsp;about QDir::separator() property (Yes, Q Toolkit, Qt). So the article was explaining why this property is harmful and so on. Well, at the begging of times, Windows only accepted inverse slash as a directory separator, this and only this, so, when we wanted to navigate through CMD or passing a path as an argument, there was the handy inverse slash. On the other side, on <whatever>nix systems, the slash was the directory separator. That caused some languages to insert some constants to help you programmatic create file paths, and that was good.

Time goes by, and Windows started to understand the slash separator as a directory separator too, you can see this working when you open a CMD shell, and starts to navigate.

And here goes the bug, now-a-days when you consider testing some condition with this constant, you can trigger platform specific bugs, see this example from the qt article:
> `void testFindBiggestFile()
> {
>     QString result = findBiggestFile(mTestDir);
>     QString expected = mTestDir + QDir::separator() + "file.big";
>     QCOMPARE(biggestFile, expected);`
>
> `}`
> > This test passes on a Linux system, but fails on a Windows system: `findBiggestFile()` returns a path created by `QFileInfo`, so assuming `mTestDir` is `C:/build/tests`, `result` will be `C:/build/tests/file.big`, but&nbsp;`expected` will be `C:/build/tests\file.big`.

See how easy is to get some headaches? You would be surprise how things can go pretty wrong when you try to be platform-agnostic.

This applies to PHP too.

My advice: Always test in one, or two platforms, so you can make sure wetter you need to make some conditions, or you can share the same code.
