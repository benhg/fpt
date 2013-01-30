# Base Instructions

If you are setting this up in Linux and in the /FPT
directory as suggested,  then you can probably set all
of FPT up by running the two "make_...." scripts AS root :



./make_FPT

./make_FPT_symbolic_links



If there are no complaints, you are probably ready to go.

# Linux Instructions for Installing the 

Freshman's Programming Toolkit
May 2007
Principal Author : J.Ely

//////////////////////////////////////////////////////////////////
If you have Linux running on an Intel or compatible chip,
 there is a good chance that you can simply do steps 1, 3 ,and 6.
 Try those first and see if you get lucky.  If not, look at
 the details.
//////////////////////////////////////////////////////////////////




0. It is assumed you are on a Linux system with an X11 server
   and the X11 programming support files have been installed.
   This should be a simple matter of installing ALL X-related
   stuff that Linux offers you when you first install Linux.
   Some people have inadvertently chosen not to install the 
   X11 programming supprt files and will need to go back and
   incorporate them.

   As a check :

   0.1 issue the command,

       whereis  X11

       hopefully, you will see something like :

       X11: /etc/X11  /usr/lib/X11  /usr/include/X11


   0.2 issue the command,

       ls   /usr/include/X11

       it is a good sign if you see a bunch of names listed.
       it is not good if the command tells you that there is
          no such file or directory.

   0.3 issue the command,

       xdpyinfo

       this should return a lot of info but somewhere there
       should be some lines that somewhat resemble :

       number of visuals:    2
       default visual id:  0x21
       visual:
        visual id:    0x21
        class:    TrueColor
        depth:    24 planes
        available colormap entries:    256 per subfield
        red, green, blue masks:    0xff0000, 0xff00, 0xff
        significant bits in color specification:    8 bits

       what is important here is that our default visual
       is TrueColor, has a depth of 24 planes, and has
       red,green,blue masks:     0xff0000, 0xff00, 0xff

    If these three commands pan out, you should be in business.



/////////////////////////////////////////////////////////////////////
/////////////////////////////////////////////////////////////////////
Now for the details of installing the Freshman Programming Toolkit :


1. The usual expectation is that this Freshman Programming
   Toolkit is installed in

        /FPT

   To do this :
 
     become root
     cd /
     copy or otherwise download  FPT.tgz   to  /
     tar xfz FPT.tgz   (this should create a directory called FPT)
     ls                (you should now see the FPT directory)
     cd FPT            (you are now in the FPT directory)
     ls 
       Now you should see the files
          acom, bcom,
       and the directories
          Dotos, Examples. Source, and Readmes


2. If you have chosen to install FPT in some other location you will
   need to edit the two compile scripts, acom and bcom to reflect
   where you actually installed this stuff.


3. As root :
   ln    -s  /FPT/acom       /usr/local/bin/acom
   ln    -s  /FPT/bcom       /usr/local/bin/bcom
   ln    -s  /FPT/ycom       /usr/local/bin/ycom
   ln    -s  /FPT/zcom       /usr/local/bin/zcom

   this assumes you've installed this stuff in /FPT


4. You may need to recompile the   FPT/DotosC/*.o   files.
   This can easily be done by moving into the FPT/Dotos
   directory and issuing

   ./compile_dotos


   Similarly, recompile the files in FPT/DotosGPP



   You should also move into the directory, ArrayFilter,
   and issue the command,

   ./compile

   which will re-create the program, filter_arrays.exe
   which is used by the bcom and zcom compilation scripts.



5. It is very likely that others can already read and execute
   what they need  but if not, you should make sure they can
   read and execute the directories

   /FPT
   /FPT/Dotos
   /FPT/Examples
   /FPT/Source

   that they can read and execute the files

   /FPT/acom
   /FPT/bcom

   and that they can read the files

   /FPT/Readme01
   /FPT/Readme02
   /FPT/Examples/*
   /FPT/Dotos/*.o
   /FPT/Source/*.h

   You can discover the permissions by listing your files
   with the -l flag, i.e.

   As an example :

   ls -l  acom

   might show something like

   -rwxr-xr--   and other info

   Ignoring the first -,
   the next three symbols show that the owner of the file
   can rwx (read, write, and execute) the file.  The next 3
   show the permissions of the group (ignore these) and the
   last three show the permissions for others.  In this case
   r-- indicates that others can read the file but not write
   or execute it.  We don't want them to be able to write 
   (alter) it but we do want them to be able to execute it
   because it is a compile script, so we issue the command,

   chmod o+x acom

   Now the command,

   ls -l acom    

   should show 

   -rwxr-xr-x   and other info

   where the last x indicates that others can now execute
   the file.



6. As a test of the installation


   cd Examples

   acom t01a.c    [this will invoke the compile script, acom,
                   to compile the sample program, t01a.c]
   ./a.out        [run the program]


   hopefully something visual happens.

# Instructions for Installing the Freshman's Programming Toolkit on Mac OSX 10.4, 10.5 and 10.6

Original Linux instructions by J. Ely
Updated for Mac by W. Javins: Jan. 2011

//////////////////////////////////////////////////////////////////
These instructions were tested with OSX 10.4.11 Tiger, 10.5.4 
Leopard, and 10.6.6 Snow Leopard running on an intel macbook pro.
//////////////////////////////////////////////////////////////////


/////////// Installing the Developer Tools and X11 ///////////////

0. You will need a Intel Mac running OSX and the install disks 
   that came with your computer.

   0.1	Insert the OSX Install Disk

	Open the XCode Tools folder

	Open the XcodeTools.mpkg and follow the installer 
	instructions

	For simplicity's sake, you can leave the default settings
	and install all the default Software Development Kits 
	(SDKs) even though you only need a few for our purposes.

   0.2  After installation, check that you have the necessary 
	tools.  Open the Terminal application and issue the 
	commands:

	ls  /usr/bin/cc

	you should get a file, if you get a "No such file or 
	directory" error, something is wrong

	ls  /Applications/Utilities/X11.app

	you should see a folder "Contents"

   	If these commands pan out, you should be in
	business.


////////// Installing the Freshman Programming Toolkit ///////////

1. The usual expectation is that this Freshman's Programming
   Toolkit is installed in:

	/FPT

   To do this :

   1.1	Download and unzip the FPT file (You're reading this 
	document, so you're probably this far already)

   1.2	copy FPT to / 

	In Terminal, navigate to the parent directory of FTP and
	enter the command:

	cp  FPT  /

	Or in Finder, the Macintosh HD and drag the FTP  folder
	into it.

   1.3	If you have chosen to install FPT in some other 
    location you will need to edit the two compile scripts, 
    acom and bcom to reflect where you actually installed 
    this stuff.

2. Open Terminal

   2.1	Issue the commands:

	cd  /FPT

    ls

	You should see the files:
	   acom, acomGPP, bcom, and sed.control

	and you should see the directories:
       Dotos, DotosGPP, Examples, ExamplesGPP, Readmes
       and Source

   2.2	Issue the commands:

	sudo ln  -s  /FPT/acom  /usr/bin/acom
	sudo ln  -s  /FPT/bcom  /usr/bin/bcom

	You should be asked for your password.  The sudo command 
	cannot run without it.

	This assumes you've installed the FTP at /FPT.  These two
	commands create links from the system's command library to
	the actual acom and bcom commands.
	
   2.3  At this point, the FPT *should* be installed.  You are
    safe to skip to step 5.  If the test fails, then you many
    need to come back to steps 3 and 4.


3. 	You may need to recompile the   FPT/Dotos/*.o   files.
   	This can easily be done by navigating to the FPT/Dotos
   	directory and issuing the command:

   ./compile_dotos


4. It is very likely that others can already read and execute 
   what they need  but if not, you should make sure they can:

   4.1	Read and execute the directories:

	/FPT
	/FPT/Dotos
	/FPT/Examples
	/FPT/Source

   4.2	That they can read and execute the files:

	/FPT/acom
	/FPT/bcom

   4.3	And that they can read the files:

	/FPT/ReadmeMac
	/FPT/sed.control
	/FPT/Examples/*
	/FPT/OldFiles/*
	/FPT/Dotos/*.o
	/FPT/Source/*.h

   4.4  If you've never worked with file permissions before,
	see Appendix I to learn about file permissions, including
    how to view and edit them.

5. You've installed the FPT!

   5.1 	You are now in business for text based programs! (e.g. 
	the first half of CS1.)  To test this, issue the commands:

	cd  Examples

	bcom  helloworld.c	[this will invoke the compile 
				 		script, bcom, to compile the 
				 		sample program, helloworld.c]
				 		
	./a.out				[run the program]

	You should see "Hello World!" in your Terminal.

   5.2	However, for graphical programs (anything requiring 
	G_init_graphics()), there are a few more Mac related 
	things to be done.


////////////// Starting X11 and Setting up Terminal //////////////

6.	Before you can run any graphical programs you need to:

   6.1	Start the X11 application.  It is found at:

	/Applications/Utilities/X11.app

   6.2	Do one of the following:
	
	Either:
	Use xterm to execute the graphical program.  For instance 
	the command:   ./a.out   must be issued in xterm, even if 
	you did your editing and compiling elsewhere.

	Or:
	You can work from Terminal if you enter the command:

	export  DISPLAY=:0.0

	before executing a graphical program.  Note:  This command 
	does not have to be reissued as long as you keep Terminal 
	open.


7. 	Time to test that everything works!

   7.1	As a test of the installation, make sure X11 is running
   	and one of 8.2's options is in effect.  Issue the commands:

	cd  /FPT/Examples

	acom  t01a.c   [this will invoke the compile script, acom,
                   to compile the sample program, t01a.c]
                   
	./a.out        [run the program]

	Hopefully something visual happens.



///////////////// Appendix I (File Permissions) /////////////////

	You can discover the permissions of a file using the
	command: 

	ls -l

	As an example:

	ls -l  acom

	might show something like

	-rwxr-xr--    1 user  admin   986 Jan  1 00:00 acom

	The permissions are displayed in the first 10 characters 
	(-rwxr-xr-x).  Ignoring the first -, the next three symbols 
	show that the owner of the file can rwx (read, write, and 
	execute) the file.  The next 3 show the permissions of the 
	group (ignore these) and the last three show the 
	permissions for others.  In this case r-- indicates that
	others can read the file but not write or execute it.  We
	don't want them to be able to write (alter) it but we do
	want them to be able to execute it because it is a compile
	script, so we issue the command:

	chmod o+x  acom

	Now the command:

	ls -l  acom    

	should show:

	-rwxr-xr-x    1 user  admin   986 Jan  1 00:00 acom

   	where the last x indicates that others can now execute
   	the file.

   	The string o+x from the example can be adjusted to change
   	any of the rwx values for the owner(u), the group(g) or
   	others(o). For instance:

	chmod u-r  acom

	would remove read permission from the owner.

	chmod g+w  acom

	would add write permission for the group.

	For more information on file permissions type the command:

	man chmod

	(Hit q to exit a man page.  Use the up and down arrows to 
	scroll.)
	
	
# Source documentation

acom  fname.c
  invokes the C compiler and links in with all of
  the graphical and math routines, producing the
  executable, a.out

bcom fname.c
  does the same thing but first preprocesses your
  source file to allow for doubles to be used
  as subscripts in arrays






ycom  fname.c
  invokes the C++ compiler and links in with all of
  the graphical and math routines, producing the
  executable, a.out

zcom fname.c
  does the same thing (C++) but first preprocesses your
  source file to allow for doubles to be used
  as subscripts in arrays

