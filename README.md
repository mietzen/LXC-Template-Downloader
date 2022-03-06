# LXC-Template-Downloader
CLI to Download LXC Templates from https://uk.lxd.images.canonical.com

This command line interface will help you to find and download LXC Templates.
It provides a search method and will give you hints to find the correct image.

You can download for images:

[![asciicast](https://asciinema.org/a/aLoIUHElAC3uAmxfEvOLeepkB.svg)](https://asciinema.org/a/aLoIUHElAC3uAmxfEvOLeepkB)

This function will also give you hints:

[![asciicast](https://asciinema.org/a/4r4t6Bt6hkejKQvxMdJ73Auob.svg)](https://asciinema.org/a/4r4t6Bt6hkejKQvxMdJ73Auob)

Or you can search for keywords:

[![asciicast](https://asciinema.org/a/XBU8LGApV1NyPjjuUcQtRrSe6.svg)](https://asciinema.org/a/XBU8LGApV1NyPjjuUcQtRrSe6)

Beware, therefore a the howl file tree musst be crawled, this will take some time:

[![asciicast](https://asciinema.org/a/gBbhe14oFICeKUb315TQJ4ZGz.svg)](https://asciinema.org/a/gBbhe14oFICeKUb315TQJ4ZGz)


```
Usage: lxc-template-downloader COMMAND [OPTIONS]

Overview:
  ┌──────────┬────────────────────────────────────────┬─────────────────┐
  │ Command: │  Arguments:                            │ Options:        │
  ├──────────┼────────────────────────────────────────┼─────────────────┤
  │  help    │                                        │                 │
  │  get     │  name version arch *type *timestamp    │  -d | --dir     │
  │  list    │                                        │  -d | --depth   │
  │  search  │  keyword                               │                 │
  └──────────┴────────────────────────────────────────┴─────────────────┘

Commands:
    - help:
        Display this

    - get:
        Downloads a template LXC rootfs.
        e.g.:
            lxc-template-downloader get alpine edge amd64
        
        This will Download the latest default alpine edge template for amd64
        You can also specify the type, e.g. cloud and a timestamp if you don't want the latest image.
        e.g.:
            lxc-template-downloader get alpine edge amd64 cloud 20220305_13:00
        
        Timestamps can be looked up with the command list.
        ou may set the output directory with -d or --dir.
        e.g.:
            lxc-template-downloader get alpine 3.12 arm64 -d /tmp

    - list:
        Print a yaml formated tree of all availabe images. 
        You may set the depth with -d or --depth to:
            ┌──────┬─────────┬──────┬──────┬───────────┐
            │   1  │    2    │  3   │  4   │     5     │
            ├──────┼─────────┼──────┼──────┼───────────┤
            │ Name │ Version │ Arch │ Type │ TimeStamp │
            └──────┴─────────┴──────┴──────┴───────────┘
        
        e.g.:
            lxc-template-downloader list -d 5
        
        If depth is not provided the default depth is Version (2).
        Beware: Higher query depth will take more time!

    - search:
        You can search for keywords, like the architecture.
        e.g.:
            lxc-template-downloader search arm64
        
        On first run this will create a full tree of all availabe images.
        This will take some time this this a recursive web crawl over ~2000 Images.
        On the second run the tree is cached, but musst be updated daily.
```