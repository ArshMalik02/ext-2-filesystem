
# ext2 file system

This project is based on developing a 1 MiB ext2 file system with 2 directories, 1 regular file, and 1 symbolic link.

## Building

After editing the code in the file `ext2-create.c`, you can build the code using the `make` command. After successful build, an executable `ext2-create` will be created in the current working directory.

## Running

After building the source code and obtaining the executable `ext2-create` in the current working directory, we can run the executable to create the filesystem image using the following command:
```
./ext2-create
```
Now, we have the filesystem image created in our working directory, named `cs111-base.img`. 

Next, we go ahead and mount the filesystem image we created onto our filesystem. The steps to mount the filesystem image are as follows:

1. Create a new directory to use for mounting. For example, `mnt`

    ```
    mkdir mnt
    ```
2. Mount the filesystem image `cs111-base.img`. loop let's you use a file.

    ```
    sudo mount -o loop cs111-base.img mnt
    ```

Now, we have successfully mounted our filesystem in `mnt` directory. We can explore the new directory by running `cd mnt` followed by `ls-ain`.

An example of the mounted filesystem can be seen below:
```
total 7
      2 drwxr-xr-x 3    0    0 1024 Jun  2 18:01 .
1203741 drwxr-xr-x 4 1000 1000 4096 Jun  2 18:01 ..
     13 lrw-r--r-- 1 1000 1000   11 Jun  2 18:01 hello -> hello-world
     12 -rw-r--r-- 1 1000 1000   12 Jun  2 18:01 hello-world
     11 drwxr-xr-x 2    0    0 1024 Jun  2 18:01 lost+found
``` 

## Cleaning up

To unmount the filesystem,

1. Run the following shell command while in the parent directory of `mnt`.

    ```
    sudo umount mnt
    ```

2. Delete the directory used to mount the filesystem.

    ```
    rmdir mnt
    ```

To clean up the binary files, run `make clean`
