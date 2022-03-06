# LXC-Template-Downloader
CLI to Download LXC Templates from https://uk.lxd.images.canonical.com

This command line interface will help you to find and download LXC Templates.
It provides a search method and will give you hints to find the correct image.

## Installation
### Requirements
Install requirements [yq](https://github.com/mikefarah/yq) and curl

**Ubuntu**: 
```
snap install yq
sudo apt install curl
```
**macOS**:
```
brew install yq curl
```
### Downloader
Install lxc-template-downloader
```
sudo curl -s -o /usr/bin/lxc-template-downloader https://raw.githubusercontent.com/n-stone/LXC-Template-Downloader/main/lxc-template-downloader
sudo chmod +x /usr/bin/lxc-template-downloader
```

## Example
You can download for images:

![get images](examples/get.svg)

This function will also give you hints:

![get images display hints](examples/get-hints.svg)

Or you can search for keywords:

![search for images](examples/search.svg)

Beware, therefore a the whole file tree musst be crawled, this will take some time:

![search for images first run](examples/search-first-run.svg)
