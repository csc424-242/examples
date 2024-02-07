#
# makefile for netbounce example
# Jan 12,2016
# Jan 26,2022
# bjr
#

CC = gcc
MACHINE = localhost
MACHINE = 34.227.66.241
PORT = 3333
IF = eth0

all:
	@echo "update MACHINE macro with server IP"
	@echo "run |make run-server| to start server"
	@echo "run |make run-client| to bounce"
	make netbounce

netbounce: netbounce-server netbounce-client

netbounce-server: netbounce-server.c 
	${CC} -o $@ $<
	
netbounce-client: netbounce-client.c 
	${CC} -o $@ $<
	
test:
	@echo In one window, make run-server
	@echo Then, in another window, make run-client
	
run-server: netbounce-server
	@echo Ready to bounce!
	./netbounce-server -lv -p ${PORT}

run-client: netbounce-client
	./netbounce-client -h ${MACHINE} -p ${PORT} -v "The amazing net bounce!"

find-pid:
	@echo problem- bind: Address already in use
	@echo use netstat to find the pid holding the port then kill -9
	netstat -tulpn | grep ${PORT}

tcpdump:
	sudo tcpdump -i ${IF} -x udp port ${PORT}

clean:
	-rm netbounce-client netbounce-server

