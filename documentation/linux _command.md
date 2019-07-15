## Serial port

	```
	ls -l /dev |grep ttyUSB
	sudo chmod 777 /dev/ttyUSB0
	```

## System

	```
	free -m
	df -h
	ps -ef |grep [thread-name]
	kill -s 9 [PID]
	```

## Directory Management

### Check directory

	```
	cd ..
	cd [directory]
	ls
	```

### Make file

	```
	mkdir [directory]
	```

### Remove file

	```
	rm -f [file]
	rm -dir -f [directory]
	```

## Software Management

	```
	sudo apt-get install [software]-*
	sudo apt-get remove [software]-*
	```
