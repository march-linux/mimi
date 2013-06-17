#What is this?
mimi is an improved verision of xdg-open.
The original xdg-open works horribly without DE environment.

#usage
1. you can define a list of 'how-to-open' in '~/.config/mimi/mime.conf' (read below for format)
2. or you are lazy, mimi will search a best-fit app using .desktop file. Best fit is defined as 
	the first option sorted by mime order and then , if they have the same mime order, reverse sorted by generality
	
	For example, the best-fit app says it can open 'text/html' in the very beginning of its mime definition.
	if two or more apps have the same priority, then we choose the app that can open the most number of file types.
	
#search order
for example, I want to define how to open 'text/html'. mime will search in order like this

1. 'txt' in your config
2. <protocol> in your config (i.e. http, ftp, magnet) ...etc.
3. 'text/html' in your config
4. 'text/' in your config
5. 'text/html' in .desktop
6. 'text/' in .desktop
7. if mimi still cannot find anything, it will open dmenu and bug you.

note:

1. sometimes, mimi is smart enough to figure out protocol based on mime-type when it searches for .desktop.
2. sometimes, if an app requires a terminal to run (ncurses programs), mimi is able to find one terminal app in .desktop.

#customize
this is my own stuff

    text/: xterm -e vim
    application/pdf: zathura
    video/: vlc
    image/: feh
    audio/: vlc
    application/x-tar: xterm -e 2a
    application/x-gzip: xterm -e 2a
    application/x-bzip2: xterm -e 2a
    application/x-rar: xterm -e 2a
    application/x-xz: xterm -e 2a
    application/zip: xterm -e 2a
    inode/directory: xterm -e ranger

it can be simplified by using:
    
    rar: xterm -e 2a

but if you have time, using mime-type is more precise
