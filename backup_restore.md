### backup
```shell
sudo tar -cvpzf backup.tar.gz --exclude=/home/server/backup.tar.gz --one-file-system / 
	-c	create new tar file
	-v	verbos
	-p	perserve the permission
	-z	gzip compresion is smaller
	-f	file name and location
```

### restore
```shell
sudo tar -xvpzf /home/server/backup.tar.gz -C / --numeric-owner 
	-x extract 
```
