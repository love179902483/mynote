### random set wallpaper

```
#!/bin/bash
sleep 60
WALLPAPERS="/home/qinyu/Downloads/background"
ALIST=( `ls -w1 $WALLPAPERS` )

while true;
do
RANGE=${#ALIST[*]}
SHOW=$(( $RANDOM % $RANGE ))

feh --bg-scale $WALLPAPERS/${ALIST[$SHOW]}

sleep 600
done &
```
