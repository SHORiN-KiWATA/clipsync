# Clipsync

Clipboard synchronization sctipts for Wayland Compositor ( X11 <--> Wayland )

- Dependencies

`xclip` `wl-clipboard` `clipnotify`

- Usage

    ```
    systemctl enable --user clipsync
    ```

- Features

    This project contains three scripts and one service.

    `clipsync-x2w` for X11 to Wayland synchronization.

    `clipsync-w2x` for Wayland to X11.

    `clipsync` manage these two sctips.

    `clipsync.service` which will run `clipsync` automatically.

## machanism

- X11 --> Wayland

    Ues `clipnotify` as trigger:

    ```
    xclip -o -sel clip -t <type> | wl-copy -t <type>
    ```
- Wayland --> X11

    Use `wl-paste --watch` as trigger

    ```
    wl-paste -t <type> | xclip -sel clip -t <type>
    ```
- check

    Use `md5sum` for data checking. 
