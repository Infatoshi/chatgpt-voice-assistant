# chatgpt-voice-assistant

make sure you are on python 3.6 or above
to check, run the following command in your terminal `python --version`

install the following dependencies:
`pip install openai python-dotenv speechrecognition pyttsx3 numpy pyaudio`


the input and output of the script are based off your default audio devices. (check/change this in your settings if on windows)
Check/Change default audio devices on raspberry pi:
run `sudo raspi-config`
use the arrow keys to navigate through options. go to the -> system -> audio -> select your prefered audio output (if you aren't sure use audio output 0)

For audio input:
To make your Raspberry Pi listen to your microphone as input, you can follow these steps:

First, connect your mic device to your Raspberry Pi and make sure that it is recognized by the system. You can do this by running 
the following command in the terminal:
`lsusb`
This command will list all the USB devices connected to your Raspberry Pi. Look for your mic in the list.
Next, you need to install the necessary packages to work with audio. You can do this by running the following command in the terminal.
`sudo apt-get install alsa-utils`
This command will install the ALSA (Advanced Linux Sound Architecture) utilities, which are used to configure audio on Linux systems.
Once the packages are installed, you can check if your microphone is recognized by the system by running the following command:
`arecord -l`
Remember the number for your prefered audio device. (starts with "card") 
This command will list all the audio devices connected to your Raspberry Pi. Look for your webcam microphone in the list.
If your microphone is recognized by the system, you can set it as the default audio input device by editing the ALSA configuration 
file. To do this, run the following command:
`sudo nano /usr/share/alsa/alsa.conf`
This command will open the ALSA configuration file in the Nano text editor.
In the configuration file, look for the following lines:
`; defaults.ctl.card 0`
`; defaults.pcm.card 0`
Uncomment these lines by removing the semicolon at the beginning of each line, and change the value from 0 to the number of your 
webcam microphone. For example, if your webcam microphone is listed as "card 1" in the output of the arecord -l command, you should change the lines to:
`defaults.ctl.card 1`
`defaults.pcm.card 1`
Save the changes to the configuration file by pressing Ctrl+O, then exit the text editor by pressing Ctrl+X.
Finally, you can test your microphone by running the following command:
`arecord -f cd -D hw:1 | aplay`
This command will record audio from your mic and play it back through the default audio output device. If you hear 
the sound, it means that your microphone is working correctly.

At some point in the process you may encounter a libespeak error on the raspberry pi. Running the following command on the terminal should fix it `sudo apt-get install libespeak1`.

Great Job! Try running the script by navigating to the project folder via `cd folder_name` then running `python main.py`


I respond the fastest to discord so shoot me a dm through that if you have any questions or errors, I plan on upgrading this project over time. ( Infatoshi Nakamoto#3233 )
Follow me on Twitter - X: https://twitter.com/elliotarledge
