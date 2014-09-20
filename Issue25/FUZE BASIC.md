FUZE BASIC
Part 1 : Back to BASIC with the Raspberry Pi

Over the next few months The MagPi will publish a new series on learning BASIC. To whet your appetite, this month we will provide some background to the language and explain why it is still a great way to learn how to program.

There's a lot of talk about programming at the moment. The UK Government has done a fair bit to get it back on the education curriculum to make sure UK schools are teaching kids how to program from an early start. In fact, from this September schools in England must teach the fundamentals of computing in early primary school, and text based programming from key-stage 3 onwards (age 12).

While there may be some debate about how programming is being introduced into the cirriculum, what is important is that something is being done.

In the beginning...

Roughly 2 million years ago computers like the Research Machines 380Z were bulky things with clunky keyboards, terrible graphics and sound. Actually, some of them didn't have clunky keyboards. Instead they had little rubber pads for keys that felt like a cat's tongue!

These machines were limited in so many ways. For example, the Sinclair ZX Spectrum had just one sound channel and the only noise it could make was a beep. In fact, the command it had for this was BEEP! BEEP 1, 0 would make a C tone (0) for one second (1 ). I t gets worse. While it was beeping it was thought that it couldn't do anything else, so to make a game with music playing was considered impossible.

The Commodore 64 had huge great borders around the screen which again was originally considered impossible to display anything on. So early games were displayed on the letterbox in the middle of the screen.

The BBC Micro originally had no hardware to display character graphics (sprites) so it was originally considered impossible to program games in anything other than text.

Then the wizards came. They made the Spectrum sing and dance; turned the BBC Micro into an arcade machine with almost perfect renditions of Pac Man, Defender and Asteroids; and the Commodore 64 became a graphical and audio tour de force. I t really was the strangest time and of course it was not 2 million years ago, but just 30 years ago.

I t all started back in the mid to late 1 970's with companies like Atari and Apple. Atari decided to turn its console technology into something more sophisticated. The Atari 400 and 800 computers were ahead of their time in 1 979. High resolution graphics, 8 KB of RAM, up to 256 colours and 4 channel sound. Apple launched the Apple I in 1 976 and then soon after the Apple II . These were powerful machines, but they were also very expensive.

Compare this to the Sinclair ZX80 which was released in the UK, a year after the Atari 400, by the somewhat lesser known Clive (later to be Sir Clive) Sinclair. The Sinclair ZX80 had no sound, no graphics, no colour and had just 1 KB RAM.

However, it was cheap... less than ¡ê1 00 cheap... and all things considered it can be held partly responsible for kick-starting the home computer industry in the UK.

A brain by any other name

I t would be very unfair to credit any one company for the advent of the home computing revolution. I t would be more considerate to attribute this to those responsible for designing and manufacturing the CPUs and custom silicon that were the bedrock of all the computers of the day. While many home computers were released between 1 979 and 1 984, there were only three commonly used CPUs (Central Processing Unit). The CPU is the brain of any computer and, in general, everything else within the computer either is controlled by or feeds information to the CPU.

The CPUs of the time were the Zilog Z80, the MOS 6502 and the less common Motorola 6800. Their hardware and software designers are the people responsible for the digital world we live in today.

While all these machines were designed by different companies with different specifications and configurations, they all had one major thing in common. They were all supplied with the programming language BASIC. (Ok, not every single one came with BASIC. The Jupiter Ace was supplied with Forth! )

The earliest computers were generally programmed in either bare metal mode, known as machine code, or in the slightly more friendly Assembly Language. Machine code is often cited as being the most complicated programming language ever devised, but it is actually one of the simplest and it certainly has the smallest number of instructions to learn. The complexity comes from having to know the hardware inside-out: how the memory is structured, the input/output system, the video capabilities, etc. We won't even go into interrupts, storage or sound.

Next came a few languages designed to perform specific tasks. COBOL, for example, was suited to business applications whereas Fortran was suited to mathematics and science.

Between the late 1 950's and the early 1 970's many programming languages were developed. A number of them have survived... or at least variations of them have. C is possibly the best example as this is still one of the most commonly used languages today.

Welcome to BASIC

So what about BASIC then? BASIC (Beginner's Allpurpose Symbolic Instruction Code) was written to simplify programming into a more understandable, less mathematically reliant language that could be used to develop a wide variety of applications.

First launched 50 years ago, in 1 964, as Dartmouth BASIC by John Kemeny and Thomas Kurtz, its accessibility meant it went on to spawn many other versions over the next 30+ years. See http://www.dartmouth.edu/basicfifty for more info.

The first software product sold by Microsoft was a version of BASIC co-written by Bill Gates. I t went on to ship with every IBM PC and many others for years to come. A number of Microsoft BASIC products are still incredibly popular. Visual BASIC and VB.NET are in common use today.

Back to the 1 980's

In their heyday, the popular computers of the time - Apple, Commodore, Tandy, Sinclair, Atari and the Acorn BBC Micro - were all supplied with BASIC built in. Switch on and you would soon see the "Ready >_" prompt or something similar. Type in something, press the ENTER key and see what happened. At first you would invariably get a "Syntax Error", but you soon picked up the user guide and started reading tutorials. The first thing to learn was,

followed quickly by how to load a game from a cassette or, if you were very lucky, a disk drive!

Then came the magazines with game and program listings you could type in. Countless hours were spent entering these listings, often with very poor print quality, only to be bombarded with error after error when you came to run them.

The learning curve was steep, but fast, and before you knew it you were experimenting with your own programs and showing off to friends. I f you had it in you, you would be applying for a programming job in a fledgling game publisher or trying to set up you own.

That an industry was born is not surprising, as over 50 million 8-bit home computers were sold globally. The exposure to programming grabbed the interest of many.

What happened next however was a bit odd. At the time, programming was seen as the next big thing and so it was taught in schools, done at home or at a friends place and so on. However, it reached a critical mass fairly quickly. Programmers went on to develop more powerful programming languages, gaming systems took over, small publishing companies grew into huge corporations and programming became something of an elite occupation. As the industry settled down, programming all but dropped off the curriculum.

Back to BASIC

But 30 years later and now there is a huge wakeup call by many that has prompted the UK Government to realise that we do not have enough programmers available in the UK to supply demand. But this time around computers are "black boxes", with no easy way to learn about physical computing. Instead the entry point is a complex programming environment, developed by programmers for programmers. So where do we start?

At primary school children are being introduced to visual programming environments like Scratch that simplify the programming experience and do a great job of introducing computational concepts. They do not however offer the exposure to advanced programming that inspired so many of today's entrepreneurs the first time round.

In secondary school it looks like Python, another language derived from the early days, is being positioned as the language to best prepare students for the real world. However, BASIC is even easier to learn and the concepts learned with BASIC will provide a solid foundation for learning other languages.

BASIC for today and tomorrow

BASIC has continued to be developed over the years to keep it up-to-date and comparable to many other modern languages. Commands that were once considered bad practice (e.g. GOTO and GOSUB) along with line numbers are gone and replaced with structured programming techniques.

The main attraction to BASIC is its instant accessibility: enter your program, RUN it, get an error, fix it and try again.

Thirty years ago those original computers ran BASIC slowly - it was its Achilles heel. You could just about do anything with it apart from do it quickly. That was why once you had mastered the basic principles you quickly advanced on to more complicated, compiled languages.

Today, BASIC runs on machines measured in gigahertz, not megahertz, and with gigabytes of RAM, not kilobytes. I t is fast enough to program sophisticated games, especially when compared to the applications being published on today's mobile devices and tablets.

So if you are interested in learning to program but were wondering where to start, you will do yourself a favour by following our BASIC tutorials with your Raspberry Pi over the coming months.