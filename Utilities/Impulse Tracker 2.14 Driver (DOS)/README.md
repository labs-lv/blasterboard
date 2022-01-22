**Blasterboard sound card driver for Impulse Tracker v2.14**
------------------------------------------------------------

1) Place ITBB.DRV file into your Impulse Tracker folder containing IT.EXE file.
2) Use /s command line switch to force Impulse Tracker to use the driver:

	IT.EXE /sITBB.DRV /m50000

/m switch sets the playback rate. Up to 62500Hz is supported, which is the default if the /m switch is omitted. 
Current playback rate can be checked by pressing Shift+F5 inside the Impulse Tracker.