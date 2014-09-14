FUZE BASIC
Part 2: Variables, procedures and sprites

A few years ago I brought my old BBC Micro down from the loft to show my kids how I started in computing. To my surprise my two girls Molly and Gracie, and my son David were all intrigued by the BASIC prompt and the Syntax Error response returned by about every input.

They wanted to know more so we spent a few days learning a few BASIC programming commands and playing some classic games. It got me thinking that wouldn¡¯t it be great to bring back a computer in the same vein... something that brought access to programming right to the forefront just like it was back in the 1980's.

The Raspberry Pi turned out to be the answer as it retains many attributes of the BBC Micro such as accessible GPIO ports. The only downside was that it did not have a version of BASIC directly suited to our needs. Enter Gordon Henderson, the author of the WiringPi libraries, who developed a version of BASIC called RTB (Return To BASIC). If you have programmed in BBC BASIC (arguably one of the best ever versions of BASIC) then you will be very familiar with RTB. It is designed specifically to support the Raspberry Pi and its GPIO.

A deal was struck between FUZE and Gordon to produce FUZE BASIC, which includes a vast array of enhancements. These tailor FUZE BASIC so it is more in line with the requirements of the newly revised UK IT curriculum.

At FUZE we focus on FUZE BASIC to deliver a learning experience far more accessible to a broader age range and ability group than more complex languages. Quite simply, BASIC is easier to pick up and learn than just about any other language ever devised. You do not need to be adept at maths, you do not need to understand the operating system to any great extent and you certainly don¡¯t need to have programmed before.

While more experienced programmers might scoff at us BASIC students, I assure you that BASIC has something for everyone. Even the most adept coders will find BASIC a great platform to test out ideas and experiment.

Getting FUZE BASIC

I am very pleased to announce that FUZE BASIC is available for FREE! Visit http://www.fuze.co.uk click on Resources and then download the latest FUZE boot image from the FUZE BASIC Updates tab. The FUZE boot image is the same as the Raspbian boot image, but configured with the latest version of FUZE BASIC.

You will need to unzip the boot image file and install it onto an SD card. Please note that you need a minimum 8GB SD card. You also need software to install the image onto the SD card. Windows users can use Win32DiskImager, but full installation details for Linux, MacOS and Windows are available from the official Raspberry Pi website at http://www.raspberrypi.org/documentation/installation/installing-images/.

Next boot your Raspberry Pi with your new FUZE image. There isn¡¯t anything particularly different with the boot image compared to the standard Raspbian image, except for a new Desktop background image and a FUZE BASIC icon.

First, open the Fuze folder and then open the Programs folder. Inside this, create a new folder called MagPi .

We are going to create a game with this tutorial so the next thing is to download the graphics.

Please go back to http://www.fuze.co.uk and to the Resources page. Click on the Tutorials tab and download the six sprites contained in 'The MagPi Tutorial' section. These sprites are the player's rocket ship, the enemy rocks and the ever important bullet. Download and copy these six files into the MagPi folder we created earlier.

On the FUZE desktop, double click the FUZE BASIC icon to start FUZE BASIC.

The welcome screen will appear and you will be presented with the Ready> prompt.

Let's familiarise ourselves with the environment.

The Ready> prompt means you are in Direct mode. Type in Hello and press <Enter>. You will get the message, ¡°Equals expected¡±. That is exactly what should happen. The computer has no idea what Hello means. Instead, enter:

I suspect there are many of you who are already more than comfortable with what is going on here, but we need to explain to the newcomers.

Variables

The words Number1, Number2 and Answer are just names. They are called variables. Variables are tags we store values in. We could have used any name but generally it is best to use names that make sense in the context of the program. I f we wrote a program using variables like N1 and N2 and A then when we come back to the program later we will have no idea what everything means. However, variable names like ShipX and ShipY are more obvious. Try and make this a habit. You will appreciate it later.

So, we stored the number 10 in the variable Number1 and 10 in the variable Number2. We then said that the variable Answer equals Number1 + Number2.

At this point you should know what the value of Answer is. Do you? I hope so or we¡¯re in big trouble! Enter:

You should see 20.

If anything else whatsoever happens then something has not gone to plan and you should go back and check where you went wrong.

Direct mode and Edit mode

We are currently in Direct mode. This is where we can enter commands and expect an immediate response. For example we can check variables and enter simple instructions. I t¡¯s not programming though is it? Press F2 to enter the FUZE BASIC Editor.

Useful commands/shortcuts in Direct mode

EXIT Exit and return to the desktop
DIR List files in the current folder
CD name Change to folder name
CD . . Go back one folder
LOAD name Load program name
SAVE name Save program name
NEW or F12 Clear program from memory
F2 Open the editor
RUN or F3 Run the current program

You will see a blank screen with a green flashing cursor and a dotted line across the bottom. This is the Editor environment. Here we can enter a list of program instructions that can be saved and executed (RUN) whenever we want.

Press F2 again. This will take you back to Direct mode. Actually it will ask you for a file name. In this first case don¡¯t bother, just press F2 again and it will put you in Direct mode again. One last time, press F2 again and you will be back in the Editor. You get the idea - F2 takes you between the Editor and Direct mode.

Hello MagPi

In the Editor enter the following program:

You don¡¯t actually need to worry about capitals or lower case when entering commands. It is a good habit in FUZE BASIC to type commands in capitals, but it is not essential. However the names we give to variables, as we did above with Number1 and Answer etc., are set in stone. I f we give a variable the name NUMBER1 then we must refer to it as such every time in our program. Variable names are case-sensitive. If we expect the variable numBER1 to return the same result then we are in for a big surprise. The variable numBER1 has not been defined so will generate an error.

Enough of the dull stuff! You should at this point be in the Editor with the program as listed on the left. Press F3. If at this point the program has not been saved then it will ask you to do so. Just enter a name like Hello and press <Enter>. The program should then run. ¡°Hello MagPi¡± should display in a never ending list down the screen.

To stop it, press the <Esc> key.

Press F2 to go back to the Editor and change the program so that it looks like the following:

The only difference is that we have added a space in between MagPi and the end quotation mark and added a semi-colon to the end of the PRINT line. The semi-colon tells BASIC to display the next item immediately after the last one and not on a new line. The space just puts a gap in between. Press F3 to run the program again. This time instead of a long list of ¡°Hello MagPi¡± going down the screen, this time it displays ¡°Hello MagPi ¡± across the screen.

More about the Editor

Again, press <Esc> to exit the program and then F12 to wipe the current program from memory. You should have a blank screen in the Editor. I f not then try pressing F2 and F12 until you get there. When you are in Direct mode you can type, to exit the program.

Right now we need to be in Direct mode with no program in memory.

I f you type,

in Direct mode it will clear the memory so when you go into the Editor it will be blank. In direct mode enter:

Among other things, you should see a directory called MagPi , if you did everything above. Enter:

This will put us in the same directory, or folder, where we saved the sprites earlier. When we create our program we want it to be in the same folder as the sprites.

Press F2 to go to the Editor and enter the following program:

Press F3 to run the program. The first time, it will ask you for a file name. Enter MagPi and press <Enter>. The FUZE BASIC Editor automatically adds the file extension . fuze to file names. When you press <Enter> the program will run but nothing of any interest will happen as we haven¡¯t done anything of interest yet! I f you have entered anything incorrectly you may get an error in which case F2 will take you back to the Editor. If all is well, the screen will just go blank as the program is in an infinite loop (CYCLE / REPEAT).

Press the <Esc> key and then F2 to return to the Editor. Note, you can get help at any time in the Editor by pressing F1.

This is the basic structure of our program. It is important as we progress to try and build some good habits. When naming variables a popular method is called Camel Case. ThisIsCamelCase. The reason we use it is because we are not allowed to use spaces in variable names. Camel Case (notice the humps) makes things readable at a glance.

As you write larger programs another variable issue will raise its head. Short, non-related variable names WILL cause you grief later. A 200+ line program will be very difficult to understand if you have used variable names like pbx instead of PlayerBulletX and just X instead of PlayerX.

Long names take more time when editing, but they will save hours later when debugging. Also consider at some point your code might be scrutinised by someone else. You do want to make your program legible!

Time to play a game

We are going to store our variables in a PROCedure called Setup, along with our sprites and sound files. This keeps our program organised. The CYCLE and REPEAT commands define our main program loop. This is where all the action will happen.

Now we need to load the sprites so we can start having some fun. Open the Editor by pressing F2, if you¡¯re not already in it.

Edit the MagPi code so it becomes:

It should look something like this in the Editor.

When you run the program you might be surprised to see a bright pink (magenta) box surrounding our space ship. Don¡¯t worry, there¡¯s nothing wrong... we just need to set this colour to be transparent. FUZE BASIC will not draw any colour that is specified as the transparent colour.

We need this because a sprite graphic is simply a box and everything in the box is drawn. So if we have a white background in our sprite it will display a white box, which is no good on our black space background. We can stop this by specifying a single colour to be transparent so it is not drawn.

Add the setSpriteTrans command directly below the loadSprite command, as shown below, and then press F3 to run the program again:

That¡¯s much better!

Program explanation

Now that we have something more substantial, let¡¯s take a proper look at what is going on. We'll explain each section of the code line by line.

Anything displayed after the // one the same line is ignored. This allows us to add comments to make the program easy to understand.

Tells the program to jump to the procedure called Setup, run whatever is there and return when it comes to the ENDPROC command.

These three lines define our main program loop. Whatever is between the CYCLE / REPEAT loop will be repeated indefinitely.

END signifies the end of the program. When the program executes the command it will return to Direct mode. In our program this can only happen when <Esc> is pressed.

This starts the definition of the ScreenUpdate procedure. It will update everything on the screen

The plotSprite command draws a sprite (Ship) at screen coordinates X (ShipX) and Y (ShipY) using version 0. Having different versions of a sprite enables animation.

When we draw graphics to the screen they are actually drawn to a background screen. The UPDATE command copies the background screen to the main screen. This keeps everything running smoothly and simplifies game programming.

Return back to where the procedure was called.

The Setup procedure is deliberately placed at the end of the program. It is a good habit to keep all the main setup commands in one place so it is easy to find them. Also this will usually end up being quite a big routine so you don¡¯t want it getting in the way at the beginning.

This initialises high-resolution graphics mode.

Sets the screen update system to manual.

ShipX and ShipY are used to store the X and Y coordinates of the player¡¯s ship. ShipY takes a system constant called gHeight, which is the pixel height of the screen, and divides it by 2 to determine the vertical middle of the screen.

This creates a sprite ID called Ship with room for just one version of the graphic. The version count starts from 0. Later we will increase the number of versions so we can animate the sprite.

The loadSprite command assigns the named graphic image to a sprite ID (Ship) and stores it as version 0.

This specifies the transparent colour of the sprite ID (Ship) to bright pink using red (255), green (0) and blue (255) values between 0 and 255.

Return back to where the procedure was called.

Add controls and movement

We are now making progress but unfortunately we do not have space for much more this month. Let¡¯s add one more piece to our game to make it feel like we are really getting somewhere.

We are going to add a new procedure called CheckControls which will check for the Up, Down, Left and Right arrow keys being pressed and correspondingly change the position of the rocket.

First we add the call to the CheckControls procedure to our main program loop:

Now add the definition of the CheckControls procedure to your program. It does not matter where you place this procedure but we will place it before the definition of the ScreenUpdate procedure:

Your new code should look something like this in the Editor.

Run the program by pressing F3. I ¡¯m going to be very disappointed if you have not worked out what will happen when you press the cursor keys.

Coming up...

Next time we will learn more BASIC commands plus add a few enemies and some fire power to our game.

COMPETITION TEASER

In our October issue, the folks at FUZE are planning to run a FUZE BASIC programming competition, with an incredible ¡ê500 of prizes!

First prize is the amazing FUZE T2-R kit, worth ¡ê230. Not only does this have everything you need to maximise your enjoyment of the Raspberry Pi, it also includes an OWI programmable robotic arm kit!

Second prize is the superb FUZE T2-A kit, worth ¡ê1 80. Again, this contains everything you need including a Raspberry Pi Model B, solderless breadboard, various electronic components, SD card with FUZE BASIC, printed Programmer's Reference Guide and much more!

Third prize is the excellent FUZE T2-C kit for your Raspberry Pi. Worth ¡ê80, this kit contains the FUZE case, keyboard, integrated USB hub, FUZE I /O board and power supply.

Details of the prizes can be found at http://www.fuze.co.uk/products.

Over the coming months you will learn everything that you need, but if you want to give yourself a head start then download the FUZE BASIC Programmer's Reference Guide from http://www.fuze.co.uk/resources-2/.