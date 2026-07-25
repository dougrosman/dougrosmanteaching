---
title: Learn2Code 2026
draft: false
tags:
description: An online introduction to (creative) coding and software for media artists
date: 2026-07-26
---
![[learn2code2026-banner.png]]
https://editor.p5js.org/dougrosman/sketches/Ja8iV6-Ue
## ✩⋰ Overview ⋱✩

As artists working with . °˖✧ technology ✧ ˖°., we encounter code everywhere. There is much we can do creatively with off-the-shelf software and graphical user interfaces, but at some point our creative practice may require us to actually write some code.

This workshop introduces code broadly as an expressive medium, and as a tool—a glue that holds various parts of your projects together. What does it mean to make with code? Why (or why should we) learn to code at all when generative AI can conjure software seemingly out of thin air? Whatever our reasons are, the world of code and software can be complicated, abstract, and intimidating. The goal of this workshop is not necessarily to teach you how to code, but to provide a starting point for understanding where code lives, when and why you might need it, and how it fits together.

### Agenda

1. 10:00a – 10:20a — Settle in, make sure software is ready, introductions
2. 10:20a – 10:35a — What, where, how, why code?
3. 10:35a – 10:50a — The command line
4. 10:50a – 11:00a — Markdown
5. 11:00a – 11:30a — "Creative Coding" with p5.js

11:30a – 11:45a — Break

6. 11:45a – 12:15p — Making a website
7. 12:15p – 12:30p — "Create a Python script that..."
8. 12:30p – 12:45p — On TouchDesigner
9. 12:45p – 1:00p — Questions, open time

## 1 Preparation

1. **Create an account for the [p5.js web editor](https://editor.p5js.org/).** p5.js is a creative coding library built on JavaScript.
2. **Download and install [Visual Studio Code](https://code.visualstudio.com/) (VS Code).** VS Code is a *text editor*, which is a place to write code.
3. **Create an account on [GitHub.com](https://github.com/).** GitHub is a platform that allows you to store and share your code with others. (If you already have an account, please sign in to it in your default browser, you'll need that for the next step)
4. **Download and install [GitHub Desktop](https://desktop.github.com/download/)**. GitHub Desktop is a tool that makes GitHub (and git) a little easier to work with. Once installed, you can sign into your account.


## 2 What, where, how, why code?

![[allison-parrish-quote.png]]
https://www.instagram.com/p/Dal8D1bjswF/?img_index=1

> i haven't really gotten Political about this on insta, but i didn't use generative AI for any part of this project, not coding, not pcb design, not text annotation, and i don't use it anywhere else in my creative or production process either. can you imagine—refusing to savor even the smallest drop of the joys of attention and making—shirking even the smallest part of my duty to make and share knowledge—yuk

**Stray thoughts**
- Learning the core principles of code/computation (abstraction, logic, pattern recognition, data structures) is more important than learning a particular coding language. Coding languages don't die, but what is popular changes over time. Languages themselves change over time.
- Focusing on a single coding language first will make it easier to learn other languages later.
- Don't seek to "learn a coding language". Rather, understand what is needed for a given project, and find the tools that will get you there (this is difficult)
- Learning math, unfortunately, is important
- Sometimes the code is the art. Sometimes the code is simply required to make the art. Gain the wisdom to know the difference.
- [There is rarely a single tool for or approach to a given process](https://canitrundoom.org/).
- Learning code—like most things—is non-linear. Like most things, it requires patience, time, and curiosity.
- When are we artists? When are we technicians?

## 3 The command line

The command line, which we access through a *terminal*, is a way to control your computer through written commands. You can navigate files, execute programs, and change how your operating system functions. The command line preceded the graphical user interfaces we're used to (clicking on buttons with a mouse), and is traditionally how people have interfaced with computers.

The command line has taken on a new valence of importance in the wake of agentic AI models. Since AI models rely on text, the command line—as a text-based interface—is what allows AI models to perform so many functions on your computer.

### What we did

Everything below is Mac-specific. On Windows, you'd use PowerShell or Command Prompt, and some of the commands are different.

1. **Open the Terminal.** Use Spotlight (`⌘` + `Space`) and type "terminal", or find it in Applications → Utilities.
2. **Type `ls` and press enter.** `ls` means "list": show me the folders and files in the directory I'm currently in.
3. **Notice the `~`.** That squiggle is shorthand for your *home folder*—that's where the terminal starts you off.
4. **Type `open .` and press enter.** This opens a Finder window showing wherever you currently are in the terminal. It's a nice way to connect the two ways of looking at your computer: the terminal and the Finder are showing you the *same files*.
5. **Type `cd Desktop` and press enter.** `cd` means "change directory." You can only `cd` into a folder that exists inside the folder you're currently in.
6. **Type `ls` again.** Now you're seeing the contents of your desktop.
7. **Type `clear` when things get messy.** It just wipes the screen so you can start fresh.

### A command line program: FFmpeg

[FFmpeg](https://ffmpeg.org/) is a command line tool for working with video and audio. It's quietly built into an enormous amount of the software we already use. It doesn't come with your computer, but it's easy to install.

I used it to make an aggressively compressed version of a video of my cat:

```bash
ffmpeg -i butternut.mov -c:v libx264 -crf 51 -b:a 16k butternut-low.mp4
```

Reading that left to right: run `ffmpeg`, take `butternut.mov` as the input (`-i`), encode the video with the H.264 codec (`-c:v libx264`), set the quality to be very bad (`-crf 51`—higher numbers mean more compression), squash the audio down to a low bitrate (`-b:a 16k`), and write the result out to `butternut-low.mp4`.

You are not here to memorize any of that. The point is what it *feels* like to do something on your computer from the command line: you type things in very particular ways, and then a program does the work that you might otherwise do by exporting from Premiere.

### Automating with a bash script

A single command does one thing once. A **bash script** (a `.sh` file) is a list of commands you can run together, and repeat.

I had an AI model write me a script that runs that same FFmpeg command over and over on its own output, so the video gets compressed, then re-compressed, then re-compressed:

```bash
./compressloop.sh 40
```

That produced 40 progressively destroyed versions of the video. By version 40 both the image and the audio are extremely crunchy—which might be exactly what you want, if compression artifacts are your material.

Some honesty here: I could not write that script from scratch right now. I know *how* I would learn it, and I know where to look, but this is a place where I lean on AI models to write small scripts for me. The most complicated thing I've done this way was using FFmpeg to stitch together every participant's AI-generated video from a workshop, with each person's prompt rendered as white text on a black frame before their clip—instead of manually assembling all of that in Premiere.

One more thing worth knowing: everything that bash script did could also have been written in Python. Which is better? In this case, neither. It depends on the project and on what you're comfortable with.

### Where to learn more

- [The Missing Semester of Your CS Education](https://missing.csail.mit.edu/) (MIT) — Free, and the single best place to actually learn the command line. Start with lecture 1 ("Course overview + the shell") and lecture 2 ("Shell Tools and Scripting"). It's aimed at CS students, but it's teaching exactly the practical stuff nobody ever teaches you.
- [explainshell.com](https://explainshell.com/) — Paste in any command you find online and it breaks down what every single flag does. Extremely useful when an AI model or a tutorial hands you something cryptic.
- [Installing FFmpeg](https://ffmpeg.org/download.html) — On a Mac, the easiest route is to install [Homebrew](https://brew.sh/) first, then run `brew install ffmpeg`.

## 4 Markdown

Markdown is a widely-used "plaintext" language, and increasingly, another fundamental building block for how people prompt AI agents. I use markdown for note-taking in Obsidian, and then publish these simple markdown pages as web pages.

### Plain text is the foundation

Before we write any code, let's bring our attention to **files**. Code is an abstract thing, but it begins as text, and that text usually lives inside a file.

Open TextEdit (or Notepad on Windows). By default it opens in **rich text**—you can change fonts, center things, make it look nice. That's word processing. Now go to Format → Make Plain Text. What you have left is a document that is *exclusively* text. No formatting, no hidden extra stuff.

Now type the word `hello` and save it. The file **extension** you give it decides what the text is understood to be:

- `hello.txt` — a text file, meant to be read
- `hello.py` — technically a Python script (it won't run, because "hello" isn't valid Python)
- `hello.js` — technically a JavaScript file
- `hello.md` — a Markdown file

Same text. Different meaning. Plain text is the stripped-down foundation that becomes code.

### So what is Markdown?

Markdown sits somewhere between plain text and code. It's plain text with a little formatting sprinkled on top—certain characters you type trigger an effect when the file gets rendered.

```markdown
# A heading
### A smaller heading

Some normal text with **bold words** and *italic words* in it.

- a list item
- another list item

1. a numbered item
2. another numbered item

[a link](https://example.com)
![an image](my-image.png)

> a quotation
```

That's most of it. It really is simpler than it seems.

### Why I use it

This whole workshop page was written in Markdown, in a free note-taking app called [Obsidian](https://obsidian.md/), and then published as the website you're reading.

I used to use Notion for my class documents and notes. The downside of Notion (and Google Docs, and Canvas) is that your writing lives in a proprietary format on somebody else's cloud. If the company goes away, or I get locked out of my account, what happens to my notes? You can always export, sure—but that's not the file's *native* state.

I like Markdown because it always already *is* what it is. It looks nice when it's rendered, but I can also just open it in TextEdit and read it. There's no extra special stuff complicating it. It's on my computer at the end of the day.

### Markdown and AI

The other reason to know about Markdown right now: large language models ingest text and generate text, and Markdown has become something like their native format.

Rather than just sitting down and typing into a chat box, people increasingly write out long, structured specifications for a prompt or a project *as a Markdown file*, and then hand that file to an AI agent to read and execute. You'll also see `.md` files all over coding projects—READMEs, documentation, agent instructions. When you see one, remember: it's just text, with a little formatting sprinkled on top.

One confusing bit of terminology: it's called **Markdown**, but the *type* of language it is is a **markup language**—the same category as HTML. Don't get too caught up on names. There's a lot of terminology, and you're not going to memorize 10% of it today.

## 5 "Creative Coding" with p5.js

Go to the [p5.js web editor](https://editor.p5js.org/). You don't strictly need an account, but it's nice to have one so you can save and share your sketches.

Some have described code as *language that executes*—language that does things, language that performs. There's a whole subfield of **critical code studies** concerned with how we talk about what code does, and organizations like the [Electronic Literature Organization](https://eliterature.org/) dealing with poetry and code and the ways code itself becomes poetry. (Judd Morrissey, one of our faculty, works right in this space.)

Markdown had *traces* of code. Now we're actually programming.

### First, some terminology

**p5.js is not a programming language.** It's a **library**: a big piece of code, written on top of a programming language, that extends what that language can easily do.

The language underneath is **JavaScript**—the native programming language of the web. If you're using the web, you're encountering JavaScript. It has loops and variables and if-statements, just like other languages.

If you open the little arrow on the left of the editor, you'll see the sketch is actually three files: `index.html`, `sketch.js`, and `style.css`. For now, close that back up and work only in `sketch.js`.

### What we did

1. **Delete everything in `sketch.js`** so we're starting from an empty file.
2. **Write a `setup` function.** Type `function setup()`, then an opening curly bracket `{`. The editor makes the closing one for you; press enter and it drops to its own line. Everything between the curly brackets belongs to this function.
3. **Inside `setup`, type `createCanvas(400, 400);`** — spelling and capitalization have to be exact. This makes a 400 × 400 pixel canvas.
4. **Below that, type `background(100);`** — a dark gray.
5. **Press play.** There's your canvas.
6. **Below `setup`—outside its curly brackets—make a second function: `function draw() { }`.**
7. **Inside `draw`, type `ellipse(100, 100, 60, 100);` and press play.** A circle appears. Check the **auto-refresh** box at the top so you don't have to keep pressing play.

Those four numbers are **arguments** we're passing to the `ellipse` function: x position, y position, width, height.

A thing worth pausing on: in math class, the origin is at the bottom-left and positive Y goes *up*. On a screen—in p5.js, in Processing, in most graphics contexts—**`0, 0` is the top-left corner and positive Y goes *down***.

8. **Replace `100, 100` with `mouseX, mouseY`.** Now you have a drawing program.
9. **Add `print(mouseX);` to see what that actually is.** Move your cursor around and watch the numbers in the console below. `mouseX` is *just a number*—somewhere between 0 and 400, because that's how wide the canvas is.
10. **Since they're just numbers, put `mouseX` and `mouseY` in the width and height slots too.** Now your mouse position controls the size of the ellipse as well as its location.
11. **Add color with `fill()`, above the `ellipse` line.** Order matters—p5.js runs top-to-bottom, so `fill` has to come before the shape it's filling. `fill()` takes red, green, and blue values from 0 to 255. I googled "color picker" and pasted in a green I liked.
12. **Then swap `mouseX` and `mouseY` into the color values too.** Now your cursor is painting with color.
13. **Leave yourself a comment.** Two forward slashes (`//`) in JavaScript makes a note that does nothing. Useful for remembering what four anonymous numbers mean.
14. **Do a little math.** If the ellipse gets too big in the bottom-right corner, divide: `mouseX / 4`.

Where we ended up:

```javascript
function setup() {
  createCanvas(400, 400);
  background(100);
}

function draw() {
  fill(mouseX, 150, mouseY);
  // ellipse: x position, y position, width, height
  ellipse(mouseX, mouseY, mouseX / 4, mouseY / 4);
}
```

About fifteen lines of code, and this is roughly what it feels like to work with code: you change little words, and the little words have big knock-on effects on the expression of your program. Much of what code really *is*, is moving numbers around—making one kind of data interact with another. Here, we're turning numbers into color.

### `print()` vs `console.log()`

Try `console.log("hello");` — it does the same thing as `print()`. `console.log` is vanilla JavaScript; `print` is p5.js.

So why does `print` exist? Because `console.log` already assumes you know what a console *is*. (If a website is a stage with the curtains up, the console is backstage: messages getting passed around that never appear on the page itself. Every browser has one.) p5.js was made by a community of artists and educators trying to make coding less intimidating, so they repackaged `console.log` into something closer to human language. That repackaging *is* the library.

The traditional first program in most languages prints "hello world." In p5.js, the hello world is drawing an ellipse.

### So, what's a library?

Open `index.html` in the editor. Up at the top, there's a line importing p5.js from a web server somewhere else in the world—a CDN called jsDelivr. Click through to that link and you'll find a **massive** JavaScript file that a community of people has been adding to and tweaking for a decade.

JavaScript has no `ellipse()` function. JavaScript has no `fill()`. p5.js does. When you write `ellipse`, JavaScript looks into that library file to find out what you mean. You *could* do all of this in plain JavaScript—it would just take a lot more complicated code.

So much of how we interact with software is through libraries. p5.js is a nice bubble on top of JavaScript that simplifies things for making interactive visuals and audio.

### A little history

**Processing** was created in 2001 by Casey Reas and Ben Fry—two computer scientists/artists—as a creative coding environment built on Java, which was the dominant programming language at the time. (Java and JavaScript are *not* siblings, despite the names. Someone once put it: Java is to JavaScript as car is to carpet.)

**p5.js** was spearheaded by the artist [Lauren McCarthy](https://lauren-mccarthy.com/) around 2014–2015, essentially asking: what if Processing ran natively on the web? Lauren visited SAIC for a lecture this past spring; her work critically examines the social dimension of smart technologies and how technology shapes our relationships.

We've taught p5.js in our department's intro class for years. Not because it's the "right" language, but because setting up coding environments—making sure the right files are in the right places talking to each other—is genuinely the hard part, and it's a rough place to spend your first day. p5.js lets you sit down, write a few words, and make something beautiful happen on the screen.

I also just love it. It's my sketchbook. I don't draw well by hand, so when I want to make something without it being a big research-driven project, I use p5.js. And code doesn't have to stay on the screen: I like taking p5.js sketches, exporting them as vector files, and drawing them out with a pen plotter.

## 6 Making a Website

This is the most hands-on part of the workshop. In about thirty minutes we made a real, public, free website.

### 6.1 Make a repository on GitHub

1. Go to [github.com](https://github.com/) and make sure you're signed in.
2. Click the **+** dropdown in the upper right → **New repository**.
3. Give it a name (I used `learn2code-2026`). Names are up to you.
4. Leave the visibility set to **Public**.
5. Check **Add a README file**. GitHub repos don't like being empty—the README just gives it something to start with.
6. Click **Create repository**.

Note what shows up: a `README.md` file. Markdown again.

A **repository** ("repo") is, for our purposes, a fancy folder. You *can* create and edit files directly on github.com, but its editor is bare-bones—that's not where we want to work.

### 6.2 Clone it to your computer with GitHub Desktop

1. On your repo's page, click the green **Code** button → **Open with GitHub Desktop**.
2. GitHub Desktop will ask where to put it. This is the **local path**—where the folder will live on your computer. I put mine on my desktop for the workshop; normally I keep all my repos in one place.
3. Click **Clone**. "Clone" is a fancy way of saying "download this folder to my computer."
4. In GitHub Desktop, find the button that says **Open in Visual Studio Code** (or **Open in External Editor**) and click it.

### 6.3 Wait—what are all these tools?

![[learn2code-2026-draw.png]]

- **GitHub** is a platform—a cloud where your code lives. Think of it as a social network for code: people upload their projects, and if they're public, other people can read them, download them, and build on them. This is the culture of **open source**. Companies also use it so that many people can collaborate on the same body of code. (GitHub is owned by Microsoft.)
- **Git** is not GitHub. Git is free and open source **version control** software—it keeps track of every change you make, and it lets you go back in time to earlier versions. Sort of like Google Docs' version history, except Git makes you save your checkpoints *manually*.
- **GitHub Desktop** is just a tool that helps you move code between GitHub in the cloud and your own computer. Git on its own can be genuinely annoying to work with; GitHub Desktop makes it friendlier.
- **VS Code** is a **text editor**. In the same way that Microsoft Word has tools built in to help you write papers, VS Code has tools built in to help you write software. By itself it's just a way to view and edit files that already exist on your computer. (Also a Microsoft product.)

The loop you'll repeat forever: **write code on your computer → commit → push it up to GitHub.** And because it's on GitHub, you can clone it onto any other computer and pick up where you left off.

Plus, GitHub offers **GitHub Pages**: a free service that turns the code in your repo into a public website.

### 6.4 Write some HTML

1. In VS Code's file explorer on the left, click the **new file** icon and name it `index.html`. **All lowercase, no spaces.**
2. In the empty file, type a single exclamation point `!` and press enter. VS Code generates all the required components of an HTML page for you.
3. Find the `<body>` tags. `<body>` is an opening tag; `</body>` is a closing tag (you can tell by the forward slash). Everything we put on the page goes between them.
4. Add a heading and a paragraph:

```html
<body>
    <h1>Welcome to my website</h1>
    <p>Here is some text.</p>
</body>
```

HTML stands for **HyperText Markup Language**. It's pretty straightforward compared to JavaScript—you're not doing complicated programming, you're assembling content and linking things together. Every element is an opening tag, a closing tag, and content in the middle.

### 6.5 Actually look at your page

The quick way: right-click `index.html` in the file explorer → **Reveal in Finder** → double-click the file. It opens in your browser. (Notice the URL starts with `file:///Users/...`—you're looking at a file on your computer.)

That works, but you have to save and refresh manually every time you change something. Better:

1. Click the **Extensions** icon in VS Code's left sidebar.
2. Search for **Live Server** (by Ritwick Dey—it's the one with ~80 million downloads). Click **Install**.
3. Open VS Code's settings (gear icon, bottom left → Settings), search for **autosave**, and set **Files: Auto Save** to **afterDelay**. Now your files save themselves about a second after you stop typing.
4. With `index.html` open, click **Go Live** in the bottom bar of VS Code.

Your page opens at something like `http://127.0.0.1:5500`. Arrange your windows so you can see the code and the page side by side—now the page updates as you type.

One important note: that URL *looks* like a website, but it's a little pretend web server running on your computer only. If you copy that link and send it to a friend, they'll get nothing.

### 6.6 Add some CSS

1. Make a new file called `style.css`.
2. **CSS** is the styling language of the web: typography, layout, color. It's its own language with its own syntax—curly brackets instead of angle brackets, and a semicolon at the end of each line.

```css
body {
  background-color: darkseagreen;
}
```

Everything inside those curly brackets styles the `<body>` tag—which means everything inside the body of your HTML.

(`darkseagreen` is one of ~140 named colors hardcoded into the early web, back when computers couldn't handle the 16.7 million colors we take for granted now. A nice bit of history still with us. You can also use RGB values.)

3. **Nothing happens.** Being in the same folder does *not* mean two files are talking to each other. Go back to `index.html` and, inside the `<head>` section, type `link` and press enter. Then set the `href` (short for hypertext *reference*) to your CSS file:

```html
<link rel="stylesheet" href="style.css">
```

Now you get a green background.

This is the thing I most want to drive home: the initial discomfort of learning to code usually isn't the code. It's the *setup*—the server, the autosave, knowing where files live and how to make them talk to each other. Most of teaching Intro to Web Development was teaching students how files exist on a computer.

### 6.7 Commit and push

1. Go back to **GitHub Desktop**. It's showing you a list of changes—green plus signs for new files.
2. In the bottom left, write a short **summary** of what you did. "Add new files" is fine. Think of it as a checkpoint, or a save file in a video game. It's for future you.
3. Click **Commit to main**. That logs your changes in an official format.
4. Click **Push origin**. *That's* what actually sends them up to GitHub.

Refresh your repo on github.com and you'll see `index.html` and `style.css` sitting there.

### 6.8 Publish it with GitHub Pages

1. On your repo page, click **Settings** (the repository's settings, not your account settings).
2. Click **Pages** in the left sidebar.
3. Under Branch, choose **main**, then click **Save**.
4. Wait a minute or two. Refresh, and a link will appear at the top with a **Visit site** button.

That's a real, public, free website.

For all the HTML and CSS knowledge we have—which isn't much—I think it's genuinely cool to be able to publish something like this and share it with anyone. My own site, [dougrosman.com](https://dougrosman.com/), works the same way: I write code in VS Code, commit and push in GitHub Desktop, and the site updates. (I publish through [Netlify](https://www.netlify.com/) rather than GitHub Pages, mostly because it makes custom domain names easier.)

### 6.9 Bonus: put a p5.js sketch on your page

1. Make a new file called `sketch.js` and paste in your p5.js code from the web editor.
2. In `index.html`, at the very end of the `<body>` section, type `script` and press enter, then set the source:

```html
<script src="sketch.js"></script>
```

3. Nothing draws yet—**you haven't imported the library.** Go back to the p5.js web editor, open its `index.html`, and copy the line that loads p5 from jsDelivr. Paste it into the `<head>` of your own `index.html`:

```html
<!-- copy this exact line out of index.html in the p5.js web editor -->
<script src="https://cdn.jsdelivr.net/npm/p5@x.x.x/lib/p5.min.js"></script>
```

Now your canvas shows up.

Worth doing along the way: open your browser's console (right-click → **Inspect** → **Console** in Chrome/Arc/Firefox; in Safari you first have to enable Settings → Advanced → **Show features for web developers**, then Develop → Show JavaScript Console). Drop a `console.log("hello world")` into `sketch.js` to confirm your JavaScript is actually connected to your HTML. This is how you check your wiring.

4. To make the sketch full-screen, use `windowWidth` and `windowHeight` instead of hardcoded numbers, and add a `windowResized` function so the canvas keeps up when someone resizes their browser:

```javascript
function setup() {
  createCanvas(windowWidth, windowHeight);
  background(100);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
  background(100);
}
```

5. `createCanvas()` creates an actual HTML element called `<canvas>`—JavaScript can write HTML into your page. You never typed it, but it's there, which means CSS can style it:

```css
canvas {
  position: fixed;
  left: 0;
  top: 0;
  z-index: -1;
}

body {
  background-color: darkseagreen;
  font-family: Arial, sans-serif;
  color: white;
  font-size: 60px;
}
```

Think of a webpage as a sandwich of stacked layers. **`z-index`** controls the stacking order. Setting it to `-1` pushes the canvas *behind* the content of the page, so your sketch runs in the background and your text sits on top.

6. Commit and push again. Give it 30 seconds to a minute—on the repo's code page there's a small dot next to your latest commit showing deployment progress (orange = pending, green check = live).

**If your site still looks old:** your browser is showing you a cached copy. `⌘ + R` refreshes; **`⌘ + Shift + R` refreshes *and* clears the cache**. A genuinely useful trick any time a website is behaving strangely.

### Learn Git & GitHub properly

I could run a whole workshop on just Git and GitHub. If you want to actually get comfortable with it, start here:

- [Git and GitHub for Poets](https://www.youtube.com/playlist?list=PLRqwX-V7Uu6ZF9C0YMKuns9sLDzK6zoiV) — Daniel Shiffman's playlist on The Coding Train. He teaches the whole thing by writing a poem about rainbows. It covers branches, forks, pull requests, cloning, push/pull, merge conflicts, and GitHub Pages. There's also a [companion page on the Coding Train site](https://thecodingtrain.com/tracks/git-and-github-for-poets/).

## 7 "Create a Python script that..."

A website is just one thing. As media artists working with code, maybe you're doing hardware with Arduino, maybe a live performance, maybe an interactive installation. Something can be a website *and* an interactive installation. There aren't really rules—if you can make it work, it works.

**Python** is the language I'd point you toward after p5.js. It's a language in its own right, and it's also embedded inside an enormous number of other tools (TouchDesigner, Blender, Houdini, basically all of machine learning).

To run a Python script, you write your code in a `.py` file and then, in the terminal, run:

```bash
python myscript.py
```

### What we did

The simplest version of this: go to [chatgpt.com](https://chatgpt.com/) or [claude.ai](https://claude.ai/), ask for a Python script, copy the code into a `.py` file, and run it in your terminal. That works fine.

If you're doing this a lot, though, it's better to bring the AI model *into* your coding environment. In the workshop I used Claude Code inside VS Code:

1. Ask for what you want: *"make me a Python script that generates random numbers."*
2. It writes the file directly into your project—`random_numbers.py`.
3. Open a terminal **inside VS Code** (Terminal → New Terminal—you don't need a separate app) and run it:

```bash
python random_numbers.py
```

4. Out come a bunch of random numbers. You can also just ask the model to run it for you, and it'll execute the command itself—which is exactly the loop from Section 3: AI models act on your computer *through the command line*.

### On prompting

Echo asked a version of the question a lot of people are asking: how do I learn enough code to vibe code better?

Honestly, it's a complicated problem. If you're an engineer who already works with complicated systems, you can work extremely well with these tools. If you know *some* things, you may actually be better off prompting in a general, non-specific way.

As the models improve, people are finding that instead of "build this using the MediaPipe library and React and…", you're often better off saying **"make me an interactive hand-tracking website"** and letting it choose. I'd have told you the opposite a year ago—that knowing the right terminology helps you prompt better. Things are changing fast.

So where do I land? Learning code might help you prompt better. But I think learning code mostly helps you understand *the computer* better, and that might be important enough on its own.

## 8 On TouchDesigner

I bring up [TouchDesigner](https://derivative.ca/) at the end to say that it also falls under the umbrella of creative coding, from a completely different direction.

p5.js is *explicitly* a creative coding paradigm: a coding library built for creative tasks. TouchDesigner is a commercial, **node-based** program that has gotten extremely popular with media artists over the last few years, largely because it's much more performant—it can render far more advanced graphics in real time. There's a free non-commercial license; it lets you do essentially everything but caps your output resolution and doesn't let you make money with it. I've been slowly teaching more of it in my own classes, where I used to only teach p5.js and JavaScript.

Here's why it belongs in a *Learn to Code* workshop: **TouchDesigner incorporates Python natively.** I showed a hand-tracking sketch from my computer vision class where an effect alternates between green and pink every second. There's a node making a number ramp from 0 to 1 over and over, and a tiny Python script listening to it—every time it resets, swap which of two things is being fed through.

You don't *have* to write code to do that. You could do it by getting clever with how you lay out your nodes. But at some point, familiarity with Python becomes a must if you want to level up what you can make inside TouchDesigner.

That's the broader point: code is useful on its own, and it's also the thing that gets glued on top of other systems and other tools.

On how to approach a tool like this: I started learning TouchDesigner because somebody had built a specific tool I wanted to use for a specific performance. I recommend that approach. If you have something you want to make and it seems like you must learn a tool to do it—do that. "I just want to learn TouchDesigner," with no project in mind, is a much harder way to go.

## 9 Questions, open time

A few things that came up, and a few things worth repeating.

**Which language should I start with?** p5.js if you've never coded, because it's beginner-friendly and lets you learn the big abstract principles without the surrounding complexity. Then Python, because it turns up everywhere. But really it depends on your goal.

**Can I use p5.js on my actual artist website?** Yes—that's Section 6.9. My [sketches page](https://dougrosman.com/sketches) runs on p5.js. If you use Squarespace or Cargo, it's often possible through their custom JavaScript features, but you'll jump through more hoops.

**Should I write my website from scratch?** I did, but only because I've taught Intro to Web Development for years, so it isn't much work for me. As a busy artist, I don't necessarily recommend it.

**On using AI to make the thing you want** (this came out of a question about hacking an electric typewriter): you have to be responsible for your own learning. If you're going to have it do things for you, just be honest with yourself about what you want. Do you want to understand how this works? Then ask it to teach you as it goes. Do you just want to hack the thing and make art with it? Then have it do that, and don't be precious about knowing how every single component works. But if you find you *can't* get there, or that the satisfaction isn't there when ChatGPT does it for you—take the steps to learn.

**The joy of sketching in p5.js cannot be replicated by prompting.** Those are two different things. Neither is better. They're different ways of approaching problem-solving. Do you want to work with the code yourself and figure things out, or do you want to make something beautiful and move on? As an artist, there are no rules.

**Finally:** there's so much out there that it can be genuinely overwhelming. Don't feel like you have to download and use every single thing I showed today. Pick one thing and stick with it for a while—do the Coding Train tutorials for p5.js, or jump into the Python resources below. Then your projects will take you to the other tools.

*When are we artists? When are we technicians? When are we both?*


### Resources

#### p5.js & Creative Coding
- [The Coding Train](https://thecodingtrain.com/) — Beginner-friendly coding tutorials and challenges in p5.js and Processing, run by Daniel Shiffman.
- [Patt Vira (Youtube)](https://www.youtube.com/@pattvira) — Playful, project-based creative coding tutorials for beginners.
- [Gorilla Sun](https://www.gorillasun.de/) — A blog of tutorials and essays on creative coding, generative art, and computational design.
- [The Nature of Code (book)](https://natureofcode.com/) — Daniel Shiffman's book (free online) on simulating natural systems with code, using p5.js.

#### The Command Line, Git & GitHub
- [Git and GitHub for Poets (Youtube)](https://www.youtube.com/playlist?list=PLRqwX-V7Uu6ZF9C0YMKuns9sLDzK6zoiV) — Daniel Shiffman teaches git and GitHub from scratch by writing a poem about rainbows. The friendliest introduction there is.
- [The Missing Semester of Your CS Education](https://missing.csail.mit.edu/) — MIT's free course on the command line, shell scripting, git, and all the practical tooling nobody formally teaches. Start with lectures 1 and 2.
- [explainshell.com](https://explainshell.com/) — Paste in any terminal command and it explains every flag. Useful when a tutorial or an AI model hands you something cryptic.
- [FFmpeg](https://ffmpeg.org/download.html) — The command line tool for video and audio. On a Mac, install [Homebrew](https://brew.sh/) first, then run `brew install ffmpeg`.

#### Markdown & Notes
- [Obsidian](https://obsidian.md/) — Free note-taking app built on plain markdown files that live on your own computer. This workshop page was written in it.
- [Markdown Guide](https://www.markdownguide.org/basic-syntax/) — A clear reference for markdown's (small) syntax.

#### TouchDesigner
- [Elekktronaut (Bileam) (Youtube)](https://www.youtube.com/@elekktronaut) — Tutorials on building audio-reactive and generative visuals in TouchDesigner.
- [Interactive and Immersive HQ (Youtube)](https://www.youtube.com/@TheInteractiveImmersiveHQ) — TouchDesigner tutorials and resources for interactive and immersive installation work.
- [Acrylicode (Youtube)](https://www.youtube.com/channel/UC6kz8lb80gitsmjx0gnZC8Q) — Calm, methodical beginner crash courses and project breakdowns in TouchDesigner.

#### AI & Machine Learning Art
- [Artificial Images (Youtube)](https://www.youtube.com/channel/UCaZuPdmZ380SFUMKHVsv_AA) — Derrick Schultz's demos and explanations of making art with machine learning tools, going all the way back to 2018. He also runs paid courses through [his Patreon](https://www.patreon.com/bustbright), including one on Claude Code and AI-assisted coding that's running right now.
- [ml5.js](https://ml5js.org/) — A friendly, browser-based machine learning library built for artists and creative coders, designed to pair with p5.js.

#### General Programming
- [samwho.dev](https://samwho.dev/) — Well-written and approachable visual essays that explain complicated technical concepts related to algorithms and computation
- [Freecodecamp](https://www.freecodecamp.org/) — Free, self-paced curriculum covering web development and programming fundamentals.
- [Free/open resources for learning Python](https://posts.decontextualize.com/python-resources/) — Curated by Allison Parrish
