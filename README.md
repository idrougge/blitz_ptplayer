# blitz_ptplayer
Port of Frank Wille's Protracker player v6.3 as a Blitz Basic library

******** THIS VERSION HAS A BUG, DON'T USE IT YET****************
Please take the older version, pre-2023 for now!

Blitz Basic function/statement entry points added by idrougge
Further development by E-Penguin

VBR fix by phx

compiled with vasm 1.9d, with the following options:
vasmm68k_mot.exe -devpac -Fhunkexe -kick1hunks -nosym  ptplayer.asm -o ptplayer.obj

Built wit the following configuration flags:

MINIMAL		equ	0

ENABLE_SAWRECT	equ	0

NULL_IS_CLEARED	equ	0

Command reference:
LoadBank 0,"mod.song",2 (loads module into bank 0 in chipmem (2))
MTInstall PAL=True, NTSC=False (installs player in program)
MTInit Bank#, startpos (inserts module into player)
MTInit &module_addr, &instr_addr, startpos (inserts INCBIN module into player, set instr_addr to 0 for normal modules)
MTPlay On/Off (start/stop module playback)
MTEnd (Stop playing current module)
MTSoundFX Sound#, volume (0..64)
MTSoundFX &sample_addr.l, length.w, period.w, volume.w (0..64)
MTMasterVolume 0..64 (Master volume for all music channels)
MTMusicMask bitmask.b (Set bits 0-3 to reserve channels for music only.)
MTMusicChannels 0..4 (number of channels dedicated to music)
MTE8Trigger (Value of the last E8 command in case you want to trigger game events from a module)