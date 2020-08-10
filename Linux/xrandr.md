# xrandr

xrandr can be used to set the size, orientation or reflection of the outputs for a screen.

### Check current output screens settings

```sh
xrandr

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
DVI-D-1 disconnected primary (normal left inverted right x axis y axis)
HDMI-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 527mm x 296mm
   1920x1080     60.00*+  59.96    50.00    59.94    59.93
   1680x1050     59.95    59.88
   1400x1050     59.98
   1600x900      59.95    60.00    59.82
   1280x1024     60.02
   1440x900      59.90
   1400x900      59.96    59.88
   1280x960      60.00
   1440x810      59.97
   1368x768      59.88    59.85
   1280x800      59.99    59.97    59.81    59.91
   1280x720      60.00    59.99    59.86    60.00    50.00    59.94    59.74
   1024x768      60.04    70.07    60.00
   960x720       60.00
   928x696       60.05
   896x672       60.01
   1024x576      59.95    59.96    59.90    59.82
   960x600       59.93    60.00
   960x540       59.96    59.99    59.63    59.82
   800x600       70.00    65.00    60.00    60.32    56.25
   840x525       60.01    59.88
   864x486       59.92    59.57
   720x576       50.00
   700x525       59.98
   800x450       59.95    59.82
   720x480       60.00    59.94
   640x512       60.02
   700x450       59.96    59.88
   640x480       60.00    60.00    59.94
   720x405       59.51    58.99
   720x400       70.08
   684x384       59.88    59.85
   640x400       59.88    59.98
   640x360       59.86    59.83    59.84    59.32
   512x384       70.07    60.00
   512x288       60.00    59.92
   480x270       59.63    59.82
   400x300       60.32    56.34
   432x243       59.92    59.57
   320x240       60.05
   360x202       59.51    59.13
   320x180       59.84    59.32
DP-1 disconnected (normal left inverted right x axis y axis)
```

### Change settings for specific screen

```sh
xrandr --output HDMI-1 --mode 1920x1080 --rate 60

xrandr --output HDMI-1 --auto
```
