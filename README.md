led_wall
========

Led Wall

contents of bash_profile:
========

    sleep 2
    
    while :
    do
    	echo "starting capture"
    	/home/wall/led_wall/capture
    	sleep 1
    done

mingetty setup /etc/init/tty1.conf
====

    # tty1 - getty
    #
    # This service maintains a getty on tty1 from the point the system is
    # started until it is shut down again.
    
    start on stopped rc RUNLEVEL=[2345] and (
                not-container or
                container CONTAINER=lxc or
                container CONTAINER=lxc-libvirt)
    
    stop on runlevel [!2345]
    
    respawn
    #exec /sbin/getty -8 38400 tty1
    exec /sbin/mingetty --autologin wall tty1
