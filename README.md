# LXC-Template-Downloader
CLI to Download LXC Templates from https://uk.lxd.images.canonical.com

This command line interface will help you to find and download LXC Templates.
It provides a search method and will give you hints to find the correct image.

You can download for images:

![get images](examples/get.svg)

This function will also give you hints:

![get images display hints](examples/get-hints.svg)

Or you can search for keywords:

![search for images](examples/search.svg)

Beware, therefore a the howl file tree musst be crawled, this will take some time:

![search for images first run](examples/search-first-run.svg)


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