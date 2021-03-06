Youtube2zim
=============

[![CodeFactor](https://www.codefactor.io/repository/github/openzim/youtube/badge)](https://www.codefactor.io/repository/github/openzim/youtube)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![PyPI version shields.io](https://img.shields.io/pypi/v/youtube2zim.svg)](https://pypi.org/project/youtube2zim/)

`youtube2zim` allows you to create a [ZIM file](https://openzim.org)
from a Youtube Channel/Username or one-or-more Playlists.

It downloads the video (`webm` or `mp4` extension – optionnaly
recompress them in lower-quality, smaller size), the thumbnails, the
subtitles and the authors' profile pictures ; then, it create a static
HTML files folder of it before creating a ZIM off of it.

Requirements
------------

* [`ffmpeg`](https://ffmpeg.org/) for video transcoding (only used with `--lower-quality`).
* [`zimwriterfs`](https://github.com/openzim/zimwriterfs) for ZIM file packaging. Use `--no-zim` to skip this step.
* `curl` and `unzip` to install Javascript dependencies. See `get_js_deps.sh` if you want to do it manually.

Installation
------------

Here comes a few different ways to install `youtube2zim`.

## Virtualenv

`youtube2zim` is a Python3 software. If you are not using the
[Docker](https://docker.com) image, you are advised to use it in a
[virtualenv](https://virtualenv.pypa.io) to avoid installing software
dependences on your system.

```bash
virtualenv -p python3 ./ # Create virtualenv
source bin/activate      # Activate the virtualenv
pip3 install youtube2zim # Install dependencies
youtube2zim --help       # Display youtube2zim help
```

At the end, call `deactivate` to quit the virtual environment.

See `requirements.txt` for the list of python dependencies.

## Docker

```bash
docker run -v my_dir:/output openzim/youtube youtube2zim --help
```

## Globally (on GNU/Linux)

```bash
sudo pip3 install -U youtube2zim
```

Usage
-----

`youtube2zim` uses Youtube API v3 to fetch data from Youtube. You thus need to provide an `API_KEY` to use the scraper.

To get an API:

1. Connect to [Google Developers Console](https://console.developers.google.com/apis)
2. Create a new _Project_ then Select it.
3. When asked, choose _Create Credentials_ and select the **API Key** type. ([Credentials page](https://console.developers.google.com/apis/credentials))

```bash
youtube2zim --api-key "<your-api-key>" --type user --id "Vsauce"
```

## Notes

* Your API_KEY is subject to usage quotas (10,000 requests/day) so use `--only_test_branding` when adjusting parameters and branding to not *waste your quota*.
* On macOS, the locale setting is buggy. You need to launch it with `LANGUAGE` environment variable (as ISO-639-1) for the translations to work.

```bash
LANGUAGE=fr youtube2zim --language fra
```

Development
-----------

Before contributing be sure to check out the
[CONTRIBUTING.md](CONTRIBUTING.md) guidelines.

License
-------

[GPLv3](https://www.gnu.org/licenses/gpl-3.0) or later, see
[LICENSE](LICENSE) for more details.