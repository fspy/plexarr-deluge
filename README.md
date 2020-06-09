# Deluge Media Server

### This project leverages multiple Docker images to achieve the following

- Download torrent files with [Deluge](https://deluge-torrent.org/)
  - [linuxserver/deluge](https://hub.docker.com/r/linuxserver/deluge/)
- Manage TV Shows with [Sonarr](https://sonarr.tv/)
  - [hotio/sonarr:phantom](https://hub.docker.com/r/hotio/sonarr/)
- Manage Movies with [Radarr](https://radarr.video/)
  - [hotio/radarr:aphrodite](https://hub.docker.com/r/hotio/radarr/)
- Manage and synchronize Subtitles with [Bazarr](https://www.bazarr.media/)
  - [hotio/bazarr:unstable-ffsync](https://hub.docker.com/r/hotio/bazarr/)
- Share media online with [PLEX Media Server](https://www.plex.tv/)
  - [hotio/plex:autoscan](https://hub.docker.com/r/hotio/plex/)

### Required environment variables (or `.env` file)

| Variable         | Description                                  | Example              |
| :--------------- | :------------------------------------------- | :------------------- |
| `CONFIG_PATH`    | Full path to configuration folder            | `/home/fspy/.config` |
| `DATA_PATH`      | Full path to data volume                     | `/mnt/data`          |
| `TIME_ZONE`      | Timezone used by containers                  | `Etc/UTC`            |
| `DELUGE_PORT`    | Port used by Deluge for incoming connections | `53135`              |
|                  | Also needs to be configured in Deluge        |                      |
| `DELUGEWEB_PORT` | Host port used by Deluge's Web UI            | `8112`               |
| `SONARR_PORT`    | Host port used by Sonarr's Web UI            | `8989`               |
| `RADARR_PORT`    | Host port used by Radarr's Web UI            | `7878`               |
| `BAZARR_PORT`    | Host port used by Bazarr's Web UI            | `6767`               |

The following are only required once:

| Variable        | Description                                           | Example             |
| :-------------- | :---------------------------------------------------- | :------------------ |
| `PLEX_LOGIN`    | Used by Autoscan to generate tokens                   | `email@example.com` |
| `PLEX_PASSWORD` | Used by Autoscan to generate tokens                   | `hunter2`           |
| `PLEX_CLAIM`    | Get it at https://plex.tv/claim/ to claim your server | `claim-foobar`      |

### Directory structure for `DATA_PATH`

```
data
├─ media
│  ├─ Movies
│  ├─ Music
│  └─ TV
└─ torrents
   ├─ movies
   ├─ music
   └─ tv
```

Done with help from [r/usenet](https://old.reddit.com/r/usenet/)'s wiki guide: [The Best Docker Setup](https://old.reddit.com/r/usenet/wiki/docker).
