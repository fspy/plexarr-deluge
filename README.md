# Deluge Media Server

This project leverages multiple Docker images to download, organize, manage and share media (TV shows, movies, etc).

Files are downloaded via torrent, categorized with [Deluge](https://deluge-torrent.org/), managed accordingly with [Sonarr](https://sonarr.tv/) and [Radarr](https://radarr.video/). If needed, subtitles will be obtained from various sources through [Bazarr](https://www.bazarr.media/). Organized media is shared through [PLEX Media Server](https://www.plex.tv/).

**Docker images used**
  - [linuxserver/deluge](https://hub.docker.com/r/linuxserver/deluge/)
  - [hotio/sonarr:release](https://hotio.dev/containers/sonarr/)
  - [hotio/radarr:release](https://hotio.dev/containers/radarr/)
  - [hotio/bazarr:release](https://hotio.dev/containers/bazarr/)
  - [hotio/plex:release](https://hotio.dev/containers/plex/)

### Environment Variables (or `.env` file)

| Variable           | Default              |
| :----------------- | :------------------- |
| **CONFIG_PATH**    | `/home/fspy/.config` |
| **DATA_PATH**      | `/mnt/data`          |
| **TIME_ZONE**      | `Etc/UTC`            |
| **DELUGE_PORT**    | `53135`              |
| **DELUGEWEB_PORT** | `8112`               |
| **SONARR_PORT**    | `8989`               |
| **RADARR_PORT**    | `7878`               |
| **BAZARR_PORT**    | `6767`               |

The following are only required once:

| Variable        | Example        | Description                                           |
| :-------------- | :------------- | :---------------------------------------------------- |
| **PLEX_CLAIM**  | `claim-foobar` | Get it at https://plex.tv/claim/ to claim your server |

### Directory structure for `DATA_PATH`

```
data
├─ media
│  ├─ Movies
│  ├─ Music
│  └─ TV
└─ torrents
   ├─ .uncategorized
   ├─ movies
   ├─ music
   └─ tv
```


### Deluge configuration

- **Downloads**

  Set *Download to*: `/downloads/.uncategorized`

- **Network**

  Set *Incoming Port*: `DELUGE_PORT`

- **Plugins**

  Enable `Label`

- **Create category labels**
  - Move completed to: `/downloads/<category>`

---

Done with help from [r/usenet](https://old.reddit.com/r/usenet/)'s wiki guide: [The Best Docker Setup](https://old.reddit.com/r/usenet/wiki/docker).
