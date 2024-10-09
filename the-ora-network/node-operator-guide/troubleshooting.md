---
description: Common Issues
---

# Troubleshooting

## General&#x20;

* Make sure you have downloaded the latest version of the Tora client: [https://github.com/ora-io/tora-electron-releases/releases/](https://github.com/ora-io/tora-electron-releases/releases/).
* Make sure you have the official installation of [docker](https://www.docker.com/).

## Issues

<details>

<summary>The App freezes whilst installing the desktop Tora Node</summary>

To resolve this issue try following:

1. rm -rf \~/.ora
2. run: `docker-compose up -d`

</details>

<details>

<summary>WARNING[XFORMERS]: xFormers can't load C++/CUDA extensions.</summary>

To resolve this issue:

1. Remove existing Tora Node docker images
2. Pull new version of docker images
3. Run the node again

</details>
