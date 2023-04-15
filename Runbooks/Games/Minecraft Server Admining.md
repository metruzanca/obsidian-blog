## Download world before killing server for good

### Zip everything up

Install zip
```
sudo apt install zip unzip
```
Zip server (or just world)
```
zip server.zip server/
```
If using dynmap, exclude the tiles.

### Rsync it to local drive

[source](https://stackoverflow.com/questions/9090817/copying-files-using-rsync-from-remote-server-to-local-machine)

```
rsync -chavzP --stats user@remote.host:/path/to/copy /path/to/local/storage
```



