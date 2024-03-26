# QtStart
Automatic QtStarter from Bash


#! /bin/bash

#### to make this automatic start

# after add the file to /usr/loca/bin/  => the user directory and bin files
#sudo cp ~/QtStart /usr/loca/bin/
# mv QtStart.sh QtStart

# THIS IS A SCRIPT THAT IS CALLED TO START THE QT PROGRAM AUTMATICALLY FROM THE SHELL

echo "$0 : STARTING QT CREATOR"

echo "Desired path => ~/Qt/Tools/QtCreator/bin/QtCreator.sh"
#//adjust this path accordingly
# go to the desired directory  that is ~(home/<user> //no need to just a step


QT_CREATOR=~/Qt/Tools/QtCreator/bin/qtcreator.sh

if [ -f "$QT_CREATOR" ]; then
    echo "QT Directory Found"
else
    echo "Error: QT Creator not found Check installation and/or Path"
    exit -1 #exit with failure code
fi

cd ~

if [ "$(pwd)" = "$HOME" ]; then
		echo "We are in the User home folder"
 		echo "Starting QT Creator Now"
                #just call the path above => QT_CREATOR
                $QT_CREATOR
 		#check if the QT Creator started successfully

			#nested if statements
		if [ $? -eq 0 ]; then
    			echo "Qt Creator started successfully"
    			exit 0  # Exit with success code
		else
    			echo "Error: Failed to start Qt Creator"
    			exit -1  # Exit with failure code
fi
else 
                echo "CD into Home folder $(cd ~/qt_app)"
    	        cd ~ 
#this else statement can be optimized out.

fi
## USE TMUX SO THAT YOU CAN HAVE DIFFERENT SESSIONS RUNNING COCURRENTLY WITH BASH. CLOSING BASH  
## OR ^c => CLOSES THE APP AS WELL

