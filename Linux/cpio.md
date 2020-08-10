
# cpio

## Basic Usage

- Take a list of file names from standard input and add them [o]nto an archive in cpio's binary format:

  ```sh
  echo "file1 file2 file3" | cpio -o > archive.cpio
  ```

- Copy all files and directories in a directory and add them [o]nto an archive, in [v]erbose mode:

  ```sh
  find path/to/directory | cpio -ov > archive.cpio
  ```

- P[i]ck all files from an archive, generating [d]irectories where needed, in [v]erbose mode:

  ```sh
  cpio -idv < archive.cpio
  ```
