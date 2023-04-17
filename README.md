# Blue Ocean Sound Theme

Blue Ocean Sound Theme for Plasma

## Intended usage

Each sound is intended to be used in a specific situation:

- **Login**: Play this sound after the computer boots up and the Plasma session starts.

- **Log_out**: Play when exiting the Plasma session.

- **Log_out_short**: Alternative log out sound. May also be used by applications (e.g. Instant messaging apps).

- **Volume_change**: Feedback sound when changing volume.

- **Update_notification-special**: Play when something special happens (e.g. New update available).

- **Trash**: Play after permanently deleting the contents of the trash folder.

- **SMS_notification**: Play for incoming SMS messages.

- **Question-warning_dialog**: Play when asking the user a question or when the program needs the user attention (e.g. Dialog: Do you want to save? / This action will close 20 tabs).

- **Power_plug**: Play when plugging in the charger on the laptop or phone.

- **Power_unplug**: Play when unplugging the charger.

- **Plug_device**: Play when a new device is inserted (e.g. New external drive, mouse, or bluetooth dongle).

- **Unplug_device**: Play when disconnecting a device.

- **Generic_plug**: Alternative sound used when plugging something. May also be used when enabling devices that are already connected (e.g. touchpad).

- **Generic_unplug**: Alternative sound used when unplugging something. May also be used when disabling devices that are already connected.

- **Low_battery**: Play when the battery reaches a low level (e.g. 15%).

- **Critical_battery**: Play when the battery charge reaches a very low level and the computer is about to turn off (e.g. 5%).

- **Information_dialog**: Play when giving the user some information (e.g. Dialog: You hid the title bar. Press ALT+F3 to enable it again).

- **Generic_beep**: Use when you need the computer to beep for some reason (e.g. When Audible bell is enabled in the accessibility settings).

- **Error**: Play when an error occurs (e.g. Could not save file).

- **Error_serious**: Play when an unrecoverable error happens (e.g. The program has crashed).

If you need a sound which is not provided by this pack, try to use Oxygen sounds as a fallback (e.g. minimize window sounds).

## If anyone wants to make more sounds or modify the existing ones, here's some important observations:

- I'd love to hear an improved version 2 made by someone in the community, so if you want to do that, follow the instructions below. :D

- Use the Flatpak version of LMMS to get all plugins working.

- Most instruments are based on LMMS's presets, but they're (mostly) heavily modified. Getting familiar with ZynAddSubFX is a good starting point.

- This sound theme is meant to sound soft, so if you want to make more sounds based on this, I suggest increasing the attack, release, and adding reverb (but not too much, unless we're talking about the login sound). This will help you keep the whole theme consistent.

- This sound theme is NOT meant to be modern or minimalistic. Plasma itself is not minimalistic, so it wouldn't make sense to make a minimalistic sound theme. My inspirations were KDE 3 and Windows Vista sounds.

- You may notice some tracks are disabled. The reason for that is that at some point I made the sound with the disabled instrument but then changed my mind. I kept them as backup. There's also an unused instrument for the "trash" sound. That instrument didn't fit very well with the rest of the theme, but I chose to leave it there just in case.

- As of the date I'm writing this, ZynAddSubFX does not seem to allow per-note stereo mixing. Use automation tracks to control the Pan value instead.

- You may notice there's always a detuned version of each sound. I did this to make the instruments sound fuller. The "Ultra Detune" in the login sound is a stylistic choice meant to make the sound feel more nostalgic, like a song playing from an old vinyl disc. Have you ever noticed the pitch changes as the disc wobbles and the speed slows down? :P

- Pay attention to phase cancellation and always test the sounds in a mono speaker. The current sounds are totally fine in that regard. If you make changes to this project, make sure it's still okay. If you make new sounds and you wanna make sure there's no phasing problems, you can do the following test after exporting all the sounds into one file (I'm using Audacity 3.1.3):

1. Normalize the track to something consistent like -12dB. Effects >> Normalize - Select "Remove DC offset" and "Normalize peak amplitude to". This is not the level you'll want for the final sounds, but you need a baseline loudness level to be able to compare the volume.
2. Make two copies of the main track so you can compare both (Select, copy, click outside and paste)
3. Split the stereo channels in one of the tracks (leave the other as a backup). Click on the track name over the "Silence" and "Solo" buttons and click on "Split stereo track" (**DO NOT** select "Split Stereo to Mono", that will make two identical tracks and when you combine them again you WILL get phase cancelation and lose the stereo panning, always use "Split stereo track")
4. Select one of the audio channels and use the "Invert" effect. Effects > Invert
5. Combine both channels again into one stereo track by clicking on the same place as step 3 and selecting "Make stereo track"
6. Mix the tracks down to mono (both the inverted and the backup). Go to Tracks >> Mix >> Mix Stereo Down to Mono
7. Solo your inverted track, play it. Then do the same with the original. Check which version has the highest volume. Pay attention to the dB meter. The version suffering with phase cancellation will have a lower volume, and the spectrometer will also show that difference. You'll also notice some instruments sound muffled or completely disappear in the problematic version.

There's also the "Invert" effect in LMMS but I noticed I get more phase cancellation problems with it enabled. 

- The LMMS export process seems to be non-deterministic, which means that every time you export a sound it can create a slightly different waveform. I noticed sometimes one side of the stereo track is slightly more silent, or sometimes I get a popping noise. At least with LMMS 1.2.2, there's a popping sound at the start of every sound when you export them. To work around that, I added some empty space before each sound, that way the popping gets reduced, but it doesn't go away in every case. If I re-export a few times the pop can go away. There also have been situations where the popping was only noticed after normalizing the sounds in post, so I had to re-export the sounds again (!!!). Keep that in mind and always remember to include the empty space while exporting to avoid the popping sound! You can remove the silence in post. Also remember to check the levels of each channel and, if the volume is too different between them, you can re-export or use the Loudness Normalization plugin in Audacity to normalize each channel independently.

- In post, all sounds got normalized in Audacity using the ReplayGain plugin set at -3dB. I downloaded the plugin here: https://forum.audacityteam.org/download/file.php?id=26216. In LMMS I export the sounds at 96000hz 32-bit .wav and then I convert them in Audacity to 48000hz 16bit later. You can find instructions about how you can install a Nyquist plugin here: https://manual.audacityteam.org/man/installing_effect_generator_and_analyzer_plug_ins_on_linux.html#nyquist_install

- I also manually edited the ending of a few sounds to make them shorter and remove any unwanted artifacts, like noise.

## Automate cutting and removing silence from sound using this Audacity macro

Below is the macro I used to automate part of the editing process. It sets the project to the right sample rate, cuts the beginning of each sound (leaving a little bit of silence at the beginning) and then removes silence at the end. To use it, just paste it in a .txt file, save, and import it into the macros window in Audacity. Then, import all tracks and run the macro. Note that I hard-coded the amount of tracks it will select, so, if it causes any trouble, change the number in TrackCount="20" to the number of tracks you imported into Audacity.

SetProject:Rate="48000"
Select:End="2" Mode="Set" RelativeTo="ProjectStart" Start="0" Track="0" TrackCount="20"
Delete:
SelectAll:
TruncateSilence:Action="Truncate Detected Silence" Compress="50" Independent="0" Minimum="1" Threshold="-70" Truncate="0"

## License

This work is licensed under a Creative Commons Attribution-ShareAlike 4.0 International License. Made by Guilherme Marçal Silva <guimarcalsilva@gmail.com>