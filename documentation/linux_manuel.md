# Command

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
	lspci // view hardware
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

# Problems fixing

## [`sudo apt-get update` takes too long](https://blog.csdn.net/qwqw3333333/article/details/78239448)  
do remember to backup source.list  

## [set up nvidia drivers](https://blog.csdn.net/lukaslong/article/details/81488219) 

## System program problem detected  
```
sudo vim /etc/default/apport
override `enabled = 1` to `enabled = 0`
```