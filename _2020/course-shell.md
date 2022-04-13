---
layout: lecture
title: "Kursübersicht + die Shell"
date: 2020-01-13
ready: true
video:
  aspect: 56.25
  id: Z56Jmr9Z34Q
---

# Motivation

Als Informatiker wissen wir, dass Computer eine großartige Hilfe sind bei
sich wiederholenden Aufgaben. Viel zu oft vergessen wir jedoch, dass dies
für unsere _Benutzung_ des Computers genauso gilt wie für die Berechnungen
die wir mit unseren Programmen durchführen wollen. Wir haben eine große Auswahl an Werkzeugen
zur Verfügung, die es uns ermöglichen, produktiver zu sein und
komplexere Probleme zu lösen, wenn wir an einem computerbezogenen Problem arbeiten
Problem zu lösen. Dennoch nutzen viele von uns nur einen kleinen Teil dieser Werkzeuge; wir
kennen nur genug magische Beschwörungsformeln auswendig, um zurechtzukommen, und
fügen blind Befehle aus dem Internet ein, wenn wir nicht weiterkommen.

Dieser Kurs ist ein Versuch, dieses Problem zu lösen.

Wir wollen Ihnen beibringen, wie Sie das Beste aus den Werkzeugen machen, die Sie kennen.
Ihnen neue Werkzeuge zeigen, die Sie Ihrem Werkzeugkasten hinzufügen können, und Ihnen hoffentlich
Begeisterung dafür wecken, weitere Tools selbst zu erforschen (und vielleicht auch zu bauen).
Das ist es, was unserer Meinung nach in den meisten Informatik-Lehrplänen fehlt.

# Kursstruktur

Der Kurs besteht aus 11 1-stündigen Vorlesungen, die sich jeweils auf ein
[bestimmtes Thema](/2020/) beziehen. Die Vorlesungen sind weitgehend selbständig,
Im weiteren Verlauf des Semesters werden wir jedoch davon ausgehen, dass Sie mit dem
mit dem Inhalt der früheren Vorlesungen vertraut sind. Wir haben Vorlesungsunterlagen
online, aber es werden viele Inhalte in der Vorlesung behandelt (z.B. in Form von
Form von Demos), die möglicherweise nicht in den Notizen enthalten sind. Wir werden die
Vorlesungen aufzeichnen und die Aufzeichnungen online stellen.

Wir versuchen, in nur 11 1-stündigen Vorlesungen eine Menge Stoff zu vermitteln,
daher sind die Vorlesungen ziemlich dicht.
Damit Sie etwas Zeit haben, um sich
sich in Ihrem eigenen Tempo mit dem Inhalt vertraut zu machen, enthält jede Vorlesung eine
eine Reihe von Übungen, die Sie durch die wichtigsten Punkte der Vorlesung führen. Nach
jeder Vorlesung bieten wir eine Sprechstunde an, in der wir Ihnen bei
um Ihre Fragen zu beantworten. Wenn Sie die Vorlesung
online teilnehmen, können Sie uns Fragen schicken an
[missing-semester@mit.edu](mailto:missing-semester@mit.edu).

Aufgrund der begrenzten Zeit, die uns zur Verfügung steht, können wir nicht alle Werkzeuge
in der gleichen Ausführlichkeit zu behandeln,
wie es in einem vollständigen Kurs möglich wäre. Wo möglich, werden wir
werden wir versuchen, Sie auf Ressourcen hinzuweisen,
mit denen Sie ein Werkzeug oder ein Thema vertiefen können,
aber wenn Ihnen etwas besonders gefällt,
zögern Sie nicht, uns zu kontaktieren und um Hinweise zu bitten!


# Thema 1: Die Shell

## Was ist die Shell?

Heutzutage haben Computer eine Vielzahl von Schnittstellen, um ihnen
Befehle zu erteilen; phantasievolle grafische Benutzeroberflächen, Sprachschnittstellen und
sogar AR/VR sind allgegenwärtig. Diese sind für 80 % der Anwendungsfälle großartig, aber
sie sind oft in ihren Möglichkeiten grundlegend eingeschränkt -
Sie können keine Taste drücken, die nicht da ist, oder einen Sprachbefehl geben, der
nicht programmiert wurde. Um den vollen Nutzen aus den Werkzeugen Ihres
Computer voll ausnutzen zu können, müssen wir auf die alte Schule zurückgreifen und auf eine
Schnittstelle: Die Shell.

Fast alle Plattformen, die Sie in die Finger bekommen, haben in der einen oder anderen Form
eine Shell, und viele haben mehrere Shells zur Auswahl.
Auch wenn sie sich im Detail unterscheiden, sind sie im Kern alle ungefähr
dasselbe: Sie ermöglichen es Ihnen, Programme auszuführen, Eingaben zu machen und die
ihre Ausgabe in einer halbstrukturierten Weise zu überprüfen.

In dieser Vorlesung werden wir uns auf die Bourne Again SHell, kurz "bash" genannt, konzentrieren.
Sie ist eine der am häufigsten verwendeten Shells, und ihre Syntax ist
ähnelt der Syntax vieler anderer Shells. Um eine Shell _Eingabeaufforderung_
(in die Sie Befehle eingeben können) zu öffnen, benötigen Sie zunächst ein _Terminal_.
Ihr Gerät wird wahrscheinlich mit einem solchen Terminal ausgeliefert,
oder Sie können eines
relativ leicht installieren.

## Benutzung der Shell

Wenn Sie Ihr Terminal starten, sehen Sie einen _Prompt_ (_Eingabeaufforderung_), der oft so
ähnlich wie diese aussieht:

```console
missing:~$
```

Diese Textschnittstelle ist die Hauptschnittstelle zur Shell. Sie sagt Ihnen, dass Sie
auf dem Rechner `missing` sind und dass Ihr "aktuelles Arbeitsverzeichnis",
oder wo Sie sich gerade befinden, `~` (kurz für "home") ist. Das `$` sagt Ihnen
dass Sie nicht der Root-Benutzer sind (mehr dazu später). An dieser Eingabeaufforderung können Sie
einen _Befehl_ eingeben, der dann von der Shell interpretiert wird. Der
einfachste Befehl ist die Ausführung eines Programms:

```console
missing:~$ date
Fri 10 Jan 2020 11:49:31 AM EST
missing:~$
```

Hier haben wir das Programm `date` ausgeführt, das (vielleicht wenig überraschend)
das aktuelle Datum und die Uhrzeit ausgibt. Die Shell fragt uns dann nach einem weiteren
Befehl zum Ausführen. Wir können auch einen Befehl mit _Argumenten_ ausführen:

```console
missing:~$ echo hello
hello
```

In diesem Fall haben wir die Shell angewiesen, das Programm `echo` mit dem
Argument `hello` auszuführen. Das Programm "echo" gibt einfach seine Argumente aus.
Die Shell analysiert den Befehl, indem sie ihn durch Leerzeichen trennt, und führt dann
das durch das erste Wort angegebene Programm aus und übergibt jedes folgende Wort als
Argument an das Programm, auf das es zugreifen kann. Wenn Sie ein Argument angeben wollen,
das Leerzeichen oder andere Sonderzeichen enthält (z. B. ein
Verzeichnis mit dem Namen "Meine Fotos"), können Sie das Argument entweder in Anführungszeichen mit `'`
oder `"` (`"Meine Fotos"`), oder nur die relevanten Zeichen mit `\`, dem Escape-Zeichen, schützen
(`Meine Fotos`).

Aber woher weiß die Shell, wie sie die `date`- oder `echo`-Programme findet?
Nun, die Shell ist eine Programmierumgebung, genau wie Python oder Ruby,
und so gibt es Variablen, Bedingungen, Schleifen und Funktionen (nächste
Vorlesung!). Wenn Sie Befehle in Ihrer Shell ausführen, schreiben Sie eigentlich ein
kleines Stück Code, das Ihre Shell interpretiert. Wenn die Shell dazu aufgefordert wird
einen Befehl ausführen, der nicht mit einem seiner Programmierschlüsselwörter übereinstimmt,
konsultiert sie eine _Umgebungsvariable_ namens `$PATH`, die auflistet, welche
Verzeichnisse, die Shell nach Programmen durchsuchen soll, wenn ihr ein Befehl gegeben wird:


```console
missing:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
missing:~$ which echo
/bin/echo
missing:~$ /bin/echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

Wenn wir den „echo“-Befehl ausführen, sieht die Shell, dass
das Programm `echo` ausgeführt werden soll, und durchsucht dann die durch `:` getrennte Liste der
Verzeichnisse in `$PATH` nach einer Datei mit diesem Namen. Wenn sie eine Datei findet,
führt sie die Datei aus (vorausgesetzt, die Datei ist _ausführbar_; dazu später mehr). Wir können
mit dem Programm `which`
herausfinden, welche Datei für einen bestimmten Programmnamen ausgeführt wird.
Wir können die Umgebungsvariable `$PATH` auch vollständig umgehen, indem wir
den vollständigen _Pfad_ zu der Datei, die wir ausführen möchten, angeben.

## Navigation in der Shell

Ein Pfad auf der Shell ist eine begrenzte Liste von Verzeichnissen; getrennt durch `/`
unter Linux und macOS und `\` unter Windows. Unter Linux und macOS ist der Pfad `/`
die "Wurzel" des Dateisystems, unter der alle Verzeichnisse und Dateien liegen,
wohingegen es unter Windows ein Root für jede Festplattenpartition gibt (z. B.
`C:\`). Wir gehen in dieser Klassed im Allgemeinen davon aus, dass Sie ein Linux-Dateisystem verwenden.
Ein Pfad, der mit `/` beginnt, wird als _absoluter_ Pfad bezeichnet.
Jeder andere Pfad ist ein _relativer_ Pfad. Relative Pfade sind relativ zum
aktuelles Arbeitsverzeichnis, das wir mit dem `pwd`-Befehl anzeigen und
mit dem `cd`-Befehl ändern können. In einem Pfad bezieht sich "." auf das aktuelle
Verzeichnis und `..` auf das übergeordnete Verzeichnis:

```console
missing:~$ pwd
/home/missing
missing:~$ cd /home
missing:/home$ pwd
/home
missing:/home$ cd ..
missing:/$ pwd
/
missing:/$ cd ./home
missing:/home$ pwd
/home
missing:/home$ cd missing
missing:~$ pwd
/home/missing
missing:~$ ../../bin/echo hello
hello
```

Beachten Sie, dass unser Shell-Prompt uns darüber informiert,
was unser aktuelles Arbeitsverzeichnis ist.
Sie können Ihre Eingabeaufforderung so konfigurieren, dass sie Ihnen alle
möglichen nützlichen
Informationen  anzeigt, dies werden wir in einer späteren Vorlesung behandeln.

Wenn wir ein Programm ausführen, wird es im Allgemeinen, sofern wir es nicht anders angeben,
im aktuellen
Arbeitsverzeichnis ausgeführt. Zum Beispiel wird es normalerweise hier
nach Dateien suchen und neue Dateien erstellen, wenn dies erforderlich ist.

Um zu sehen, was sich in einem bestimmten Verzeichnis befindet, verwenden wir den Befehl `ls`:

```console
missing:~$ ls
missing:~$ cd ..
missing:/home$ ls
missing
missing:/home$ cd ..
missing:/$ ls
bin
boot
dev
etc
home
...
```

Unless a directory is given as its first argument, `ls` will print the
contents of the current directory. Most commands accept flags and
options (flags with values) that start with `-` to modify their
behavior. Usually, running a program with the `-h` or `--help` flag
will print some help text that tells you what flags
and options are available. For example, `ls --help` tells us:

Wenn kein Verzeichnis als erstes Argument angegeben wird, gibt `ls` den
Inhalt des aktuellen Verzeichnisses aus. Die meisten Befehle akzeptieren Flags und
Optionen (Flags mit Werten), die mit `-` beginnen, um ihr
Verhalten zu ändern. Üblicherweise gibt ein Programm das mit dem Flag `-h` oder `--help` ausgeführt
wird, einen Hilfetext aus, der Ihnen sagt, welche Flags
und Optionen verfügbar sind. Zum Beispiel sagt uns `ls --help`:

```
  -l                         use a long listing format
```

```console
missing:~$ ls -l /home
drwxr-xr-x 1 missing  users  4096 Jun 15  2019 missing
```

Dies gibt uns eine Menge mehr Informationen über jede Datei oder jedes Verzeichnis.
Zunächst sagt uns das `d` am Anfang der Zeile
`missing` ist ein Verzeichnis. Dann folgen drei Gruppen von drei Zeichen
(`rwx`). Diese geben an, welche Berechtigungen der Besitzer (`missing`) der Datei
hat, die besitzende Gruppe (`users`) und alle anderen User an der entsprechenden Datei
haben. Ein "-" gibt an, dass der angegebene Prinzipal nicht
nicht die erteilte Erlaubnis hat. Im Beispiel oben darf nur der Eigentümer
(`w`) das Verzeichnis `missing` ändern (d. h. Dateien hinzufügen oder entfernen). Um
in ein Verzeichnis zu wechseln, muss ein Benutzer die Berechtigung "Suchen"
(dargestellt durch "execute":`x`) für dieses Verzeichnis (und seine
übergeordneten Verzeichnisse) haben. Um den Inhalt eines Verzeichnisses aufzulisten
, muss ein Benutzer Leserechte (`r`) für dieses Verzeichnis haben. Für
Dateien sind die Berechtigungen so, wie Sie es erwarten würden. Beachten Sie, dass fast alle
Dateien in `/bin` die Berechtigung `x` für die letzte Gruppe "alle anderen" haben,
damit jeder diese Programme ausführen kann.

Einige andere nützliche Programme, die Sie an dieser Stelle kennen sollten, sind `mv` (um
eine Datei umzubenennen oder zu verschieben), `cp` (um eine Datei zu kopieren)
und `mkdir` (um ein neues Verzeichnis zu erstellen).

Wenn Sie jemals _mehr_ Informationen über Argumente, Eingaben, oder
Ausgaben eines Programmes haben wollen,
oder wissen wollen, wie es im Allgemeinen funktioniert, probieren Sie das `man`-Programm aus. Es
nimmt als Argument den Namen eines Programms und zeigt Ihnen
die zugehörige Handbuchseite _man page_. Drücken Sie zum Beenden von man "q".

```console
missing:~$ man ls
```

## Programme verbinden

In der Shell sind Programmen zwei primäre "Streams" zugeordnet:
der Eingangsstream und der Ausgangsstream. Wenn das Programm versucht
Eingaben zu lesen, liest es aus dem Eingabestream und wenn es etwas druckt,
druckt es in seinen Ausgabestream. Normalerweise sind die Eingabe und die Ausgabe
eines Programms beide Ihr Terminal. Das heißt, Ihre Tastatur als Eingabe und
Ihr Bildschirm als Ausgabe. Wir können diese Streams jedoch auch neu verdrahten!

Die einfachste Form der Umleitung ist `< file` und `> file`. Diese verbinden
die Eingabe- und Ausgabeströme eines Programms jeweils mit einer Datei:

```console
missing:~$ echo hello > hello.txt
missing:~$ cat hello.txt
hello
missing:~$ cat < hello.txt
hello
missing:~$ cat < hello.txt > hello2.txt
missing:~$ cat hello2.txt
hello
```

Wie im obigen Beispiel demonstriert, ist `cat` ein Programm, das Dateien con`cat`eniert.
Wenn Dateinamen als Argumente angegeben werden, wird der Inhalt der Dateien
nacheinander in seinen Ausgabestrom kopiert. Aber wenn `cat` ohne Argumente
aufgerufen wird, druckt es den Inhalt seines Eingabestreams in seinen Ausgabestream (wie
im dritten Beispiel oben).

Um an eine Datei anzuhängen, können Sie auch `>>` verwenden. Die
Ein-/Ausgabeumleitung glänzt ganz besonders bei der Verwendung von _pipes_.
Mit dem `|` Operator können Sie Programme so "verketten", dass die Ausgabe von einem die
Eingabe des nächsten ist:

```console
missing:~$ ls -l / | tail -n1
drwxr-xr-x 1 root  root  4096 Jun 20  2019 var
missing:~$ curl --head --silent google.com | grep --ignore-case content-length | cut --delimiter=' ' -f2
219
```

In der Vorlesung über Datenwrangling werden wir viel detaillierter darauf eingehen,
wie man Pipes nutzt.

## A versatile and powerful tool

On most Unix-like systems, one user is special: the "root" user. You may
have seen it in the file listings above. The root user is above (almost)
all access restrictions, and can create, read, update, and delete any
file in the system. You will not usually log into your system as the
root user though, since it's too easy to accidentally break something.
Instead, you will be using the `sudo` command. As its name implies, it
lets you "do" something "as su" (short for "super user", or "root").
When you get permission denied errors, it is usually because you need to
do something as root. Though make sure you first double-check that you
really wanted to do it that way!

One thing you need to be root in order to do is writing to the `sysfs` file
system mounted under `/sys`. `sysfs` exposes a number of kernel parameters as
files, so that you can easily reconfigure the kernel on the fly without
specialized tools. **Note that sysfs does not exist on Windows or macOS.**

For example, the brightness of your laptop's screen is exposed through a file
called `brightness` under

```
/sys/class/backlight
```

By writing a value into that file, we can change the screen brightness.
Your first instinct might be to do something like:

```console
$ sudo find -L /sys/class/backlight -maxdepth 2 -name '*brightness*'
/sys/class/backlight/thinkpad_screen/brightness
$ cd /sys/class/backlight/thinkpad_screen
$ sudo echo 3 > brightness
An error occurred while redirecting file 'brightness'
open: Permission denied
```

This error may come as a surprise. After all, we ran the command with
`sudo`! This is an important thing to know about the shell. Operations
like `|`, `>`, and `<` are done _by the shell_, not by the individual
program. `echo` and friends do not "know" about `|`. They just read from
their input and write to their output, whatever it may be. In the case
above, the _shell_ (which is authenticated just as your user) tries to
open the brightness file for writing, before setting that as `sudo
echo`'s output, but is prevented from doing so since the shell does not
run as root. Using this knowledge, we can work around this:

```console
$ echo 3 | sudo tee brightness
```

Since the `tee` program is the one to open the `/sys` file for writing,
and _it_ is running as `root`, the permissions all work out. You can
control all sorts of fun and useful things through `/sys`, such as the
state of various system LEDs (your path might be different):

```console
$ echo 1 | sudo tee /sys/class/leds/input6::scrolllock/brightness
```

# Next steps

At this point you know your way around a shell enough to accomplish
basic tasks. You should be able to navigate around to find files of
interest and use the basic functionality of most programs. In the next
lecture, we will talk about how to perform and automate more complex
tasks using the shell and the many handy command-line programs out
there.

# Exercises

All classes in this course are accompanied by a series of exercises. Some give
you a specific task to do, while others are open-ended, like "try using X and Y
programs". We highly encourage you to try them out.

We have not written solutions for the exercises. If you are stuck on anything
in particular, feel free to send us an email describing what you've tried so
far, and we will try to help you out.

 1. For this course, you need to be using a Unix shell like Bash or ZSH. If you
    are on Linux or macOS, you don't have to do anything special. If you are on
    Windows, you need to make sure you are not running cmd.exe or PowerShell;
    you can use [Windows Subsystem for
    Linux](https://docs.microsoft.com/en-us/windows/wsl/) or a Linux virtual
    machine to use Unix-style command-line tools. To make sure you're running
    an appropriate shell, you can try the command `echo $SHELL`. If it says
    something like `/bin/bash` or `/usr/bin/zsh`, that means you're running the
    right program.
 1. Create a new directory called `missing` under `/tmp`.
 1. Look up the `touch` program. The `man` program is your friend.
 1. Use `touch` to create a new file called `semester` in `missing`.
 1. Write the following into that file, one line at a time:
    ```
    #!/bin/sh
    curl --head --silent https://missing.csail.mit.edu
    ```
    The first line might be tricky to get working. It's helpful to know that
    `#` starts a comment in Bash, and `!` has a special meaning even within
    double-quoted (`"`) strings. Bash treats single-quoted strings (`'`)
    differently: they will do the trick in this case. See the Bash
    [quoting](https://www.gnu.org/software/bash/manual/html_node/Quoting.html)
    manual page for more information.
 1. Try to execute the file, i.e. type the path to the script (`./semester`)
    into your shell and press enter. Understand why it doesn't work by
    consulting the output of `ls` (hint: look at the permission bits of the
    file).
 1. Run the command by explicitly starting the `sh` interpreter, and giving it
    the file `semester` as the first argument, i.e. `sh semester`. Why does
    this work, while `./semester` didn't?
 1. Look up the `chmod` program (e.g. use `man chmod`).
 1. Use `chmod` to make it possible to run the command `./semester` rather than
    having to type `sh semester`. How does your shell know that the file is
    supposed to be interpreted using `sh`? See this page on the
    [shebang](https://en.wikipedia.org/wiki/Shebang_(Unix)) line for more
    information.
 1. Use `|` and `>` to write the "last modified" date output by
    `semester` into a file called `last-modified.txt` in your home
    directory.
 1. Write a command that reads out your laptop battery's power level or your
    desktop machine's CPU temperature from `/sys`. Note: if you're a macOS
    user, your OS doesn't have sysfs, so you can skip this exercise.
