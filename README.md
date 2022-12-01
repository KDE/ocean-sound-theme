# Blue Ocean Sound Theme

Blue Ocean Sound Theme for Plasma

## If anyone wants to make more sounds or modify the existing ones, here's some important observations:

- I'd love to hear an improved version 2 made by someone in the community, so if you want to do that, follow the instructions below. :D

- Use the Flatpak version of LMMS to get all plugins working.

- Most instruments are based on LMMS's presets, but they're (mostly) heavily modified. Getting familiar with ZynAddSubFX is a good starting point.

- This sound theme is meant to sound soft, so if you want to make more sounds based on this, I suggest increasing the attack, release, and adding reverb (but not too much, unless we're talking about the login sound). This will help you keep the whole theme consistent.

- You may notice some tracks are disabled. The reason for that is that at some point I made the sound with the disabled instrument but then changed my mind. I kept them as backup. There's also an unused instrument for the "trash" sound. That instrument didn't fit very well with the rest of the theme, but I chose to leave it there just in case.

- As of the date I'm writing this, ZynAddSubFX does not seem to allow per-note stereo mixing. Use automation tracks to control the Pan value instead.

- You may notice there's always a detuned version of each sound. I did this to make the instruments sound fuller. The "Ultra Detune" in the login sound is a stylistic choice meant to make the sound feel more nostalgic, like a song playing from an old vinyl disc or tape. Have you ever noticed they change in pitch as they age? :P

- Pay attention to phase cancellation. You can see when it happens by doing the following after exporting all the sounds into one file (I'm using Audacity 3.1.3):

1. Normalize the track to something consistent like -12dB. Effects >> Normalize - Select "Remove DC offset" and "Normalize peak amplitude to". This is not the level you'll want for the final sounds, but you need a baseline loudness level to be able to compare the volume.
2. Make two copies of the main track so you can compare both (Select, copy, click outside and paste)
3. Split the stereo channels in one of the tracks (leave the other as a backup). Click on the track name over the Silence and Solo buttons and click on "Split stereo tracks"
4. Select one of the audio channels and use the "Invert" effect. Effects > Invert
5. Combine both channels again into one stereo track. Click on the same place as step 3 and select "Make stereo track"
6. Mix the tracks down to mono (both the inverted and the backup). Go to Tracks >> Mix >> Mix Stereo Down to Mono
7. Solo your inverted track, play it. Then do the same with the original. Check which version has the highest volume. Pay attention to the dB meter. The version suffering with phase cancellation will have a lower volume, and the spectrometer will also show that difference. You'll also notice some instruments sound muffled or completely disappear in the problematic version.

There's also the "Invert" effect in LMMS but I noticed I get more phase cancellation problems with it enabled. The current sounds are okay without inverting one of the channels. If you make changes to this project, make sure it's still okay.

- At least with LMMS 1.2.2, there's a popping sound at the start of every sound when you export them. To work around that, I added some empty space before each sound, that way the popping gets reduced, but it doesn't go away in every case. For some reason, if I re-export a few times the pop goes away. There also have been situations where the pop was only noticed after normalizing the sounds in post, so I had to re-export the sounds and it went away. Keep that in mind and always remember to include the empty space while exporting to avoid the popping sound! You can remove the silence in post.

- In post, all sounds got normalized in Audacity using the ReplayGain plugin set at -3dB (with the exception of the sound for changing volume. That one had to be normalized to –6dB to avoid clipping). I downloaded the plugin here: https://forum.audacityteam.org/download/file.php?id=26216. In LMMS I export the sounds at 96000hz 32-bit .wav and then I convert them in Audacity to 48000hz 16bit later. You can find instructions about how you can install a Nyquist plugin here: https://manual.audacityteam.org/man/installing_effect_generator_and_analyzer_plug_ins_on_linux.html#nyquist_install

- I also manually edited the ending of a few sounds to make them shorter and remove any unwanted artifacts.


## Automate cutting and removing silence from sound using this Audacity macro

Below is the macro I used to automate part of the editing process. It sets the project to the right sample rate, cuts the beginning of each sound (leaving a little bit of silence at the beginning) and then removes silence at the end. To use it, just paste it in a .txt file, save, and import it into the macros window in Audacity. Then, import all tracks and run the macro. Note that I hard-coded the amount of tracks it will select, so, if you make more, change the number in TrackCount="20" to the number of tracks you imported into Audacity.

SetProject:Rate="48000"
Select:End="2" Mode="Set" RelativeTo="ProjectStart" Start="0" Track="0" TrackCount="20"
Delete:
SelectAll:
TruncateSilence:Action="Truncate Detected Silence" Compress="50" Independent="0" Minimum="1" Threshold="-70" Truncate="0"

## License

This work is licensed under a Creative Commons Attribution-ShareAlike 4.0 International License. Made by Guilherme Marçal Silva <guimarcalsilva@gmail.com>
